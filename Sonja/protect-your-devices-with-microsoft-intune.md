---
title: "Schützen von Geräten | Microsoft Intune"
description: "Erfahren Sie mehr über die Möglichkeiten, die Intune helfen können, dass Sie Ihre Geräte vor unbefugtem Zugriff und ausgefeilte schützen."
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: af47644a4d9808ee43a80e8e211ae82b738080aa
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Schützen von Geräten mit Microsoft Intune

Microsoft Intune bietet eine vollständige Reihe von Funktionen, mit denen Sie die Geräte schützen, die Sie verwalten, und klicken Sie auf diese Geräte gespeicherten Daten an. Lesen Sie dieses Thema, die Grundlagen des diese Funktionen sowie weitere Informationen zu erhalten.

## Allgemeine Methoden zum Schützen von allen Geräten

### Konfiguration des Geräts
Intune- [Konfigurationsrichtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md), helfen Ihnen schützen und Konfigurieren von Geräten unter einer Vielzahl von Einstellungen und Features steuern. Beispiel:
- Sie können die Verwendung von Hardwarefeatures auf dem Gerät, beispielsweise die Kamera oder eines Bluetooth einschränken.
- Sie können kompatible und nicht kompatible apps konfigurieren. Sie werden darüber benachrichtigt, wenn eine nicht kompatible app installiert ist (und einige Plattformen können die Installation tatsächlich blockieren).

### Zurücksetzen Sie die Kennungen, wenn Benutzer von aktivierten Geräte gesperrt sind
Da der erste Schritt beim Schutz von Unternehmensdaten auf mobilen Geräten, einen Kenncode mit dem Gerät erforderlich ist, manchmal Sie müssen [einen Kenncode zurücksetzen](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) oder Hilfen ein Mitarbeiters können, entweder über die Kennung entfernen oder einen temporären Kenncode Remote festlegen. Sie können auch [ein Gerät Remote Sperren](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) bei Verlust oder Diebstahl.

### Geräte zurückziehen und Entfernen von Daten
Wenn ein Gerät [aus der Verwaltung von Intune entfernt](retire-devices-from-microsoft-intune-management) werden muss (beispielsweise ein Benutzer verlässt oder das Gerät ist verloren gegangen sind oder gestohlen), ist zu rechnen, sollten Sie Daten aus dem Gerät zu entfernen. Intune bietet es sich um eine Reihe von Methoden, um sicherzustellen, dass die Daten des Unternehmens sicher bleiben.

### Vorschreiben von Geräten kompatibel sein
Intune Features [Gerät Compliance-Richtlinien](introduction-to-device-compliance-policies-in-microsoft-intune) , mit denen Sie die Geräte, die Regeln nicht erfüllen ausgewertet werden soll (und in einigen Fällen beheben) Geben Sie an. Beispielsweise können Sie zur iOS-Geräte melden, die sind Jailbroken, gibt an, ob Geräte verschlüsselt sind oder ob Windows 10 Geräte als fehlerfrei vom Dienst Befähigungsnachweis Dienststatus angegeben werden.

### Schützen von apps und die Daten, die sie verwenden
Intune bietet Ihnen einen Bereich von Funktionen, die Sie apps und ihre Daten schützen können. Beispielsweise können mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) verhindern, dass die Daten in einer geschützten app gesichert, einschränken kopieren und Einfügen an andere apps, erfordern eine PIN, um eine app und vieles mehr zuzugreifen. Weitere Informationen zum Schutz von apps finden Sie unter [schützen apps und Daten mit Microsoft Intune](protect-apps-and-data-with-microsoft-intune)

## Weitere Funktionen für Windows-Geräte

### Hinzufügen von eine zusätzliche Schutzebene zu Windows-Geräten
[Mehrstufige Authentifizierung (MFA)](protect-windows-devices-with-multi-factor-authentication.md) ist sicherer lässt die Benutzerauthentifizierung von Windows und Windows Phone-Geräten im Netzwerk.  Mit MFA müssen Benutzer ihre Identität über Benutzernamen und Ihr Kennwort ein, über einen Anruf oder Textnachricht zu bestätigen.

### Steuerelement Windows Hallo für Business-Einstellungen auf Windows-Geräten
Intune können Sie die Integration in [Windows Hallo for Business](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (vormals Microsoft Passport) eine alternative Anmeldung Methode für Windows 10 und höher, die Active Directory oder Azure-Active Directory-Konto verwendet ist, um ein Kennwort, Smartcard oder virtuelle Smartcard ersetzt werden.

## Weitere Funktionen für iOS-Geräte

### Umgehen Sie Aktivierung Sperren auf iOS-Geräte
Aktivierung Sperren ist ein Feature, mit deren Hilfe Benutzer Geräte mit Anforderung ihren Apple-ID und das Kennwort eingegeben werden, bevor alle Benutzer löschen, und das Gerät reaktivieren schützen. Dies kann jedoch zu Problemen, wenn der Benutzer das Unternehmen verlässt, ohne die Sperre entfernen beispielsweise führen. [iOS Aktivierung Sperren umgehen](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) kann Ihnen dabei helfen Kontrolle iOS-Geräte, so dass Sie neu zuordnen, oder löschen sie die Sperre aufheben.



## Schützen von Windows-PCs mit dem Client Intune verwaltet
Intune Sicherheitsrichtlinien unterstützt weiterhin für Windows-PCs, die Sie nicht registrieren, aber der Intune Computer Clientsoftware verwalten. Um herauszufinden, wie diese Richtlinien organisieren können, dass Sie Ihre Windows-PCs secure, finden Sie unter [Verwenden von Richtlinien zum Schutz des Windows-PCs, die die Intune-Clientsoftware ausführen](policies-to-protect-windows-pcs-in-microsoft-intune.md).
