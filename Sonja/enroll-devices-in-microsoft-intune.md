---
title: "Registrieren Geräte | Microsoft Intune"
description: "Verwaltung mobiler Geräte (MDM) verwendet Registrierung zeigen Sie die Geräte Management und den Zugriff auf Ressourcen."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 4dbf5123fc909d5372a0ca29c22d0df6d0eef26b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Registrieren Sie für die Verwaltung von Intune Geräte
Sie können Geräte, einschließlich der Windows-PCs, um die Verwaltung mobiler Geräte (MDM) mit Microsoft Intune aktivieren registrieren. In diesem Thema werden gibt unterschiedliche Methoden für mobile Geräte in Intune Verwaltung zu registrieren. Wie Geräte Geräte registrieren, hängt davon ab Typ des Geräts, Besitz und die Ebene der Verwaltung erforderlich. "Bringen Sie Ihre eigenen Gerät" Registrierung (BYOD) ermöglicht Benutzern, die ihre persönlichen Telefone, Tablets oder PCs registrieren. Im Besitz eines Corporate Gerät (Lieferung) Registrierung ermöglicht Management Szenarien wie Remotezurücksetzung, freigegebenen Geräte oder Benutzer Zugehörigkeit für ein Gerät.

Wenn Sie [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), entweder lokal verwenden oder in der Cloud gehostet wird, können Sie einfaches Intune Management ohne Registrierung aktivieren. Windows-PCs können auch mit [Intune-Clientsoftware](#manage-windows-pcs-with-intune)verwaltet werden.

## Übersicht über die Gerät Registrierungs-Methoden

Die folgende Tabelle zeigt Intunes Registrierungsmethoden, mit deren unterstützten Funktionen. Diese Funktionen umfassen:
- **Wischen Sie** -Factory zurücksetzen das Gerät, alle Daten entfernt. [Deaktivieren von Geräten](retire-devices-from-microsoft-intune-management.md)
- **Zugehörigkeit** - Associates Geräte mit Benutzern. Für mobile anwendungsverwaltung (MAM) und bedingten Zugriff auf Unternehmensdaten erforderlich ist. [Benutzer Zugehörigkeit](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **Sperren** Verhindert, dass Benutzer das Gerät aus der Verwaltung zu entfernen. iOS-Geräte erfordern Supervised Modus für Sperren. [Remote Sperren](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**iOS Registrierungsmethoden**

| **Methode** |  **Wischen Sie** |  **Zugehörigkeit**    |   **Sperren** | **Details** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nein|    Ja |   Nein | [Weitere](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   Nein |Nein |Nein  | [Weitere](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Ja |   Optional |  Optional|[Weitere](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Ja |   Optional |  Nein| [Weitere](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-direkte](#usb-direct)**| Nein |    Nein  | Nein|[Weitere](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows und Android Registrierungsmethoden**

| **Methode** |  **Wischen Sie** |  **Zugehörigkeit**    |   **Sperren** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nein|    Ja |   Nein | [Weitere](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   Nein |Nein |Nein  |[Weitere](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Für eine Reihe von Fragen, mit deren Hilfe Sie finden die richtige Methode finden Sie unter [auswählen, wie Sie Geräte registrieren](/intune/get-started/choose-how-to-enroll-devices1).

## BYOD
"Schalten Sie Ihr eigenes Gerät" Benutzer die app Unternehmen Portal installieren und Geräts zu registrieren. Dies kann Benutzer eine Verbindung mit dem Firmennetzwerk, Teilnahme an der Domäne oder Azure Active Directory herstellen lassen. Aktivieren BYOD ist Registrierung Vorbedingung für viele Lieferung Szenarien für die meisten Plattformen. [Erforderliche Komponenten für die Registrierung Gerät](prerequisites-for-enrollment.md)finden Sie unter. ([Wieder in der Tabelle](#overview-of-device-enrollment-methods))

## Im Besitz eines Corporate Geräte
Im Besitz eines Corporate Geräte (Lieferung) können mit der Intune-Verwaltungskonsole verwaltet werden. iOS-Geräte können direkt über Tools von Apple registriert sein. Alle Gerätetypen können von einem Administrator oder Manager mit dem Gerät Registrierungs-Manager registriert sein. Geräte mit einer Nummer IMEI können auch identifiziert und als Lieferung Szenarien unterstützen Unternehmen im Besitz markiert.

[Registrieren Sie Ihres Unternehmens im Besitz Geräte](manage-corporate-owned-devices.md)

### DEM
Geräte Registrierungs-Manager ist eine spezielle Intune verwendete Konto zum Registrieren und Verwalten von mehreren corporate im Besitz Geräte. Manager können Sie das Unternehmen Portal installieren und viele Benutzer zugängliche Geräte registrieren. Weitere Informationen zu [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Wieder in der Tabelle](#overview-of-device-enrollment-methods))

### DEP
Verwaltung von Apple Gerät Registrierungs-Programm (DEP) können Sie die erstellen und Bereitstellen von Richtlinie "über die Luft" zu iOS-Geräte gekauft und verwaltet werden, mit der Datenausführungsverhinderung Das Gerät ist registriert, wenn der Benutzer auf dem Gerät zum ersten Mal verwandelt und die iOS-Setup-Assistenten führt. Diese Methode unterstützt **iOS Supervised** Modus, wodurch wiederum kann:
  - Gesperrte Registrierung
  - Bedingte access
  - Jailbreak Erkennung
  - Mobile anwendungsverwaltung

Weitere Informationen zu [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Wieder in der Tabelle](#overview-of-device-enrollment-methods))

### USB-SA
Setup-Assistenten Registrierung USB verbunden. Der Administrator erstellt eine Richtlinie Intune und es zu Apple-Konfiguration exportiert. USB-verbunden, corporate im Besitz Geräte werden mit Intune Richtlinie vorbereitet. Der Administrator muss jedes Gerät von hand zu registrieren. Benutzer erhalten aktivierten Geräte, und führen Sie Setup-Assistenten, Geräts registrieren. Diese Methode unterstützt **iOS Supervised** Modus, wodurch wiederum an:
  - Bedingte access
  - Jailbreak Erkennung
  - Mobile anwendungsverwaltung

Weitere Informationen zu den [Setup-Assistenten Registrierung mit Apple-Konfiguration](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Wieder in der Tabelle](#overview-of-device-enrollment-methods))

### USB-direkte
Direkte Registrierung. Der Administrator erstellt eine Richtlinie Intune und es zu Apple-Konfiguration exportiert. USB-verbunden, corporate im Besitz Geräte registriert sind, direkt ohne eine Fabrik zurücksetzen. Der Administrator muss jedes Gerät von hand zu registrieren. Geräte werden als Benutzer zugängliche Geräte verwaltet. Sie sind nicht gesperrt oder überwacht und bedingte Access, Jailbreak Erkennung, mobilen anwendungsverwaltung können nicht unterstützen. Weitere Informationen zu [direkte Registrierung mit Apple-Konfiguration](ios-direct-enrollment-in-microsoft-intune.md). ([Wieder in der Tabelle](#overview-of-device-enrollment-methods))

## Verwaltung mobiler Geräte mit Exchange ActiveSync und Intune
Mobile Geräte, werden nicht registriert, aber, die Verbindung zu Exchange ActiveSync (EAS) können von Intune mit EAS MDM Richtlinie verwaltet werden. Intune ein Exchange-Connector zur Kommunikation mit EAS, entweder lokal verwendet und Cloud-gehostet wird.

[Verwaltung mobiler Geräte mit Exchange ActiveSync und Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Verwalten von Windows-PCs mit Intune  
Microsoft Intune können Sie auch die Verwaltung von Windows-PCs Intune-Clientsoftware verwenden. PCs, die mit der Intune Client kann verwaltet werden:

 - Bericht Software- und Bestände
 - Installieren von desktopanwendungen (beispielsweise .exe und MSI-Dateien)
 - Firewall-Einstellungen

Mit der Intune-Clientsoftware verwaltete PCs können nicht endgültig gelöscht werden, und können nicht viele Intune Verwaltungsfunktionen wie bedingte Access, VPN und Wi-Fi-Einstellungen oder Bereitstellung von Zertifikaten und e-Mail-Konfigurationen nutzen.

[Verwalten von Windows-PCs mit Intune](manage-windows-pcs-with-microsoft-intune.md)

##  Unterstützte Plattformen

Intune kann die folgenden Geräteplattformen verwalten:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Nächste Schritte
- [Erforderliche Komponenten für die Registrierung Gerät](prerequisites-for-enrollment.md)
- [Verwalten Sie Ihres Unternehmens im Besitz Geräten](manage-corporate-owned-devices.md)
- [Unterstützte mobile Geräte und Computer](../get-started/supported-mobile-devices-and-computers.md)
