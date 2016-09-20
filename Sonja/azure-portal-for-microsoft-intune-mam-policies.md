---
title: "Azure-Portal für MAM Richtlinien | Microsoft Intune"
description: "Mobile-app Informationsverwaltungsrichtlinien, die über das Azure-Portal zu erstellen. Die hier von Ihnen erstellten Richtlinien können auf Geräten mit oder ohne Registrierung in Intune angewendet werden."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 1ddb7a30a6f23a3f3d754bd18975c50f32662578
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Azure-Portal für Microsoft Intune MAM Richtlinien
## Zugreifen auf das Portal Azure
Im **Portal Azure** ermöglicht erstellen und Verwalten von Informationsverwaltungsrichtlinien mobile-app.

Azure Portals unterstützt das Erstellen von MAM Richtlinien für:
- Apps für Geräte **registriert und von Intune verwaltet wird**ausgeführt.
- Apps für Geräte, die in einer beliebigen MDM Lösung **nicht registriert** sind ausgeführt.
- Apps für Geräte, die **in der Lösung eines Drittanbieters MDM registriert**sind ausgeführt.

>[!IMPORTANT]

> Wenn Sie derzeit die Intune-Verwaltungskonsole zum Verwalten von Ihren Geräten verwenden, können Sie eine Richtlinie MAM erstellen, die Apps für Geräte in Intune mithilfe der [Verwaltungskonsole Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)registriert unterstützt.

> Alle MAM Richtlinieneinstellungen in der Administrator Intune-Verwaltungskonsole möglicherweise nicht angezeigt. Das Azure Portal ist die neue Administratorkonsole zum Erstellen von MAM. Wenn Sie sowohl Intune-Verwaltungskonsole und Azure-Portal MAM Richtlinien erstellen, ist die Richtlinie Azure-Portal die apps angewendet und für Benutzer bereitgestellt.

## Melden Sie sich im Portal Azure und Anpassen der Startseite angezeigt

1.  Wechseln Sie im [Portal Azure](https://portal.azure.com) , und melden Sie sich mit Ihrem [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Anmeldeinformationen.

    ![Screenshot der Azure-Portal-Protokoll Seite](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  Sobald Sie erfolgreich angemeldet sind, wird das **Dashboard**angezeigt. Die Seite **Dashboard** kann angepasst werden.

    ![Screenshot des Portals Azure Dashboards](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Finden Sie im Menü **Durchsuchen** **Intune**aus. ![Screenshot des Menüs durchsuchen mit hervorgehobenem Intune](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Wählen Sie **Intune > mobile anwendungsverwaltung Intune > Einstellungen**.

    ![Screenshot des Intune mobilen Anwendung Management Blades](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Eine Blade zur **Startseite** anheften, können Sie die **Pin** -Option auf das Blade.  Klicken Sie auf das Symbol für Fixieren auf das **Intune mobilen Anwendung Management Blade**, um zur **Startseite** zu fixieren.

    ![Screenshot des Intune mobilen Anwendung Management Blades mit dem Pinsymbol hervorgehoben](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Screenshot des Dashboards mit der angehefteten Intune-Kachel](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## Nächste Schritte
[Bereiten Sie sich zum Konfigurieren von Informationsverwaltungsrichtlinien für mobile-app](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
