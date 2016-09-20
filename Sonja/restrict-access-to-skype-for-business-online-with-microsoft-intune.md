---
title: "Einschränken des Zugriffs auf Skype für Business Online | Microsoft Intune"
description: "Schützen Sie und steuern Sie des Zugriffs auf Skype für Business Online mit bedingten Zugriff."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: a0db4bd6d1ae55b5d82152f8d4910204e857cc85
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einschränken des Zugriffs auf Skype für Business Online mit Microsoft Intune
Verwenden Sie zum Steuern des Zugriffs auf Skype für Business Online bedingte Zugriffsrichtlinie für **Skype für Business Online** ein.
Bedingte Access besteht aus zwei Komponenten:
- Gerät Compliance-Richtlinie, die das Gerät mit erfüllen müssen, damit kompatibel sein.
- Bedingte Zugriffsrichtlinie, in dem Sie die Konditionen, die das Gerät erfüllen muss, um den Zugriff auf den Dienst angeben.
Weitere Informationen zu wie bedingte Access Works Informationen hierzu im Artikel [Einschränken des Zugriffs auf e-Mail- und O365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

Wenn ein Benutzer den versucht, Skype für Business Online auf ihrem Gerät verwenden, tritt auf, die nach der Auswertung:

![Diagramm zeigt die Entscheidungspunkte, die verwendet wird, um festzustellen, ob ein Gerät Zugriff auf Skype für Business Online erlaubt oder blockiert](../media/ConditionalAccess_SkypeforBusiness.png)

**Vor** eine bedingten Zugriffsrichtlinie für Skype für Business Online zu konfigurieren, müssen Sie folgende Aktionen ausführen:
- Ein **Skype für Business Online-Abonnement** verfügen und Benutzern Skype für Business Online-Lizenz zuweisen.
- Verfügen Sie über ein Abonnement für die **Enterprise-Mobilität Suite** oder **Azure Active Directory Premium**.
-   [Aktivieren Sie moderne Authentifizierung](https://docs.microsoft.com/en-us/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) für Skype für Business Online.
-  Alle Endbenutzer müssen **Skype für Business Online**verwenden. Wenn Sie eine Bereitstellung mit Skype für Business Online und Skype für Business lokalen verfügen, wird bedingte Zugriffsrichtlinie auf Endbenutzer nicht angewendet.

    Das Gerät, das Zugriff auf die Skype für Business Online erledigen muss:

-   Werden Sie einem **Android** oder **iOS** -Gerät an.

-   Mit **registriert** sein [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   **Kompatibel** mit einem beliebigen bereitgestellt werden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Compliance-Richtlinien.


Der Zustand Gerät wird in Azure Active Directory gespeichert, die gewährt oder blockiert Access, basierend auf den von Ihnen angegebenen.

Wenn eine Bedingung nicht erfüllt ist, wird dem Benutzer mit eine der folgenden Fehlermeldungen angezeigt, wenn sie sich anmelden:

-   Wenn das Gerät nicht registriert wird, mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], oder ist nicht registriert in Azure Active Directory, wird eine Meldung angezeigt, mit einer Anleitung dazu, wie Sie die Unternehmen Portal app installieren und registrieren.

-   Wenn das Gerät nicht kompatibel ist, wird eine Meldung angezeigt, die den Benutzer zur weiterleitet der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Unternehmen Portal Website oder Unternehmen Portal app, wo sie Informationen über das Problem und so beheben sie finden können.

## Konfigurieren von bedingten Zugriff für Skype für Business Online

### Schritt 1: Konfigurieren von Active Directory-Sicherheitsgruppen
Bevor Sie beginnen, konfigurieren Sie Azure Active Directory-Sicherheitsgruppen für die bedingte Zugriffsrichtlinie auf. Sie können diesen Gruppen in der **Office 365-Verwaltungskonsole**konfigurieren. Diese Gruppen werden Ziel oder ausgenommenen Benutzer von der Richtlinie verwendet werden. Wenn ein Benutzer von einer Richtlinie vorgesehen ist, muss jedes Gerät, mit denen sie den Zugriff auf Ressourcen kompatibel sein.

Sie können angeben, dass zwei Arten von für die Skype für Business Richtlinie verwendet werden soll:

-   **Gezielte Gruppen** – enthält Gruppen von Benutzern, die die Richtlinie angewendet wird.

-   **Exempted Gruppen** – enthält Gruppen von Benutzern, die von der Richtlinie ausgenommen sind.

Wenn ein Benutzer in beiden Gruppen ist, werden sie von der Richtlinie ausgenommen.

### Schritt 2: Konfigurieren und Bereitstellen einer Richtlinie compliance
[Erstellen](create-a-device-compliance-policy-in-microsoft-intune.md) und [Bereitstellen](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) einer Compliance-Richtlinie an alle Geräte, die von der Richtlinie beeinflusst. Diese wäre alle Geräte, die von den Benutzern in den **Gruppen gezielte**verwendet werden.

> [!NOTE]
> Während Sie auf Compliance-Richtlinien bereitgestellt werden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] gruppiert, bedingten Richtlinien sind Ziel Azure Active Directory-Sicherheitsgruppen Zugriff.


> [!IMPORTANT]
> Wenn Sie eine Richtlinie Compliance nicht bereitgestellt haben, werden die Geräte als kompatibel angesehen.

Wenn Sie bereit sind, fahren Sie mit **Schritt 3**fort.

### Schritt 3: Konfigurieren der Skype für Business Online Richtlinie
Konfigurieren Sie anschließend die Richtlinie, um festzulegen, dass nur verwaltete und kompatible Geräte Skype für Business Online zugreifen können. Kann ich diese Richtlinie wird in Azure Active Directory gespeichert werden.

####
1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com)auf die **Richtlinie** > **Bedingte Access** > **Skype für Business Online Richtlinie**.

![Screenshot von Skype für Business Online bedingte Richtlinie Datenzugriffsseite](./media/conditional_access_SFBPolicy.png)

2.  Wählen Sie **bedingte Zugriffsrichtlinie aktivieren**.

3.  Wählen Sie unter **Zugriff auf die Anwendung**können Sie bedingte Access Richtlinie angewendet werden soll:

    -   **iOS**

    -   **Android**

4.  Klicken Sie auf **Ändern** , um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die die Richtlinie angewendet wird, klicken Sie unter **Gruppen ausgerichtet**. Sie können dies für alle Benutzer oder nur einer ausgewählten Gruppe von Benutzern als Ziel auswählen.

5.  Klicken Sie unter **Gruppen ausgenommen**optional, klicken Sie auf **Ändern** , um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die von dieser Richtlinie ausgenommen sind.

6.  Wenn Sie fertig sind, klicken Sie auf **Speichern**.

Sie haben nun bedingten Zugriff für Skype für Business Online konfiguriert. Sie verfügen nicht über die bedingte Zugriffsrichtlinie bereitstellen, wird sofort wirksam.


## Überwachen Sie die Einhaltung von Vorschriften und bedingte Richtlinien
Klicken Sie im Arbeitsbereich **Gruppen** können Sie den bedingten Zugriffsstatus Ihrer Geräte anzeigen.

Wählen Sie eine Gruppe mobilen Gerät aus, und klicken Sie dann auf die Registerkarte **Geräte** , wählen Sie eine der folgenden **Filter**:

* **Geräte, die nicht mit AAD registriert sind** – diese Geräte von Skype für Business Online blockiert werden.

* **Geräte, die nicht kompatibel sind** – diese Geräte von Skype für Business Online blockiert werden.

* **Geräte, die mit AAD und kompatible registriert** – diese Geräte können Skype für Business Online zugreifen.
