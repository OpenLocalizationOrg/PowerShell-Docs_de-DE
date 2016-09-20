---
title: Erhalten einer Benachrichtigung von Benachrichtigungen | Microsoft Intune
description: Erfahren Sie, wie Benachrichtigungen, dass Sie an, was in Microsoft Intune passiert.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 396ea714-0433-4bd5-a934-8d0b477f28e4
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: da881ccb5ed26fbec77e1964ff85f7adccb48d53
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Erhalten einer Benachrichtigung von Microsoft Intune Benachrichtigungen
Benachrichtigungen, die Sie an, was in Microsoft Intune passiert beibehalten.

Beispielsweise können Sie Benachrichtigungen über die folgenden Ereignisse benachrichtigen:

-   Ein Problem mit dem Exchange-Connector die Verwaltung mobiler Geräte wirkt sich auf

-   Auf einem Computer wurde Malware gefunden.

-   Ein Konflikt zwischen zwei Intune-Richtlinien wurde erkannt.


## Funktionsweise von Benachrichtigungen
Benachrichtigungen werden generiert basierend auf **Benachrichtigen Arten**, einen Satz von vorkonfigurierten Regeln Intune integriert. Beispielsweise den Typ der Warnung, **Cloud-Speicher hat 10 % freier Speicherplatz oder weniger**, benachrichtigt Sie beim Ausführen von Speicherplatz zu Ihrer apps in der Cloud zu speichern. Aktivieren oder Deaktivieren des Benachrichtigungssounds Arten, und konfigurieren Sie die Eigenschaften für jeden benachrichtigen. Beispielsweise können mit der oben angegebenen Typ der Warnung, Sie konfigurieren:

-   **Zustand:** Gibt an, ob dieser Typ der Warnung aktiviert oder deaktiviert ist

-   **Schwere:** Wie ernst diese Warnung wird?


|Schwere|Details|
|--------|-------|
    |![Warnung vom Typ Kritisch](../media/Critical-Alert.jpg)|Gibt ein schwerwiegenden Problem, das Sie so früh wie möglich, beispielsweise untersuchen sollte an, ob es sich bei Malware auf einem Computer erkannt wurde.|
    |![Warnung](../media/Warning-Alert.jpg)|Zeigt an, ein Problem, das ist nicht aktuell schwerwiegende aber möglicherweise sind kritisch, wenn Sie darauf, zur Teilnahme an nicht werden beispielsweise Sicherheitsupdates warten auf installiert sein.|
    |![Warnung Information](../media/Informational-Alert.jpg)|Gibt an, dass die Informationen, die entscheidend, Ihre Vorgänge, beispielsweise eine neue Version von Exchange Connector ist nicht verfügbar ist.|

Möglicherweise müssen Sie andere Arten benachrichtigen verschiedene Elemente, die Sie konfigurieren können, wie der Prozentwert der Geräte, die durch ein bekanntes Problem betroffen sein, bevor eine Warnung generiert wird.

**Wenn die Kriterien in einem benachrichtigen Typ erfüllt ist, wird eine Warnung generiert und angezeigt, in der die Intune-Verwaltungskonsole.**

Darüber hinaus können Sie konfigurieren Intune per e-Mail benachrichtigt werden, wenn eine Warnung generiert wird.

## Einrichten von Benachrichtigungen
Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Administrator** &gt; **Benachrichtigungen und Benachrichtigungen**, und wählen Sie dann eine der folgenden Aufgaben:

|Aufgabe|Beschreibung|
|--------|---------------|
|**Benachrichtigen Typen**|Wählen Sie den Typ der Warnung, den Sie konfigurieren möchten, und führen Sie dann eine der folgenden Aktionen aus:<br /><br />Wählen Sie **Konfigurieren**. Klicken Sie im Dialogfeld **Benachrichtigungstyp konfigurieren** konfigurieren Sie die gewünschten Einstellungen, und wählen Sie dann auf **OK**.<br /><br />**Aktivieren** oder **Deaktivieren** Sie die Benachrichtigung.<br /><br />Erweitern Sie den Knoten **Benachrichtigung Arten** , und wählen Sie eine Kategorie aus, um nur die Benachrichtigung Arten in dieser Kategorie anzuzeigen.|
|**Empfänger**|Wählen Sie **Hinzufügen** , um eine neue e-Mail-Adresse hinzuzufügen, die die e-Mail-Benachrichtigungen erhalten, die Sie einrichten.<br /><br />Sie können auch **Bearbeiten** oder **Löschen** einer vorhandenen Empfänger.<br /><br />Um Benachrichtigungen erhalten möchten, müssen Sie auch diese e-Mail-Adresse als unter **Regeln für die Benachrichtigung**Empfänger hinzufügen.|
|**Benachrichtigungsregeln**|Konfiguriert Regeln, die definieren, die an eine e-Mail-Benachrichtigung gesendet wird. Sie können:<br /><br />**Wählen Sie eine vorhandene Regel** - wählen Sie eine Regel aus, und wählen Sie dann auf **Empfänger auswählen**. Sie können dann alle Empfänger auswählen, die eine e-Mail-Nachricht erhalten sollen, wenn eine Warnung, die mit dieser Regel erfüllt generiert wird.<br /><br />**Erstellen einer neuen Regel** - Geben Sie einen Namen für die Regel ein, wählen Sie die Benachrichtigung Kategorien und benachrichtigen schwere, die auf die Regeln anzuwenden, wählen die Gerätegruppen, denen die Regel gilt für, und wählen Sie die Benutzer, die eine e-Mail-Nachricht erhalten sollen, wenn eine Warnung generiert wird.<br /><br />Sie können auch **Aktivieren**, **Deaktivieren**, **Bearbeiten**oder **Löschen** einer vorhandenen Regel.|

## Arbeiten mit Benachrichtigungen
Verwenden Sie die folgenden Optionen helfen Ihnen bei der Arbeit mit Benachrichtigungen der Administrator Intune-Verwaltungskonsole.

|Option|Beschreibung|
|----------|---------------|
|**Aktive Benachrichtigungen anzeigen**|Wählen Sie eine der:<br /><br />**Anzeigen einer Benachrichtigung Zusammenfassung** – im **Dashboard** -Arbeitsbereich, werden die oberen Fehler im Bereich Benachrichtigungen angezeigt. Auswählen des Bereichs, um weitere ausführliche Informationen finden Sie unter.<br /><br />Darüber hinaus können Sie eine Zusammenfassung Benachrichtigung auf der Seite **Übersicht** des Arbeitsbereichs **Benachrichtigungen** anzeigen.<br /><br />**Anzeigen aller Benachrichtigungen** - wählen Sie im Arbeitsbereich **Benachrichtigungen** **Alle Benachrichtigungen**aus.|
|**Hinweise anzeigen**|Wählen Sie eine der:<br /><br />Wählen Sie im **Dashboard** -Arbeitsbereich **bemerkt**.<br /><br />Wählen Sie im Arbeitsbereich **Benachrichtigungen** **Alle Benachrichtigungen** &gt; **bemerkt**.|
|**Schließen einer Benachrichtigung**|Wählen Sie in der Liste der Benachrichtigungen die Warnung zu schließen, und wählen Sie die **Benachrichtigung zu schließen**.<br /><br />Geschlossene Benachrichtigungen werden nach 90 Tagen endgültig gelöscht.|
|**Erneutes Aktivieren einer geschlossenen Benachrichtigung**|Setzen Sie in der Liste der Benachrichtigungen **Filter** Dropdown-Liste in **geschlossen**.<br /><br />Klicken Sie in der Liste der geschlossenen Benachrichtigungen wählen Sie die Benachrichtigung, die Sie erneut aktivieren möchten, und wählen Sie dann **Benachrichtigung reaktivieren möchten**.|
Intune Benachrichtigungen bleiben aktiv bis:

-   Das Problem, das die Benachrichtigung verursacht hat eine feste Position

-   Schließen Sie manuell die Benachrichtigung

-   45 Tage bestanden wurden, da die Warnung erzeugt wurde

> [!TIP]
> Wenn die gleiche Benachrichtigung von Geräten, die verschiedenen Betriebssysteme ausgeführt werden generiert wird, möglicherweise mehrere Versionen der gleichen Warnung in der Liste der Benachrichtigungen angezeigt.

### Siehe auch
[Überwachung und Berichte mit Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
