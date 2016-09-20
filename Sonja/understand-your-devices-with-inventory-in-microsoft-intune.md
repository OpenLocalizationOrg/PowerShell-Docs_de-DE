---
title: "Grundlegendes zu Ihren Geräten mit Inventory | Microsoft Intune"
description: "Verwenden Sie zum Anzeigen von Informationen über die Hardware der Geräte, dass Sie verwalten Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: a195ca39169d2288d76b1337a003db8a0ae11997
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Grundlegendes zu Ihren Geräten mit Beständen in Microsoft Intune
Microsoft Intune ermöglicht Ihnen das Anzeigen der Bestandsaufnahme registrierten Geräte und Windows-PCs, die die Intune-Clientsoftware ausgeführt werden.
Intune sammelt normalerweise Inventory verwalteten Geräte alle 7 Tage. Aus diesem Grund es möglicherweise eine Verzögerung bevor Berichte die Ergebnisse beliebiger zuletzt verwendete anzeigen ändert sich in Geräte, beispielsweise eine Änderung an das Gerät Namen oder freier Speicherplatz.

## Was ist von registrierten Geräten gesammelt?
Führen Sie zum Anzeigen des Bestand, der von mobilen Geräten gesammelten [Mobile Geräte Inventory Berichte](understand-microsoft-intune-operations-by-using-reports.md)aus. Intune sammelt die folgenden Inventory von registrierten Geräte:

|Eigenschaft|Gesammelte, indem Sie|
|------------|-----------------------|
|**Namen**|Alle Geräte|
|**Betriebssystem**|Alle Geräte|
|**Hersteller**|Alle Geräte|
|**Modell**|Alle Geräte|
|**Projektmanagement-Kanal**|Alle Geräte|
|**AAD registriert**|Alle Geräte mit Ausnahme von Mac OS X|
|**Kompatible**|Alle Geräte|
|**EAS aktiviert**|Alle Geräte mit Ausnahme von Mac OS X|
|**EAS Aktivierungs-ID**|Alle Geräte mit Ausnahme von Mac OS X|
|**EAS Aktivierung Uhrzeit**|Alle Geräte mit Ausnahme von Mac OS X|
|**Bundesstaat Management**|Alle Geräte|
|**E-Mail-Adresse**|Alle Geräte|
|**Exchange ActiveSync-ID**|Alle Geräte|
|**Jailbroken oder einen Stamm**|iOS und Android-Geräten|
|**Eindeutige Geräte-ID**|Alle Geräte mit Ausnahme von Exchange ActiveSync|
|**Fortlaufende Zahl**|iOS, Mac OS X, Android, Windows 8.1 und Windows-10-Geräte|
|**Total Speicherplatz**|iOS, Mac OS X, Windows 8.1 und Windows-10-Geräte|
|**Freier Speicherplatz**|iOS, Mac OS X, Windows 8.1 und Windows-10-Geräte|
|**Rufnummer**<br>Telefone, die als corporate kategorisiert werden, werden gekennzeichnet, mit ihren vollständigen Telefonnummer (beispielsweise, wenn Sie einen mobiles Gerät Inventory Bericht ausführen). BYOD Zahlen sind mit maskierte Telefon & #42; und es werden nur die letzten vier Ziffern angezeigt.|iOS, Android und Windows Phone-Geräte|
|**IMEI**|Exchange ActiveSync, iOS, Android und Windows Phone-Geräte|
|**MEID**<br>Bezeichner für Mobile Geräte|nur iOS-Geräte|
|**Wi-Fi-MAC**|Alle Geräte mit Ausnahme von Exchange ActiveSync|
|**Abonnenten Carrier**|iOS und Android-Geräten|
|**Mobile-Technologie**|iOS und Android-Geräten|
|**Überwacht**|nur iOS-Geräte|
|**Sperren Aktivierungsstatus**|nur iOS-Geräte|
|**Registrierten Datum**|Alle Geräte|
|**Letzte Aktualisierung**|Alle Geräte|
|**Ethernet MAC**|Nur Mac OS X-Geräte|
|**Aktivierung Sperren aktiviert**|nur iOS-Geräte|
|**Verschlüsselung aktiviert**|Alle Geräte|

## Was ist von Windows-PCs gesammelt?
> [!IMPORTANT]
> Dieser Abschnitt gilt nur für Windows-PCs, die die Computer mit Windows Intune-Clientsoftware ausgeführt werden.

Führen Sie zum Anzeigen des Bestand, der von Windows-PCs gesammelten [Computer Inventory Berichte](understand-microsoft-intune-operations-by-using-reports.md)aus. Intune sammelt die folgenden Inventory von Windows-PCs:

-   **Namen**

-   **Gehäusetyp**

-   **Hersteller**

-   **Modell**

-   **Betriebssystem**

-   **TPM-Version**

-   **Gesamter Speicherplatz**

-   **Verwendeten Festplattenspeicher**

-   **Freier Festplattenspeicher**

-   **Name des Laufwerks OS**

-   **OS Festplattenspeicher**

-   **OS freier Speicherplatz**

-   **Arbeitsspeicher**

-   **Name der Prozessor**

-   **Prozessor-Architektur**

-   **CPU-Geschwindigkeit**

-   **IP-Adresse**

-   **Fortlaufende Zahl**

-   **Letzte Benutzer anmelden**

-   **Zugewiesene Benutzer**

-   **Letzte Aktualisierung**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->
