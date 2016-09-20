---
title: Bereitstellen von apps | Microsoft Intune
description: "In diesem Thema wird erläutert, Konzepte zu verstehen, bevor Sie beginnen, Bereitstellen von apps mit Intune benötigen."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: ef042e24af2300250cf2bd1bf9803678e252b773
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Mit Microsoft Intune apps bereitstellen

In diesem Thema wird erläutert, einige der Konzepte, die Sie vor Beginn der Bereitstellung von apps mit Microsoft Intune verstehen müssen.


## Aktionen für App-Bereitstellung
Wenn Sie apps bereitstellen, können Sie auf eine der folgenden Aktionen Bereitstellung auswählen:

-   **Erforderliche installieren** – die app wird mit keine Eingriff erforderlich auf dem Gerät installiert.

    > [!TIP]
    > IOS-Geräte, die nicht im Modus Kontrolle sind, sowie alle Android-Geräten, muss der Benutzer app Ihr Angebot annehmen, bevor sie installiert wird.
    >
    >  Wenn ein Benutzer eine app, die Sie als erforderlich-Installation bereitgestellt deinstalliert, installiert Intune die app automatisch nach dem nächsten Zyklus Inventory, das in der Regel alle sieben Tage auftritt, neu.

-   **Installieren verfügbar** – die app im Portal Unternehmen angezeigt wird, und Benutzer können sie bei Bedarf installieren.

-   **Deinstallieren** – die app wird auf dem Gerät deinstalliert.

-   **Nicht verfügbar** – die app im Portal Unternehmen nicht angezeigt, und klicken Sie auf alle Geräte, die nicht installiert ist.

#### Verstehen Sie, welche Aktionen für die Bereitstellung für jeden Installer verfügbar sind

|Installer-Datentyp|Installation erforderlich|Verfügbare Installation|Deinstallieren Sie|Nicht verfügbar|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows-app-Paket (einer Benutzergruppe bereitgestellt)|Ja|Ja|Ja|Ja|
|Windows-app-Paket (einer Gruppe Gerät bereitgestellt)|Ja|Nein|Ja|Ja|
|App-Pakets für mobile Geräte (einer Benutzergruppe bereitgestellt)|Ja|Ja|Ja|Ja|
|App-Pakets für mobile Geräte (zu einer Gerätegruppe bereitgestellt)|Ja|Nein|Ja|Ja|
|Windows Installer (einer Benutzergruppe bereitgestellt)|Nein|Ja|Nein|Ja|
|Windows Installer (zu einer Gerätegruppe bereitgestellt)|Ja|Nein|Ja|Ja|
|Externer Link (einer Benutzergruppe bereitgestellt)|Nein|Ja|Nein|Ja|
|Externer Link (zu einer Gerätegruppe bereitgestellt)|Nein|Nein|Nein|Nein|
|Verwaltete iOS-app aus dem app Store (einer Benutzergruppe bereitgestellt)|Ja|Ja|Ja|Ja|
|Verwaltete iOS-app aus dem app Store (zu einer Gerätegruppe bereitgestellt)|Ja|Nein|Ja|Ja|
> [!TIP]
> Beim Bereitstellen von apps, wenn Sie Benutzer und Gerätegruppen auswählen, können Sie nur die app als eine **Verfügbare Installation**bereitstellen.

## Bereitstellungskonflikte
Wenn zwei Bereitstellungen mit der gleichen Bereitstellungsaktion von einem Gerät empfangen werden, gelten die folgenden Regeln:

-   Zu einer Gerätegruppe Bereitstellungen haben Vorrang vor Bereitstellungen mit einer Benutzergruppe. Jedoch wird eine app zu einer Benutzergruppe mit einer Bereitstellungsaktion von **verfügbar**bereitgestellt wird, und die gleiche app bereitgestellt wird auch zu einer Gerätegruppe mit einer Bereitstellungsaktion von **Nicht verfügbar**, die app im Unternehmen Portal für Benutzer zum Installieren bereitgestellt werden.

-   Aktion Installieren Vorrang vor einer Aktion deinstallieren.

-   Wenn Sie über ein Gerät mit einem erforderlichen und eine verfügbare Installation empfangen werden, werden die Aktionen kombiniert. Kurzum, kann der Benutzer installieren verfügbar vom Unternehmen Portal vor Beginn die Installation erforderliche.


## Nächste Schritte

Erfahren Sie, wie Sie [apps in Microsoft Intune Bereitstellen](deploy-apps-in-microsoft-intune.md).
