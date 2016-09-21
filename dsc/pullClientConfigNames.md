# Einrichten eines mit Konfigurationsnamen Abruf-Clients

> Gilt für: Windows PowerShell 5.0

Jeder Zielknoten muss werden angewiesen, Abruf-Modus verwenden und anhand der URL, in dem die erste Konfigurationen fehl kontaktieren kann. Dazu müssen Sie die lokale Konfigurations-Manager (KGV) mit den erforderlichen Informationen zu konfigurieren. Um die KGV zu konfigurieren, erstellen Sie eine spezielle Art der Konfiguration, mit dem Attribut **DSCLocalConfigurationManager** versehen. Weitere Informationen zum Konfigurieren der KGV finden Sie unter [Konfigurieren der lokalen Konfigurations-Manager](metaConfig.md).

> **Hinweis**: Dieses Thema gilt für PowerShell 5.0. Informationen zum Einrichten von Clients Abruf bei der PowerShell 4.0 finden Sie unter [Einrichten eines Abruf Client-Konfigurations-ID in der PowerShell 4.0 verwenden](pullClientConfigID4.md)

Das folgende Skript konfiguriert das KGV Abruf Konfigurationen von einem Server mit dem Namen "CONTOSO-PullSrv":

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

Im Skript definiert des Zeitraums **ConfigurationRepositoryWeb** der fehl. Die **Server-URL** -Eigenschaft gibt den Endpunkt für den Abruf Server an.

Die Eigenschaft **RegistrationKey** ist ein gemeinsamer Schlüssel zwischen alle Client-Knoten für einen Server abrufen und diese fehl. Der gleiche Wert wird in einer Datei auf dem Server Abruf gespeichert. Die Eigenschaft **ConfigurationNames** gibt den Namen der Konfiguration, die für den Clientknoten an. Auf dem Server abrufen muss der MOF für diesen Clientknoten *ConfigurationNames*.mof, Name der Konfigurationsdatei, bei denen *ConfigurationNames* den Wert der Eigenschaft **ConfigurationNames** übereinstimmt, die Sie in dieser Metaconfiguration festlegen.

Nach der Ausführung dieser Skripts, erstellt einen neue Ausgabeordner mit dem Namen **PullClientConfigID** und eine Metaconfiguration MOF-Datei es verschoben. In diesem Fall die Metaconfiguration MOF-Datei erhält den Namen `localhost.meta.mof`.

Rufen Sie zum Anwenden der Konfigurations des Cmdlets **Set-DscLocalConfigurationManager** durch den **Pfad** zu dem Speicherort der Metaconfiguration MOF-Datei festlegen. Beispiel: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> **Hinweis**: Registrierungsschlüssel funktionieren nur mit Abruf-Webservern. Sie müssen weiterhin **ConfigurationID** mit einem SMB Abruf Server verwenden. Informationen zum Konfigurieren von einem Abruf Server mit **ConfigurationID**finden Sie unter [Einrichten eines Abruf-Clients mithilfe des Konfigurations-ID](pullClientConfigID.md)

## Ressourcen- und Berichts-servers

Standardmäßig erhält Client-Knotens erforderlichen Ressourcen aus und Berichte Status Konfiguration Abruf Server an. Allerdings können Sie verschiedene Abruf Servern für Ressourcen und-Berichte angeben.
Um eine Ressourcenserver angeben möchten, verwenden Sie entweder eine **ResourceRepositoryWeb** (für einen Webserver Abruf) oder einen Textblock **ResourceRepositoryShare** (für eine SMB Abruf Server) an.
Wenn Sie einen Berichtsserver angeben möchten, verwenden Sie einen Block **ReportRepositoryWeb** . Ein Berichtsserver einen SMB-Server nicht möglich.
Die folgenden Metaconfiguration konfiguriert einen Abruf Client, deren Konfigurationen von **CONTOSO-PullSrv** und seine Ressourcen von **CONTOSO-ResourceSrv**und Statusberichte an **CONTOSO-ReportSrv**senden:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## Siehe auch

* [Einrichten eines Clients Abruf mit Konfigurations-ID](pullClientConfigID.md)
* [Einrichten eines DSC Abruf Webservers](pullServer.md)
