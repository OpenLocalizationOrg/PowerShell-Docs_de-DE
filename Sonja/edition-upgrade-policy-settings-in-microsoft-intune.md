---
title: Windows-Edition Richtlinieneinstellungen Upgrade | Microsoft Intune
description: "Erfahren Sie, wie die automatische Aktualisierung von Windows 10 Geräte auf die neueste Version mit Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 45130e3e12968d9df579a7a9d0cade0343b7c165
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Windows-Edition Upgradeeinstellungen Richtlinie in Microsoft Intune
Microsoft Intune **Edition Upgrade Policy** können Sie die Geräte automatisch zu aktualisieren, die eine der folgenden Windows-10-Versionen auf eine neuere Version ausgeführt werden:
* Windows-10-Desktop
* Windows 10 Hologramm
* Windows 10 Mobile

## Bevor Sie beginnen
Bevor Sie beginnen, Geräte auf die neueste Version zu aktualisieren, benötigen Sie eine der folgenden Aktionen aus:
* Einen Product Key, der so installieren Sie die neue Version von Windows auf allen Geräten, dass Sie mit der Richtlinie (für Windows-10-Desktop-Editionen) Ziel gültig ist. Sie können mehrere Aktivierung Tasten (MAK) oder Key Management Server (KMS) verwenden.
**or** Eine Lizenzdatei von Microsoft, die die Informationen zur Lizenzierung, um die neue Version von Windows auf allen Geräten zu installieren, dass Sie mit der Richtlinie (für 10 unter Windows Mobile und Windows 10 Hologramm Editionen) Ziel enthält.
* Die Windows-10-Geräte, die Sie als Ziel müssen in Microsoft Intune registriert sein. Sie können nicht die Edition Upgrade Richtlinie mit PCs verwenden, die die Intune PC-Clientsoftware ausgeführt werden.

## Upgrade Richtlinieneinstellungen Edition

|Name der Einstellung|Details|
|-|-|
|**Namen**|Geben Sie einen Namen für das Upgrade Edition Richtlinie aus.|
|**Beschreibung**|Geben Sie optional eine Beschreibung für die Richtlinie, die Sie in der Intune Verwaltungskonsole erkennen kann.
|**Edition zu aktualisieren.**|Wählen Sie aus der Dropdownliste die Version von Windows-10-Desktop, Windows 10 Hologramm oder 10 unter Windows Mobile, die Sie gezielte Geräten aktualisieren möchten.
|**Product Key**|Geben Sie an, dass der Product Key, dass Sie von Microsoft erworben, die verwendet werden können haben, um alle aktualisieren Windows 10 Desktop Geräte gerichtet.<br>Nachdem Sie eine Richtlinie, die einen Product Key enthält erstellen, keine den Product Key später bearbeitet werden. Dies liegt daran die Taste aus Sicherheitsgründen verdeckt wird. Um den Product Key ändern zu können, müssen Sie den gesamten Schlüssel erneut eingeben.
|**Lizenzdatei**|Wählen Sie **Durchsuchen** aus, um die Lizenzdatei auszuwählen, die Sie für Ihren Kunden von Microsoft, die für die Windows-Hologramm Lizenzinformationen enthält oder 10 unter Windows Mobile Edition, die Sie den Geräten aktualisieren möchten.

### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
