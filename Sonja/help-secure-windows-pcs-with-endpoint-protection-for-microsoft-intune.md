---
title: "Endpunkt Schutz für Windows-PCs | Microsoft Intune"
description: Sichern Sie Ihrer verwalteten Computer mit Endpunkt Schutz, die in Echtzeit Schutz vor Schadsoftware bereitstellt.
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 8bcc70ba6451f13f80319229b191b6feb2d5664e
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Hilfe zu Microsoft Intune sicheren Windows PCs mit Endpunkt Schutz
Microsoft-Intune helfen Ihnen zum Schützen des verwalteten Computers mit Endpunkt Schutz bietet in Echtzeit Schutz vor Schadsoftware, behält Schadsoftware Definitionen aktuell und überprüft automatisch auf Computer. Endpunkt Schutz enthält auch Tools, die Ihnen Ihnen helfen, verwalten und Überwachen von Schadsoftware Angriffen.

Wenn Sie noch nicht Intune-Client auf Ihrem Computer installiert haben, finden Sie unter [installieren den Windows-PC-Client mit Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Verwenden Sie die Informationen in den folgenden Abschnitten, mit deren Hilfe Sie konfigurieren, bereitstellen und überwachen Endpunkt Schutz.

## Wählen Sie aus, wann Endpunkt Schutz verwenden.
Frei von Malware und Viren, wie ein IT-Administrator, eine der Top-Prioritäten regelmäßige der Computer ist, die Sie verwalten. Bevor Sie Intune für Windows-PCs in Ihrer Organisation bereitstellen, sollten Sie entscheiden, wie Sie Ihre Computer schützen, indem Sie eine der folgenden Optionen aus, und konfigurieren seinen zugeordneten Richtlinien:

|Sie möchten:|Endpunkt Schutz Richtlinieneinstellungen|Weitere Informationen|
|--------------|---------------------------------------|--------------------|
|Verwenden Sie Microsoft Intune Endpunkt Schutz nur, wenn keine Drittanbieter-Endpunkt Schutz Anwendung installiert ist.<br /><br />Können Microsoft Intune Endpunkt Schutz auf allen Computern, auf dem eine Drittanbieter-Endpunkt Schutz Anwendung nicht installiert.|Installieren der Endpunkt Schutz = **Ja**<br /><br />Endpunkt Schutz aktivieren = **Ja**<br /><br />Endpunkt Schutz installieren, auch wenn eine Drittanbieter-Endpunkt Schutz Anwendung installiert ist **kein** =|Wenn eine Drittanbieter-Endpunkt Schutz Anwendung erkannt wird, Microsoft Intune Endpunkt Schutz ist nicht installiert und deinstalliert wird, wenn es zuvor installiert wurde.|
|Verwenden Sie Microsoft Intune Endpunkt Protection, selbst wenn eine Drittanbieter-Endpunkt Schutz Anwendung installiert ist.<br /><br />Bei diesem Ansatz werden Sie Microsoft Intune Endpunkt Schutz und die Drittanbieter-Endpunkt Schutz Anwendung gleichzeitig ausgeführt werden. Da potenzielle Leistungsprobleme empfohlen nicht dieser Konfiguration. |Installieren der Endpunkt Schutz = **Ja**<br /><br />Aktivieren des Schutzes Endpunkt = **Ja**<br /><br />Endpunkt Schutz installieren, auch wenn eine Drittanbieter-Endpunkt Schutz Anwendung installiert ist = **Ja**|Verwenden Sie wann aus:<br /><br />-Sie möchten bei der Verwendung von Microsoft Intune Endpunkt Schutz wechseln.<br />-Sie bereitstellen ein neues Clients, das Microsoft Intune Endpunkt Schutz verwendet wird.<br />-Sie aktualisieren jeder Client, der Microsoft Intune Endpunkt Schutz verwendet wird.|
|Verwenden Sie Intune ohne Microsoft Intune Endpunkt Schutz. In diesem Fall greifen Sie auf einer Drittanbieter-Endpunkt Schutz Anwendung zurück.|Installieren der Endpunkt Schutz = **Nein**|Wenn Sie eine Drittanbieter-Endpunkt Schutz-Anwendung nicht verwenden, werden diese Konfiguration ist nicht empfohlen, weil es Ihrer Organisation Computern Schadsoftware oder anderen Angriffen verfügbar gemacht werden kann.<br /><br />Microsoft Intune Endpunkt Schutz ist nicht installiert und deinstalliert wird, wenn es zuvor installiert wurde.|
Um von der aktuellen Endpunkt Schutz Anwendung auf Microsoft Intune Endpunkt Schutz wechseln möchten, führen Sie folgende Schritte aus:

1.  Lassen Sie Ihre aktuelle Endpunkt Schutz Anwendung, die ausgeführt werden, während Sie auf den Computern die Intune-Clientsoftware bereitstellen.

2.  Bestätigen Sie, dass Microsoft Intune Endpunkt Schutz installiert ist und trägt dazu bei Clientcomputern gesichert.

3.  Entfernen von Drittanbietern Endpunkt Schutzsoftware durch:

    -   Verwenden von Intune Software-Verteilung ein Tool zum Entfernen der Software bereitgestellt, die vom Hersteller der Anwendung Schutz Drittanbieter-Endpunkt bereitgestellt wird. Weitere Informationen finden Sie unter [Bereitstellen von apps mit Microsoft Intune](deploy-apps.md).

    -   Die Anwendung von Drittanbietern Endpunkt Schutz manuell zu entfernen.

> [!NOTE]
> Intune werden nicht automatisch von Drittanbietern Endpunkt Schutz Applikationen deinstalliert werden.

## Konfigurieren von Microsoft Intune Endpunkt Schutz
Gehen Sie folgendermaßen vor, helfen Ihnen die Konfiguration der Endpunkt Schutz für Microsoft Intune.

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/), die **Richtlinie** > **Richtlinie hinzufügen**.

2.  Erweitern Sie **Computer Verwaltung**, und wählen Sie dann auf **Microsoft Intune Agent Einstellungen**. Wählen Sie **Erstellen und Bereitstellen einer benutzerdefinierten Richtlinie** eine Richtlinie für den Endpunkt Schutz Einstellungen angeben. Wählen Sie dann die Schaltfläche **Richtlinie erstellen** aus.

Sie können die empfohlenen Einstellungen verwenden oder Anpassen der Einstellungen. Wenn Sie benötigen Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien, finden Sie im Thema [Allgemeine Windows-PC-Verwaltungsaufgaben mit dem Microsoft Intune Computer Client](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Endpunkt Schutz Einstellungen](./media/pol-sa-pc-endpoint-policy.png)

Klicken Sie auf der Seite **Alle Richtlinien** des Arbeitsbereichs **Richtlinie** können Sie die bereitgestellte Endpunkt Schutzrichtlinie anzeigen.

## Festlegen der Einstellungen für Endpunkt Schutz-Dienst

|Einstellung der Richtlinie|Details|
|------------------|--------------------|
|**Installieren der Endpunkt Schutz**|Setzen Sie auf **Ja** , Endpunkt Schutz auf verwalteten Computern zu installieren. Wenn Sie während der Installation eine Drittanbieter-Endpunkt Schutz Anwendung erkannt wird, wird Endpunkt Schutz nicht installiert werden, es sei denn, die Einstellung **Installieren Endpunkt Schutz auch wenn eine Drittanbieter - Endpunkt Schutz Anwendung installiert ist** auf **Ja**festgelegt ist. **Hinweis:** Standardmäßig wird der Intune Endpunkt Schutz auf verwalteten Computern installiert. Wenn Sie nicht Endpunkt Schutz auf verwalteten Computer installieren möchten, müssen Sie diese Richtlinie explizit auf **Nein**festlegen. Wenn Endpunkt Schutz zuvor installiert war, und die Richtlinie auf **Nein**aktualisiert wird, wird der Endpunkt Schutz Client deinstalliert werden.<br />Wert empfohlen: **Ja**|
|**Installieren Sie Endpunkt Schutz, auch wenn eine Drittanbieter-Endpunkt Schutz Anwendung installiert ist**|Setzen Sie auf **Ja** , Schutz von Microsoft Intune Endpunkt installieren, selbst wenn die Anwendung einer Drittanbieter-Endpunkt Schutz erkannt wird.<br /><br />Wert empfohlen: **Ja**|
|**Aktivieren des Schutzes Endpunkt**|Setzen Sie auf **Ja** , Microsoft Intune Endpunkt Schutz auf Computern aktivieren, die den Endpunkt Schutz Client aufweisen.<br /><br />Wenn auf **Nein**festgelegt und Microsoft Intune Endpunkt Schutz ist installiert, Endpunkt Schutz Client-Benutzeroberfläche für Benutzer nicht angezeigt wird und alle Schutzfeatures sind deaktiviert.<br /><br />Wert empfohlen: **Ja**|
|**Deaktivieren von Client-Benutzeroberfläche**|Legen Sie zum Ausblenden der Benutzeroberfläche von Microsoft Intune Endpunkt Schutz Client von Benutzern auf **Ja** (erfordert einen Neustart des Computers Client wirksam).<br /><br />Wert empfohlen: **keine**|
|**Installieren Sie Endpunkt Schutz, auch wenn eine Drittanbieter-Endpunkt Schutz Anwendung installiert ist**|Setzen Sie sich so erzwingen Sie die Installation von Microsoft Intune Endpunkt Schutz auf **Ja** , selbst wenn die Anwendung einer Drittanbieter-Endpunkt Schutz erkannt wird.<br /><br />Wert empfohlen: **keine**|
|**Erstellen Sie einen System Wiederherstellungspunkt vor Schadsoftware Behebung**|Setzen Sie auf **Ja** , ein Windows-System wiederherstellen Punkt vor Beginn alle Schadsoftware Behebung zu erstellen.<br /><br />Wert empfohlen: **Ja**|
|**Nachverfolgen von gelöst Schadsoftware (Tage)**|Ermöglicht den Endpunkt Schutz gelöst Schadsoftware für eine angegebene Zeit zu verfolgen, damit Sie zuvor infizierte Computern manuell überprüfen können.<br /><br />Sie können einen Wert von 0 bis 30 Tage angeben.<br /><br />Wert empfohlen: **7 Tage**|
Wenn Sie die Richtlinienwerte für die Einstellungen **Endpunkt Schutz installieren** und **Aktivieren von Endpunkt Schutz** auf **Ja**, und der Richtlinienwert für hergestellt haben erkennt **Installieren Endpunkt Schutz auch wenn eine Drittanbieter - Endpunkt Schutz Anwendung installiert ist** , auf **Nein**, Microsoft Intune Endpunkt Schutz an, dass eine andere Endpunkt Schutz Anwendung installiert ist. Dies bedeutet, dass Endpunkt Schutz wird nicht installiert werden, oder deinstalliert werden, wenn es bereits vorhanden ist. Microsoft Intune Endpunkt Schutz jedoch über die Integrität der anderen Endpunkt Schutz Anwendung in Intune melden.

  Microsoft Security Essentials benachrichtigt Schutz in Echtzeit beim potenzielle Risiken wie Viren und Spyware versuchen, sich selbst zu installieren, oder auf Ihrem PC ausführen. Dem Moment der in diesem Fall wird eine Meldung im Infobereich rechts neben der Taskleiste angezeigt.

### Festlegen der Einstellungen für die Schutz in Echtzeit

|Einstellung der Richtlinie|Details|
|------------------|--------------------|
|**Aktivieren des Schutzes in Echtzeit**|Ermöglicht die Überwachung und Scannen aller Dateien und Anwendungen, auf die zugegriffen werden. Es blockiert auch alle bösartige Dateien und Anwendungen, bevor Sie auf Computern ausgeführt werden kann.<br /><br />Wert empfohlen: **Ja**|
|**Scannen Sie alle downloads**|Ermöglicht das Scannen aller Dateien und Anlagen, die aus dem Internet auf Computern heruntergeladen werden.<br /><br />Wert empfohlen: **Ja**|
|**Überwachen der Aktivitäten in Datei- und Programm auf Computern**|Ermöglicht die Überwachung von eingehenden und ausgehenden Dateien und Programmaktivität auf Computern. Mit dieser Einstellung können Endpunkt Schutz überwachen beim Starten von Dateien und Programme ausführen, und informieren Sie über alle Aktionen, die sie durchführen oder die Aktionen, die diesen ausgeführt werden.<br /><br />Wert empfohlen: **Ja**|
|**Überwacht Dateien**|Können Sie auswählen, wenn nur eingehende, nur ausgehende, oder alle Dateien überwacht werden.<br /><br />Wert empfohlen: **Alle Dateien überwachen**|
|**Aktivieren Sie die Überwachung Verhalten**|Ermöglicht Microsoft Intune Endpunkt Schutz für bestimmte Muster verdächtiger Aktivitäten auf Clientcomputern überprüfen.<br /><br />Wert empfohlen: **Ja**|
|**Aktivieren Sie Network Prüfung System**|Ermöglicht Netzwerk Prüfung System (NIS) auf Clientcomputern. NIS verwendet Signaturen bekannter Sicherheitsprobleme aus dem [Microsoft Malware Protection Center](http://go.microsoft.com/fwlink/?LinkId=234249) zu erkennen und blockieren bösartiger Netzwerkverkehr.<br /><br />Wert empfohlen: **Ja**|

  ![In Echtzeit Einstellungen für den Endpunkt Schutz](./media/pol-sa-pc-policy-realtime.png)

### Festlegen der Einstellungen für Scan-Zeitplan

|Einstellung der Richtlinie|Weitere Informationen|
|------------------|--------------------|
|**Planen eines täglichen schnellen-Scans**|Wird einen täglichen schnellen-Scan von häufig verwendeten Dateien und wichtige Systemdateien auf Computern geplant. Diese schnelle-Scan weist einen minimalen Einfluss auf die Systemleistung.<br /><br />Wert empfohlen: **Ja**|
|**Führen Sie eine schnelle Überprüfung, wenn Sie zwei aufeinanderfolgende scannt verpasst haben**|Konfiguriert Endpunkt Schutz, um einen schnellen Scan automatisch auf Computern ausgeführt, wenn sie zwei aufeinander folgende schnellen scannt verpasst haben.<br /><br />Wert empfohlen: **Ja**|
|**Planen eines vollständigen Scans**|Konfiguriert einen vollständigen Scan aller Dateien und Ressourcen auf den lokalen Computerfestplatten. Diese Überprüfung Zeit und Leistung des Computers (die Betrag benötigte Zeit hängt von der Anzahl von Dateien und Ressourcen, die gescannt werden) kann beeinflussen.<br /><br />Wert empfohlen: **keine**|
|**Führen Sie eine vollständige Überprüfung, wenn Sie zwei aufeinander folgende vollständige scannt verpasst haben**|Konfiguriert Endpunkt Schutz um automatisch einen vollständigen Scan auf Computern ausgeführt, wenn sie zwei aufeinanderfolgende scannt verpasst haben.<br /><br />Wert empfehlen: nicht konfiguriert|

### Festlegen der Einstellungen für Scan-Optionen

|Einstellung der Richtlinie|Details|
|------------------|--------------------|
|**Führen Sie eine vollständige Überprüfung nach der Installation von Endpunkt Schutz**|Setzen Sie auf **Ja** , um zu informieren Endpunkt Schutz automatisch eine vollständige Überprüfung ausgeführt wird, nachdem es auf dem Computer installiert ist. Diese Überprüfung ausgeführt wird nur, wenn Computer im Leerlauf zu minimieren des Effekts klicken Sie auf Benutzerproduktivität befinden.<br /><br />Wert empfohlen: **Ja**|
|**Führen Sie automatisch einen vollständigen Scan bei Bedarf von Schadsoftware freistellen folgen**|Setzen Sie auf **Ja** , damit Endpunkt Schutz automatisch eine vollständige Überprüfung auf Computern nach dem Entfernen von Schadsoftware, um zu bestätigen, dass andere Dateien nicht betroffenen ausführen können.<br /><br />Wert empfohlen: **Ja**|
|**Starten einer geplanten Überprüfung, nur, wenn der Computer inaktiv ist**|Setzen Sie auf **Ja** , um zu verhindern, dass geplante Ihrer beginnend mit dem Computer befinden sich in verwenden, um alle Verlust der Produktivität der Benutzer zu verhindern.<br /><br />Wert empfohlen: **Ja**|
|**Prüfen Sie die neuesten Schadsoftware Definitionen vor dem Starten einer Überprüfung**|Setzen Sie auf **Ja** , um zu informieren Endpunkt Schutz automatisch nach den neuesten Schadsoftware Definitionen gesucht, bevor eine Überprüfung auf Computern gestartet wird.<br /><br />Wert empfohlen: **Ja**|
|**Scannen Archivieren von Dateien**|Setzen Sie auf **Ja** , um den Endpunkt Schutz für Malware in Archivieren von Dateien (wie ZIP oder CAB-Dateien) auf Computern Scannen konfigurieren.<br /><br />Wert empfohlen: **keine**|
|**Scannen von e-Mail-Nachrichten**|Setzen Sie auf **Ja** , Schutz der Endpunkt um Scannen von eingehender e-Mail-Nachrichten bei auf Computern Ankunft konfigurieren.<br /><br />Wert empfohlen: **Ja**|
|**Scannen von Dateien in einer freigegebenen Netzwerkordnern geöffnet**|Setzen Sie auf **Ja** , so konfigurieren Sie Endpunkt Schutz zum Überprüfen von Dateien, die aus freigegebenen Ordnern im Netzwerk geöffnet werden. Dies sind in der Regel Dateien, die mithilfe eines Pfads Universal Naming Convention (UNC) zugegriffen werden. Dieses Feature aktivieren kann für Benutzer Probleme verursachen, die nur schreibgeschützten Zugriff haben, da Malware entfernt werden kann.<br /><br />Wert empfohlen: **keine**|
|**Scannen lösende**|Setzen Sie auf **Ja** , um den Endpunkt Schutz zum Überprüfen von Dateien auf lösende konfigurieren. Dieses Feature aktivieren kann für Benutzer Probleme verursachen, die nur schreibgeschützten Zugriff haben, da Malware entfernt werden kann.<br /><br />Wert empfohlen: **keine**|
|**Austauschbare Laufwerke scannen**|Legen Sie auf **Ja** , so konfigurieren Sie Endpunkt Schutz Scannen Schadsoftware und unerwünschte Software auf austauschbare Laufwerke, wie USB-Laufwerke, wenn Sie eine vollständige Überprüfung auf Computern ausführen.<br /><br />Wert empfohlen: **Ja**|
|**CPU-Auslastung während einer Überprüfung zu beschränken.**|Legen Sie den maximalen Prozentsatz der CPU-Auslastung bei geplanten durchsucht auf Computern verwendet werden kann. Sie können diesen Wert von 1 auf 100 % festgelegt.<br /><br />Wert empfohlen: **50 %**|

### Wählen Sie Standardwerte für Aktionen Einstellungen

Die Einstellung **Wählen Sie aus, wie Endpunkt Schutz auf Schadsoftware folgende Benachrichtigung Ebenen fungiert** gibt die Standardaktion, über die Endpunkt Schutz zu gelangen, wenn der verschiedenen benachrichtigen Ebenen Malware erkannt wird. Für jede Ebene benachrichtigen können Sie Schadsoftware zu entfernen, unter Quarantäne gestellt wird oder von Microsoft empfohlene agieren.

Wert empfohlen: **Empfohlene Aktion**, womit Endpunkt Schutz Aktion empfehlen zu können.   

### Entscheiden Sie, ob die Einstellungen für ausgeschlossenen Dateien und Ordner auswählen

Die Einstellung **Dateien und Ordner, wann ausschließen, einen Scan ausgeführt, oder verwenden Sie Schutz in Echtzeit** ausgeschlossen werden bestimmte Dateien oder Ordner ein Scan ausführen oder wenn Schutz in Echtzeit auf Computern verwendet wird.

### Entscheiden Sie, ob die Einstellungen von ausgeschlossene Prozesse auswählen

Die Einstellung **-Vorgänge, um Sie beim Ausführen eines Scans auszuschließen, oder verwenden Sie Schutz in Echtzeit** können Sie bestimmte Prozesse ausschließen, wenn eine Überprüfung wird ausführen oder wenn Schutz in Echtzeit auf Computern verwendet wird. Sie können nur Dateien mit den folgenden Erweiterungen ausschließen: **.exe**, **.com**oder **.scr**.

### Entscheiden Sie, ob die ausgeschlossene Datei Typen Einstellungen auswählen

Die Einstellung **Dateierweiterungen wann ausschließen Durchführen einer Suche, oder verwenden Sie in Echtzeit Schutz** können Sie bestimmte Dateinamenerweiterungen ausschließen, wenn eine Überprüfung wird ausführen oder wenn Schutz in Echtzeit auf Computern verwendet wird.

### Festlegen der Einstellungen für Microsoft Active Schutz-Dienst
Microsoft Active Protection Service ist eine Onlinecommunity, die Ihnen bei der Entscheidung zum reagieren möglicherweise Risiken hilft. Die Community hilft auch die Seitenansicht des neuen Malware infiziert beenden. Sie können **Teilnehmen an Microsoft aktiven Protection Service** , indem Sie **Ja**auswählen und dann Ihre **Mitgliedschaft Ebene**angeben:
  - **Grundlegende** - sendet grundlegende Informationen an Microsoft erkannten Schadsoftware. Dies umfasst die Stelle, an der die Software von stammt, die Aktionen, die Sie anwenden oder Endpunkt Schutz wird automatisch angewendet werden soll, und, ob die Aktionen erfolgreich waren.
  - **Erweitert** – werden weitere Informationen zu Malware, Spyware und potenziell unerwünschte Software an Microsoft gesendet. Dies umfasst Informationen über den Speicherort der Software, Dateinamen, wie die Software in Betrieb sind und wie sie Ihr Computer betroffen hat.

Sie können auch **empfangen dynamische Definitionen basierend auf Microsoft Active Protection Service-Berichte**.

## Wählen Sie Verwaltungsaufgaben für den Endpunkt Schutz
Die folgenden Aufgaben helfen Ihnen unterschiedliche Verwaltungsaufgaben auf verwalteten Computern ausführen, die Endpunkt Schutz ausgeführt werden:
 - Aktualisieren Sie die Schadsoftware Definitionen
  - Intune console - aus dem Arbeitsbereich **Gruppen** , wählen die Computer, die Sie aktualisieren möchten. Wählen Sie **Remote Aufgaben** &gt; **Schadsoftware Definitionen aktualisieren**.
  - Starten Sie verwaltete Computer - die Clientsoftware Endpunkt Schutz von Windows-Infobereich angezeigt. Wählen Sie die Registerkarte **Update** aus, und wählen Sie dann auf **Aktualisieren**.
 - Führen Sie eine Schadsoftware Überprüfung:
  - Intune console - aus dem Arbeitsbereich **Gruppen** , wählen die Computern, die Sie überprüfen möchten. Wählen Sie **einen vollständigen Schadsoftware Scan ausführen** oder **einen schnellen Schadsoftware Scan ausführen**.
  - Starten Sie verwaltete Computer - die Clientsoftware Endpunkt Schutz von Windows-Infobereich angezeigt. Wählen Sie **schnelle**, **vollständige**oder **Benutzerdefiniert**, und wählen Sie dann auf **Jetzt scannen**.

Sie können den Status eines Vorgangs remote anzeigen, indem der Link **Remote Vorgänge** in der unteren rechten Ecke der Intune-Konsole auswählen. Das Dialogfeld **Remote Vorgangsstatus** Listen aktuellen remote Vorgänge, Vorgangsstatus, Gerätenamen und alle dokumentierten Fehler. Darüber hinaus einen Link zu Problembehandlungsinformationen, sofern zutreffend.

## Monitor Endpunkt Schutz
Sie können den Status der Malware auf Ihren Computern überwachen, mithilfe des Arbeitsbereichs **Schutz** der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/). In diesem Arbeitsbereich enthält zwei Seiten:
 - **Überblick über Schutz** -zeigt wichtige Probleme als Links, die Sie für Weitere Informationen auswählen können. Einbeziehen von Problemen, die möglicherweise angezeigt werden:
  - **Schadsoftware Instanzen benötigen, die Sie nachverfolgen** – klicken Sie auf der Link, um eine Liste der Schadsoftware anzuzeigen, einschließlich der auszuführenden Aktion Probleme, die zur Lösung des Problems absolviert werden muss. Sie können weiteren Untersuchen dieser Liste, um anzuzeigen, welchen Computern sind betroffen.
  - **Computer mit Schadsoftware, die nachverfolgung benötigen** – klicken Sie auf der Link, um alle Computer mit nicht aufgelöst Schadsoftware anzuzeigen, sowie der auszuführenden Aktion Probleme, die zur Lösung des Problems absolviert werden muss.
  - **Geräte, die nicht geschützt werden** – klicken Sie auf den Link, um den Computer anzuzeigen, die nicht von einem beliebigen Endpunkt Schutzsoftware geschützt sind, da keine Software installiert ist oder ein Fehler auftritt. Wählen Sie einen Computer, um weitere Details anzuzeigen.
  - **Geräte mit einem anderen Endpunkt Schutz Anwendung ausführen** – klicken Sie auf den Link, um die Computer anzuzeigen, die eine Drittanbieter-Endpunkt Schutz Anwendung ausgeführt werden.
 - **Alle Schadsoftware** - zeigt eine Liste aller aktiven Schadsoftware, die auf Ihrem Computer gefunden wird. Sie können diese Liste, um allen Computern, die betroffen sind, finden unter einen bestimmten Teil der Malware erkunden, oder wählen Sie eine der folgenden Aufgaben:
  - **Eigenschaften der Datenansicht** – öffnet eine Seite mit weiteren Informationen über die ausgewählten Schadsoftware.
  - **Informationen zu dieser Schadsoftware** – öffnet ein Thema aus der Microsoft Malware Protection Center mit weiteren Informationen über die Schadsoftware.

> [!IMPORTANT]
> Der **Schutz** Arbeitsbereich wird nicht in der Verwaltungskonsole angezeigt, bis Sie den Client installiert haben und mindestens einem Computer Client verwaltet werden.

  ![Monitor Endpunkt Schutz](./media/pol-sa-ep-monitor.png)

### Wie Sie zuletzt verwendete Erkennung Pfade für Schadsoftware auf Computern anzeigen
Intune kann die Pfade von bis zu 10 der am häufigsten zuletzt erkannten Instanzen von Schadsoftware auf einem Gerät anzeigen. Der **Aktuelle Erkennung Pfad** ist standardmäßig deaktiviert. So aktivieren Sie diese Ansicht:

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** > **Alle Geräte** > **Schadsoftware**.

2.  Klicken Sie auf eine Spaltenüberschrift. Eine Liste der verfügbaren Spalten wird angezeigt.

3.  Wählen Sie das Kontrollkästchen **Aktuelle Erkennung Netzwerkpfade** in der Liste aus. Die **Aktuelle Erkennung Pfade** Spalte wird eingeblendet und zeigt bis zu 10 der am häufigsten zuletzt überwachten Schadsoftware Instanzen auf dem Gerät.

## Führen Sie eine Überprüfung Schadsoftware oder aktualisieren Sie die Schadsoftware Definitionen auf einem computer
Intune kann entweder einen vollständige oder schnelle Schadsoftware Scan ausführen, mithilfe von Endpunkt Schutz oder Windows Defender auf einem Remote verwalteten Computer, auf dem der Intune-Client installiert ist.

1. Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/)zu **Gruppen** > **Übersicht** > **Alle Geräte** > **Alle Computer**, und wählen Sie den Computer, die Sie gezielt ansprechen möchten.

2. Wählen Sie aus der Dropdownliste **Remote-Aufgaben** , und wählen Sie den Vorgang auf dem Remotecomputer ausführen.




## Benötigen Sie weitere Hilfe?
Weitere Hilfe und Support finden Sie unter [Behandeln von Problemen mit Endpunkt Schutz in Microsoft Intune](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune).

### Siehe auch
[Richtlinien zum Schutz von Windows-PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md)
