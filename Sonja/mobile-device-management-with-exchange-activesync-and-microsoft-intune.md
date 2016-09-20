---
title: "Exchange ActiveSync-Gerät Management | Microsoft Intune"
description: "Verwalten von mobilen Geräten mit Exchange ActiveSync (EAS) Management mit dem Exchange-connector"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 3e8ca71a8a7011eb4d2e34c61ef869dbf0abe3b7
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwaltung von Exchange ActiveSync mobiler Geräte mit Microsoft Intune
Für Microsoft Intune zum Verwalten von mobiler Geräten direkt müssen Geräte [in Intune registriert](get-ready-to-enroll-devices-in-microsoft-intune.md)sein. Alternativ können Administratoren eine begrenzte Lösung aktivieren, die Exchange ActiveSync (EAS) Management mit einem Exchange-Connector verwendet. Geräte können mit lokalen Exchange-Servern und Exchange Online mithilfe von Office 365 verwaltet werden. Intune unterstützt nur ein Exchange-Connector-Verbindung eines beliebigen Typs pro Abonnement.

## Exchange Access Regeln für mobile Geräte ##

Exchange benötigt eine Reihe von Regeln, die definiert, was passiert, wenn mobile Geräte Verbindungsversuch zur EAS. Diese Regeln werden in der Intune-Verwaltungskonsole verwaltet.

[Exchange Access Regeln für mobile Geräte](exchange-access-rules-for-mobile-devices.md)

## Installieren Sie den Exchange-connector
Der Exchange-Connector können Sie Ihre Exchange-Bereitstellung in der Intune Verwaltungskonsole verwalten. Sie müssen zuerst installieren und konfigurieren den entsprechenden Intune zu Exchange-Verbinder. Wählen Sie die entsprechende Option basiert, ob Ihr Exchange Server lokal ist oder als in der Cloud-Dienst gehostet werden:

-   [Konfigurieren Sie das Intune für Exchange Online oder neue Exchange Online dedizierter Umgebungen](intune-service-to-service-exchange-connector.md)
-   [Installieren des Verbinders Intune für lokalen Exchange-Servern und Exchange Online dedizierter legacy-Umgebungen](intune-on-premises-exchange-connector.md)


## Anwenden einer Richtlinie für mobile Geräte Exchange verwaltet
Die Intune-Verwaltungskonsole zum Verwalten [EAS-Richtlinieneinstellungen](exchange-activesync-policy-settings-in-microsoft-intune.md) verwendet werden kann und zum [Einschränken des Zugriffs auf Unternehmensressourcen](restrict-access-to-email-and-o365-services-with-microsoft-intune.md). Eine Liste der Exchange ActiveSync-Richtlinieneinstellungen und von bestimmter mobilen Geräten unterstützt werden finden Sie unter [Exchange ActiveSync-Client-Vergleichstabelle](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Nach dem Anschließen Intune zu einem Microsoft Exchange-Umgebung, wird die Richtlinie EAS für alle Benutzer, die über Intune verwaltet der aktuellen Standardrichtlinie auf dem Microsoft Exchange Server zurückgesetzt werden, es sei denn, eine weitere spezifische Richtlinie innerhalb Intune definiert ist.

## Wischen Sie Unternehmensdaten von mobilen Geräten
Schließlich können Sie [Zurücksetzen aus Unternehmensdaten von mobilen Geräten EAS verwaltet](wipe-for-exchange-managed-mobile-devices.md) , wenn sie nicht mehr verwendet werden, oder wenn Geräte verloren gehen oder gestohlen werden.
