---
title: "Anpassen von Console-Ansichten für Administratorrollen | Microsoft Intune"
description: "Verwenden Sie dieses Thema, mit deren Hilfe Sie Filtern der Intune Administrator Console-Ansicht Ihrer Administratoren nur die Elemente anzeigen, für die jeweilige Rolle benötigten zulässig."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 1059aae1c90e3623201281d4cf14d9db442e3f20
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Anpassen von Intune Console Ansichten entsprechend Administratorrollen
Sie können die Microsoft Intune Administration Console Sicht, um zulassen Ihrer Administratoren nur die Elemente angezeigt, dass sie müssen ihre Rolle finden Sie unter Filtern. Beispielsweise können Sie nur Administrator Console-Operatoren Schadsoftware Definitionen aktualisieren oder Zurücksetzen die Kennung auf Geräten ermöglichen. Dazu verwenden vordefinierte **Bezeichnungen** , die Sie bestimmten Benutzern zuweisen. Wenn diese Benutzer Zugriff auf die Verwaltungskonsole können nur Elemente angezeigt, die zu ihrer Bezeichnung spezifisch sind.

## Erstellen eine benutzerdefinierte Ansicht

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com) **Administrator** &gt; **Dienstadministratoren**.

2.  Wählen Sie aus der Liste der Dienstadministratoren den Benutzer, dessen Bezeichnung Sie ändern möchten, und wählen Sie dann auf **Verwalten des Zugriffs**.

3.  Wählen Sie im Dialogfeld **Zugriff verwalten** der Zugriffsebene, die Sie den ausgewählten Benutzer gewähren möchten. Sie können auswählen:

    -   **Vollzugriff**
    -   **Schreibgeschützten Zugriff**
    -   **Helpdesk - Knoten Gruppen**

    Vollzugriff und schreibgeschützten Zugriff sind sofort verständlich. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    **Helpdesk - Knoten Gruppen** beschränkt, was der Administrator kann finden Sie unter und führen Sie die folgende:

    -   Listen der Benutzer und Geräte anzuzeigen. Der Administrator kann nicht Filter verwenden, um die Ansicht zu ändern. Sie können jedoch Gruppe filtern um zu ändern, was der Administrator sehen kann. Weitere Informationen hierzu finden Sie unter [verwenden Gruppen auf Benutzer und Geräte mit Microsoft Intune verwalten](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Drucken Sie die Liste der Benutzer und Geräte

    -   Exportieren Sie die Liste der Benutzer und Geräte

    -   Anzeigen der Eigenschaften eines Benutzers oder Gerät

    -   Führen Sie die folgenden remote-Aufgaben:

        -   Führen Sie eine vollständige Schadsoftware Überprüfung

        -   Führen Sie eine schnelle Schadsoftware Überprüfung

        -   Starten Sie einen Computer neu.

        -   Aktualisieren Sie die Schadsoftware Definitionen

        -   Aktualisieren von Richtlinien

        -   Inventory aktualisieren

        -   Ein Gerät Remote Sperren

        -   Einen Kenncode zurücksetzen

Wenn der Administrator aus, dem Sie als Nächstes konfiguriert die Administrator Intune-Verwaltungskonsole geöffnet wird, werden sie die gewünschte Zugriffsebene für erhalten, die Sie festgelegt.
