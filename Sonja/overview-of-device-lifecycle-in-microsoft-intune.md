---
title: "Übersicht über den Lebenszyklus MDM | Microsoft Intune"
description: "Erfahren Sie, wie Intune Geräte ihrer Nutzungsdauer verwalten kann – von der Registrierung, bis zur endgültigen Rente-Konfiguration."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 8e769d5912de0a821add180053034ed14eb58537
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Übersicht des Lifecycle Management (MDM) mobilen Gerät

Alle Geräte, die Sie verwalten haben wir einen *Lebenszyklus*anrufen. Intune hilft Ihnen dieser Lebenszyklus Verwalten – von der Registrierung, über die Konfiguration und Schutz, um das Gerät zurückziehen, wenn es nicht mehr erforderlich ist:

![Das Gerät Lebenszyklus](./media/device-lifecycle.png "the Intune device lifecycle")

## Registrieren
Strategien für das heutige Mobilgerät Management (MDM) Umgang mit einer Vielzahl von Mobiltelefonen und Tablets PCs (iOS, Android, Windows und Mac OS X). Wenn Sie müssen in der Lage zum Verwalten des Geräts, die häufig der Fall für Geräte Ihres Unternehmens im Besitz ist, ist der erste Schritt [Gerät Registrierung](enroll-devices-in-microsoft-intune.md)einrichten. Sie können auch Windows-PCs durch registrieren, die mit Intune (MDM) oder durch [Installieren der Clientsoftware Intune](manage-windows-pcs-with-microsoft-intune.md)verwalten.

## Konfigurieren
Erste Ihren Geräten registriert ist nur der erste Schritt. Alle diese Intune Angebote nutzen und sicherzustellen, dass Ihre Geräte Sicherheit und Einhaltung von Unternehmens-Standards sind, können Sie aus einer Vielzahl von Richtlinien auswählen. Diese ermöglichen Ihnen die Konfiguration von fast jeden Aspekt der wie verwalteten Geräte ausgeführt werden. Beispielsweise sollten Benutzer ein Kennwort auf Geräten haben, die Daten zu Firmennamen enthalten? Sie können eine erforderlich. Verfügen Sie über WLAN im Unternehmen? Sie können automatisch konfigurieren. Hier werden die Arten von Optionen für die Konfiguration, die verfügbar sind:

- [**Konfiguration von Richtlinien**](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). Diese Richtlinien ermöglichen Ihnen die Konfiguration, die Features und Funktionen der Geräte, die Sie verwalten. Angenommen, konnte Sie die Verwendung eines Kennworts für Windows Phones oder deaktivieren Sie die Verwendung der Kamera auf iPhones müssen
- [**Unternehmensrichtlinien Ressource-Zugriff**](enable-access-to-company-resources-with-microsoft-intune.md). Wenn Sie die Benutzer ihre Arbeit an ihren persönlichen Geräten zugreifen können, kann dies mit Herausforderung präsentieren. Beispielsweise sicherstellen wie Sie, dass alle Geräte Unternehmens-e-Mails müssen ordnungsgemäß konfiguriert werden? Wie können Sie sicherstellen, dass Benutzer das Unternehmensnetzwerk mit einer VPN-Verbindung zugreifen können, ohne komplexe Einstellungen kennen zu müssen? Intune kann dazu beitragen reduziert werden diese Last automatisch die Geräte, die Sie Zugriff auf allgemeine Unternehmensressourcen verwalten.
- [**Windows-PC Informationsverwaltungsrichtlinien (mit der Intune-Clientsoftware)**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). Beim Registrieren von Windows-PCs mit Intune Ihnen die meisten Geräteverwaltungsfunktionen bietet, weiterhin Intune zur Unterstützung der Verwaltung von Windows-PCs mit Intune-Clientsoftware. Wenn die benötigten Informationen zu einigen der Aufgaben, die Sie mit PCs ausführen können, beginnen Sie hier.

## Schützen
In der modernen IT-Welt ist Geräte vor unbefugtem Zugriff schützen eine der wichtigsten Aufgaben, die ausgeführt werden. Zusätzlich zu den Elementen im Schritt **Konfigurieren** des Lebenszyklus Gerät bietet Intune diese Funktionen, die Ihnen helfen, Geräte schützen, die Sie vor unbefugtem Zugriff oder Angriffen verwalten:
- [**Mehrstufige Authentifizierung**](protect-windows-devices-with-multi-factor-authentication.md). Hinzufügen einer zusätzlichen Ebene der Authentifizierung für Benutzer anmelden-ins helfen Geräte auch sicherer zu machen. Unter Windows, Windows Phone und Windows Mobile Geräte bieten mehrstufige Authentifizierung, die eine zweite Ebene der Authentifizierung, z. B. ein Telefonanruf oder Textnachricht erfordert, bevor Benutzer zugreifen können.
- [**Microsoft Passport-Einstellungen**](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md). Microsoft Passport ist eine alternative Anmeldung Methode, die Benutzer einer *Bewegung*verwenden kann – wie etwa einen Fingerabdruck oder Windows Hallo – anmelden, ohne dass ein Kennwort.
- [**Richtlinien zum Schutz von Windows-PCs (mit der Intune-Clientsoftware)**](policies-to-protect-windows-pcs-in-microsoft-intune.md). Wenn Sie PCs Windows Intune-Clientsoftware mit verwalten, Richtlinien zur Verfügung stehen, mit denen Sie steuern, Einstellungen für den Endpunkt Schutz, Softwareupdates und Windows-Firewall auf PCs, die Sie verwalten.

## Zurückziehen
Wenn ein Gerät verloren geht oder gestohlen wird, wenn es muss ersetzt werden, oder wenn Sie Benutzer an eine andere Position zu verschieben, es weist normalerweise Zeit [zurückziehen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) oder zurücksetzen aus das Gerät. Es gibt eine Reihe von Methoden dies möglich – einschließlich das Gerät zurücksetzen, entfernen es aus der Verwaltung und die Unternehmensdaten daran Wischen.
