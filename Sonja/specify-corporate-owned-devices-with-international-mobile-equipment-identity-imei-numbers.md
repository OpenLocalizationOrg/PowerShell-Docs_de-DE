---
title: Geben Sie die Nummern IMEI | Microsoft Intune
description: "Microsoft Intune können Administratoren IMEI Zahlen für mobilen Geräteplattformen zur Identifizierung Ihres Unternehmens im Besitz eines mobile Geräten importieren"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 09902b33cc63b991ec3de3b82860fa93d347f472
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Geben Sie im Unternehmen im Besitz eines Geräte mit internationalen mobile Geräte Identität (IMEI) Zahlen
Microsoft Intune können Administratoren internationale mobile Geräte Identität (IMEI) Zahlen für Plattformen für mobile Geräte mit einer IMEI-Nummern zum Identifizieren von mobilen Geräten im Unternehmen im Besitz importieren. Nachdem Intune registriert, können Geräte mit den importierten IMEI Zahlen angezeigt werden, klicken Sie unter **Gruppen** > **Übersicht** > **Alle Geräte**. **Gerätegruppe** **Corporate** Anzeigegeräte mit den importierten IMEI Zahlen in der Spalte **Besitz** aufgeführt.

1. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com) **Gruppen** &gt; **Alle Geräte** &gt; **Alle Corporate Pre-enrolled Geräte** &gt; **Durch IMEI (alle Plattformen)**, und wählen Sie dann auf **... Geräte hinzufügen**. Sie können Geräte auf zwei Arten hinzufügen:

    -   **Hochladen einer CSV-Datei mit fortlaufenden Zahlen** – Erstellen einer durch Trennzeichen getrennte Wert (CSV) Liste von zwei Spalten ohne eine Kopfzeile 5000 Geräte oder 5 MB pro CSV-Datei zugänglich.

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;#1-Gerätedetails&gt;|
        |&lt;IMEI #2&gt;|&lt;#2-Gerätedetails&gt;|
        Diese CSV-Datei, die bei der Anzeige in einem Text-Editor wird als angezeigt:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Manuelles Gerätedetails hinzufügen** - Geben Sie die IMEI Zahl und Gerät Details von bis zu fünf Geräte

   *Details* sind für administrative verwenden, damit Sie erkennen können, welche IMEI-Nummer ein Gerät zugeordnet ist. Diese Informationen nicht an das Gerät gesendet, aber in der Intune Verwaltungskonsole angezeigt.

2.   Wählen Sie auf **Weiter**.
3.  Im Bereich **Geräte überprüfen** können Sie überprüfen, welche Gerät IMEI Zahlen importiert werden. Sie können auch entscheiden, ob die **Details** für erneuten Import IMEI-Nummern zu überschreiben. Deaktivieren Sie das Kontrollkästchen **Überschreiben** , um die aktuellen Details zu erhalten. Wählen Sie auf **Fertig stellen** , um die Zahlen IMEI importieren.
4.  In der Liste **Nach IMEI (alle Plattformen)** werden die hinzugefügten IMEI Zahlen und Beschreibungen hinzugefügt.

Wenn das Gerät mit dieser Anzahl IMEI registriert wird, in der Regel, wenn ein Benutzer die app-Portal Unternehmen installiert und schließt den Registrierungsprozess, das Gerät wird als Unternehmen, die im Besitz markiert werden und angezeigt, in der Gruppe **IMEI Geräte** registriert werden.
