# Einrichten eines Abruf-Clients mithilfe des Konfigurations-ID

> Gilt für: Windows PowerShell 5.0

Jeder Zielknoten muss werden angewiesen, Abruf-Modus verwenden und anhand der URL, in dem die erste Konfigurationen fehl kontaktieren kann. Dazu müssen Sie die lokale Konfigurations-Manager (KGV) mit den erforderlichen Informationen zu konfigurieren. Um die KGV konfigurieren, erstellen Sie eine spezielle Art von Konfiguration, die mit dem Attribut **DSCLocalConfigurationManager** gedrosselt. Weitere Informationen zum Konfigurieren der KGV finden Sie unter [Konfigurieren der lokalen Konfigurations-Manager](metaConfig.md).

> **Hinweis**: Dieses Thema gilt für PowerShell 5.0. Informationen zum Einrichten von Clients Abruf bei der PowerShell 4.0 finden Sie unter [Einrichten eines Abruf Client-Konfigurations-ID in der PowerShell 4.0 verwenden](pullClientConfigID4.md)

Das folgende Skript konfiguriert die KGV Abruf Konfigurationen von einem Server mit dem Namen "CONTOSO-PullSrv".

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = 1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }      
    }
}
PullClientConfigID
```

Im Skript definiert des Zeitraums **ConfigurationRepositoryWeb** der fehl. Der **Server-URL**

Nach der Ausführung dieser Skripts, erstellt einen neue Ausgabeordner mit dem Namen **PullClientConfigID** und eine Metaconfiguration MOF-Datei es verschoben. In diesem Fall die Metaconfiguration MOF-Datei erhält den Namen `localhost.meta.mof`.

Rufen Sie zum Anwenden der Konfigurations des Cmdlets **Set-DscLocalConfigurationManager** durch den **Pfad** zu dem Speicherort der Metaconfiguration MOF-Datei festlegen. Beispiel: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## Konfigurations-ID

Das Skript legt die Eigenschaft **ConfigurationID** KGV auf eine GUID, die zuvor für diesen Zweck erstellten (Sie können eine GUID erstellen Sie mithilfe des Cmdlets **New-Guid** ). Die **ConfigurationID** ist, was das KGV verwendet, um die entsprechende Konfiguration auf dem Server Abruf zu finden. Die Konfiguration MOF-Datei auf dem Server abrufen muss _ConfigurationID_.mof, den Namen, in dem _ConfigurationID_ der Wert der Eigenschaft **ConfigurationID** von der Zielknoten KGV ist.

## SMB fehl

Um einen Client zum Abruf Konfigurationen aus einem SMB-Server eingerichtet haben, verwenden Sie einen Block **ConfigurationRepositoryShare** aus. In einem Block **ConfigurationRepositoryShare** Geben Sie den Pfad auf dem Server durch Festlegen der Eigenschaft **SourcePath** an. Die folgenden Metaconfiguration konfiguriert den Zielknoten aus einem SMB Abruf-Server mit dem Namen **SMBPullServer**abrufen.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## Ressourcen- und Berichts-servers

Standardmäßig erhält Client-Knotens erforderlichen Ressourcen aus und Berichte Status Konfiguration Abruf Server an. Allerdings können Sie verschiedene Abruf Servern für Ressourcen und-Berichte angeben.
Um eine Ressourcenserver angeben möchten, verwenden Sie entweder eine **ResourceRepositoryWeb** (für einen Webserver Abruf) oder einen Textblock **ResourceRepositoryShare** (für eine SMB Abruf Server) an.
Wenn Sie einen Berichtsserver angeben möchten, verwenden Sie einen Block **ReportRepositoryWeb** . Ein Berichtsserver einen SMB-Server nicht möglich.
Die folgenden Metaconfiguration konfiguriert einen Abruf Client, deren Konfigurationen von **CONTOSO-PullSrv** und seine Ressourcen von **CONTOSO-ResourceSrv**und Statusberichte an **CONTOSO-ReportSrv**senden.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
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

* [Einrichten eines Clients Abruf mit Konfigurationsnamen](pullClientConfigNames.md)