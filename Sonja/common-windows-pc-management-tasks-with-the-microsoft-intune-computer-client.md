---
title: Allgemeine Aufgaben zur Verwaltung von Windows-PC | Microsoft Intune
description: "Überprüfen Sie die Aufgaben in diesem Thema Informationen zum Verwalten von Windows-PCs, die den Software Intune-Client ausgeführt werden."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 9ef18ee054928fcfb12a36fe8ac3ad3c2909f6c1
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Allgemeine Aufgaben zur Verwaltung von Windows-PC mit dem Intune Software client
Überprüfen Sie die Aufgaben in diesem Artikel erfahren Sie, wie Ihr Computer verwalten, die den Intune Software Client ausführen. Wenn den Client noch nicht auf Ihrem Computer installiert haben, finden Sie unter [installieren den Software Intune-Client](install-the-windows-pc-client-with-microsoft-intune.md).


## Verwenden Sie Richtlinien für den PC-Verwaltung zu vereinfachen.

Windows-PCs, die mit der Intune Software Client Intunes **Computers** Informationsverwaltungsrichtlinien verwaltet werden kann.

![Richtlinien Vorlage für Windows-PCs](../media/pc_policy_template.png)

### Verwalten von Microsoft Intune Center
Benutzer finden Sie unter dem Intune Software Client als **Microsoft Intune Center**. Im Microsoft Intune Center können Benutzer an:

-   Abrufen von Applications vom Unternehmen-Portal.

-   Nach Updates suchen.

-   Verwalten von Microsoft Intune Endpunkt Schutz.

-  Remoteunterstützung anfordern.

Im Microsoft Intune Center wird auf allen verwalteten Computern installiert. Sie können die folgenden Einstellungen in einer Richtlinie Intune konfigurieren und diese für Benutzer in Microsoft Intune Center angezeigt werden:

|Einstellung der Richtlinie|Details|
|------------------|--------------------|
|**Namen**|Der Name des Administrators, die den Computer verwaltet.<br /><br />Maximale Länge: 40 Zeichen|
|**Rufnummer**|Die Telefonnummer des Administrators an, die den Computer verwaltet werden.<br /><br />Maximale Länge: 20 Zeichen|
|**E-Mail-Adresse**|Die e-Mail-Adresse des Administrators, die den Computer verwaltet.<br /><br />Maximale Länge: 40 Zeichen|
|**Namen der Website**|Der Name Ihrer Supportwebsite für Benutzer.<br /><br />Maximale Länge: 40 Zeichen|
|**Website-URL**|Die URL Ihrer Supportwebsite.<br /><br />Maximale Länge: 150 Zeichen|
|**Notizen**|Eine Notiz, die für Benutzer angezeigt wird.<br /><br />Maximale Länge: 120 Zeichen|

## Softwareupdates Einstellungen
Verwenden Sie Richtlinien so konfigurieren Sie die Einstellungen, die verwaltete Computer verwenden sollen, aktivieren Sie für, und Laden Sie Softwareupdates von Microsoft und von Drittanbietern. Diese Updates beifügen nicht Betriebssystem-Upgrades (d. h. Aktualisieren von Windows 7 auf Windows 10 oder von einer Version von Windows-10-Upgrades auf eine neuere Version). Weitere Informationen finden Sie unter [Beibehalten Windows PCs auf dem neuesten Stand mit Softwareupdates von Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).

### Endpunkt Schutz Einstellungen
Verwenden Sie Richtlinien für Endpunkt Schutz konfigurieren, die Sie dann auf verwalteten Computern bereitstellen. Dies umfasst Zeitpläne und Aktionen an, wenn Malware erkannt wird. Weitere Informationen finden Sie unter [secure Windows PCs mit Endpunkt Schutz für Microsoft Intune helfen](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

## Windows-Firewall-Einstellungen
Richtlinien vereinfachen die Verwaltung von Windows-Firewall-Einstellungen auf verwalteten Computern. Details finden Sie unter [Windows-PCs mit Windows-Firewall-Richtlinien in Microsoft Intune schützen](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md).

## Ansicht Hard- und Software inventory
Intune sammelt detaillierte Informationen zur Hardware und Software von verwalteten Computern. Verwenden Sie die Informationen in den folgenden Verfahren, um weitere Informationen zum Erstellen:

-   Einen Bericht, der Informationen zu den Hardwarefunktionen der Computer aufgeführt.

-   Einen Bericht, der die Software auf jedem Computer installiert aufgeführt.

-   Informationen zum Aktualisieren einer Inventory Computern, um sicherzustellen, dass die Daten im Bericht aktiv ist.

### Zum Anzeigen von Informationen zu Ihrem Computer

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Berichte** &gt; **Computer Inventory Berichte**.

2.  Übernehmen Sie auf der Seite **Neue Berichte erstellen** die Standardwerte oder bearbeiten Sie, um die Ergebnisse zu filtern, die vom Bericht zurückgegeben werden. Beispielsweise können Sie auswählen, dass nur Computer unter Windows 8.1 im Bericht angezeigt werden.

3.  Wählen Sie **Bericht anzeigen** , um den **Computer Inventory Bericht** in einem neuen Fenster öffnen aus.

    Sie können den Bericht anhand einer der Spalten, wie **Name**, **Gehäusetyp** oder **Hersteller** durch Auswahl jede Spaltenüberschrift sortieren.

### Die Software auf Ihrem Computer installierten anzeigen

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Berichte** &gt; **Softwareberichte erkannt**.

2.  Übernehmen Sie auf der Seite **Neue Berichte erstellen** die Standardwerte oder bearbeiten Sie, um die Ergebnisse zu filtern, die vom Bericht zurückgegeben werden. Beispielsweise können Sie auswählen, dass nur die Software von Microsoft veröffentlichten im Bericht angezeigt wird.

3.  Wählen Sie **Bericht anzeigen** , um den **Erkannt Software Bericht** in einem neuen Fenster öffnen aus.

    Sie können den Bericht nach Spalten, wie **Name**, **Publisher** oder **Kategorie** durch Auswählen jede Spaltenüberschrift sortieren. Erweitern Sie Sie die Updates in der Liste, um weitere Details (wie der Computer, auf denen es installiert ist) anzeigen, indem Sie auf den Pfeil neben dem Element klicken.

### Aktualisieren von Inventory Computer, um sicherzustellen, dass es aktiv ist.

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Geräte** (oder eine andere Gruppe mit dem Computer für die Sie Inventory aktualisieren möchten).

2.  Wählen Sie einen Computer, oder drücken Sie und halten Sie **STRG** , um mehrere Computer auszuwählen.

3.  Wählen Sie auf der Taskleiste aus **Remoteaufgaben** &gt; **Inventory aktualisieren**.

4.  Wählen Sie zum Anzeigen des Vorgangsstatus **Remoteaufgaben** in der unteren rechten Ecke der Seite ein.

    Das Dialogfeld **Vorgangsstatus** zeigt mit aktuellen remote Vorgänge, Vorgangsstatus, Gerätenamen und alle dokumentierten Fehler, und enthält einen Link zu Informationen zur Problembehandlung.


## Remote neu starten Sie, einem Windows-PC

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Geräte** (oder eine andere Gruppe mit dem Computer neu gestartet werden soll).

2.  Wählen Sie einen oder mehrere Computer aus, und wählen Sie dann **Remote Vorgänge** &gt; **Computer neu**.

3.  Wählen Sie zum Anzeigen des Vorgangsstatus **Remoteaufgaben** in der unteren rechten Ecke der Seite ein.

4.  Überprüfen Sie im Dialogfeld **Vorgangsstatus** der aktuellen remote Vorgänge, Vorgangsstatus, Gerätenamen und alle dokumentierten Fehler aus.

## Deaktivieren von einem computer

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Geräte** (oder eine andere Gruppe mit dem Computer Sie nicht mehr verwenden möchten).

2.  Wählen Sie die Geräte, die Sie nicht mehr verwenden möchten, und wählen Sie dann die **Außerkraftsetzungsrichtlinie/zurücksetzen**.

Um einen Computer erneut in Intune registrieren, installieren Sie den Software-Client auf dem Computer mit Anleitungen in [der Windows-PC-Client mit Microsoft Intune installieren](install-the-windows-pc-client-with-microsoft-intune.md)aus.

Wenn Sie ein Computer auf Intune zugreifen kann, wird eine Meldung im **Dashboard** -Arbeitsbereich angezeigt.

Wenn Sie einen Computer zurückziehen:

-   Es wird aus dem Intune Management und Inventory entfernt, und die Lizenz zugeordnet auf dem Computer für die Wiederverwendung zur Verfügung gestellt wird. Zurückziehen/zurücksetzen entfernt den Intune Software Client jedoch apps oder Daten nicht vom Computer entfernt. Diese Einstellung von Websites führt auf dem Computer keine vollständige zurücksetzen.

-   Der Status wird in der Intune Verwaltungskonsole nicht mehr angezeigt.

-   Intune entfernt den Software Client vom Computer. Wenn der Computer nicht mit dem Intune-Dienst verbunden ist, wird der Software-Client beim nächsten entfernt werden sie Herstellen einer Verbindung.

-   Microsoft Intune Endpunkt Schutz wird vom Computer entfernt. Wenn der Computer verfügt über ist eine andere Endpunkt Anwendung installiert und es deaktiviert, diese Anwendung wieder aktiviert werden kann, nachdem Microsoft Intune Endpunkt Schutz entfernt wird, um sicherzustellen, dass Ihr Computer geschützt sind.

-   Alle Richtlinien werden vom Computer entfernt, und die Werte, die von der Richtlinie festgelegt wurden geändert werden.

-   Der Computer empfängt Softwareupdates oder Schadsoftware Definitionsupdates nicht mehr aus dem Intune-Dienst.

-   Je nachdem, wie sie konfiguriert sind können nicht mehr genutzten Computer weiterhin Updates mithilfe von Windows Server Update Services, Windows Update oder Microsoft Update zu erhalten.

    > [!IMPORTANT]
    > Wenn die Clientsoftware mithilfe einer Gruppe Objekt (Gruppenrichtlinienobjekt) installiert wurde, müssen Sie die Gruppe Objekt (Gruppenrichtlinienobjekt) entfernen, bevor Sie die Clientsoftware, um zu verhindern, dass die Software neu installiert wird entfernen können.

    Wenn der Client nicht deinstallieren können, lesen Sie [Behandeln von Problemen mit Endpunkt Schutz](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) Weitere Hilfe aus.

## Verwalten der Benutzer-Gerät verknüpfen
Vor der Bereitstellung von Software für einen Benutzer müssen Sie auf den Computer des Benutzers verknüpfen. Sie können einen Benutzer auf mehreren Computern verknüpfen, aber jeder Computer kann nur ein Benutzer verknüpft werden. Benutzer werden automatisch für alle Computer verknüpft, die sie mithilfe des Portals Unternehmen in Intune zu registrieren.

### Zum Verknüpfen eines Benutzers mit einem computer

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Geräte** (oder eine andere Gruppe mit dem Computer Sie einem Benutzer verknüpfen möchten).

2.  Wählen Sie den Computer, den Sie einen Benutzer verknüpfen möchten, und wählen Sie dann auf **Link Benutzer**.

    Das Dialogfeld **Link Benutzer** zeigt eine Liste der verfügbaren Benutzer mit ihrer Benutzer-ID, Anzeigename und die Anzahl der Computer auf, denen gegenwärtig verknüpft ist. Wenn ein Benutzer bereits mit dem ausgewählten Computer verknüpft ist, werden die Namen des Benutzers und Benutzer-ID unter dem **aktuellen Benutzer**angezeigt. Wenn der Computer nicht für alle Benutzer verknüpft ist, wird **Keine Benutzer** unter **Aktueller Benutzer**angezeigt.

3.  Führen Sie eine der folgenden Aktionen aus:

    -   Verlassen den Computer verknüpft deren aktuellen Benutzer, sofern vorhanden, wählen Sie **Abbrechen**aus.

    -   Um den Link für den aktuellen Benutzer, zu entfernen, sofern vorhanden, wählen Sie **Hyperlink entfernen** &gt; **OK**.

    -   Wählen Sie den Computer eine Verknüpfung zu einem neuen Benutzer in der Liste **alle Benutzer** einen Benutzer ein. Bestätigen Sie, dass die Benutzerdaten korrekt sind, und wählen Sie dann auf **OK**.

> [!TIP]
> Wenn Sie Endbenutzer Möglichkeit zum Verknüpfen von selbst auf Computern einschränken möchten, aktivieren Sie die Option **Benutzer beschränken Möglichkeit zum Verknüpfen von selbst auf Computern** in die Richtlinie **Microsoft Intune Agent Einstellungen** aus.

## Anfordern und bieten von Remoteunterstützung für Windows-PCs

Microsoft Intune können die [TeamViewer](https://www.teamviewer.com) Software, separat erworben werden, und damit die um Benutzer von PCs zu können, die das Intune ausgeführt werden Software Client erhalten Hilfe zur Remoteunterstützung aus. Wenn ein Benutzer Hilfe aus dem Microsoft Intune Center anfordert, werden Sie informiert, durch eine Benachrichtigung können, die Anfrage annehmen und geben Sie dann auf Hilfe.
Diese Funktion ersetzt die vorhandene Windows-Remoteunterstützung-Funktionalität in Intune.


### Bevor Sie beginnen

Vor dem Einrichten von und Antworten auf Besprechungsanfragen Remoteunterstützung, müssen Sie sicherstellen, dass die folgenden Komponenten angeordnet sind:

- [Für ein Konto TeamViewer registriert](https://login.teamviewer.com/LogOn#register) müssen sich bei der Website TeamViewer anzumelden.
- Windows-PCs, die Sie verwalten möchten muss [von der Windows-PC-Client verwaltet](manage-windows-pcs-with-microsoft-intune.md)
- Alle von Intune unterstützten PC unter Windows-Betriebssysteme können verwaltet werden.

### Konfigurieren der TeamViewer Verbinder

1. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com) **Administrator**aus.
2. Wählen Sie im Arbeitsbereich **Administrator** **TeamViewer**aus.
3. Wählen Sie auf der Seite **TeamViewer** **TeamViewer Verbinder**klicken Sie unter **Aktivieren**aus.
4. In der **TeamViewer aktivieren** Sie im Dialogfeld Ansicht und dann **annehmen** der Lizenzbedingungen. Wenn Sie eine Lizenz TeamViewer nicht bereits besitzen, wählen Sie **erwerben einer Lizenz TeamViewer**.
5. Nachdem das TeamViewer Browserfenster geöffnet wird, melden Sie sich bei der Website mit Ihren Anmeldeinformationen TeamViewer.
6. Auf der Website TeamViewer lesen, und klicken Sie dann die Optionen zum Herstellen von Verbindungen mit TeamViewer Intune dürfen annehmen.
7. In der Intune-Verwaltungskonsole stellen Sie sicher, dass das Element **TeamViewer Verbinder** mit **aktiviert**angezeigt wird.


### Öffnen Sie eine Besprechungsanfrage Remoteunterstützung (Endbenutzer)

1. Öffnen Sie auf einem Windows-PC-Client **Microsoft Intune Center**aus.
2. Wählen Sie unter **Remoteunterstützung** **Remoteunterstützung anfordern**aus.
3. Nachdem Sie die Anforderung (siehe unten) zu genehmigen, öffnet TeamViewer auf dem Client. Der Benutzer muss keine Nachrichten gibt an, dass Sie der Webbrowser versucht, öffnen Sie die Anwendung TeamViewer annehmen.
4. Einem Benutzer wird eine Meldung mit der Frage, ob Sie ihren Computer steuern können. Sie müssen diese Meldung weiterhin zu übernehmen.
5. Während der Sitzung Remoteunterstützung sieht der Benutzer ein Fenster, das sie zeigt, dass Sie verbunden sind. Wenn sie dieses Fenster schließen, wird die remote-Sitzung beendet.

### Antworten Sie auf eine Besprechungsanfrage Remoteunterstützung

1. Wenn ein Benutzer eine Anforderung der Remoteunterstützung übermittelt, können Sie es anzeigen, klicken Sie im Arbeitsbereich **Benachrichtigungen** unter **Überwachung** > **Remoteunterstützung**. Beispiel:
> ![Screenshot einer Anforderung der Remoteunterstützung](./media/team-viewer.png)

<br>Wenn eine Anforderung für mehr als 4 Stunden unbeantwortete geht, wird es entfernt.
2. Wählen Sie zum Annehmen der Anfrage **Anforderung genehmigen und Remote Assistance starten**aus.
3. Wählen Sie im Dialogfeld **eine neue Remoteunterstützung Anforderung steht noch aus** **Annehmen der Anfrage Remoteunterstützung**. Falls es noch nicht installiert ist, wird der TeamViewer alle notwendigen apps auf Ihrem Computer installiert.
4. TeamViewer benachrichtigt dann den Endbenutzer die Kontrolle über ihre PC werden soll. Nachdem der Benutzer die Anforderung akzeptiert hat, TeamViewer Fenster geöffnet wird, und Sie können dem Computer steuern.

Klicken Sie in einer Sitzung mit Remoteunterstützung, können Sie alle verfügbaren TeamViewer Befehle remote-PC steuern. Hilfe bei der folgenden Befehle wird herunterzuladen Sie die [Manuelle für Fernbedienung](http://www.teamviewer.com/en/support/documents/) von der Website TeamViewer.

### Schließen Sie die Sitzung Remoteunterstützung

Wählen Sie im Menü **Aktionen** des Fensters **TeamViewer** **Sitzung beenden**aus.
