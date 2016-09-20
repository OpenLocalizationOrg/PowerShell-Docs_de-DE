---
title: Windows-Team Konfiguration Richtlinieneinstellungen | Microsoft Intune
description: "Verwenden Sie die Microsoft Intune ** Windows-10-Team allgemeine Konfiguration Richtlinie ** zum Konfigurieren der Einstellungen für Windows-10-Team Geräten wie Microsoft Surface Hub registriert."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: a8a6e72468cfabf316cb15b5926841e5308325d5
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Windows-Team Konfiguration Richtlinieneinstellungen Microsoft Intune
Verwenden Sie die Intune Microsoft **Windows-10-Team allgemeine Konfigurationsrichtlinie** zum Konfigurieren der Einstellungen für registrierten Windows-10-Team-Geräten wie dem Microsoft Surface-Hub an.

|Name der Einstellung|Details|
|----------------|-----------|
|**Zulassen Sie Bildschirm automatisch zu aktivieren, wenn eine Person im Raum**|Ermöglicht das Gerät wenn deren Sensor eine Person im Raum erkennt automatisch zu aktivieren.|
|**PIN für drahtlosen Projektion erforderlich**|Gibt an, ob Sie eine PIN eingeben müssen, bevor Sie die Funktionen drahtlosen Projektion des Geräts verwenden können.|
|**Festlegen eines Wartungszeitfensters Gerät Updates**|Konfiguriert das Fenster, wenn Updates am Gerät stattfinden können. Sie können die Startzeit des Fensters und die Dauer (von 1 bis 5 Stunden) konfigurieren.|
|**Aktivieren von Azure Betrieb Einsichten**|Azure Betrieb Einblicken, Teil des Microsoft Operations Manager Suite sammelt, speichert und analysiert Daten der Protokolldatei aus dem Windows-10-Team Geräte.<br /><br />Zum Verbinden mit Azure Betrieb Einblicken, müssen Sie eine **Arbeitsbereich-ID** und einen **Arbeitsbereich Key**angeben.|
|**Aktivieren der drahtlosen Projektion Miracast**|Aktivieren Sie diese Option, wenn Sie das Windows-10-Team Gerät aktiviert Miracast-Geräte verwenden, um project informieren möchten.<br /><br />Wenn Sie diese Option aktivieren, **Wählen Miracast Channel** wählen Sie den Miracast-Kanal verwendet, um den Projektinhalt.|
|**Wählen Sie die Besprechungsinformationen, die auf dem Bildschirm Willkommen angezeigt**|Wenn Sie diese Option aktivieren, können Sie auswählen, die Informationen, die angezeigt wird, klicken Sie auf die Kachel " **Besprechungen** " im Bildschirm **Willkommen** . Sie können:<br /><br />-   **Organisieren und die Uhrzeit nur anzeigen**<br />-   **Anzeigen der Organisator, Zeit und Betreff (Subject für private Besprechungen ausgeblendet)**|
|**Bild-URL für Lockscreen Hintergrund**|Aktivieren Sie diese Einstellung, um einen benutzerdefinierten Hintergrund auf dem Bildschirm **Willkommen** des Windows-10-Team Geräte aus der URL anzuzeigen, die Sie angeben.<br /><br />Das Bild muss im PNG-Format und die URL muss mit **https://**beginnen.|


### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

