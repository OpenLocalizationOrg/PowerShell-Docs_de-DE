---
title: "Einschränken des Zugriffs auf SharePoint Online | Microsoft Intune"
description: "Schützen Sie und steuern Sie des Zugriffs auf Unternehmensdaten in SharePoint Online mit bedingten Zugriff."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: fe1fae610e4d562b467e9778841fc1c547db3bfa
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einschränken des Zugriffs auf SharePoint Online mit Microsoft Intune
Verwenden der [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] bedingte Zugriff auf Steuern des Zugriffs auf Dateien auf SharePoint online.
Bedingte Access besteht aus zwei Komponenten:
- Gerät Compliance-Richtlinie, die das Gerät mit erfüllen müssen, damit kompatibel sein.
- Bedingte Zugriffsrichtlinie, in dem Sie die Bedingungen, die das Gerät erfüllt werden muss angeben, um den Dienst zuzugreifen.
Finden Sie weitere Informationen zum wie bedingte Access funktioniert, [beschränken Sie den Zugriff auf e-Mail, Office 365, und andere Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) Thema aus.

Die Einhaltung von Vorschriften und bedingte-Richtlinien werden dem Benutzer bereitgestellt. Jedem Gerät, die der Benutzer Zugriff auf die Dienste verwendet, die für die Einhaltung der Richtlinien aktiviert ist.

Tritt auf, wenn ein Benutzer versucht, die Verbindung mit einer Datei mit einer app unterstützte, wie etwa OneDrive auf ihrem Gerät, die folgende Auswertung:

![Diagramm, um die Entscheidungspunkte anzeigen, die bestimmen, ob ein Gerät Zugriff auf SharePoint zulässig ist ist gesperrt. ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>Bedingte Zugriff für PCs und 10 unter Windows Mobile Geräte mit apps über moderne Authentifizierung steht derzeit nicht für alle Intune Kunden. Wenn Sie bereits diese Features verwenden, müssen Sie keine Aktionen durchführen. Sie können weiterhin verwenden können.

>Wenn Sie nicht für erstellt haben bedingte Richtlinien für PCs oder 10 unter Windows Mobile apps mit modernen Authentifizierung und muss möchte, damit Sie sich für die öffentliche Azure Active Directory-Vorschau Gerät wozu bedingten Zugriff für verwaltete Intune basiert miteinander Geräten oder Domäne Windows PCs. Weitere Informationen zu [Dieser Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/) zu lesen.

**Vor dem** Konfigurieren einer bedingten Zugriffsrichtlinie für SharePoint Online, müssen Sie folgende Aktionen ausführen:
- Ein **SharePoint Online-Abonnement** verfügen und Benutzer für SharePoint Online lizenziert werden müssen.
- Haben Sie ein Abonnement für die **Enterprise-Mobilität Suite** oder **Azure Active Directory Premium**.

  Zum Verbinden mit den erforderlichen Dateien, müssen das Gerät aus:
-   Mit **registriert** sein [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] oder einem PC Domänenverbund.

-   **Registrieren Sie sich das Gerät** in Azure Active Directory (Dies geschieht automatisch, wenn das Gerät mit registriert ist [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).


-   Kompatibel sein, mit einem beliebigen bereitgestellt [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Compliance-Regeln

Die des Geräts wird in Azure Active Directory gespeichert, die gewährt oder Zugriff auf Dateien, basierend auf den von Ihnen angegebenen blockiert.

Wenn eine Bedingung nicht erfüllt ist, wird dem Benutzer mit eine der folgenden Fehlermeldungen angezeigt, wenn sie sich anmelden:

-   Wenn das Gerät nicht registriert wird, mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], oder ist nicht registriert in Azure Active Directory, wird eine Meldung mit Anweisungen zum Installieren der app-Portal Unternehmen und registrieren, angezeigt.

-   Wenn das Gerät nicht kompatibel ist, wird eine Meldung angezeigt, die den Benutzer zur weiterleitet die [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Unternehmen Portal-Website, wo sie Informationen über das Problem und so beheben sie finden können.

**Bedingte Access wird erzwungen über alle SharePoint-Websites und externe Freigabe ist gesperrt.**

>[!NOTE]
>Wenn Sie bedingte Zugriff für SharePoint Online aktivieren, empfehlen wir, dass Sie die Domäne in der Liste deaktivieren, wie im Thema [Entfernen-SPOTenantSyncClientRestriction](https://technet.microsoft.com/en-us/library/dn917451.aspx) beschrieben.  
## Unterstützung für mobile Geräte
- iOS 8.0 und höher
- Android 4.0 und höher, Samsung Knox Standard 4.0 oder höher
- Windows Phone 8.1 und höher

Sie können in SharePoint Online beim Zugriff über einen Browser von **iOS** und **Android** -Geräten Zugriff einschränken.  Zugriff wird nur von nur unterstützte Browser auf kompatiblen Geräten zulässig sein:
* Safari (iOS)
* Chrome (Android)
* Verwaltete Browser (iOS und Android)

**Nicht unterstützte Browser blockiert werden**.

## Unterstützung für PCs
- Windows 8.1 und höher (wenn mit Intune registriert)
- Windows 7.0 oder Windows 8.1 (wenn Domänenverbund)

  - Domänenverbund PCs müssen eingerichtet werden, bei Azure Active Directory [automatisch zu registrieren](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) .
AAD DRS wird für Intune und Office-365-Kunden automatisch aktiviert. Kunden, die bereits ADFS Gerät Registrierungsdienst bereitgestellt haben, werden nicht registriert Geräte in deren lokalen Active Directory angezeigt.

  - Wenn die Richtlinie auf beitreten zu einer Domäne vorschreiben festgelegt ist, und dem Computer ist nicht für die Domäne, wird eine Meldung angezeigt, wenden Sie sich an die IT-Administrator.

  - Wenn die Richtlinie Join-Domäne vorschreiben festgelegt ist oder kompatible, und dem Computer wird entweder Anforderung nicht gerecht, mit Anweisungen zum Installieren der app-Portal Unternehmen und registrieren, wird eine Meldung angezeigt.
  >[!NOTE]
  >Bedingte Access wird auf den Intune Computer Client-PCs nicht unterstützt.

-    [Office 365 moderne Authentifizierung muss aktiviert sein](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), und die neuesten Office-Updates installiert haben.

    Modernes Authentifizierung bringt Anmeldung Active Directory Authentifizierung Bibliothek (ADAL) basierend auf Office 2013 Windows-Clients und Erhöhung der Sicherheit wie **mehrstufige Authentifizierung**und **Zertifikaten basierende Authentifizierung**ermöglicht.


## Konfigurieren von bedingten Zugriff für SharePoint Online

### Schritt 1: Konfigurieren von Active Directory-Sicherheitsgruppen
Bevor Sie beginnen, konfigurieren Sie Azure Active Directory-Sicherheitsgruppen für die bedingte Zugriffsrichtlinie auf. Sie können diesen Gruppen in der **Office 365-Verwaltungskonsole**oder im **Portal für Intune-Konto**konfigurieren. Diesen Gruppen werden von der Richtlinie Ziel oder ausgenommenen Benutzer verwendet werden. Wenn ein Benutzer durch eine Richtlinie vorgesehen ist, muss jedem Gerät, mit denen sie den Zugriff auf Ressourcen kompatibel sein.

Sie können zwei Arten von in einer SharePoint Online-Richtlinie angeben:

-   **Gezielte Gruppen** – enthält Gruppen von Benutzern, die die Richtlinie angewendet wird.

-   **Exempted Gruppen** – enthält Gruppen von Benutzern, die von der Richtlinie ausgenommen sind.

Wenn ein Benutzer in beiden Gruppen ist, werden sie von der Richtlinie ausgenommen.

### Schritt 2: Konfigurieren und Bereitstellen einer Richtlinie compliance
Wenn Sie dies nicht bereits getan haben, erstellen und Bereitstellen von Compliance-Richtlinien für Benutzer, denen die SharePoint Online-Richtlinie ausgerichtet ist.

> [!NOTE]
> Während der Compliance-Richtlinien für bereitgestellt werden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] gruppiert, bedingte Richtlinien sind Ziel Sicherheitsgruppen Azure Active Directory Access.

Weitere Informationen dazu, wie Sie die Compliance-Richtlinien konfigurieren finden Sie unter [Erstellen einer Richtlinie Compliance](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT]
> Wenn Sie eine Richtlinie Compliance nicht bereitgestellt haben, werden die Geräte als kompatibel angesehen.

Wenn Sie bereit sind, fahren Sie mit **Schritt 3**fort.

### Schritt 3: Konfigurieren der SharePoint Online-Richtlinie
Als Nächstes konfigurieren Sie die Richtlinie erfordern, dass nur verwaltete und kompatible Geräte SharePoint Online zugreifen können. Kann ich diese Richtlinie wird in Azure Active Directory gespeichert werden.

#### <a name="bkmk_spopolicy"></a>

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** > **Bedingte Access** > **SharePoint Online-Richtlinie**.
![Screenshot der Seite SharePoint Online-Richtlinie](../media/mdm-ca-spo-policy-configuration.png)

2.  Wählen Sie **bedingte Zugriffsrichtlinie für SharePoint Online zu aktivieren**.

3.  Sie können bedingte Access Richtlinie angewendet werden soll, wählen Sie unter **Zugriff auf die Anwendung**:

    -   **Alle Plattformen**

        Dieser Vorgang erfordert, dass jedem Gerät zum Zugreifen auf **SharePoint Online**verwendet wird registriert Intune und mit den Richtlinien kompatibel.  Jeder Clientanwendung mit **modernen Authentifizierung** unterliegt der bedingten Zugriffsrichtlinie aus. Wenn die Plattform von Intune derzeit nicht unterstützt wird, ist der Zugriff auf **SharePoint Online** blockiert.

        Markieren **alle Plattformen** bedeutet Option die Azure Active Directory alle Authentifizierungsanfragen, unabhängig davon, die von der Clientanwendung gemeldet Plattform dieser Richtlinie angewendet wird.  Alle Plattformen zu müssen registriert und erst kompatibel sind, mit Ausnahme von:
        *   Windows-Geräten werden benötigt registrierten und kompatible,-Domäne, die mit lokalen Active Directory oder beides hinzugefügt werden
        * Nicht unterstützte Plattformen wie Mac.  Jedoch werden mit modernen Authentifizierung aus diesen Plattformen stammen apps werden weiterhin blockiert.
        >[!TIP]
        >Diese Option möglicherweise nicht angezeigt, wenn Sie noch nicht mit bedingten Zugriff für PCs.  Verwenden Sie stattdessen die **bestimmten Plattformen** . Bedingte Zugriff für PCs ist nicht für alle Intune Kunden derzeit verfügbar.   Finden Sie weitere Informationen zum Zugriff auf dieses Feature [in diesem Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/)zu erhalten.

    -   **Bestimmten Plattformen**

         Bedingte Zugriffsrichtlinie gelten für alle Client-app, die mithilfe der moderne Authentifizierung ist auf den angegebenen Plattformen.

     Für Windows-PCs, dem Computer muss entweder sein, Domänenverbund oder registrierten mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und kompatibel. Sie können die folgenden Anforderungen festlegen:

     -   **Geräte müssen Domänenverbund oder kompatibel sein.** Wählen Sie diese Option, wenn Sie möchten, dass die PCs, um entweder werden Domänenverbund oder kompatible mit den festgelegten Richtlinien [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Wenn auf dem Computer nicht mit einer der folgenden Anforderungen erfüllt, wird der Benutzer aufgefordert, das Gerät mit registrieren [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **Geräte müssen Domänenverbund.** Wählen Sie diese Option, um die erfordern, dass die PCs Domänenverbund Exchange Online Zugriff auf sein müssen. Wenn der Computer nicht Domäne ist Zugriff auf e-Mails blockiert und der Benutzer wird aufgefordert, wenden Sie sich an die IT-Administrator.

     -   **Geräte müssen kompatibel sein.** Wählen Sie diese Option, um festzulegen, dass die PCs registriert sein müssen [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und kompatibel. Wenn auf dem Computer nicht registriert ist, wird eine Meldung mit Anweisungen zum Registrieren angezeigt.

4.   Wählen Sie unter **Zugriff über einen Webbrowser** zu SharePoint Online und OneDrive for Business können Sie den Zugriff auf Exchange Online nur über den unterstützten Browsern auswählen: Safari (iOS) und Chrome (Android). Zugriff von anderen Browsern werden blockiert.  Die gleiche Plattform Einschränkungen für die Anwendungszugriff für OneDrive ausgewählten gelten auch hier.

  **Android** -Geräten müssen Benutzern den Zugriff über einen Webbrowser ermöglichen.  Hierfür den Endbenutzer müssen die Option "Aktivieren Zugriff über einen Webbrowser" auf dem Gerät registrierten folgendermaßen aktivieren:
  1.    Starten Sie die **Portalseite app Unternehmen**ein.
  2.    Wechseln Sie zu der Seite **Einstellungen** , die drei Punkte (...) oder die Menütaste.
  3.    Drücken Sie die Schaltfläche **Zugriff über einen Webbrowser aktivieren** aus.
  4.  Abmelden bei Office 365 und Chrome Neustart des Chrome-Browsers.

  Auf **iOS und Android** -Plattformen wird um das Gerät zu identifizieren, das verwendet wird, den Zugriff auf Dienste, Azure Active Directory ein Zertifikat für Transport Layer Security (TLS) mit dem Gerät ausgeben.  Das Gerät zeigt das Zertifikat mit einer Aufforderung des Endbenutzers für das Zertifikat auszuwählen, wie in den folgenden Screenshots zu sehen. Der Endbenutzer muss dieses Zertifikat aktivieren, bevor sie weiterhin im Browser verwenden können.

  **iOS**

  ![Screenshot der Aufforderung Zertifikat auf einem ipad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![Screenshot der Aufforderung Zertifikat auf einem Android-Gerät](../media/mdm-browser-ca-android-cert-prompt.png)
5.  Wählen Sie unter **Gruppen als Ziel**aus **Ändern** , um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die die Richtlinie angewendet wird. Sie können dies alle Benutzer oder nur eine ausgewählte Gruppen von Benutzern als Ziel auswählen.

6.  Wählen Sie unter **Gruppen ausgenommen**optional **Ändern** , um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die von dieser Richtlinie ausgenommen sind.

6.  Wenn Sie fertig sind, wählen Sie **Speichern**aus.

Sie verfügen nicht über die bedingte Zugriffsrichtlinie bereitstellen, wird sofort wirksam.

### Schritt 4: Überwachen der Kompatibilität und bedingte Richtlinien
Klicken Sie im Arbeitsbereich **Gruppen** können Sie den Status Ihrer Geräte anzeigen.

Wählen Sie eine Gruppe mobilen Gerät aus, und klicken Sie dann auf die Registerkarte **Geräte** , wählen Sie eine der folgenden **Filter**:

-   **Geräte, die nicht mit AAD registriert sind** – diese Geräte von SharePoint Online gesperrt sind.

-   **Geräte, die nicht kompatibel sind** – diese Geräte von SharePoint Online gesperrt sind.

-   **Geräte, die mit AAD und kompatible registriert** – diese Geräte auf SharePoint Online zugreifen können.

### Siehe auch
[Zugriff auf e-Mail und Office 365-Diensten mit Microsoft Intune einschränken](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
