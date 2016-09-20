---
title: "Softwareupdates für Windows-PCs | Microsoft Intune"
description: Intune hilft Ihnen der verwalteten Computer auf dem neuesten Stand halten, indem Sie die jeweils neuesten Updates sicherstellen und Softwareupdates schnell installiert sind.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: e26786066b98adf187a6cf3ccbf172e919871f50
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Windows-PCs in Microsoft Intune mit Softwareupdates auf dem neuesten Stand halten
Microsoft Intune helfen Ihnen zum Schützen des verwalteten Computers in eine Reihe von Methoden, einschließlich der Verwaltung von Softwareupdates, die Ihre Computer auf dem neuesten Stand halten, indem Sie die neuesten Patches und Software sicherzustellen schnell Updates installiert werden.

Wenn Sie noch nicht Intune-Client auf Ihrem Computer installiert haben, finden Sie unter [installieren den Windows-PC-Client, mit dem Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Wenn neue Updates aus Microsoft Update stehen, oder eine Aktualisierung von Drittanbietern erstellt haben und sie auf die verwaltete Computer verfügbar sind, wird auf der Seite **Übersicht** des Arbeitsbereichs **Updates** eine Benachrichtigung angezeigt. Nachdem Sie diese Benachrichtigungslink auswählen, können Sie dann verschiedene Vorgänge wie Weitere Informationen zu den Update anzeigen durchführen genehmigen oder degressive das Aktualisieren und Anzeigen der Computer, auf denen das Update installiert werden, wenn es genehmigt ist.

> [!IMPORTANT]
> Der Arbeitsbereich **Updates** wird nicht in der Verwaltungskonsole angezeigt, bis auf den Client installiert haben, und mindestens einem Computer Client erfolgreich verwaltet werden.

Wie Updates genehmigt und installiert haben, können Sie den Erfolg oder Fehler bei der Installation von der Intune-Verwaltungskonsole im Arbeitsbereich **Updates** überprüfen.

In den folgenden Abschnitten hilft Ihnen Software des verwalteten Computers auf dem neuesten Stand zu bleiben.

## Bevor Sie beginnen
Bevor Sie beginnen, erstellen und Genehmigen von Softwareupdates, konfigurieren und Bereitstellen von Richtlinien auf Ihrem Computer, die steuern, wann und wie die Updates installiert werden.

### So konfigurieren Sie die Richtlinieneinstellungen aktualisieren

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), die **Richtlinie** &gt; **Übersicht** &gt; **Richtlinie hinzufügen**.

2.  Konfigurieren und Bereitstellen einer Richtlinie **Microsoft Intune Agent Einstellungen** für die Update-Einstellungen. Sie können empfohlene Einstellungen verwenden oder Anpassen der Einstellungen. Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien, finden Sie unter [Allgemeine Windows-PC-Verwaltungsaufgaben mit dem Microsoft Intune Computer Client](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

Die folgende Tabelle zeigt die Werte, dass Sie die Richtlinie und auch die empfohlenen Werte, die verwendet werden, wenn Sie die Richtlinie anpassen nicht konfigurieren können. Sie können diese Einstellungen im Abschnitt **Updates** suchen.

  |Einstellung der Richtlinie|Details|
    |------------------|--------------------|
    |**Aktualisierung und Anwendung Erkennung Häufigkeit (Stunden)** |Gibt Intune Prüfungen nach neuen Updates und Anwendungen, wie häufig (von 8-22 Stunden) an.<br /><br />Wert empfohlen: **8** Stunden.|
    |**Automatisierte oder Aufforderung Installation von Updates und Anwendungen** |Gibt an, ob die Updates automatisch installiert werden, oder gibt an, ob der Benutzer vor der Installation aufgefordert wird. Außerdem können Sie diese Einstellung die Installation von Updates und Anwendungen zu planen.<br /><br />**Installieren von Updates und Applikationen automatisch als geplanten** Installationen Updates und Anwendungen, die mit dem angegebenen Zeitplan.<br /><br />Als abhängige Richtlinie festlegen gibt an, **automatische Wartung für Windows verwenden Computer** , im Zeitfenster Wartung Windows automatische Updates und Applikationen installiert werden.<br /><br />**Benutzer auffordern, für die Installation** der Benutzer aufgefordert, Updates installieren, wenn sie bereit sind.<br /><br />Empfohlene Werte:<br /><br />**Installieren von Updates und Applikationen automatisch als geplanten** ausgewählt<br /><br />**Tag geplant: jeden Tag**<br /><br />**Wie viel Zeit: 3:00 zurück**<br /><br />**Verwenden automatische Wartung für Windows Computern** ausgewählt|
    |**Zulassen Sie sofortige Installation von Updates, die unterbrechen Windows nicht** |**Zulassen** installiert Updates sofort nach sie heruntergeladen werden, eine Ausnahme bilden jedoch Updates, die unterbrechen möchten, oder starten Sie Windows erneut. Diese Updates werden entsprechend der Konfiguration der Einstellung für das **Automatische oder Aufforderung Installation von Updates** installiert.<br /><br />**Lassen Sie nicht** installiert Updates entsprechend der Konfiguration der Einstellung für das **Automatische oder Aufforderung Installation von Updates** .<br /><br />Wert empfohlen: **Zulassen** |
    |**Verzögerung Windows neu starten, nach der Installation von geplanten Updates und Applikationen (Minuten)** |Gibt an (von 1-30 Minuten), die Zeit, warten Sie nach der Installation von geplanten Updates und Applikationen Windows neu starten.<br /><br />Wert empfohlen: **15 Minuten** |
    |**Verpasste Verzögerung direkt nach Windows neu starten, um die Installation zu beginnen, geplante Updates und Applikationen (Minuten)** |Gibt an (von 1 bis 60 Minuten), wie lange warten, um die Installation von Updates und Applikationen zu starten, nachdem Windows neu gestartet wird, wenn ein geplantes Update verpasst wurde.<br /><br />Wert empfohlen: **5 Minuten**|
    |**Zulassen Sie Windows-Neustart nach der Installation von geplanten Updates und Applikationen steuern Benutzer angemeldet** |Gibt an, ob der Benutzer angemeldet einen Neustart von Windows beseitigt werden kann (wenn auf **Ja**festgelegt), oder benachrichtigt werden, der den automatischen Neustart von Windows (wenn auf **Nein**festgelegt). Wenn kein Benutzer angemeldet ist, wenn die geplante Installation von Updates und Applikationen abgeschlossen ist, wird Windows automatisch neu gestartet, wenn erforderlich. Beim Festlegen auf **Nein**, standardmäßig wird die Zeit vor dem Neustart von Windows auf 5 Minuten festgelegt.<br /><br />Wert empfohlen: **Ja**|
    |**Benutzer aufgefordert, Windows Intune-Client-Agent verbindliche Updates während der neu** |Gibt an, ob der angemeldeten Benutzer wird dazu aufgefordert werden, Windows neu zu starten, wenn eine obligatorische Intune Client-Aktualisierung von Windows neu starten erfordert.<br /><br />Wert empfohlen: **Ja**|
    |**Microsoft Intune-Client-Agent obligatorisch aktualisiert Installation Terminplan** |Terminpläne, wenn die Installation von Client-Updates ausgeführt werden.<br /><br />Wert empfohlen: nicht konfiguriert|
    |**Verzögerung zwischen Anweisungen, um nach der Installation von geplante Updates Windows neu starten und Applikationen (Minuten)** |Wie häufig (zwischen 1 und 1440 Minuten) angibt, der Benutzer aufgefordert, Windows neu zu starten, wenn ein geplante Aktualisierung oder eine Anwendung, die erfordert einen Neustart von Windows installiert ist, und der Benutzer wird den Neustart verzögert.<br /><br />Wert empfohlen: **30 Minuten** |

## Änderungen der Microsoft Update-software
Aktualisieren von Microsoft-Software erfordert sehr kleinen Arbeit aus. Bevor Sie beginnen, gibt es jedoch zwei Dinge zu konfigurierender:

-   **Produktkategorien und Update Klassifizierung** – definiert Kategorien und Klassifizierung der Updates, die Sie auf Computern zur Verfügung stellen möchten. Beispielsweise könnten Sie, dass nur wichtige Updates für Microsoft Office installiert werden sollen.

-   **Regeln für automatische Genehmigung** – diese Regeln automatisch bestimmte Arten von Update genehmigen und Ihr Verwaltungsaufwand verringern. Angenommen, möchten Sie alle wichtigen Softwareupdates automatisch genehmigen.

Verwenden Sie die beiden folgenden Verfahren Sie bereit sind, verwenden Sie Softwareupdates optimal nutzen können:

### Konfigurieren Sie die Produktkategorien und Update Klassifizierung, die Sie für verwaltete Computer zur Verfügung stellen möchten

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Administrator** &gt; **Updates**.

2.  Klicken Sie auf die **Diensteinstellungen: Updates** Seite, wählen Sie in der Liste **Produktkategorie** Update Kategorien, die Sie auf Computern zur Verfügung stellen möchten. Beachten Sie, dass die am häufigsten verwendeten Updates standardmäßig aktiviert sind.

    > [!IMPORTANT]
    > Um sicherzustellen, dass der Computer Updates zu erhalten, die von der Administrator genehmigt wurden, die Einstellung Windows Server Update Services (WSUS) Gruppenrichtlinien **angeben Intranet Microsoft Update-Dienstspeicherort** darf auf Computern, die mit Intune registriert wurden angewendet.

3.  Wählen Sie in der Liste **Aktualisieren Klassifizierung** der Klassen des Updates, die Sie für verwaltete Computer zur Verfügung stellen möchten. In diesem Fall sind die am häufigsten verwendeten Optionen standardmäßig aktiviert.

4.  Wählen Sie auf **Speichern** , um Ihre Auswahl zu speichern.

### So konfigurieren Sie die automatische Genehmigung für Softwareupdates von Regeln

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Administrator** &gt; **Updates**.

2.  Im Abschnitt **Regeln für automatische Genehmigung** für die **servereinstellungen: Updates** Seite, und wählen Sie **neu**.

3.  Klicken Sie auf der Seite " **Allgemein** " des Assistenten Regel automatische Genehmigung erstellen Geben Sie einen Namen und optional eine Beschreibung für die Regel ein.

4.  Wählen Sie auf der Seite **Produktkategorien** alle Produkte für die Updates automatisch genehmigt haben soll.

5.  Geben Sie auf der Seite **Klassifizierung aktualisieren** die Update-Einstufung, die automatisch genehmigt haben soll.

6.  Klicken Sie auf der Seite **Bereitstellung** folgendermaßen Sie vor:

    -   Wählen Sie die Computergruppen,, die Sie die neue Regel bereitstellen möchten, und wählen Sie dann auf **Hinzufügen**.

    -   Wenn Sie einen Stichtag für die Installation der Updates angeben möchten, aktivieren Sie das Kontrollkästchen **erzwingen einen Stichtag für die Installation für diese Updates** , und wählen Sie dann in der Liste der **Installation Stichtag** Termin für die Installation.

        > [!NOTE]
        > Wenn Sie einen Stichtag für die Installation angeben, möglicherweise verwaltete Computer eine oder mehrere Neustarten erfordern, nach Ablauf des Intervalls Stichtag.

    -   Wenn Sie fertig sind, wählen Sie **Weiter**.

7.  Klicken Sie auf der Seite **Zusammenfassung** überprüfen Sie die Einstellungen für die neue Regel zu, und wählen Sie dann auf **Fertig stellen**.

Die neue Regel werden im Abschnitt **Regeln für automatische Genehmigung** von der **Diensteinstellungen: Updates** Seite.

> [!NOTE]
> Beim Erstellen einer Regel für automatische Genehmigung erkannt nur zukünftige Updates genehmigt und werden nicht automatisch genehmigen zuvor vorhandene Updates, die in Intune bereits vorhanden sind. Wenn Sie diese Updates genehmigen müssen Sie die automatische Genehmigung Regel ausgeführt werden.


### Führen Sie zum Bearbeiten oder Löschen einer Regel automatisch genehmigten update

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Administrator** &gt; **Updates**.

2.  Im Abschnitt **Regeln für automatische Genehmigung** wählen Sie eine Regel, und führen Sie dann eine der folgenden Aktionen aus:

    -   Um die Regel zu bearbeiten, wählen Sie **Bearbeiten**aus, und ändern Sie dann auf die Regel, deren Parameter in der **Regel-Assistent für Update automatische Genehmigung**.

    -   Wenn die Regel ausführen möchten, wählen Sie **Ausführen ausgewählt**.

    -   Wenn Sie die Regel löschen möchten, wählen Sie **Löschen**aus.

        > [!NOTE]
        > Löschen einer Regel wirkt sich nicht auf früheren Updates aus, die durch die gelöschten Regel genehmigt wurden.

## Vorgenommen nicht von Microsoft Update-software
Sie können Updates für Software bereitstellen, die nicht von Microsoft vorgenommen werden. Dazu müssen Sie das Update Speicherplatz verschwendet Cloud verschaffen, nach dem Sie genehmigen oder ablehnen das Update stellt wie mit Microsoft-Software mit dem Assistenten **Aktualisieren hochladen** .

### Hochladen und Konfigurieren einer Drittanbieter-update

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/), die **Updates** &gt; **Übersicht** &gt; **Hochladen**.

2.  Wählen Sie auf der Seite **Aktualisieren Dateien** **Durchsuchen** , um den Setup-Dateien auszuwählen, die erforderlich sind, um das Update-Paket zu installieren. Die Datei kann eine Datei für Windows Installer (MSI-Datei), eine Windows Installer-Patch (.msp)-Datei oder ein Programm .exe-Datei sein. Sie können ebenfalls sind zusätzliche Dateien oder Ordner, die in denselben Ordner wie die Setupdatei sind.

    Die Gesamtgröße der ausgewählten Dateien hochladen wird angezeigt. Beachten Sie, dass diese Größe die Größe nicht komprimiert oder erweiterten Installation Dateien nicht enthalten ist.

3.  Nachdem Sie die Setup-Dateien angegeben haben, zeigt die Seite **Aktualisieren der Beschreibung** der Name, Beschreibung und Klassifizierung Software Informationen, die Intune aus der Software Setup-Dateien extrahiert. Sie können auswählen, eine Einstufung beschriften den Typ des Updates werden Sie bereitstellen (Updates, wichtige Updates, Sicherheitsupdates, Updaterollups oder Service Packs). Wählen Sie **Weiter** , wenn Sie fertig sind.

4.  Wählen Sie auf der Seite des Assistenten **Anforderungen** die Architektur (32-Bit-, 64-Bit- oder beide) und den Betriebssystemen der verwalteten Computer, die dieses Update verfügbar sein.

5.  Geben Sie auf der Seite **Erkennung Regeln** an, wie Intune bestimmt, ob das Update auf verwalteten Computern bereits vorhanden ist. Wenn Sie die Standardoption verwenden, Installationen **verwenden die Regeln für die Erkennung**, Intune immer das Update-Paket auf den Zielcomputern einmal.

    > [!NOTE]
    > Wenn Sie das Update setup-Datei, die Sie angegeben ist ein Windows Installer oder .msp-Datei, die **Erkennung Regeln** Seite des Assistenten wird nicht angezeigt. Dies ist, da Windows Installer und MSP-Dateien Eigene Anweisungen zum Auffinden von vorherigen Installationen enthalten.

    Wählen Sie eine oder mehrere der folgenden Regeln feststellen, ob das Update auf verwalteten Computern bereits installiert ist:

    -   **Datei vorhanden ist**

    -   **MSI-Produktcode vorhanden ist.**

    -   **Registrierungsschlüssel vorhanden ist**

6.  Finden Sie weitere Informationen, die erforderlich ist, so konfigurieren Sie die Regel Erkennung, wie etwa einen Dateipfad und Name, Windows Installer-Produktcode oder eines Registrierungsschlüssels deaktiviert, und wählen Sie dann auf **Weiter**.

7.  Klicken Sie auf der Seite des Assistenten **erforderliche Komponenten** Geben Sie die Software, die bereits installiert sein muss, bevor Sie dieses Update installiert werden kann. Können Sie **keine**angeben, wählen Sie ein Softwarepaket, die bereits hinzugefügt wurde, und von Intune verwaltet wird, oder Sie können eine der folgenden Regeln zur Beschreibung der Software angeben:

    -   **Datei vorhanden ist**

    -   **MSI-Produktcode vorhanden ist.**

    -   **Registrierungsschlüssel vorhanden ist**

8.  Finden Sie weitere Informationen, die erforderlich ist, so konfigurieren Sie die Regel Erkennung wie ein Dateipfad und Name, Windows Installer-Produktcode oder eines Registrierungsschlüssels deaktiviert, und wählen Sie dann auf **Weiter**.

9. Klicken Sie auf der Seite **Befehlszeilenargumente** des Assistenten können Sie alle erforderlichen Installationseigenschaften an die Installationsbefehlszeile so ändern Sie das Verhalten der Datei hinzufügen. Einige Software unterstützt beispielsweise die **Eigenschaft/q** Hintergrundinstallation aktivieren. Schlagen Sie in der Dokumentation für Ihre Software-Paket alle unterstützten Befehlszeilenargumente lernen. Geben Sie alle Befehlszeilenargumente Sie benötigen, und wählen Sie dann auf **Weiter**.

    > [!NOTE]
    > Wenn die Aktualisierung Hintergrundinstallation nicht unterstützt, können keine Installation des Updates Intune verwenden

10. Auf der Seite **Codes zurückgeben** des Assistenten können Sie angeben, wie die Eingabe aus dem Update codes Installation interpretiert werden. Standardmäßig verwendet Intune Industriestandard Absenderadresse Codes, um eine fehlgeschlagene oder erfolgreiche Installation von ein Update-Paket zu melden. Die angegebene Absenderadresse Codes sind:

|Code zurück|Details|
|---------------|------------------|
|**0**|Erfolg|
|**3010**|Erfolg mit Neustart|

11. Rückgabetyp Code, der nicht aufgeführt ist, wird einen Fehler betrachtet.
Einige Updates verwenden nicht standardmäßige Interpretationen für Codes zurückgegeben. In diesem Fall, können Sie eigene Interpretationen zurückgegebene Code angeben.

12. Geben Sie oder bearbeiten Sie die erforderlichen Absenderadresse Codes, und wählen Sie dann auf **Weiter**.

13. Überprüfen Sie auf der Seite **Zusammenfassung** des Assistenten die Aktionen, die übernommen, und wählen Sie dann auf **Hochladen** , um den Assistenten abzuschließen.

Die hochgeladene Aktualisierung wird in der Cloud-Speicher Intune gespeichert. Wenn Sie nicht ausreichenden freien Speicherplatz das Update-Paket hochgeladen haben, werden Sie diesen während während des Uploads benachrichtigt. Intune kann nicht ausreichenden freien Speicherplatz bis zu ermitteln, nachdem der Update Upload begonnen hat, da Setup komprimiert und für die Installationsdateien erforderlich mehr Platz aus, wenn diese nicht komprimiert ist.

Nachdem sie in Intune hochgeladen wurde, wird eine Aktualisierung von Drittanbietern im Arbeitsbereich **aktualisiert** **Alle Aktualisierungen** im Bereich angezeigt. Dann können Sie das Update bereitstellen und genehmigen. Weitere Informationen finden Sie unter den folgenden Abschnitt "Updates genehmigen und Ablehnen".

## Genehmigen und Ablehnen von updates
Wenn Updates installiert werden, wird eine Nachricht auf der Seite **Übersicht Updates** des Arbeitsbereichs **Updates** unter **Aktualisierungsstatus**angezeigt. Wählen Sie diese Meldung zum Öffnen der Seite **Alle Updates** , um anzuzeigen, welche Updates genehmigt werden.

Die Liste der **Filter** können Sie um nach Updates suchen zu erleichtern. Beispielsweise können Sie anzeigen, nur Updates, die nicht oder Updates, die ersetzt werden.

Wenn Sie ein Update aus der Liste auswählen, weitere Befehle zur Verfügung, mit denen Sie die Updates verwalten, wie in der folgenden Tabelle dargestellt:

|Aufgabe|Details|
|--------|--------------------|
|**Eigenschaften der Datenansicht**|Zeigt detaillierte Informationen über das Update, einschließlich der Anzahl der Computer, die verfügbar ist.|
|**Bearbeiten**|Nur Updates nicht von Microsoft. Können Sie die Eigenschaften des Updates zu bearbeiten.|
|**Genehmigen**|Das ausgewählte Update genehmigt und ermöglicht Sie so konfigurieren Sie die Gruppen ist, wird auf bereitgestellt werden. Weitere Informationen finden Sie unter die Vorgehensweise **zum Genehmigen von Updates** in diesem Thema.|
|**Ablehnen**|Vorherigen Genehmigungen für das Update entfernt, und blendet die von den Standardansichten aktualisieren. Darüber hinaus werden alle Berichtsdaten für das Update entfernt.<br /><br />Wenn Sie später eine abgelehnten Updates suchen möchten, setzen Sie den Filter auf der Seite **Alle Updates** auf **abgelehnt**. Dann können Sie dieses Update nach Bedarf genehmigen.<br /><br />Wenn Sie ein Update abgelehnt wurde, da das Update in Microsoft Update abgelaufen wurde, kann nicht das Update in der Intune-Verwaltungskonsole genehmigt werden.<br /><br />Wenn Sie eine Richtlinie Updates, die auf Computern bereitgestellt wird löschen, werden die Werte des betreffenden Richtlinieneinstellungen Updates für das Betriebssystem, das im Standardzustand zurückgesetzt, die auf dem Computer installiert ist.|
|**Löschen**|Nur Updates nicht von Microsoft. Löscht das ausgewählte Update.|
|**Hochladen**|Startet den **Hochladen Update** -Assistenten, mit dem Sie zum Hochladen von nicht-Microsoft-Updates, die Sie bereitstellen möchten.|

### Genehmigen von updates

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Updates** &gt; **Übersicht** &gt; **neuen Updates zu genehmigen**.

    Wählen Sie im Arbeitsbereich **Updates** **Übersicht** &gt; **neuen Updates zu genehmigen**.

    > [!NOTE]
    > Der **neuen Updates zu genehmigen** -Link im Statusbereich **Updates** angezeigt wird, nur wenn mindestens eine verwalteter Computer vorhanden ist, die ein Update benötigt genehmigt werden.

2.  Wählen Sie ein Update aus, überprüfen Sie die Aktualisierungseigenschaften am unteren Rand der Seite, um sicherzustellen, dass Sie das Update genehmigen, und wählen Sie dann auf **Genehmigen**möchten. Sie können mehrere Updates auswählen, indem Sie die **STRG** -Taste gedrückt halten, während Sie jedes Element auswählen.

3.  Klicken Sie auf der Seite **Gruppen auswählen** wählen Sie eine Gruppe aus, der Sie die Updates für bereitstellen möchten, und wählen Sie dann auf **Hinzufügen**. Wenn Sie die Gruppen angeben abgeschlossen haben, wählen Sie **Weiter**.

4.  Klicken Sie auf der Seite **Aktion Bereitstellung** gehen Sie für jede Gruppe in der Liste:

    -   Wählen Sie in der Liste der **Genehmigung** eine der folgenden Aktionen aus:

        -   **Installieren erforderlicher** - installiert das Update auf Computern in der angegebenen Gruppe.

        -   **Installieren Sie nicht** - Anwendungsmöglichkeiten nur Berichte und installieren Sie das Update nicht.

        -   **Installieren von verfügbar** – der Benutzer kann die Anwendung bei Bedarf vom Unternehmen-Portal installieren.

        -   **Deinstallieren** – entfernt Updates von Computern in der Gruppe gezielte.

            > [!IMPORTANT]
            > Auch wenn sie nicht durch Intune installiert wurde, wird das Update entfernt.

    -   Wählen Sie in der Liste der **Termin** eine der folgenden Aktionen aus:

        -   **Keine** – gibt an, dass keine Stichtag wird für die Installation des Updates erzwungen und Benutzer die Aktualisierung ständig ablehnen können.

        -   **So früh wie möglich** - Installationen das Update bei der nächsten Gelegenheit auf Zielcomputern ein.

        -   **Benutzerdefinierte** - gibt an, dass das Datum und die Uhrzeit, die genehmigt Updates installiert sind.

        -   **Eine Woche**, **zwei Wochen**, **einen Monat** – installiert das Update innerhalb des angegebenen Zeitraums.

5.  Wählen Sie **Fertig stellen** , um die Einstellungen zu speichern, oder **Abbrechen** , um verwerfen die Einstellungen, und kehren Sie zu der Liste der Updates zurück.

    > [!IMPORTANT]
    > Wenn die Aktion **Nicht installieren**, **Erforderlich installieren**oder **Deinstallieren** explizit für eine untergeordnete Gruppe konfiguriert wurde, wird eine Aktion für eine übergeordnete Gruppe so konfiguriert, dass alle untergeordneten vererbt.

6.  Aktivieren Sie im Detailbereich "am unteren Rand der Seite **Alle Updates** für Erinnerungsnachrichten über das Update.


### Siehe auch
[Richtlinien zum Schutz von Windows-PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md)
