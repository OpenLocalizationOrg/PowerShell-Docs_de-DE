# Problembehandlung bei DSC222

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

In diesem Thema werden die Methoden zum Abrufen Ihrer gewünscht Zustand Konfiguration (DSC) Skripts ohne Fehler ausgeführt. Mithilfe von Protokollen effektiv werden zum Aufspüren von Fehlern und wissen, wie den Cache, um die sofortige Ergebnisse der Änderungen Ressourcen finden Sie unter Papierkorb Sie DSC effektiver behandeln können. Diese Technics werden in zwei Abschnitten beschrieben:

* Wird nicht mein Skript auszuführen: **DSC mithilfe von Protokollen Skriptfehler diagnostizieren**
* Meine Ressourcen wird nicht aktualisiert: **zum Zurücksetzen des Caches**

## Wird nicht mein Skript auszuführen: DSC mithilfe der Protokolle auffordern um Skriptfehler diagnostizieren

Wie alle Windows-Software, DSC zeichnet Fehler und Ereignisse in [Protokolle](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) können, die über die [Ereignisanzeige](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer)angezeigt werden. Diese Protokolle untersuchen kann Ihnen helfen zu verstehen, warum ein bestimmter Vorgang fehlgeschlagen ist, und wie Sie Fehler in der Zukunft zu verhindern. Schreiben Konfigurationsskripts können knifflig sein, also verwenden, um vereinfachen Verlauf Fehler als Sie Autor der Ressource DSC Log Verfolgen des Fortschritts der Konfiguration im Ereignisprotokoll DSC analytisches sein.

## Wo befinden sich DSC-Ereignisprotokollen?

In der Ereignisanzeige DSC Ereignisse sind: **Anwendungen und Dienste Protokolle/Microsoft/Windows/gewünschte Konfiguration**

Das entsprechende PowerShell-Cmdlet [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), kann auch ausgeführt werden, um den Ereignisprotokollen anzuzeigen:

```
PS C:\Users> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Wie oben gezeigt wird, ist DSC des primären Log Namen **Microsoft -> Windows -> DSC** (die Namen anderer Log unter Windows sind nicht dargestellt hier aus Platzgründen). Der Name der Protokolldatei abgeschlossen erstellen ChannelName ist der Name des primäre angefügt. DSC-Engine schreibt hauptsächlich in drei Arten von Protokollen: [Betrieb, analytischen, und Debuggen protokolliert](https://technet.microsoft.com/library/cc722404.aspx). Seit der analytischen und Debuggen Protokolle standardmäßig deaktiviert sind, sollten Sie diese in der Ereignisanzeige aktivieren. Hierzu öffnen Sie Ereignisanzeige, indem Sie den Befehl eventvwr ein in Windows PowerShell eingeben; oder möchten, klicken Sie auf die Schaltfläche **Start** , klicken Sie auf **Systemsteuerung**, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Ereignisanzeige**. Klicken Sie in der Ereignisanzeige im Menü **Ansicht** auf **analytischen anzeigen und Debuggen von Protokollen**. Der Name für den Analysedaten Kanal ist **Microsoft-Windows-Dsc/analytischen**und der Debuggen-Kanal ist **Microsoft-Windows-Dsc und Debuggen**. Auch können das Programm [Wevtutil](https://technet.microsoft.com/library/cc732848.aspx) So aktivieren Sie die Protokolle, wie im folgenden Beispiel dargestellt.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## Was enthalten DSC Protokolle?

DSC Protokolle werden den drei Log-Kanal basierend auf die Wichtigkeit einer Nachricht teilen. Der Betrieb Log in DSC enthält alle Fehlermeldungen und kann verwendet werden, um ein Problem identifizieren. Protokoll der analytischen weist eine höhere Anzahl von Ereignissen und kann zu identifizieren, wo Fehler aufgetreten ist. Dieser Kanal enthält auch ausführliche Meldungen (falls vorhanden). Das Fehlerprotokoll enthält Protokolle, die Ihnen zu verstehen helfen, wie der Fehler aufgetreten ist. DSC Ereignisnachrichten sind strukturiert, sodass jeder Ereignisnachricht mit einer Position ID beginnt, die einen Vorgang DSC eindeutig darstellt. Im folgenden Beispiel wird versucht, die Nachricht aus dem ersten Ereignis der Betrieb DSC Log angemeldet zu erhalten.

```powershell
PS C:\Users> $AllDscOpEvents=get-winevent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\Users> $FirstOperationalEvent=$AllDscOpEvents[0]
PS C:\Users> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

DSC Ereignisse sind in einer bestimmten Struktur angemeldet, die den Benutzer auf Aggregieren Ereignisse aus einem DSC Position ermöglicht. Die Struktur sieht wie folgt aus:

**Auftrags-ID: \<Guid\>**
**\<Ereignisnachricht\> **

## Tragen Ereignisse aus einem einzigen DSC Vorgang

DSC Ereignisprotokollen enthalten von verschiedenen Vorgängen anzeigen DSC generierte Ereignisse. Jedoch erhalten Sie normalerweise mit den Details zu nur einem bestimmten Vorgang betroffenen sein. Alle DSC Protokolle können durch die ID-Eigenschaft Position gruppiert werden, die für jeden Vorgang DSC eindeutig ist. Die Auftrags-ID wird als Wert der ersten Eigenschaft in allen DSC Ereignissen angezeigt. Die folgenden Schritte erläutert, wie um alle Ereignisse in einer gruppierten Arraystruktur zu sammeln.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-windows-dsc/operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-Winevent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations=$DscEvents | Group {$_.Properties[0].value}  
```

Hier wird die Variable `$SeparateDscOperations` Protokolle, gruppiert nach den Auftrag IDs enthält. Jedes Element der Matrix dieser Variablen stellt eine Gruppe von Ereignissen, die von einem anderen DSC-Vorgang gewähren des Zugriffs auf Weitere Informationen über die Protokolle protokolliert.

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

Sie können die Daten in der Variablen extrahieren `$SeparateDscOperations` [Where-Object](https://technet.microsoft.com/library/ee177028.aspx)verwenden. Im folgenden werden die fünf Szenarien, in denen Sie möglicherweise Daten zur Behandlung dieses Problems DSC extrahieren möchten:

### 1: Fehler bei

Alle Ereignisse verfügen über [schwere Ebenen](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Diese Informationen kann verwendet werden, um die zurück-Ereignisse zu identifizieren:

```
PS C:\> $SeparateDscOperations  | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2: Details von JOIN-Operationen in der letzten halben Stunde ausführen

`TimeCreated`, eine Eigenschaft jedes Ereignisses Windows besagt die Uhrzeit des Ereignisses erstellt wurde. Vergleich der Unterschiede bei dieser Eigenschaft mit einem bestimmten Datum/Uhrzeit-Objekt kann verwendet werden, um alle Ereignisse zu filtern:

```powershell
PS C:\> $DateLatest=(Get-date).AddMinutes(-30)
PS C:\> $SeparateDscOperations  | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3: Nachrichten aus den letzten Vorgang

Der letzten Vorgang befindet sich an den ersten Index in der Gruppe "Matrix" `$SeparateDscOperations`. Abfragen der Gruppe Nachrichten für Index 0, gibt für den aktuellen Vorgang aller Nachrichten:

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### 4: für zuletzt verwendete fehlgeschlagene Vorgänge protokolliert Fehlermeldungen

`$SeparateDscOperations[0].Group` enthält einen Satz von Ereignissen für den aktuellen Vorgang an. Ausführen der `Where-Object` -Cmdlet zum Filtern der Ereignisse basierend auf deren Anzeigenamen Ebene. Ergebnisse werden gespeichert, der `$myFailedEvent` Variable, wenn Sie die Ereignis Meldung darüber informiert geschnitten der weitergegeben werden kann:

```powershell
PS C:\> $myFailedEvent=($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### 5: alle Ereignisse für eine bestimmte Position ID generiert

`$SeparateDscOperations` ist ein Array von Gruppen, von denen jede den Namen wie die ID eindeutige Position hat Durch Ausführen der `Where-Object` Cmdlet, Sie können diese Gruppen von Ereignissen, die eine bestimmte Position ID extrahieren:

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## Bei Verwendung xDscDiagnostics DSC analysieren Protokollen

**xDscDiagnostics** ist ein PowerShell-Modul, das besteht aus zwei einfache Vorgänge, die Ihnen helfen können DSC Fehlern auf Ihrem Computer analysieren: `Get-xDscOperation` und `Trace-xDscOperation`. Diese Funktionen können Sie alle lokalen Ereignisse aus vergangenen DSC Vorgänge oder DSC Ereignisse auf Remotecomputern (mit gültigen Anmeldeinformationen) leichter identifizieren. Im folgenden sehen Sie, den Ausdruck DSC Vorgang verwendet, um eine einzelne eindeutige DSC Ausführung von deren a bis zum Ende definieren. Beispielsweise `Test-DscConfiguration` einem separaten DSC Vorgang wäre. Auf ähnliche Weise jeder anderen Cmdlet in DSC (z. B. `Get-DscConfiguration`, `Start-DscConfiguration`usw.) konnte jeweils als separate DSC Vorgänge identifiziert werden. Die beiden Cmdlets werden in [xDscDiagnostics](https://powershellgallery.com/packages/xDscDiagnostics) PowerShell-Modul (DSC Resource Kit) und nachfolgend ausführlicher erläutert. Hilfe steht ausgeführt `Get-Help <cmdlet name>`.

## Get-xDscOperation

Dieses Cmdlet können Sie die Ergebnisse der Vorgänge zur DSC zu finden, die auf einem oder mehreren Computern ausführen, und gibt ein Objekt, die Auflistung von Ereignissen, die bei jedem Vorgang DSC gefertigt enthält. Beispielsweise wurden in die Ausgabe der folgenden drei Befehle ausgeführt. Der ersten Phase übergeben, und die anderen zwei fehlgeschlagen ist. Diese Ergebnisse werden in der Ausgabe der zusammengefasst `Get-xDscOperation`.

Zu erledigen: Ersetzen Sie dieses Bild, das Get-xDscOperation Ausgabe zeigt

### Parameter

* **Absteigend**: akzeptiert eine ganze Zahl, um die Anzahl der anzuzeigenden Vorgänge anzugeben. Standardmäßig gibt es 10 neuesten Vorgänge an. Beispielsweise erledigen: Anzeigen Get-xDscOperation-neueste 5
* **ComputerName**: Parameter, die ein Array von Zeichenfolgen, jede enthält den Namen eines Computers akzeptiert aus, in dem Sie DSC Ereignisprotokolldaten sammeln möchten. Standardmäßig werden Daten vom Host-Computer gesammelt. Um dieses Feature zu aktivieren, müssen Sie den folgenden Befehl in den Remotecomputern im erweiterten Modus ausführen, damit die Auflistung von Ereignissen, zulassen
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* **Anmeldeinformationen**: Geben Sie Parameter, ist der, PSCredential, der Zugriff auf die in den Parameter ComputerName angegebenen Computer unterstützen kann.

### Zurückgegebene Objekt

Das Cmdlet gibt ein Array von Objekten jeweils vom Typ **Microsoft.PowerShell.xDscDiagnostics.GroupedEvents**. Jedes Objekt in folgendem Array bezieht sich auf einen anderen DSC-Vorgang. Die Standardanzeige für dieses Objekt weist die folgenden Eigenschaften
* **SequenceID**: Gibt die inkrementell basierend auf der Uhrzeit der DSC-Vorgang zugeordnete Nummer an. Beispielsweise den letzten ausgeführten Vorgangs müssten SequenceID als 1, die zweite zum letzten DSC Vorgang würde haben SequenceID von 2 usw.. Diese Zahl ist, einen anderen Bezeichner für jedes Objekt in der gelieferten Matrix.
* **TimeCreated**: ein DateTime-Wert, der angibt, wann der DSC Vorgang begonnen hat.
* **ComputerName**: den Namen des Computers aus, in dem die Ergebnisse aggregiert werden.
* **Ergebnis**: eine Zeichenfolge mit dem Wert **Fehler** oder **Erfolg** , das zeigt an, ob dieser Vorgang DSC oder nicht, einen Fehler haben Hilfethemas.
* **AllEvents**: ein Objekt, eine Auflistung von Ereignissen darstellt, der Vorgang DSC erzeugt.

Beispielsweise die folgende Ausgabe zeigt die Ergebnisse des letzten Vorgangs aus mehreren Computern: erledigen: Ersetzen Bild für Get-xDscOperation Remotecomputer Protokolle angezeigt werden.

## Spur-xDscOperation

Dieses Cmdlet gibt ein Objekt mit einer Auflistung von Ereignissen, deren Ereignistypen und die Ausgabe der Nachricht, die aus einer bestimmten DSC Operation generiert. In der Regel, wenn Sie finden einen Fehler in die Vorgänge mit `Get-xDscOperation`, möchten Sie diesen Vorgang aus, um herauszufinden, welche der Ereignisse einen Fehler verursacht verfolgen.

### Parameter

* **SequenceID**: Dies ist der ganzzahlige Wert auf jeden Vorgang, der in Verbindung mit einem bestimmten Computer Gruppenrichtlinien zugewiesen. Durch Angeben von werden eine Sequenz-ID sagen, 4, die Spur für die DSC-Vorgang, der aus dem letzten 4th wurde Ausgabe

Spur-xDscOperation mit Sequenz-ID angegeben
* **Auftrags**: Dies ist der GUID Wert von KGV xDscOperation zugeordnet wird, eine Operation eindeutig identifizieren. Wenn eines Auftrags angegeben wird, ist der Spur der entsprechenden DSC Vorgang Ausgabe an.
  Zu erledigen: Ersetzen Bild für Spur-xDscOperation aufzeichnen Auftrags als Parameter
* **ComputerName** und **Anmeldeinformationen**: diesen Parametern können Sie die Spur von Remotecomputern gesammelt werden:
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  Zu erledigen: Ersetzen Bild für Spur-xDscOperation auf einem anderen Computer ausführen

Beachten Sie, dass, da `Trace-xDscOperation` aggregiert Ereignisse aus der analytischen, Debuggen und Betrieb Protokolle, fordert Sie diese Protokolle aktivieren, wie zuvor beschrieben.

### Zurückgegebene Objekt

Das Cmdlet gibt ein Array von Objekten, jede Datentyp `Microsoft.PowerShell.xDscDiagnostics.TraceOutput`. Jedes Objekt in folgendem Array enthält die folgenden Felder:
* **ComputerName**: den Namen des Computers aus, in dem die Protokolle gesammelt werden.
* **Ereignistyp**: Dies ist ein Feld des Datentyps Enumerator, die Informationen auf den Typ des Ereignisses enthält. Dies möglicherweise eine der folgenden Aktionen aus:
  - *Betrieb*: das Ereignis aus dem Protokoll funktionsfähig ist.
  - *Analytischen*: das Ereignis aus dem analytischen Protokoll ist.
  - *Debuggen*: das Ereignis aus dem Protokoll Debuggen ist.
  - *Ausführlich*: Ereignisse Ausgabe als ausführliche Meldungen während der Ausführung. Ausführlichen Meldungen erleichtern die Abfolge von Ereignissen zu identifizieren, die veröffentlicht werden.
  - *Fehler*: Fehlerereignisse. Anhand der für die Ereignisse zurück, finden Sie in der Regel schnell die Ursache des Fehlers.
* **TimeCreated**: einen DateTime-Wert, der angibt, wenn das Ereignis durch DSC protokolliert wurde.
* **Meldung**: die Nachricht, die vom DSC in den Ereignisprotokollen protokolliert wurde.

Im folgenden werden die Felder in diesem Objekt, die für Weitere Informationen über das Ereignis verwendet werden kann, aber nicht standardmäßig angezeigt werden:

* **Auftrags**: die Auftrags-ID (GUID-Format) für die Operation DSC spezifisch.
* **SequenceID**: das SequenceID für diesen Vorgang DSC in diesem Computer eindeutig.
* **Ereignis**: Dies ist das tatsächliche Ereignis erfasst, DSC, vom Typ `System.Diagnostics.Eventing.Reader.EventLogRecord`. Dies kann auch den ergebenden durch das Cmdlet ausgeführt `Get-WinEvent`. Sie enthält weitere Informationen, wie die Aufgabe, EventID und Ebene des Ereignisses.

Abwechselnd, Sie können Sammeln von Informationen zu den Ereignissen durch Speichern der Ausgabe des `Trace-xDscOperation` in einer Variablen zu speichern. Mit dem folgenden Befehl können alle Ereignisse für einen bestimmten DSC Vorgang angezeigt werden:

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

Dadurch wird angezeigt, die gleichen Ergebnisse wie die `Get-WinEvent` Cmdlet, wie in der folgenden Ausgabe: erledigen: Was ausgeben?

Idealerweise würden Sie zuerst verwenden `Get-xDscOperations` ab dem letzten paar DSC auflisten Konfiguration auf Ihrem Computer ausgeführt wird. Anschluss daran, können Sie mit einem einzelnen Vorgang (mithilfe des zugehörigen SequenceID oder Auftrags) untersuchen `Trace-xDscOperation` zu finden, was sie Hintergrundinformationen hat.

## Meine Ressourcen wird nicht aktualisiert: zum Zurücksetzen des Caches

DSC-Engine werden als ein PowerShell-Modul für Effizienz Zwecke implementierte Ressourcen zwischengespeichert. Dies kann jedoch Probleme verursachen, wenn Sie eine Ressource authoring und es gleichzeitig testen, da DSC die zwischengespeicherte Version geladen wird erst nach dem Neustart des Prozesses. Die einzige Möglichkeit zum Laden der neueren Version DSC stellen ist den Prozess, die DSC-Engine hostet explizit beenden.

Wenn Sie auf ähnliche Weise ausführen `Start-DSCConfiguration`, nach dem Hinzufügen und ändern eine benutzerdefinierte Ressource, die Änderung möglicherweise nicht ausführen, es sei denn, oder bis, der Computer neu gestartet wird. Dies liegt daran DSC ausgeführt, in der WMI-Anbieter Hostprozess (WmiPrvSE wird), und in der Regel stehen viele Instanzen von WmiPrvSE auf einmal ausgeführt. Bei einem Neustart, dem Neustart des Hostprozesses und der Cache deaktiviert ist.

Um erfolgreich Papierkorb die Konfiguration, und leeren Sie den Cache ohne neu zu starten, müssen Sie beenden und starten Sie den Hostprozess. Dies kann auf Basis pro Instanz, erfolgen vererbungseinstellungen identifizieren Sie den Prozess, beenden sie und starten Sie ihn erneut. Alternativ können Sie `DebugMode`, wie unten, dargestellt, um die Ressource PowerShell DSC neu zu laden.

Zum erkennen, welcher Prozess DSC-Engine gehostet wird, und beenden ihn auf Basis pro Instanz, können Sie die Prozess-ID des der WmiPrvSE aufgelistet, bei die DSC-Engine gehostet wird. Klicken Sie dann um den Anbieter zu aktualisieren, beenden Sie den Prozess WmiPrvSE mithilfe der folgenden Befehle, und führen Sie dann erneut auf **Start-DscConfiguration** .

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## Debug-Modus verwenden

Können Sie die DSC lokalen Konfiguration Manager (KGV) verwenden konfigurieren `DebugMode` immer den Cache zu löschen, wenn der Hostprozess neu gestartet wird. Wenn **TRUE**festgelegt ist, bewirkt, dass es das Modul für die Ressource PowerShell DSC immer neu zu laden. Sobald Sie fertig sind schreiben Ressource steht, können Sie es auf **FALSE** festlegen und die-Engine wird das Verhalten der Module Zwischenspeichern zurückgesetzt.

Es folgt eine Demo angezeigt wie `DebugMode` können den Cache automatisch aktualisieren. Zunächst wollen wir die standardmäßige Konfiguration:

```
PS C:\Users\WinVMAdmin\Desktop> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

Sie können sehen, das `DebugMode` auf **FALSE**festgelegt ist.

Einrichten der `DebugMode` Demo, verwenden Sie die folgende PowerShell Ressource:

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1"|Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

Erstellen Sie nun eine Konfiguration unter Verwendung der oben genannten Ressource mit dem Namen `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Sehen Sie, dass der Inhalt der Datei: "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" ist- **1**.

Aktualisieren Sie nun den Anbietercode mithilfe des folgenden Skripts aus:

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput"|Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Dieses Skript generiert eine Zufallszahl und aktualisiert entsprechend den cade-Anbieter. Mit `DebugMode` falsch festgelegt, werden nie den Inhalt der Datei "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" geändert.

Legen Sie nun `DebugMode` **Wahr** in Ihrem Konfigurationsskript:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

Wenn Sie das obige Skript erneut ausführen, sehen Sie sich, dass der Inhalt der Datei jedes Mal abweicht. (Sie können ausführen `Get-DscConfiguration` überprüfen). Nachstehend ist das Ergebnis zwei zusätzliche wird ausgeführt (Ihre Ergebnisse möglicherweise anders, wenn Sie das Skript ausführen):

```powershell
PS C:\Users\WinVMAdmin\Desktop> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\Users\WinVMAdmin\Desktop> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14 
```

## Siehe auch

### Bezug
* [DSC Log-Ressourcen](logResource.md)

### Konzepte
* [Erstellen Sie benutzerdefinierter Windows PowerShell gewünscht staatliche Konfigurationsressourcen](authoringResource.md)

### Weitere Ressourcen
* [Windows PowerShell gewünscht staatliche Konfigurations-Cmdlets](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)
