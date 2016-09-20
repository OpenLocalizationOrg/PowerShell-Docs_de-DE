---
title: "Verwalten Ihres Unternehmens im Besitz Geräten | Microsoft Intune"
description: "Zeigen Sie die Verwaltung auf vielfältige Weise, abhängig von dem Gerät, wie es gekauft wurde und Organisation Anforderungen Ihres Unternehmens im Besitz Geräte (Lieferung)."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 6c8a658532ba9e7367c12c62581486399ff77840
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Registrieren Sie Ihres Unternehmens im Besitz eines Geräte mit Microsoft Intune
Organisation oder Ihres Unternehmens im Besitz Geräte (Lieferung) können geschaltet werden in der Verwaltung von Intune auf vielfältige Weise, das Gerät, wie es gekauft wurde und den Anforderungen der Organisation abhängig. Im Besitz eines Corporate Geräte auch registriert und verwaltet werden können nach der Installation des Unternehmens Portal app wie "bringen Ihre eigenen Gerät" Szenarien (BYOD).

## Im Besitz eines Corporate iOS-Geräte
Diese Registrierungsmethoden eignen sich für "Auswählen, Ihr eigenes Gerät" (CYOD) Szenarien, in dem die Organisation EC-oder die Geräte für Benutzer, jedoch Management des Geräts beibehalten möchte. Wenn Ihre Organisation iOS-Geräte erworben hat, können Sie Registrierungs vorab konfigurieren, damit das Gerät aus der ersten Mal verwaltet wird, deren Benutzer aktiviert wird. Intune unterstützen die Registrierung über [Apple Gerät Registrierungs-Programm (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) oder mithilfe des Tools für Apple-Konfiguration auf einem Mac für [direkte](ios-direct-enrollment-in-microsoft-intune.md) oder eine bestimmte Registrierung [Setup-Assistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md) ausführen.

[Registrieren Sie Ihres Unternehmens im Besitz iOS-Geräte](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Geräte Registrierungs-manager
Organisationen können Intune zum Verwalten von großen Anzahl von mobilen Geräten mit eines einzelnen Benutzerkontos bezeichnet ein Gerät Registrierungs-Manager-Konto verwenden. Nachdem Sie ein Gerät Registrierungs-Manager-Konto erstellt haben, kann dieses Konto von einem Manager mehr Zeichen als die standardmäßige fünf Geräte standardmäßig für normale Benutzer zulässig registrieren verwendet werden. Registrieren die Geräte mit einem Gerät Registrierungs-Manager funktioniert nur für Geräte, die nicht von einem bestimmten Benutzer verwendet. Diese Geräte sind gut für POS oder Utility apps, zum Beispiel, jedoch schlecht für Benutzer, die Zugriff auf e-Mail- oder einen Firmennamen Ressourcen benötigen.

[Registrieren Sie Ihres Unternehmens im Besitz Geräte mit der Registrierung Geräte-manager](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Registrieren Sie Ihres Unternehmens im Besitz eines Windows 10 desktops

Wenn Ihre Organisation Azure Active Directory Premium (AADP) oder Enterprise Management Suite (EMS) verfügt, können Sie [Windows 10 für Enterprise registrieren](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) , und diese automatisch markiert als "corporate Eigentümer" Wenn Benutzer seine Arbeit hinzufügen oder Schule Konto.

## Identifizieren von Geräten als corporate im Besitz

Geräte im Besitz eines Unternehmen werden als **Corporate** unter **Besitz** in Listen Geräte aufgeführt. Geräte können als corporate im Besitz eines der folgenden Verfahren identifiziert werden:

 - [Registriert mit Geräte Registrierungs-Manager (DEM)](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)
 - Registriert mit Apple [Gerät Registrierungs-Programm (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) oder [Apple-Konfiguration](ios-setup-assistant-enrollment-in-microsoft-intune.md)
 - [Predeclare Geräte mit IMEI-Nummern](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
 - [Azure Active Directory/Enterprise Management Suite-Registrierung von Windows-10-Geräte](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)

### Internationale mobile Geräte Identität (IMEI)

Eindeutige internationale mobile Geräte Identität (IMEI) Zahlen sind eine allgemeine Geräteeigenschaft für vielen Herstellern von mobilen Geräten. Intune-Administratoren können IMEI Zahlen für Geräte importieren, die zum Unternehmen gehören. Wenn das Gerät von Intune verwaltet wird, wird es als ein Gerät corporate im Besitz markiert.

[Geben Sie im Unternehmen im Besitz eines Geräte mit internationalen mobile Geräte Identität (IMEI) Zahlen](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
