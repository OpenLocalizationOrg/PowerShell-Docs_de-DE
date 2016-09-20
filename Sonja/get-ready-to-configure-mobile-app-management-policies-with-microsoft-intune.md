---
title: Bereiten Sie sich zum Konfigurieren von Richtlinien MAM | Microsoft Intune
description: "In diesem Thema werden die erforderlichen Komponenten und Einrichten von Benutzern, bevor Sie mobile-app Informationsverwaltungsrichtlinien erstellen können."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: aeaa64124384a71126eeca7339416b80d395d07d
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune Fertigstellen
In diesem Thema wird beschrieben, was Sie tun müssen, bevor Sie mobile-app Informationsverwaltungsrichtlinien (MAM) im Azure-Portal erstellen können.

Das Azure Portal ist die neue Administratorkonsole zum Erstellen von MAM. Es empfiehlt sich, dass Sie mithilfe dieser Portal um MAM Richtlinien zu erstellen. Azure-Portal unterstützt die folgenden MAM Szenarien:
- Geräte, die Intune registriert sind
- Geräte, die von der Lösung eines Drittanbieters MDM verwaltet werden
- Geräte, die nicht von einem beliebigen MDM-Lösung (BYOD) verwaltet werden

Wenn Sie bei der Verwendung von Azure-Portal nicht vertraut sind, lesen Sie das Thema [Azure-Portal für Microsoft Intune MAM Richtlinien](azure-portal-for-microsoft-intune-mam-policies.md) , um einen schnellen Überblick zu erhalten.

>[!IMPORTANT]

> Wenn Sie derzeit die Intune-Verwaltungskonsole zum Verwalten von Ihren Geräten verwenden, können Sie MAM Richtlinien erstellen, die apps für Geräte in Intune mithilfe der Verwaltungskonsole Intune registriert unterstützen. Wir empfehlen jedoch die Verwendung des Azure-Portals auch für Geräte, der Intune registriert sind. Anweisungen zum Erstellen einer MAM-Richtlinie mithilfe der Verwaltungskonsole Intune finden Sie unter [Konfigurieren und Bereitstellen von Informationsverwaltungsrichtlinien in der Microsoft Intune Verwaltungskonsole mobilen Anwendung](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Alle MAM Richtlinieneinstellungen in der Administrator Intune-Verwaltungskonsole möglicherweise nicht angezeigt. Wenn Sie sowohl die Intune-Verwaltungskonsole und Azure-Portal MAM Richtlinien erstellen, ist die Richtlinie in Azure-Portal die apps angewendet und für Benutzer bereitgestellt.
> MAM Richtlinien, die in der Verwaltungskonsole Intune erstellt werden können nicht in der Azure-Portal importiert werden.  Die Richtlinien MAM müssen in der Azure-Portal neu erstellt werden.


##  Unterstützte Plattformen
- iOS 8.1 oder höher

- Android 4 oder höher

Windows-Geräten werden derzeit nicht unterstützt.
##  Unterstützte apps
* **Microsoft-apps:** Dieser apps das App SDK sich Intune und erfordern keine weitere Verarbeitung, bevor Sie MAM Richtlinien anwenden.
Um die vollständige Liste der unterstützten Microsoft-apps anzuzeigen, wechseln Sie zur [Microsoft Intune mobilen Anwendung Katalog](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) auf der Seite von Microsoft Intune Anwendung Partner zur Verfügung. Klicken Sie auf einer app zu den unterstützten Szenarien und Plattformen finden Sie unter, und prüfen, ob die app mehrere Identitäten unterstützt.
* **Ihrer Organisation Branchen apps:** Diese erfordern Vorbereiten der apps Intune App SDK aufnehmen möchten, bevor Sie MAM Richtlinien anwenden können.

  * Geräte, die von Intune verwaltet werden, finden Sie unter [entscheiden, wie apps für MAM vorbereiten](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).
  * Für Geräte, die nicht (wie im Besitz eines Mitarbeiters Geräte) verwaltet werden, oder für Geräte, die von einer Lösung Mobilgerät Drittanbieters verwaltet werden, finden Sie unter [schützen Branchen apps und Daten auf Geräten, die nicht in Intune registriert](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

*Bevor* Sie MAM Richtlinien konfigurieren können, benötigen Sie Folgendes:

-   Ein Microsoft-Intune-Abonnement.    Müssen Benutzer [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Lizenzen für apps zu erhalten, die Richtlinien MAM aufweisen.

-   Ein Office 365-Abonnement für Folgendes erforderlich ist:
  - Apps mit Unterstützung für mehrere MAM Richtlinien zuweisen.
  - Zum Erstellen von SharePoint Online und Exchange Online-Arbeit-Konten. Lokalen Exchange und SharePoint lokal werden nicht unterstützt.
-   Skype für Business Online-Setup für moderne Authentifizierung. Weitere Informationen finden Sie unter [moderne Authentifizierung aktivieren](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).


- Azure Active Directory (Azure AD) zum Erstellen von Benutzern. Azure AD authentifiziert Benutzer aus, wenn sie die app zu öffnen, und geben Sie ihre Anmeldeinformationen für die Arbeit.

    > [!NOTE]
    > Wenn Sie Benutzer mithilfe von Einrichten der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] console, beachten Sie, dass die Konfiguration der MAM Azure-Portal verschoben werden. Wenn Sie dieses Portal verwenden möchten, müssen Sie mithilfe von Office 365-Portal Azure AD-Benutzergruppen einrichten.


## Erstellen von Benutzern und Zuweisen von Lizenzen für Microsoft Intune

1. Stellen Sie sicher, dass Sie über eine Intune-Abonnement verfügen. Bereits eine [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Abonnement, wenn Sie aktuell arbeiten [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] zum Verwalten Ihrer Geräte.  Haben Sie auch eine [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Abonnement, wenn Sie eine Lizenz für Enterprise Mobilität Suite (EMS) erworben haben. Wenn Sie versuchen, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] checken Sie die Funktionen MAM Sie können ein Testkonto auf der [Microsoft Intune Webseite](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)abrufen.

    Prüfen, ob die stehen Ihnen eine [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Abonnement im Office-Portal, wechseln Sie zu der Seite **Abrechnung** .  Sie sollten finden Sie unter [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] als **aktiv** in der Abonnements.

2.  Melden Sie sich mit dem [Office-Portal](http://portal.office.com) mit Administrator-Anmeldeberechtigungen.

3.  Wechseln Sie zu der Seite **Aktive Benutzer** zum Hinzufügen von Benutzern und Zuweisen von [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Lizenzen.

    ![Seite mit aktiven Benutzer in Office-portal](../media/AppManagement/OfficePortal_AddUsers.png)

    ![Bearbeiten der Seite "Benutzer" im Office-Portal](../media/AppManagement/OfficePortal_AssignLicenses.png)

4.  Zum Erteilen Sie einem Benutzer des Zugriff auf die Office-Portal, Azure AD-Portal und dem Azure-Portal die Rolle des **globalen Administrators** dem Benutzer zuweisen.

    ![Seite zum Bearbeiten von Benutzerrollen in Office-portal](../media/AppManagement/OfficePortal_AddRoletoUser.png)

5.  MAM-Richtlinien werden auf Benutzergruppen in Azure Active Directory bereitgestellt. Um die Benutzergruppen für Ihre MAM Richtlinien zu erstellen, wechseln Sie zu der Seite **Gruppen** in Office-Portal, und wählen Sie im oberen Menü zum Erstellen einer neuen Sicherheitsgruppe die **Gruppenoption hinzufügen** aus.  Geben Sie einen Namen und eine Beschreibung ein, und klicken Sie dann auf **Erstellen**. Beim Erstellen die Gruppe können Sie Benutzer zur Gruppe hinzufügen, indem Sie auf **Bearbeiten der Mitglieder**. Die Sicherheitsgruppe wird in Azure Active Directory erstellt.

    ![Seite für Sicherheitsgruppen in Office-portal](../media/AppManagement/OfficePortal_CreateGroups.png)

Die folgende Tabelle listet die Rollen und Berechtigungen, die für Benutzer Administrator zugewiesen werden können.

|||
|--|----|
|**Rolle**|**Berechtigungen**|
|Globaler Administrator (Office 365-Portal)|Zugriff auf Office 365-Portal und Azure AD-Portal.<br /><br />Zugriff auf den Azure-Portal (können sowohl Rolle Management und mobile-app-Verwaltungsaufgaben ausführen).|
|Besitzer (Azure Portal)|Zugriff auf den Azure-Portal (können sowohl Rolle Verwaltung und mobile-app-Verwaltungsaufgaben ausführen).|
|Mitwirkender (Azure Portal)|Zugriff auf den Azure-Portal (können nur in der mobilen app-Verwaltungsaufgaben ausführen).|

## Zuweisen der Rolle "Mitwirkender" für einen Benutzer

Globale Administratoren haben Zugriff auf das [Azure-Portal](https://portal.azure.com)an.  Wenn andere Benutzer Administrator in der Lage ist, führen Sie zum Konfigurieren von Richtlinien und andere mobile-app-Verwaltungsaufgaben sein soll, können Sie die Rolle "Mitwirkender" für die Benutzer zuweisen:


1.  Klicken Sie auf **Einstellungen** vorher, in dem im Abschnitt **Ressource verwalten** klicken Sie auf **Benutzer**.

    ![Benutzer vorher in der Azure-portal](../media/AppManagement/AzurePortal_MAM_AddUsers.png)

2.  Klicken Sie auf **Hinzufügen** , um das Blade **Access hinzufügen** zu öffnen.

3.  Klicken Sie auf, **Wählen Sie eine Rolle aus**, und klicken Sie dann auf **Mitwirkender**.

    ![Wählen Sie eine Rolle Blade Azure-Portal](../media/AppManagement/AzurePortal_MAM_AddRole.png)

4.  Klicken Sie auf **Benutzer hinzufügen**, und suchen Sie nach Namen oder e-Mail-Adressen für den Benutzer. Benutzer, die Sie in dieser Liste zu sehen sind die ersten 1.000 Benutzer, die Sie zuvor in Azure Active Directory erstellt haben, mithilfe das Office-Portal an. Klicken Sie auf das **Hinzufügen von Access** Blade zu speichern und die Benutzer die Rolle zuweisen auf **OK** .

    ![Hinzufügen von Benutzern Blade Azure-Portal](../media/AppManagement/AzurePortal_MAM_AddusertoRole.png)

    > [!IMPORTANT]
    > Wenn Sie einen Benutzer auswählen, die keinen enthält eine [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Lizenz zugewiesen werden, sie sind nicht in der Lage, auf das Portal zugreifen.

## Nächste Schritte
[Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien mit Microsoft Intune mobile-app](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
