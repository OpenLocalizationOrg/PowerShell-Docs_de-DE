# Einrichten eines mithilfe des Konfigurations-ID in PowerShell 4.0 Abruf-Clients

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Jeder Zielknoten muss werden angewiesen, Abruf-Modus verwenden und anhand der URL, in dem die erste Konfigurationen fehl kontaktieren kann. Dazu müssen Sie die lokale Konfigurations-Manager (KGV) mit den erforderlichen Informationen zu konfigurieren. Um die KGV zu konfigurieren, erstellen Sie eine spezielle Art der Konfiguration als ein "Metaconfiguration" bezeichnet. Weitere Informationen zum Konfigurieren der KGV finden Sie unter [Windows PowerShell 4.0 gewünscht Zustand Konfiguration lokale Konfigurations-Manager](metaConfig4.md)

Das folgende Skript konfiguriert das KGV Abruf Konfigurationen von einem Server mit dem Namen "PullServer".

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 15;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

Klicken Sie im Skript **DownloadManagerCustomData** übergibt die URL des Servers abrufen und (in diesem Beispiel) eine ungeschützte Verbindung ermöglicht. 

Nach der Ausführung dieser Skripts, erstellt einen neue Ausgabeordner mit dem Namen **SimpleMetaConfigurationForPull** und eine Metaconfiguration MOF-Datei es verschoben.

Verwenden Sie **Set-DscLocalConfigurationManager** mit den Parametern für **ComputerName** (verwenden Sie "Localhost") und **Pfad** (den Pfad zum Speicherort der Datei für die Zielknoten localhost.meta.mof) aus, um die Konfiguration anzuwenden. Beispiel: 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## Konfigurations-ID
Das Skript legt das KGV die Eigenschaft **ConfigurationID** auf eine GUID, die zuvor für diesen Zweck erstellten (Sie können eine GUID erstellen Sie mithilfe des Cmdlets **New-Guid** ). Die **ConfigurationID** ist, was das KGV verwendet, um die entsprechende Konfiguration auf dem Server Abruf zu finden. Die Konfiguration MOF-Datei auf dem Server abrufen muss den Namen `ConfigurationID.mof`, wobei *ConfigurationID* den Wert der Eigenschaft **ConfigurationID** von der Zielknoten KGV ist.
