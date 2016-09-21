# Konfiguration des PowerShell gewünscht teilweise Konfigurationen Test Abhängigkeit

>Gilt für: Windows PowerShell 5.0

In PowerShell-5.0 ermöglicht gewünscht Bundesstaat Konfiguration (DSC) Konfigurationen Fragmente und aus mehreren Quellen übermittelt werden konnte. Die lokale Konfiguration Manager (KGV) auf die Zielknoten verschoben die Fragmente zusammen bevor Sie diese als eine einzelne Konfiguration anwenden. Diese Funktion ermöglicht die Kontrolle über die Konfiguration zwischen Teams oder Personen freigeben. Beispielsweise, wenn zwei oder mehr Teams der Entwickler in einem Dienst zusammenarbeiten, möglicherweise sie jede Konfigurationen zum Verwalten von deren Bestandteil der Dienstleistung erstellen möchten. Jede dieser Konfigurationen konnte aus verschiedenen Abruf Servern abgerufen werden, und diese in verschiedenen Phasen einer Entwicklung hinzugefügt werden konnte. Teilweise Konfigurationen zulassen auch an unterschiedliche Personen oder Teams steuern verschiedene Aspekte des Knoten konfigurieren, ohne das Bearbeiten eines Dokuments Konfiguration für einzelne koordinieren. Ein Team möglicherweise z. B. verantwortlich für die Bereitstellung von einer virtuellen Computer und Betriebssystem, während ein anderes Team möglicherweise von anderen Anwendungen und Dienste auf diesen virtuellen Computer bereitstellen. Mit teilweise Konfigurationen kann jedes Team die eigene Konfiguration, ohne eine von ihnen gerade unnötig kompliziert erstellen.

Teilweise Konfigurationen in Pushbenachrichtigungen Modus, Abruf Modus oder eine Kombination aus beiden können.

## Teilweise Konfigurationen im Modus für Pushbenachrichtigungen
Um teilweise Konfigurationen in Pushbenachrichtigungen Modus zu verwenden, konfigurieren Sie die KGV auf die Zielknoten die teilweisen Konfigurationen erhalten. Jede teilweise Konfiguration muss an die Zielwebsite mithilfe des Veröffentlichen-DSCConfiguration Cmdlets abgelegt werden. Der Zielknoten kombiniert dann die teilweise Konfiguration in eine einzelne, und wenden Sie die Konfiguration, indem Sie das Cmdlet [Start-DscConfigurationxt](https://technet.microsoft.com/en-us/library/dn521623.aspx) .

### Konfigurieren der KGV für teilweise Konfigurationen Pushbenachrichtigungen-Modus
Zum Konfigurieren der KGV für teilweise Konfigurationen im Modus für Pushbenachrichtigungen erstellen Sie eine **DSCLocalConfigurationManager** Konfiguration mit einer **PartialConfiguration** blockieren für jede teilweise Konfiguration aus. Weitere Informationen zum Konfigurieren der KGV finden Sie unter [Windows im Konfigurations-Manager für lokale konfigurieren](https://technet.microsoft.com/en-us/library/mt421188.aspx). Im folgenden Beispiel wird eine KGV-Konfiguration, die zwei teilweise Konfigurationen erwartet – eine, die das Betriebssystem bereitstellt, und die bereitstellen und Konfigurieren von SharePoint.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        
           PartialConfiguration OSInstall
        {
            Description = 'Configuration for the Base OS'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo 
```

Der **RefreshMode** für jede teilweise Konfiguration ist "Pushbenachrichtigungen" festgelegt. Die Namen der **PartialConfiguration** Blöcke (in diesem Fall "OSInstall" und "SharePointConfig") müssen genau die Namen der Konfigurationen übereinstimmen, die auf den Zielknoten abgelegt werden.

### Veröffentlichen und teilweise Konfigurationen Pushbenachrichtigungen-Modus starten
![PartialConfig-Ordnerstruktur](./images/Pull1.png)

Rufen Sie dann **Veröffentlichen-DSCConfiguration** für jede Konfiguration, übergeben die Ordner, die die Konfigurationsdokumente als die Parameter Pfad enthalten. Sie können nach der Veröffentlichung beide Konfigurationen, anrufen `Start-DSCConfiguration –UseExisting` auf dem Zielknoten.

## Teilweise Konfigurationen im Abruf Modus

Teilweise Konfigurationen können aus einem oder mehreren Abruf Servern herausgezogen werden (Weitere Informationen zu Abruf-Servern finden Sie unter [Windows PowerShell gewünscht Zustand Konfiguration Abruf-Servern](pullServer.md). Dazu müssen Sie die KGV auf dem Zielknoten, ziehen Sie die teilweisen Konfigurationen, und nennen Sie aus, und suchen Sie die Konfigurationsdokumente ordnungsgemäß auf den Servern Abruf konfigurieren.

### Konfigurieren der KGV für Abruf Knoten Konfigurationen

Um die KGV zum Extrahieren teilweiser Konfigurationen aus einem Abruf Server zu konfigurieren, definieren Sie den Abruf Server in einem **ConfigurationRepositoryWeb** (für eine HTTP-Abruf Server) oder **ConfigurationRepositoryShare** (für eine SMB Abruf Server) blockieren aus. Anschließend erstellen Sie **PartialConfiguration** Blöcke, die auf dem Server Abruf verweisen mithilfe der Eigenschaft **ConfigurationSource** . Sie müssen außerdem einen Textblock Einstellungen, um anzugeben, dass die KGV Abruf Modus verwendet, und die ConfigurationID angeben, die fehl und die Zielknoten verwenden, identifizieren Sie die Konfigurationen, erstellen. Die folgende Metatag-Konfiguration definiert HTTP-Abruf Server mit dem Namen ' CONTOSO-PullSrv, und ziehen Sie zwei teilweise Konfigurationen, mit denen die Server.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
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
        
           PartialConfiguration OSInstall
        {
            Description = 'Configuration for the Base OS'
            ConfigurationSource = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the Sharepoint Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn = [PartialConfiguration]OSInstall
            RefreshMode = 'Pull'
        }
    }
}
PartialConfigDemo 
```

Sie können die teilweise Konfigurationen von mehr als einem Abruf Server herauszuziehen – einfach müssten definieren jedes fehl, und klicken Sie dann auf dem Server entsprechenden Abruf in jedem Block PartialConfiguration verweisen.

Nach dem Erstellen der Metatag-Konfigurations, müssen Sie es zum Erstellen eines Dokuments Konfiguration (eine MOF-Datei), und rufen Sie dann auf [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) zum Konfigurieren der KGV ausführen.

### Benennen und wobei die Konfigurationsdokumente auf dem Server abrufen

Teilweise Konfigurationsdokumente in den Ordner, in den **ConfigurationPath** festgelegte platziert werden müssen die `web.config` Datei für den Abruf Server (in der Regel `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Die Konfigurationsdokumente müssen den Namen wie folgt: _ConfigurationName_. _ConfigurationID_`.mof`, wobei _ConfigurationName_ der Name der teilweise Konfiguration ist und _ConfigurationID_ die Konfigurations-ID in der KGV auf dem Zielknoten definiert. Unsere beispielsweise sollten die Konfigurationsdokumente Namen wie folgt.
![PartialConfig Namen auf fehl](images/Pull1.png)

### Teilweise Konfigurationen aus einem Abruf Server ausgeführt

Nach der KGV auf dem Zielknoten konfiguriert wurde, und die Konfigurationsdokumente erstellt und auf dem Server Abruf ordnungsgemäß benannt wurden, werden der Zielknoten ziehen Sie die teilweisen Konfigurationen, kombinieren Sie sie, und wenden Sie die resultierende Konfiguration in regelmäßigen Abständen gemäß der Eigenschaft **RefreshFrequencyMins** der KGV. Wenn Sie eine Aktualisierung zu erzwingen möchten, können Sie das Cmdlet Update-DscConfiguration aus, um die möchten, ziehen Sie anrufen und `Start-DSCConfiguration –UseExisting` sie angewendet.

## Teilweise Konfigurationen in gemischten Modi für Pushbenachrichtigungen fest, und ziehen

Sie können auch Pushbenachrichtigungen mischen klicken und ziehen Modi für teilweise Konfigurationen. D. h., haben Sie eine teilweise Konfiguration, die gezogen wird von einem Server abrufen, während eine andere teilweise Konfiguration abgelegt wird. Behandeln Sie jede teilweise Konfiguration, wie Sie vorgehen, je nach den Aktualisierungsmodus in den vorherigen Abschnitten beschriebenen. Beispielsweise werden die folgende Metatag-Konfiguration das gleiche Beispiel, mit der Konfiguration des Betriebssystems teilweise im Modus Abruf und die teilweise SharePoint-Konfiguration im Modus für Pushbenachrichtigungen.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
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
        
           PartialConfiguration OSInstall
        {
            Description = 'Configuration for the Base OS'
            ConfigurationSource = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the Sharepoint Server'
            DependsOn = [PartialConfiguration]OSInstall
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo 
```

Beachten Sie, dass der **RefreshMode** in den Einstellungen Block angegeben ist "Extrahieren", aber die **RefreshMode** für die teilweise OSInstall-Konfiguration "Pushbenachrichtigungen" ein.

Sie benennen, und suchen Sie nach der Konfigurationsdokumente für ihre jeweiligen aktualisieren Modi wie oben beschrieben. Möchten Sie **Veröffentlichen-DSCConfiguration** , um die SharePointInstall teilweise Konfiguration veröffentlichen aufrufen und entweder warten, bis die OSInstall-Konfiguration aus den Abruf Server oder Erzwingen einer Aktualisierung bereitstehen, indem Sie die [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).

##Siehe auch 

**Konzepte**
[Windows PowerShell gewünscht staatliche Konfiguration herauszuziehen Servern](pullServer.md) 
[Windows konfigurieren die lokale Konfigurations-Manager](https://technet.microsoft.com/en-us/library/mt421188.aspx) 
