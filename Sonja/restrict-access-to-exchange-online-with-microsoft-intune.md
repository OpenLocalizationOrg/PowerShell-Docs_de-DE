---
title: "Einschränken der e-Mail-Zugriff auf Exchange Online | Microsoft Intune"
description: "Schützen Sie und steuern Sie des Zugriffs auf Unternehmens-e-Mail auf Exchange Online mit bedingten Zugriff."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 15aeddc7353c57e19fb43077b2e5dacb32808fc6
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# E-Mail-Zugriff auf Exchange Online und neuer Exchange Online dedizierter mit Intune einschränken

Wenn Sie eine Exchange Online dedizierte Umgebung besitzen müssen, um herauszufinden, ob es in der neuen oder älteren Konfigurations handelt, wenden Sie sich an Ihren Account Manager.

Konfigurieren Sie zur Steuerung des e-Mail-Zugriffs auf Exchange Online oder auf Ihrer neuen Umgebung für Exchange Online dedizierter bedingten Zugriff für Exchange Online in Intune ein.
Weitere Informationen zum wie bedingte Access funktioniert, lesen Sie im Artikel [Einschränken des Zugriffs auf e-Mail, Office 365, und andere Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

>[!IMPORTANT]
>Bedingte Zugriff für PCs und 10 unter Windows Mobile Geräte mit apps über moderne Authentifizierung steht derzeit nicht für alle Intune Kunden. Wenn Sie bereits diese Features verwenden, müssen Sie keine Aktionen durchführen. Sie können weiterhin verwenden können.

>Wenn Sie nicht für erstellt haben bedingte Richtlinien für PCs oder 10 unter Windows Mobile apps mit modernen Authentifizierung und muss möchte, damit Sie sich für die öffentliche Azure Active Directory-Vorschau Gerät wozu bedingten Zugriff für verwaltete Intune basiert miteinander Geräten oder Domäne Windows PCs. Lesen Sie weitere Informationen zu [Dieser Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/) .  

**Bevor** Sie bedingte Access konfigurieren können, müssen Sie folgende Aktionen ausführen:

-   Haben Sie ein **Office 365-Abonnement, die Exchange Online (z. B. E3) enthält** , und Benutzer für Exchange Online lizenziert werden müssen.

-  Erwägen Sie optional konfigurieren **Intune Microsoft-Dienst Verbinder**, der eine Verbindung herstellt [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Microsoft Exchange Online-und hilft, die Sie Geräteinformationen über verwalten die [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Console. Sie müssen nicht von der Verbinder um Compliance oder Richtlinien für bedingte Access verwenden, aber ist es erforderlich, zum Ausführen von Berichten, die Ihnen helfen, den Einfluss von bedingten Access ausgewertet werden soll.

   > [!NOTE]
   > Wenn Sie beabsichtigen, bedingten Zugriff für Exchange Online und Exchange lokal verwenden nicht konfigurieren Sie den Connector Dienst

   Anweisungen zum Konfigurieren des Verbinders finden Sie unter [Intune - Dienst connector](intune-service-to-service-exchange-connector.md)

Wenn bedingte-Richtlinien werden konfiguriert und dessen Ziel eines Benutzers, bevor ein Benutzer auf ihre e-Mails eine Verbindung herstellen kann, muss das **Gerät** , die sie verwenden:

-   **Registrierte** mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] oder ist eine Domäne beigetreten PC.

-  **Registriert in Azure-Active Directory**. Dies geschieht automatisch, wenn das Gerät mit registriert ist [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Darüber hinaus den Client, die, den Exchange ActiveSync-ID bei Azure Active Directory registriert sein.

  AAD DRS wird für Intune und Office 365-Kunden automatisch aktiviert. Kunden, die bereits ADFS Gerät Registrierungsdienst bereitgestellt haben, werden keine eingetragenen Geräte in ihrer lokalen Active Directory angezeigt.

-   **Kompatibel** mit einem [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Compliance-Richtlinien, die auf dem Gerät bereitgestellt oder die Domäne, die eine lokale Domäne hinzugefügt.

Wenn eine bedingte Zugriffsrichtlinie nicht erfüllt ist, wird dem Benutzer mit eine der folgenden Fehlermeldungen angezeigt, wenn sie sich anmelden:

- Wenn das Gerät nicht registriert wird, mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], oder ist nicht registriert in Azure Active Directory, wird eine Meldung mit Anweisungen zum Installieren der Portalseite Unternehmen-app, das Gerät zu registrieren, und aktivieren e-Mail angezeigt. Dieses Verfahren ordnet des Geräts Exchange ActiveSync-ID auch den Eintrag in Azure Active Directory.

-   Wenn das Gerät als nicht kompatibel mit der Richtlinie Compliance-Regeln ausgewertet wird, wird der Endbenutzer umgeleitet, zu der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Website Unternehmen Portal oder im Unternehmen Portal app, wo sie Informationen über das Problem und so beheben sie finden können.


Die folgende Abbildung zeigt den Ablauf von bedingten Richtlinien für Exchange Online verwendet wird.

![Diagramm, das die Entscheidungen Punkte dargestellt werden, die bestimmen, ob das Gerät ist der Zugriff erlaubt oder blockiert](../media/ConditionalAccess8-1.png)

## Unterstützung für mobile Geräte
Sie können den Zugriff auf Exchange Online-e-Mail einschränken, von **Outlook** und andere **apps, die moderne Authentifizierung verwenden**:-

- Android 4.0 und höher, Samsung Knox Standard 4.0 und höher
- iOS 8.0 und höher
- Windows Phone 8.1 und höher

**Modernes Authentifizierung** sorgt für Active Directory-Authentifizierung Bibliothek ADAL-basierten melden Sie sich bei Microsoft Office-Clients.

-   Die ADAL basiert Authentifizierung ermöglicht Office-Clients browserbasierte Authentifizierung (auch bekannt als passiven Authentifizierung) Teilnahme an.  Zum Authentifizieren, wird der Benutzer zu einer Webseite Anmeldung geleitet. Diese neue Methode Anmeldung ermöglicht Erhöhung der Sicherheit wie **mehrstufige Authentifizierung**und **Zertifikaten basierende Authentifizierung**.
In diesem [Artikel](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) enthält weitere Informationen wie moderne Authentifizierung funktioniert detaillierte.
Setup ADFS Ansprüche Regeln nicht Modern Authentifizierungsprotokolle blockieren. Wenn Sie ausführliche Anweisungen werden in Szenario 3: [Alle Zugriff auf Office 365 mit Ausnahme von Applications browserbasierte Sperren](https://technet.microsoft.com/library/dn592182.aspx)bereitgestellt.

Sie können mit **Outlook Web Access (OWA)** auf Exchange Online beim Zugriff über einen Browser auf **iOS** und **Android** -Geräten Zugriff einschränken.  Nur von nur unterstützte Browser auf kompatiblen Geräten Zugriff zulässig:

* Safari (iOS)
* Chrome (Android)
* Verwaltete Browser (iOS und Android)

**Nicht unterstützte Browser blockiert werden**.

Der OWA-apps für iOS und Android werden nicht unterstützt.  Sie sollten über ADFS Ansprüche Regeln blockiert werden.




Sie können den Zugriff auf Exchange-e-der integrierten **Exchange ActiveSync-e-Mail-Client** auf den folgenden Plattformen einschränken:

- Android 4.0 und höher, Samsung Knox Standard 4.0 und höher

- iOS 8.0 und höher

- Windows Phone 8.1 und höher

## Unterstützung für PCs

Sie können bedingte Zugriff für PCs einrichten, die ausgeführt Office-desktopanwendungen werden für **Exchange Online** und **SharePoint Online** für PCs zugreifen, die die folgenden Anforderungen entsprechen:

-   Dem Computer muss Windows 7.0 oder Windows 8.1 ausgeführt werden.

-   Dem Computer muss entweder Domäne verknüpften oder mit der Richtlinie Compliance-Regeln kompatibel sein.

    Kompatibel sein, muss der PC in registriert sein [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und die Richtlinien einzuhalten.

    Für die Domäne PCs hinzugefügt, müssen Sie ihn nach Zeitphasen bis zum [registrieren automatisch auf das Gerät](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) mit Azure Active Directory festlegen.
    >[!NOTE]
    >Bedingte Access wird auf den Intune Computer Client-PCs nicht unterstützt.

-   [Office 365 moderne Authentifizierung muss aktiviert sein](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), und die neuesten Office-Updates installiert haben.

    Modernes Authentifizierung bringt Anmeldung Active Directory Authentifizierung Bibliothek (ADAL) basierend auf Office 2013 Windows-Clients und Erhöhung der Sicherheit wie **mehrstufige Authentifizierung**und **Zertifikaten basierende Authentifizierung**ermöglicht.

-   Richten Sie ADFS Ansprüche Regeln nicht Modern Authentifizierungsprotokolle blockieren. Detaillierte Informationen werden in Szenario 3: [Blockieren aller Zugriff auf O365 mit Ausnahme von Applications browserbasierte](https://technet.microsoft.com/library/dn592182.aspx)bereitgestellt.

## Konfigurieren von bedingten Zugriff
### Schritt 1: Konfigurieren und Bereitstellen einer Richtlinie compliance
Stellen Sie sicher, dass Sie [Erstellen](create-a-device-compliance-policy-in-microsoft-intune.md) und [Bereitstellen](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) Compliance-Richtlinien auf die Benutzergruppen, die auch die bedingte Zugriffsrichtlinie erhalten werden.


> [!IMPORTANT]
> Wenn Sie eine Richtlinie Compliance nicht bereitgestellt haben, wird die Geräte kompatibel eingestuft und kann Zugriff auf Exchange.

### Schritt 2: Auswerten des Effekts der bedingten Zugriffsrichtlinie
Die **Mobile Geräte Inventory Berichte** können Sie die Geräte identifizieren möchten, die Zugriff auf Exchange, nachdem Sie die bedingte Zugriffsrichtlinie konfigurieren blockiert werden konnte.

Konfigurieren Sie hierzu eine Verbindung zwischen [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und Exchange mithilfe von [Microsoft Intune-Dienst Verbinder](intune-service-to-service-exchange-connector.md).
1.  Navigieren Sie zu **Berichten -> Mobilgerät Inventory Berichte**.
![Screenshot der Berichtsseite Inventory mobilen Gerät](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  Wählen Sie in den Berichtsparametern, die [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Gruppe ausgewertet werden soll und, falls erforderlich, die Geräteplattformen, dem die Richtlinie angewendet wird.
3.  Nachdem Sie die Kriterien, die den Anforderungen Ihrer Organisation entspricht ausgewählt haben, wählen Sie **Bericht anzeigen**.
Berichts-Viewer wird in einem neuen Fenster geöffnet.
![Screenshot eines mobilen Geräts Inventory-Beispielbericht](../media/IntuneSA2cViewReport.PNG)

Nachdem Sie den Bericht ausführen, untersuchen Sie diese vier Spalten, um festzustellen, ob ein Benutzer blockiert werden:

-   **Projektmanagement-Kanal** – gibt an, ob das Gerät von Intune, Exchange ActiveSync oder beides verwaltet wird.

-   **AAD registriert** – gibt an, ob das Gerät Azure Active Directory (Arbeitsplatz teilnehmen genannt) registriert ist.

-   **Kompatibel** – gibt an, ob das Gerät mit einem beliebigen Compliance-Richtlinien, die Sie bereitgestellt wird.

-   **Exchange ActiveSync-ID** – iOS und Android-Geräten sind erforderlich, deren Exchange ActiveSync-ID dem Gerät Registrierungsdatensatz in Azure Active Directory zugeordnet haben. Dies geschieht, wenn der Benutzer den **Aktivieren e-Mail-** Link in der e-Mail Quarantäne auswählt.

    > [!NOTE]
    > Windows Phone-Geräten werden immer einen Wert in dieser Spalte anzeigen.

Geräte, die eine ausgewählte Benutzergruppe gehören, werden den Zugriff auf Exchange, es sei denn, Sie Spaltenwerte entsprechen, die in der folgenden Tabelle aufgeführten blockiert werden:

--------------------------
|Projektmanagement-Kanal|AAD registriert|Kompatibel|Exchange ActiveSync-ID|Resultierende Aktion|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Von Microsoft Intune und Exchange ActiveSync verwaltet werden**|Ja|Ja|Ein Wert wird angezeigt.|E-Mail-Zugriff zulässig.|
|Alle anderen Werte|Nein|Nein|Kein Wert wird angezeigt.|Blockierte e-Mail-Zugriff|
----------------------
Sie können exportieren Sie den Inhalt des Berichts und die Spalte **E-Mail-Adresse** Ihre Benutzer informieren, dass diese blockiert werden.

### Schritt 3: Konfigurieren von Benutzergruppen für die bedingte Zugriffsrichtlinie
Bedingte-Richtlinien werden auf verschiedenen Azure Active Directory-Sicherheitsgruppen Benutzer abgestimmt. Sie können auch bestimmte Benutzergruppen aus dieser Richtlinie ausnehmen.  Wenn ein Benutzer von einer Richtlinie vorgesehen ist, muss jedem Gerät, mit denen sie akzeptieren, um-e-Mails kompatibel sein.

Sie können diesen Gruppen in der **Office 365-Verwaltungskonsole**oder im **Portal von Intune-Konto**konfigurieren.

Sie können zwei Arten von in jeder Richtlinie angeben:

-   **Gezielte Gruppen** – Benutzergruppen auf den die Richtlinie angewendet wird.

-   **Exempted Gruppen** – Benutzergruppen, die nicht in die Richtlinie (optional)

Wenn ein Benutzer in beiden Gruppen ist, werden sie von der Richtlinie ausgenommen.

Nur die von der Richtlinie bedingten Zugriff ausgelegt sind Gruppen ausgewertet werden.

### Schritt 4: Konfigurieren der bedingten Zugriffsrichtlinie

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** > **Bedingte Access** > **Exchange Online-Richtlinie**.
![Screenshot der Seite Richtlinie Exchange Online bedingten Zugriff](../media/mdm-ca-exo-policy-configuration.png)

2.  Wählen Sie auf der Seite **Exchange Online-Richtlinie** **bedingte Zugriffsrichtlinie für Exchange Online zu aktivieren**.

    > [!NOTE]
    > Wenn Sie eine Richtlinie Compliance nicht bereitgestellt haben, werden der Geräte als kompatibel angesehen.
    >
    > Alle Benutzer, die von der Richtlinie ausgelegt sind werden unabhängig vom Status Compliance aktivierten Geräte mit registrieren erforderlich werden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

3.  Wählen Sie unter **Zugriff auf die Anwendung**müssen für apps, die moderne Authentifizierung, verwenden Sie zwei Arten von auswählen welchen Plattformen die Richtlinie angewendet werden soll. Unterstützte Plattformen: Android, iOS, Windows und Windows Phone.

    -   **Alle Plattformen**

        Dieser Vorgang erfordert, dass jedem Gerät **Exchange Online**, und mit den Richtlinien Intune registriert sein Zugriff auf verwendet.  Jeder Clientanwendung mit **modernen Authentifizierung** unterliegt der bedingten Zugriffsrichtlinie und Zugriff auf **Exchange Online** ist gesperrt, wenn die Plattform von Intune derzeit nicht unterstützt wird.

        Markieren die Option **alle Plattformen** bedeutet die Azure Active Directory alle Authentifizierungsanfragen, unabhängig davon, die von der Clientanwendung gemeldet Plattform dieser Richtlinie angewendet wird.  Alle Plattformen zu müssen registriert und erst kompatibel sind, mit Ausnahme von:
        *   Windows-Geräten werden benötigt registrierten und kompatible,-Domäne, die mit lokalen Active Directory oder beides hinzugefügt werden
        * Nicht unterstützte Plattformen wie Mac OS.  Jedoch werden mit modernen Authentifizierung aus diesen Plattformen stammen apps werden weiterhin blockiert.

        >[!TIP]
           Diese Option möglicherweise nicht angezeigt, wenn Sie noch nicht mit bedingten Zugriff für PCs.  Verwenden Sie stattdessen die **bestimmten Plattformen** . Es ist nicht bedingten Zugriff für PCs derzeit für alle Intune Kunden verfügbar.   Finden Sie weitere Informationen dazu, wie Sie Zugriff auf dieses Feature [in diesem Blogbeitrag ](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azuread-conditional-access-policies-for-ios-android-and-windows-are-in-preview/)zu erhalten.

    -   **Bestimmten Plattformen**

         Bedingte Zugriffsrichtlinie wendet auf eine beliebige app, Client, die auf dem Geräteplattformen, die Sie angeben, **moderne Authentifizierung** verwendet wird.

4. Wählen Sie unter **Outlook Web Access (OWA)**, können Sie den Zugriff auf Exchange Online nur über den unterstützten Browsern auswählen: Safari (iOS) und Chrome (Android). Zugriff von anderen Browsern werden blockiert. Die gleiche Plattform Einschränkungen für die Anwendungszugriff für Outlook ausgewählten gelten auch hier.

  **Android** -Geräten müssen Benutzern den Zugriff über einen Webbrowser ermöglichen.  Hierfür den Endbenutzer müssen die Option "Aktivieren Zugriff über einen Webbrowser" auf dem Gerät registrierten folgendermaßen aktivieren:
  1.    Starten Sie die **Unternehmens-app-Portal**an.
  2.    Wechseln Sie zu der Seite **Einstellungen** , die drei Punkte (...) oder die Menütaste.
  3.    Drücken Sie die Schaltfläche **Zugriff über einen Webbrowser aktivieren** aus.
  4.    Abmelden bei Office 365 und Chrome Neustart des Chrome-Browsers.

  Auf **iOS und Android** -Plattformen wird um das Gerät zu identifizieren, das verwendet wird, den Zugriff auf Dienste, Azure Active Directory ein Zertifikat für Transport Layer Security (TLS) mit dem Gerät ausgeben.  Das Gerät zeigt das Zertifikat mit einer Aufforderung des Endbenutzers für das Zertifikat auszuwählen, wie in den folgenden Screenshots zu sehen. Der Endbenutzer muss dieses Zertifikat aktivieren, bevor sie weiterhin im Browser verwenden können.

  **iOS**

  ![Screenshot der Aufforderung Zertifikat auf einem ipad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![Screenshot der Aufforderung Zertifikat auf einem Android-Gerät](../media/mdm-browser-ca-android-cert-prompt.png)

5.  Klicken Sie unter **Exchange ActiveSync-apps**können Sie den Zugriff auf Exchange Online nicht kompatible Geräte blockieren auswählen. Sie können auch auswählen, ob So ermöglichen oder Sperren Zugriff auf e-Mails aus, wenn das Gerät nicht unterstützte Plattform ausgeführt wird. Unterstützte Plattformen: Android, iOS, Windows und Windows Phone.

6.  Wählen Sie unter **Gruppen als Ziel**der Active Directory-Sicherheitsgruppen der Benutzer, die die Richtlinie angewendet wird. Sie können entweder alle Benutzer oder eine ausgewählte Liste von Benutzergruppen als Ziel auswählen.
![Screenshot der Exchange Online bedingten Zugriff Richtlinienseite mit den Optionen für gezielte und Exempted Gruppe](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE]
    > Für Benutzer, die in den **Gruppen gezielte**sind, das Intune Richtlinien wird Exchange Regeln und Richtlinien zu ersetzen.
    >
    > Exchange wird nur im Exchange erzwingen zulassen, blockieren und Quarantäne Regeln und Richtlinien Exchange, wenn:
    >
    > -   Der Benutzer ist nicht für Intune lizenziert.
    > -   Der Benutzer für Intune lizenziert ist, aber der Benutzer nicht zu Ziel waren die bedingte Zugriffsrichtlinie Sicherheitsgruppen gehört.

6.  Wählen Sie unter **Gruppen ausgenommen**der Active Directory-Sicherheitsgruppen von Benutzern, die von dieser Richtlinie ausgenommen werden. Wenn ein Benutzer in den Gruppen zielgerichteten und ausgenommenen ist, werden sie von der Richtlinie ausgenommen.

7.  Wenn Sie fertig sind, wählen Sie **Speichern**aus.

-   Sie verfügen nicht über die bedingte Zugriffsrichtlinie bereitstellen, wird sofort wirksam.

-   Nachdem ein Benutzer ein e-Mail-Konto erstellt hat, wird das Gerät sofort blockiert.

-   Wenn ein Benutzer gesperrten Gerät mit registriert wird [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und Korrekturen bei einem beliebigen nicht-Konformität Probleme, e-Mail-Zugriff wird innerhalb von zwei Minuten freigegeben werden soll.

-   Wenn der Benutzer un-Geräts, registriert e-Mail wird nach ungefähr 6 Stunden blockiert.

**Einige Beispielszenarien der, wie Sie bedingte Zugriffsrichtlinie zum Einschränken des Zugriffs Gerät konfigurieren möchten, finden Sie unter [Beispielszenarien für e-Mail-Zugriff einschränken](restrict-email-access-example-scenarios.md).**

## Überwachen Sie die Einhaltung von Vorschriften und bedingte Richtlinien

#### Geräte anzeigen möchten, die von Exchange gesperrt sind

Klicken Sie auf die [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Dashboard, wählen Sie die Kachel **Blockiert Geräte von Exchange** , um die Anzahl der blockierten Geräte und Links zu weiteren Informationen anzuzeigen.
![Screenshot der Intune-Dashboard mit der Anzahl der Geräte, die Zugriff auf Exchange blockiert werden](../media/IntuneSA6BlockedDevices.PNG)

## Nächste Schritte
[Einschränken des Zugriffs auf SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Einschränken des Zugriffs auf Skype für Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
