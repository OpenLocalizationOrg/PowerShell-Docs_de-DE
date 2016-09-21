# Konfigurieren der lokalen Konfigurations-Manager

> Gilt für: Windows PowerShell 5.0

Die lokale Konfigurations-Manager (KGV) ist das Modul für Windows PowerShell gewünscht Bundesstaat Konfiguration (DSC). Die KGV auf den einzelnen Zielknoten ausgeführt wird, und ist verantwortlich für die Analyse und Umsetzung Konfigurationen, die auf den Knoten gesendet werden. Es ist auch für eine Reihe von anderen Aspekten der DSC, einschließlich der folgenden verantwortlich ist.

* Bestimmen Aktualisierungsmodus (Pushbenachrichtigungen oder Abruf).
* Angeben, wie oft ein Knoten abruft und setzt Konfigurationen um.
* Zuweisen des Knotens zu Abruf-Servern an.
* Angeben von teilweise Konfigurationen.

Sie verwenden eine spezielle Art der Konfiguration zum Konfigurieren der KGV um jedes dieser Verhalten anzugeben. In den folgenden Abschnitten wird beschrieben, wie die KGV konfigurieren.

> **Hinweis**: Dieses Thema bezieht sich auf die KGV in Windows PowerShell 5.0 eingeführt werden. Informationen zum Konfigurieren der KGV in Windows PowerShell 4.0 finden Sie unter Windows PowerShell 4.0 gewünscht Bundesstaat Konfiguration lokale Konfigurations-Manager.

## Schreiben und Umsetzung einer KGV Konfigurations

Zum Konfigurieren der KGV erstellen und eine spezielle Art von Konfiguration ausführen. Um eine KGV Konfiguration angeben möchten, verwenden Sie das Attribut DscLocalConfigurationManager. Die nachstehende Abbildung zeigt eine einfache Konfiguration, die die KGV auf Pushbenachrichtigungen Modus festlegt.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
} 
```

Sie anrufen, und führen Sie die Konfiguration zum Erstellen der Konfigurations MOF, wie eine normale Konfiguration (Informationen zum Erstellen der Konfigurations MOF finden Sie unter Erste Schritte mit Windows PowerShell gewünscht Zustand Konfiguration). Anders als bei normaler möchten Sie eine KGV Konfiguration nicht widersprechenden, indem Sie das Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) . Rufen Sie stattdessen das Cmdlet Set-DscLocalConfigurationManager den Pfad für die Konfiguration MOF als Parameter angeben. Nachdem Sie die Konfiguration widersprechenden, können Sie die Eigenschaften der KGV, indem Sie das Cmdlet " [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) " anzeigen.

Eine KGV Konfiguration kann nur für eine begrenzte Anzahl von Ressourcen Blöcke enthalten. Im vorherigen Beispiel ist die einzige Ressource mit dem Namen **Einstellungen**. Die anderen verfügbaren Ressourcen eingesetzt werden:

* **ConfigurationRepositoryWeb**: Gibt einen HTTP-Abruf Server für Konfigurationen. 
* **ConfigurationRepositoryShare**: Gibt einen SMB Abruf Server für Konfigurationen.
* **ResourceRepositoryWeb**: Gibt einen HTTP-Abruf Server für Module.
* **ResourceRepositoryShare**: Gibt einen SMB Abruf Server für Module.
* **ReportServerWeb**: Gibt einen HTTP-Abruf-Server an die Berichte gesendet werden.
* **PartialConfiguration**: Gibt die teilweise Konfigurationen an.

## Grundlegende Einstellungen

Als Abruf Servers und teilweise Konfigurationen angeben, werden alle Eigenschaften von der KGV in einen Textblock **Einstellungen** konfiguriert. Die folgenden Eigenschaften stehen in einen Textblock **Einstellungen** .

|  Eigenschaft  |  Typ  |  Beschreibung   | 
|--- |--- |---| 
| ConfigurationModeFrequencyMins| UInt32| Wie häufig in Minuten, die aktuelle Konfiguration aktiviert und angewendet wird. Wenn die Eigenschaft für ConfigurationMode den ApplyOnly festgelegt ist, wird diese Eigenschaft ignoriert. Der Standardwert ist 15. __Hinweis__: entweder der Wert dieser Eigenschaft muss ein Vielfaches von den Wert der Eigenschaft __RefreshFrequencyMins__ oder der Wert der Eigenschaft __RefreshFrequencyMins__ muss ein Vielfaches von den Wert dieser Eigenschaft.| 
| RebootNodeIfNeeded| bool| Legen Sie den Wert __$true__ automatisch den Knoten nach einer Konfiguration neu gestartet, die erfordert einen Neustart wird angewendet. Andernfalls müssen Sie manuell den Knoten für jede Konfiguration neu zu starten, die dies erforderlich macht. Der Standardwert ist __$false__.| 
| ConfigurationMode| Zeichenfolge | Gibt an, wie die KGV tatsächlich die Konfiguration auf die Zielknoten angewendet wird. Dauert die folgenden Werte: __"ApplyOnly"__: DSC gilt für die Konfiguration und unterstützt keine weiteren, es sei denn, eine neue Konfiguration abgelegt wird die Zielknoten oder eine neue Konfiguration von einem Server gezogen wird. Nach der anfänglichen Anwendung einer neuen Konfiguration überprüft DSC nicht für Drift aus einem zuvor konfiguriert Zustand. __"ApplyAndMonitor"__: Dies ist der Standardwert. Die KGV gilt für alle neuen Konfigurationen. Nach dem ersten Anwendung einer neuen Konfiguration, wenn der Zielknoten in der gewünschten Status zu driftet DSC Berichte der Differenz in Protokolle __"ApplyAndAutoCorrect"__: DSC gilt für alle neuen Konfigurationen. Nach der anfänglichen Anwendung einer neuen Konfiguration Wenn der Zielknoten in der gewünschten Status zu driftet DSC Berichte der Abweichung in Protokollen und wendet die aktuelle Konfiguration erneut.| 
| ActionAfterReboot| Zeichenfolge| Gibt an, was bei der Anwendung einer Konfiguration nach einem Neustart geschieht. Die möglichen Werte sind wie folgt: __"ContuinueConfiguration"__: Anwenden der aktuellen Konfigurations fortsetzen. __"StopConfiguraiton"__: die aktuelle Konfiguration beenden.| 
| RefreshMode| Zeichenfolge| Gibt an, wie die KGV Konfigurationen erhält. Die möglichen Werte sind wie folgt: __"Deaktiviert"__: DSC Konfigurationen für diesen Knoten deaktiviert werden. __"Pushbenachrichtigungen"__: Konfigurationen, indem Sie das Cmdlet Start-DscConfiguration initiiert werden. Die Konfiguration wird sofort auf den Knoten angewendet. Dies ist der Standardwert. __Extrahieren:__ Der Knoten ist für Konfigurationen von einem Server Abruf regelmäßig konfiguriert. Wenn diese Eigenschaft auf Abruf festgelegt ist, müssen Sie einen Server Abruf in einen Textblock __ConfigurationRepositoryWeb__ oder __ConfigurationRepositoryShare__ angeben. Weitere Informationen zu Abruf-Servern finden Sie unter [Einrichten einer DSC fehl](pullServer.md).| 
| CertificateID| Zeichenfolge| Eine GUID, ein Zertifikat verwendet, um die Anmeldeinformationen für den Zugriff auf die Konfiguration secure angibt. Weitere Informationen finden Sie unter ? [Anmeldeinformationen in Windows PowerShell gewünscht Zustand Konfiguration schützen möchten](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).| 
| ConfigurationID| Zeichenfolge| Eine GUID, Konfigurationsdatei zum Abrufen von einem Server Abruf im Modus Abruf identifiziert. Ziehen Sie der Knoten wird Server Konfigurationen auf dem Abrufen, wenn Sie der Namen der Konfiguration MOF ConfigurationID.mof benannt wird. __Hinweis:__ Wenn Sie diese Eigenschaft, Registrieren des Knotens mit einem Abruf Server mit __RegistryKeys__ und nicht funktioniert. Weitere Informationen finden Sie unter [Einrichten einer Abruf Client mit Konfigurationsnamen](pullClientConfigNames.md).| 
| RefreshFrequencyMins| UInt32| Das Zeitintervall in Minuten, an denen die KGV einer fehl, um aktualisierte Konfigurationen erhalten überprüft werden soll. Dieser Wert wird ignoriert, wenn die KGV in Abruf Modus konfiguriert ist. Der Standardwert ist 30. __Hinweis:__  Entweder der Wert dieser Eigenschaft muss ein Vielfaches von den Wert der Eigenschaft __ConfigurationModeFrequencyMins__ oder der Wert der Eigenschaft __ConfigurationModeFrequencyMins__ muss ein Vielfaches von den Wert dieser Eigenschaft.| 
| AllowModlueOverwrite| bool| __$TRUE__ Wenn neue Konfigurationen vom Konfigurationsserver heruntergeladen dürfen den alten auf die Zielknoten überschrieben. Andernfalls, $FALSE.| 
| Debug-Modus| bool| Wenn __$TRUE__festgelegt, dies der KGV DSC Ressourcen, erneut laden verursacht, auch wenn zuvor zwischengespeichert wurden. Festlegen Sie auf $FALSE zwischengespeicherte Ressourcen verwendet. In der Regel würden Sie diese Eigenschaft auf __$TRUE__ beim Debuggen einer Ressource und auf __$FALSE__ für Herstellung setzen. Der Standardwert ist __$FALSE__.| 
| ConfigurationDownloadManagers| CimInstance]| Veraltete. Verwenden Sie __ConfigurationRepositoryWeb__ und __ConfigurationRepositoryShare__ Blöcke Konfiguration Abruf Servern definiert.| 
| ResourceModuleManagers| CimInstance]| Veraltete. Verwenden Sie __ResourceRepositoryWeb__ und __ResourceRepositoryShare__ Blöcke zum Definieren von Ressourcen abrufen Servern.| 
| ReportManagers| CimInstance]| Veraltete. Verwenden Sie __ReportServerWeb__ Blöcke zum Abruf Berichtsservern definieren.| 
| PartialConfigurations| CimInstance| Nicht implementiert. Verwenden Sie nicht.| 
| StatusRetentionTimeInDays | UInt32| Die Anzahl der Tage, die die KGV den Status der aktuellen Konfiguration hält.| 

## Ziehen Sie servers

Ein Server Abruf ist entweder einen OData-Webdienst oder eine SMB freigeben, die als zentrale für DSC Dateien verwendet wird. KGV Konfiguration unterstützt die folgenden Arten von Abruf Servern definieren:

* **Konfigurations-Server**: ein Repository für DSC Konfigurationen. Definieren Konfiguration trennt mithilfe von **ConfigurationRepositoryWeb** (für webbasierte Server) und **ConfigurationRepositoryShare** (für SMB-basierten Server) blockiert.
* Ressourcenserver – ein Repository für DSC Ressourcen, die als PowerShell-Module verpackt. Definieren von Ressourcen mithilfe von **ResourceRepositoryWeb** (für webbasierte Server) und **ResourceRepositoryShare** (für SMB-basierten Server) Blöcke trennt.
* Berichtsserver – ein Dienst, der DSC Berichtdaten sendet. Definieren Sie Berichtsservern mithilfe von Bausteinen **ReportServerWeb** . Ein Berichtsserver muss einem Webdienst.

Informationen zum Einrichten und Verwenden von Abruf-Servern finden Sie unter [Einrichten einer DSC fehl](pullServer.md).

## Konfiguration Server Blöcke

Definieren einer webbasierten Konfigurations Server, erstellen Sie einen Block **ConfigurationRepositoryWeb** . Eine **ConfigurationRepositoryWeb** definiert die folgenden Eigenschaften.

|Eigenschaft|Typ|Beschreibung|
|---|---|---| 
|AllowUnsecureConnection|bool|Klicken Sie auf **$TRUE** festgelegt, aus dem Knoten Verbindungen, auf dem Server ohne Authentifizierung zulässt. Legen Sie **$FALSE** um Authentifizierung erforderlich ist.|
|CertificateID|Zeichenfolge|Eine GUID, die das Zertifikat zum Authentifizieren auf dem Server darstellt.|
|ConfigurationNames|String]|Ein Array von Namen von Konfigurationen vornehmen, um durch die Zielknoten abgerufen werden. Diese werden nur, wenn der Knoten mit dem Server Abruf registriert ist, mithilfe einer **RegistrationKey**verwendet. Weitere Informationen finden Sie unter [Einrichten einer Abruf Client mit Konfigurationsnamen](pullClientConfigNames.md).|
|RegistrationKey|Zeichenfolge|Eine GUID, die den Knoten mit dem Server Abruf registriert. Weitere Informationen finden Sie unter [Einrichten einer Abruf Client mit Konfigurationsnamen](pullClientConfigNames.md).|
|Server-URL|Zeichenfolge|Die URL des Servers Konfiguration.|

Um eine SMB-basierten Konfigurationsserver zu definieren, erstellen Sie einen Block **ConfigurationRepositoryShare** . Eine **ConfigurationRepositoryShare** definiert die folgenden Eigenschaften.

|Eigenschaft|Typ|Beschreibung|
|---|---|---|
|Anmeldeinformationen|MSFT_Credential|Die Anmeldeinformationen für die Freigabe SMB Authentifizierung verwendet.|
|SourcePath|Zeichenfolge|Der Pfad der Freigabe SMB.|

## Ressource Server Blöcke

Definieren eine Ressource webbasierten Server, erstellen Sie einen Block **ResourceRepositoryWeb** . Einer **ResourceRepositoryWeb** definiert die folgenden Eigenschaften.

|Eigenschaft|Typ|Beschreibung|
|---|---|---|
|AllowUnsecureConnection|bool|Klicken Sie auf **$TRUE** festgelegt, aus dem Knoten Verbindungen, auf dem Server ohne Authentifizierung zulässt. Legen Sie **$FALSE** um Authentifizierung erforderlich ist.|
|CertificateID|Zeichenfolge|Eine GUID, die das Zertifikat zum Authentifizieren auf dem Server darstellt.|
|RegistrationKey|Zeichenfolge|Eine GUID, die den Knoten zum Abruf Server identifiziert. Weitere Informationen finden Sie unter einem Knoten mit einem DSC Abruf Server registrieren.|
|Server-URL|Zeichenfolge|Die URL des Servers Konfiguration.|
 
Um eine SMB-basierten Ressourcenserver zu definieren, erstellen Sie einen Block **ResourceRepositoryShare** . **ResourceRepositoryShare** definiert die folgenden Eigenschaften.

|Eigenschaft|Typ|Beschreibung|
|---|---|---|
|Anmeldeinformationen|MSFT_Credential|Die Anmeldeinformationen für die Freigabe SMB Authentifizierung verwendet.|
|SourcePath|Zeichenfolge|Der Pfad der Freigabe SMB.|

## Bericht Server Blöcke

Ein Berichtsserver muss einen OData-Webdienst. Um einen Berichtsserver zu definieren, erstellen Sie einen Block **ReportServerWeb** . **ReportServerWeb** definiert die folgenden Eigenschaften.

|Eigenschaft|Typ|Beschreibung|
|---|---|---| 
|AllowUnsecureConnection|bool|Klicken Sie auf **$TRUE** festgelegt, aus dem Knoten Verbindungen, auf dem Server ohne Authentifizierung zulässt. Legen Sie **$FALSE** um Authentifizierung erforderlich ist.|
|CertificateID|Zeichenfolge|Eine GUID, die das Zertifikat zum Authentifizieren auf dem Server darstellt.|
|RegistrationKey|Zeichenfolge|Eine GUID, die den Knoten zum Abruf Server identifiziert. Weitere Informationen finden Sie unter einem Knoten mit einem DSC Abruf Server registrieren.|
|Server-URL|Zeichenfolge|Die URL des Servers Konfiguration.|

## Teilweise Konfigurationen

Um teilweise Konfigurationen zu definieren, erstellen Sie einen Block **PartialConfiguration** . Weitere Informationen zu teilweise Konfigurationen finden Sie unter [DSC teilweise Konfigurationen](partialConfigs.md). **PartialConfiguration** definiert die folgenden Eigenschaften.

|Eigenschaft|Typ|Beschreibung|
|---|---|---| 
|ConfigurationSource|String]|Ein Array von Namen der Konfiguration, zuvor definierten in **ConfiguratoinRepositoryWeb** und **ConfigurationRepositoryShare** Blöcke, wo die teilweise Konfiguration vom gezogen wird.|
|DependsOn|Zeichenfolge: {}|Eine Liste der Namen weiterer Konfigurationen an, die abgeschlossen sein müssen, bevor diese teilweise Konfiguration angewendet wird.|
|Beschreibung|Zeichenfolge|Text verwendet, um die teilweise Konfiguration beschrieben.|
|ExclusiveResources|String]|Ein Array von Ressourcen ausschließlich auf diese teilweise Konfiguration.|
|RefreshMode|Zeichenfolge|Gibt an, wie diese teilweise Konfiguration von DCS ruft... Mögliche Werte sind wie folgt: **deaktiviert**: Diese teilweise Konfiguration deaktiviert ist. **Pushbenachrichtigungen**: die teilweise Konfiguration wird auf den Knoten, indem Sie das Cmdlet [Veröffentlichen-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) abgelegt. Nachdem alle teilweise Konfigurationen für den Knoten entweder abgelegt oder von einem Server wurden, kann die Konfiguration eingeleiteten Aufrufen `Start-DscConfiguration –UseExisting`. Dies ist der Standardwert. **Abruf**: der Knoten ist so konfiguriert, dass Sie regelmäßig prüfen, ob die teilweise Konfiguration von einem Server abrufen. Wenn diese Eigenschaft auf "Abrufen" festgelegt ist, müssen Sie einen Server Abruf durch Festlegen der Eigenschaft **ConfigurationSource** angeben. Weitere Informationen zu Abruf-Servern finden Sie unter [Einrichten einer DSC fehl](pullServer.md).|
|ResourceModlueSource|String]|Ein Array von die Namen der Ressourcenserver erforderliche Ressourcen für diese teilweise Konfiguration download von. Diese Namen müssen auf Ressourcenservern zuvor definiert **ResourceRepositoryWeb** und **ResourceRepositoryShare** Blöcke verweisen.|

## Siehe auch 

### Konzepte
Erste Schritte mit Windows PowerShell gewünscht Zustand Konfiguration [Einrichten eines DSC Abruf Servers](pullServer.md) 
[Windows PowerShell 4.0 gewünscht Zustand Konfiguration lokale Konfigurations-Manager](metaConfig4.md) 

### Weitere Ressourcen
[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) 
[Einstellung Abruf Client für den Konfigurationsnamen](pullClientConfigNames.md) 
