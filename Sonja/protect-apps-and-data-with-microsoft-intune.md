---
title: "Schützen apps und Daten | Microsoft Intune"
description: 
keywords: "In diesem Thema werden die verschiedenen Intune Features und Funktionen, die Sie zum Schutz Ihres Unternehmens apps und Ihrer Daten verfügbar sind."
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: cf2ef1510aa9dafeddf54855123c826c9ccc2fd0
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Schützen von Daten mit Microsoft Intune und apps


Intune Loss Unternehmensdaten durch mehrere Technologieebenen.  Auf der Ebene Identität Loss bedingte Access Zugriff auf Dienste von Dokumenten, indem nur Zugriff von verwalteten und kompatiblen Geräten.  Auf der Ebene Client-Anwendung Loss mobile-app Management (MAM) Datenverlust aus, indem Sie verhindern, dass Daten nicht geschützt apps oder Speicherorte verschieben und Wischen Daten ein, wenn ein Gerät verloren gegangen sind oder gestohlen wird.  Diese beiden Ebenen des Schutzes sollte gemeinsam verwendet werden, um Daten zu sichern, während Ihre mobilen Mitarbeiter produktiv zu bleiben.

Ein wichtiger erster Schritt zum Schutz von Unternehmensdaten ist bedingten Zugriff implementieren, indem Sie sicherstellen, dass Geräte verwendet, um die Daten zuzugreifen Sicherheitsmaßnahmen wie sicheres Kennwort, Verschlüsselung und sind nicht Jailbroken verwenden. Microsoft Intune gibt Ihnen die Möglichkeit zum Festlegen von Bedingungen, die die Geräte, einhalten, bevor sie Ihre Unternehmens-e-Mail und Daten zugreifen dürfen.

[Bedingte Zugriff](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) wird durch zwei Arten von Richtlinien festgelegt, die in Intune festgelegt werden können:
- [Compliance-Richtlinien](introduction-to-device-compliance-policies-in-microsoft-intune.md) bestimmen, die Compliance von einem Gerät. Diese Einstellungen ausgewertet werden soll, und Bedingungen wie:
  - PIN und Kennwörter: Sie können Regeln erstellen, um Kennwörter zu verlangen, bevor Sie ein Gerät, die Komplexität Anforderungen für das Kennwort und andere kennworteinstellungen entsperren.
  - Verschlüsselung: Sie können den Zugriff auf Geräte einschränken, die verschlüsselt sind.
  - Gerät ist nicht Jailbroken oder einen Stamm: Intune kann erkennen, ob ein Gerät registrierten Jailbroken ist, und Sie, dass die Richtlinie festlegen können, den Zugriff auf solche Geräten sperren.
- [Bedingte-Richtlinien](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) werden so konfiguriert, dass für einen bestimmten Dienst wie Exchange Online oder SharePoint Online. Für jeden Dienst können Sie festlegen, welche Benutzergruppen auf diesen Richtlinien angewendet werden soll. Beispielsweise können Sie sicherstellen, dass jede Person in das Finanzen Abteilung können nur Access Unternehmen von registrierten und kompatiblen Geräten per e-Mail senden.

Sichern des Zugriffs auf Unternehmensressourcen ist nur der erste Schritt zum Schutz von Unternehmensdaten. Sie benötigen weiterhin die Möglichkeit, die Daten zu schützen, nachdem es auf dem Gerät zugegriffen wurde. Die Daten können jetzt werden kopiert, verschoben, in einem anderen Speicherort gespeichert oder freigegeben. Intune löst dieses Problem und bietet Ihnen die Möglichkeit zum Verschieben von Daten durch Erstellen eines Regelsatzes wie einschränken:
- Blockieren kopieren und einfügen oder Datenübertragung außerhalb des Kontexts Arbeit zu verhindern.
- Verhindern, dass Sicherung zu persönlichen Cloud-Speicher, verhindern, dass speichern unter.
- Sicheren Sie Zugriff app durch erfordern PIN/Kenncode oder corporate Anmeldeinformationen an.
- Lassen Sie alle Weblinks, die dem Intune verwaltet Browser öffnen.

Diese Regelsatzes werden als [mobile-app Informationsverwaltungsrichtlinien (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)bezeichnet.  MAM Richtlinien können angewendet werden, um apps für Geräte, die möglicherweise oder können nicht verwaltet werden, indem Sie ausgeführt.  

Sie können Ihre Firmendaten mit MAM Richtlinien für Geräte, die **im Intune registriert**sind, Geräten, die **registriert und von einem Programm eines Drittanbieters MDM verwaltet**werden oder ein Gerät, das ist **nicht registriert in einer beliebigen MDM-Lösung**, wie der Mitarbeiter im Besitz Geräte schützen.

Um eine app einer Richtlinie MAM zuzuordnen, muss die app Einbinden von Microsoft Intune App Software Development Kit (SDK), oder verwenden Sie das App-Tool Textumbruch.

Apps wie Microsoft Office-apps müssen die App SDK integriert. Die vollständige Liste der unterstützten apps finden Sie auf der [Microsoft Intune mobilen Anwendung Katalog](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) auf der Seite Microsoft Intune Anwendung Partner zur Verfügung. Wählen Sie die app zu den unterstützten Szenarien finden Sie unter Plattformen und unabhängig davon, ob die app mit mehreren Identität unterstützt.

Außerdem können Sie zur Verwendung mit MAM Richtlinien [Ihrer benutzerdefinierte Programme Textzeile Geschäfts-apps zu aktivieren](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) .

Zusätzlich zum Einschränken der Verlagerung von Daten, wenn ein Gerät verloren oder gestohlen wird oder wenn der Benutzer nicht mehr mit Ihrem Unternehmen arbeitet, Sie [Selektives Wischen Unternehmensdaten können](wipe-managed-company-app-data-with-microsoft-intune.md), hinterlassen nur persönliche Daten.
