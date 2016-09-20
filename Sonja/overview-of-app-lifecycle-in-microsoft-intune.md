---
title: "Übersicht über die app-Lebenszyklus | Microsoft Intune"
description: "Lernen Sie des Lebenszyklus von apps Intune verwaltet, aus hinzufügen, deren tatsächlichen Rente aus."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: c93efd43a85c8046c7cfd6aa8341352b75ab0cfd
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Übersicht über die app-Lebenszyklus

Des app-Lebenszyklus Intune beginnt, wenn eine app hinzugefügt wird und verändernden durch, bis Sie weitere Phasen der app entfernen.

![Die app-Lebenszyklus](./media/app-lifecycle.png "the Intune app lifecycle")

## Hinzufügen

Dieser erste Schritt in der app-Bereitstellung ist der apps, hinzufügen, die Sie verwenden möchten, verwalten und bereitstellen, um Intune. Während der Arbeit mit vielen verschiedenen app Typen können, sind die grundlegenden Vorgehensweisen gleich aus. Mit Intune können Sie apps für [Geräte registriert](add-apps-for-mobile-devices-in-microsoft-intune.md) und [Windows-PCs verwalten Sie mit der Intune-Clientsoftware](add-apps-for-windows-pcs-in-microsoft-intune.md)hinzufügen.

## Bereitstellen

Nachdem Sie die app Intune hinzugefügt haben, können Sie dann [Bereitstellen er Geräten, die Sie verwalten](deploy-apps.md). Intune vereinfacht diesen Vorgang, und nachdem die app bereitgestellt wird, können Sie den [Monitor den Erfolg](monitor-apps-in-microsoft-intune.md) der Bereitstellung von der Intune-Verwaltungskonsole. In einigen app Stores, wie die [Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md) und [Windows](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md) -app speichert, können Sie darüber hinaus in Massen app-Lizenzen für Ihr Unternehmen erwerben. Intune kann Daten mit diesen Speichern synchronisieren, damit Sie bereitstellen und verfolgen die Lizenzverwendung für diese Typen von apps rechts von der Intune-Verwaltungskonsole.

## Konfigurieren

Als Teil des app-Lebenszyklus werden neuere Versionen von apps regelmäßig freigegeben. Intune stellt Tools auf einfache Weise [Aktualisieren von apps](update-apps-using-microsoft-intune.md) , die Sie auf eine neuere Version bereitgestellt haben. Darüber hinaus können Sie zusätzliche Funktionen für einige apps, beispielsweise konfigurieren:
- [iOS-app Konfigurationsrichtlinien](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md) Lieferung Einstellungen für kompatible iOS-apps, die verwendet werden, wenn die app ausgeführt wird. Eine app möglicherweise z. B. Herstellen einer Verbindung mit bestimmten branding Einstellungen oder den Namen eines Servers erfordern.
- [Verwaltete Browserrichtlinien](manage-internet-access-using-managed-browser-policies.md) helfen Ihnen so konfigurieren Sie Einstellungen für den verwalteten Intune-Browser, das Gerät Standardbrowser ersetzt und ermöglicht Ihnen die Websites einschränken, die Benutzer zugreifen können.

## Schützen

Intune bietet Ihnen viele Methoden zum Schutz die Daten in Ihrer apps. Die wichtigsten Methoden sind:
- [Bedingten Zugriff](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) steuert den Zugriff auf e-Mail und andere Dienste basierend auf Bedingungen, die Sie angeben. Bedingungen gehören Arten von Geräten oder Konformität mit einem [Gerät Compliance-Richtlinien](introduction-to-device-compliance-policies-in-microsoft-intune.md) , die Sie bereitgestellt.
- [Mobile anwendungsverwaltung (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) funktioniert mit einzelne apps zum Schutz des Unternehmensdaten, die sie verwenden. Beispielsweise Kopieren von Daten zwischen nicht verwalteten apps und apps, die Sie verwalten können einschränken, oder Sie können verhindern, dass apps auf Geräten, die als Stamm oder Jailbroken wurden ausgeführt.

## Zurückziehen

Schließlich ist es wahrscheinlich apps, die Sie bereitgestellt veralten und müssen entfernt werden. Intune erleichtert die [apps vom Dienst zurückziehen](retire-apps-using-microsoft-intune.md).
