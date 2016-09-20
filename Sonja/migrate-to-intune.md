---
title: Migrieren zu Intune | Microsoft Intune
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: b2e4e606327a452a49cd2066a13e030db808836c
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Migrieren zu Intune


Die Migration zu Intune aus Ihrer vorhandenen Lösung für Enterprise Mobilität Management möglicherweise führen Sie die allgemeine Abfolge der folgenden Schritte aus:

![Migrationsschritte zum Intune](./media/migrate-intune-steps.png)

## Benutzer benachrichtigen

Nachdem Sie sind, dass die Pilotprojekte Intune-Bereitstellung Ihren Anforderungen erfüllt, kommunizieren Sie für Ihre Benutzer über die anstehende Migration von deren Geräten Intune. E-Mail-Nachrichten, [Poster](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT) und Anweisungen helfen setzen Sie und Bereitstellen von erforderlichen Registrierungs-Details auf die Benutzer Schritte zum erledigen kontinuierlichen Verbindung zu Unternehmensressourcen und Anwendungen verwalten. Stellen Sie sicher, dass das Supportteam bereit sind, unterstützen Benutzer des Migrationsvorgangs ist.

## Ändern der vorhandenen Lösung für Enterprise Mobilität management

Abhängig davon, wie Sie bedingte Richtlinien zwischen Ihrem vorhandenen Lösung für Enterprise Mobilität Management und Intune behandeln möchten müssen Sie möglicherweise Ihre vorhandene bedingte Richtlinien deaktivieren. Sie werden Ihre vorhandene bedingte Richtlinien deaktivieren oder die vorhandene bedingte Richtlinien zum nicht Benutzer/Geräte einschließen, die Sie migrieren zu Intune Bereich.  Verfügen Sie nicht sowohl Intune und Ihre vorhandene Mobilität Lösung für Enterprise Management Richtlinien für bedingten Zugriff auf die gleichen Benutzer/Geräte anwenden.

## Aktivieren Sie Intune bedingte Zugriffsrichtlinie (optional)

Wenn Sie entschieden haben, zu sofort ohne eine Nachfrist für die Migration die bedingte Richtlinien zu erzwingen Geräte, Richtlinien für bedingten Zugriff in Intune in diesem Schritt aktivieren.  Stellen Sie sicher, dass diese Entscheidung allen Beteiligten vermittelte mit den Benutzern und Ihrem Helpdeskteam ist.  Wenn Geräte werden nicht in Intune registriert und nicht mit Intune-Richtlinien, wird nicht die Benutzer auf Ressourcen des Unternehmens zugreifen, bis er in Intune registrieren, und die Geräte mit Intune-Richtlinien kompatibel sind.

## Unenrolling Geräte aus Ihrer vorhandenen Lösung für Enterprise Mobilität management

Geräte müssen aus Ihrer vorhandenen Mobilität Lösung für Enterprise Management vor in Intune registrieren unenrolled werden. Wird unsere empfohlen, Benutzern aktivierten Geräte selbst Benutzer am besten Anmeldung kündigen zu ermöglichen.  Achten Sie darauf, dass der Unenrollment Anleitung aus der Lösungsanbieter, um sicherzustellen, dass Sie Benutzer und Geräte aus Ihrer Plattform, ordnungsgemäß entfernen Sicherstellung kleinsten möglichen Unterbrechung für Ihre Endbenutzer folgen.

## Registrieren die Geräte in Intune

Benutzer für die Migration geplant sollte sofort registrieren in Intune entweder wieder erhalten oder Verlust des Zugriffs auf Ressourcen des Unternehmens, e-Mail- und Anwendungen zu verhindern. Wenn Sie bedingten Zugriff konfiguriert haben und Benutzer versuchen, eine Verbindung herstellen zu e-Mails in Intune registrieren, deren Zugriff ist gesperrt, und eine e-Mail Registrierungs begrüßt sie. Diese e-Mail-Nachricht hinzufügen, begleitet, um deren Intune-Gerät zu registrieren.  Alternativ können Benutzer in Intune mithilfe der app Intune Unternehmen Portal oder systembedingt über das Betriebssystem Windows 8.1 und 10 unter Windows Mobile registrieren. Weitere Hinweise zur Registrierung Schritte pro Plattform finden Sie in [was Ihre Endbenutzer zur Verwendung von Microsoft Intune zu informieren](what-to-tell-your-end-users-about-using-microsoft-intune.md) .

## Konfigurieren von bedingten Zugriff Intune (optional)

Wenn Sie eine Nachfrist für bedingten Zugriff Durchsetzung zugelassen haben, aktivieren Sie bedingte Richtlinien in Intune Durchsetzung gestartet wird, wenn der Nachfrist, die Sie für Ihre Endbenutzer kommuniziert haben beendet wurde. Dieser Vorgang sofort alle Geräte, die die bedingte Zugriffsrichtlinie Intune erfüllen erfordert.

## Verbleibende Geräte und Benutzer registrieren

Jetzt, da Sie bedingte Zugriff aktiviert haben, müssen alle Benutzer in Intune registrieren und den Richtlinien Ihrer Organisation Compliance Zugriff auf Ressourcen des Unternehmens zu entsprechen. Wenn Sie die Benutzer in einer SmartArt-Registrierung (nicht alle auf einmal) migriert haben, wiederholen Sie die obigen Schritte, bis alle Geräte und Benutzer registriert und von Intune verwaltet werden.

## Deaktivieren der vorherigen Lösung für Enterprise Mobilität management

Nachdem Sie alle Ihre Benutzer migriert haben und Geräte in Intune Sie überprüft haben, dass die Migration zu Intune erfolgreich sind, können Sie die vorherigen Lösung für Enterprise Mobilität Management zurückziehen und/oder Dienst kündigen. Achten Sie darauf, dass Sie die Anleitung aus der Lösungsanbieter, um sicherzustellen, dass Sie ordnungsgemäß entfernen alle nicht benötigten Infrastruktur Anforderungen und Kündigen eines Abonnements-Lizenzen folgen.

## Die Migration – zusätzliche Ressourcen

Benötigen Sie zusätzliche Hilfe bei der Migration zu Intune? Wir erläutern die notwendigen Unterstützung durch Experten Optionen zu sorgen dafür, dass die Migration ist Probleme frei:

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Microsoft-Beratungsdienste](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Intune technischen und nicht technischen support](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Microsoft Intune TechNet-forum](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## Herunterladen einer Kopie der in diesem Handbuch erhalten

Zum Herunterladen einer Kopie der das gesamte Handbuch erhalten möchten, finden Sie auf der [TechNet-Katalog](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387).
