# Windows PowerShell 4.0 gewünscht staatliche Konfiguration lokale Konfigurations-Manager (KGV)

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Lokale Konfigurations-Manager ist das Modul für Windows PowerShell gewünscht Zustand Konfiguration (DSC). Es auf allen Zielknoten ausgeführt wird, und ist verantwortlich für das Anrufen von der Konfigurationsressourcen, die in einem DSC Konfigurationsskript enthalten sind. Dieses Thema listet die Eigenschaften der lokalen Konfigurations-Manager und beschreibt, wie Sie die lokale Konfigurations-Manager-Einstellungen auf einem Zielknoten ändern können.

## Konfigurations-Manager für lokale Eigenschaften
Im folgenden werden die lokale Konfigurations-Manager-Eigenschaften, die Sie festlegen oder abrufen können.
 
* **AllowModuleOverwrite**: Steuerelemente, ob neue Konfigurationen vom Konfigurationsserver heruntergeladen darf den alten auf dem Zielknoten überschrieben werden. Mögliche Werte sind wahr und falsch.
* **CertificateID**: GUID ein Zertifikat zum Sichern von Anmeldeinformationen für den Zugriff auf die Konfiguration verwendet. Weitere Informationen finden Sie unter [Anmeldeinformationen in Windows PowerShell gewünscht Zustand Konfiguration sichern möchten?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
* **ConfigurationID**: Gibt eine GUID die zum Abrufen von einer bestimmten Konfigurationsdatei von einem Server eingerichtet werden als "fehl" verwendet wird. Die GUID wird sichergestellt, dass die richtige Konfigurationsdatei zugegriffen wird.
* **ConfigurationMode**: Gibt an, wie im Konfigurations-Manager für lokale tatsächlich die Konfiguration die Zielknoten gilt. Sie können die folgenden Werte ausführen:
    - **ApplyOnly**: mit dieser Option DSC gilt für die Konfiguration und unterstützt keine weiteren, es sei denn, eine neue Konfiguration erkannt wird, entweder von Ihnen senden eine neue Konfiguration direkt an die Zielwebsite Knoten ("Pushbenachrichtigungen"), oder wenn Sie einen Server "extrahieren" und DSC konfiguriert haben erkennt eine neue Konfiguration, wenn sie mit dem Server "Abruf" überprüft. Wenn die Zielknoten Konfiguration wandert ab, wird keine Aktion ausgeführt.
    - **ApplyAndMonitor**: mit dieser Option (der Standard) DSC gilt alle neuen Konfigurationen, ob die von Ihnen direkt an den Zielknoten gesendet oder auf einem Server "Abruf" erkannt. Wenn die Konfiguration des Knotens Ziel aus der Konfigurationsdatei wandert ab, Berichte DSC danach die Abweichung in Protokollen auf. Weitere Informationen zur Protokollierung DSC finden Sie unter [mithilfe von Ereignisprotokollen zum Diagnostizieren von Fehlern gewünscht Zustand Konfiguration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
    - **ApplyAndAutoCorrect**: mit dieser Option DSC gilt für alle neuen Konfigurationen, ob die von Ihnen direkt an den Zielknoten gesendet oder auf einem Server "Abruf" erkannt. Danach, wenn die Konfiguration des Knotens Ziel aus der Konfigurationsdatei wandert ab, DSC Berichte der Differenz in Protokolle, und klicken Sie dann versucht, passen Sie die Konfiguration der Ziel-Knoten in Übereinstimmung mit der Konfigurationsdatei bringen.
* **ConfigurationModeFrequencyMins**: die Häufigkeit (in Minuten), die Anwendung Hintergrund der DSC versucht implementieren die aktuelle Konfiguration auf dem Zielknoten, darstellt. Der Standardwert ist 15. Dieser Wert kann in Verbindung mit RefreshMode festgelegt werden. Wenn RefreshMode Abruf festgelegt ist, wird der Zielknoten Kontakte den Konfigurationsserver ein Intervall von RefreshFrequencyMins festgelegt und downloads für die aktuelle Konfiguration. Unabhängig von der Wert RefreshMode gilt in das Intervall, indem ConfigurationModeFrequencyMins, die Konsistenz-Engine die neueste Konfiguration, die in die Zielknoten heruntergeladen wurde. RefreshFrequencyMins auf eine ganze Zahl festgelegt werden Vielfache von ConfigurationModeFrequencyMins.
* **Anmeldeinformationen**: Zeigt an, Anmeldeinformationen (mit Get-Credential) remote Zugriff auf Ressourcen, beispielsweise in Verbindung mit dem Konfigurationsserver erforderlich.
* **DownloadManagerCustomData**: darstellt eine Matrix zurück, die speziell für den Downloadmanager benutzerdefinierte Daten enthält.
* **DownloadManagerName**: Gibt den Namen der Konfiguration und Modul Download-Manager.
* **RebootNodeIfNeeded**: bestimmte Konfiguration Änderungen auf einem Zielknoten erforderlich sein neu gestartet werden, damit die Änderungen übernommen werden. Mit dem Wert **True**, dieser Eigenschaft den Knoten starten, sobald die Konfiguration wurde vollständig ohne Warnung gilt. Wenn **False** (der Standardwert), wird die Konfiguration abgeschlossen ist, aber der Knoten muss manuell neu gestartet werden damit die Änderungen wirksam werden.
* **RefreshFrequencyMins**: verwendet, wenn Sie einem Server "abrufen" eingerichtet haben. Stellt die Häufigkeit (in Minuten), lokale Konfigurations-Manager auf einen Server "abrufen" zum Herunterladen der aktuellen Konfigurations Kontakte. Dieser Wert kann in Verbindung mit ConfigurationModeFrequencyMins festgelegt werden. Wenn RefreshMode auf Abruf festgelegt wurde, wird der Zielknoten Kontakte "fehl" festlegen, indem Sie RefreshFrequencyMins Intervallen und downloads für die aktuelle Konfiguration. In dem Intervall ConfigurationModeFrequencyMins gilt für die Konsistenz-Engine klicken Sie dann auf die neueste Konfiguration, die zum Zielknoten heruntergeladen wurde. Wenn RefreshFrequencyMins nicht zu einer ganzen Zahl festgelegt ist Vielfache von ConfigurationModeFrequencyMins, das System wird aufgerundet werden kann. Der Standardwert ist 30.
* **RefreshMode**: Mögliche Werte sind, **Drücken Sie** (die Standardeinstellung), und **ziehen Sie**. In der Konfiguration "Pushbenachrichtigungen" müssen Sie eine Konfigurationsdatei auf den einzelnen Zielknoten Platzieren von jedem Clientcomputer. Im Modus "abrufen" müssen Sie festlegen, von einem Server "abrufen" für lokale-Konfigurations-Manager zu wenden Sie sich an die Dateien zugreifen.

### Beispiel für lokale Konfigurations-Manager-Einstellungen aktualisieren

Sie können die Einstellungen eines Knotens Ziel durch einen Textblock **LocalConfigurationManager** innerhalb der Knoten einschließlich in einem Konfigurationsskript blockieren Konfigurations-Manager für lokale aktualisieren, wie im folgenden Beispiel dargestellt.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullServer/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"  
```

Ausführen der Skripts im vorherigen Beispiel generiert eine MOF-Datei, die gibt an, und speichert die gewünschten Einstellungen. Wenn die Einstellungen anwenden möchten, können Sie Cmdlets **Set-DscLocalConfigurationManager** , wie im folgenden Beispiel dargestellt.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Hinweis**: für den Parameter **Pfad** Sie müssen den gleichen Pfad, den Sie für den Parameter **OutputPath** angegeben, wenn Sie die Konfiguration im vorherigen Beispiel aufgerufen angeben.

Um die aktuellen Einstellungen für lokale Konfigurations-Manager angezeigt wird, können Sie das Cmdlet " **Get-DscLocalConfigurationManager** " verwenden. Wenn Sie mit diesem Cmdlet ohne Parameter aufrufen, wird standardmäßig die lokale Konfigurations-Manager-Einstellungen für den Knoten Bezugsarten auf dem er ausgeführt. Wenn Sie einen anderen Knoten angeben möchten, verwenden Sie den Parameter **CimSession** mit diesem Cmdlet aus.