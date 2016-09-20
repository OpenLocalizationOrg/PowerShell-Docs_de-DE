---
title: "Einschränken der e-Mail-Zugriff auf Dynamics CRM Online | Microsoft Intune"
description: "Schützen Sie und steuern Sie des Zugriffs auf Dynamics CRM online mit bedingten Zugriff."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: dd322ff1a699da9444598135a6614f5e2d24ccc5
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einschränken der e-Mail-Zugriff auf Dynamics CRM Online mit Intune
Sie können Zugriff auf Microsoft Dynamics CRM Online iOS und Android-Geräten mit Microsoft Intune bedingten Zugriff steuern.  Bedingte Access Intune besteht aus zwei Komponenten:
* [Gerät Compliance-Richtlinien](introduction-to-device-compliance-policies-in-microsoft-intune.md) , die das Gerät mit erfüllen müssen, damit kompatibel sein.
* [Bedingte Zugriffsrichtlinie](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) , in dem Sie die Konditionen, die das Gerät erfüllen muss, um den Zugriff auf den Dienst angeben.

Weitere Informationen zum wie bedingte Access funktioniert, lesen Sie im Artikel [Einschränken des Zugriffs auf e-Mails, 0365, und andere Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

Tritt auf, wenn ein gezielter Benutzer versucht, die Dynamics CRM-app auf ihrem Gerät verwenden, die folgende Auswertung:

![Diagramm anzeigen, die Entscheidungspunkte verwendet, um zu bestimmen, ob ein Gerät Zugriff auf einen Dienst zulässig ist oder ist gesperrt](../media/mdm-ca-dynamics-crm-flow-diagram.png)

Das Gerät, das Zugriff auf Dynamics CRM Online erledigen muss:
* Werden Sie einem **Android** oder **iOS** -Gerät an.
* Werden Sie mit Microsoft Intune **registriert** .
* Mit einer beliebigen bereitgestellten Microsoft Intune Compliance-Richtlinien **kompatibel** sein können.

Der Zustand Gerät wird in Azure Active Directory gespeichert, die gewährt oder blockiert Access, basierend auf den von Ihnen angegebenen.

Wenn eine Bedingung nicht erfüllt ist, wird dem Benutzer mit eine der folgenden Fehlermeldungen angezeigt, wenn sie sich anmelden:
* Wenn das Gerät nicht mit Microsoft Intune registriert ist oder nicht in Azure Active Directory registriert ist, wird eine Meldung angezeigt, mit einer Anleitung dazu, wie Sie die Unternehmen Portal app installieren und registrieren.
* Wenn das Gerät nicht kompatibel ist, wird eine Meldung angezeigt, die den Benutzer der Website Microsoft Intune Unternehmen Portal oder Unternehmen Portal app anweisen, wo sie Informationen über das Problem und wie Sie es beheben finden.

## Konfigurieren von bedingten Zugriff für Dynamics CRM Online  
### Schritt 1: Konfigurieren von Active Directory-Sicherheitsgruppen

Bevor Sie beginnen, konfigurieren Sie Azure Active Directory-Sicherheitsgruppen für die bedingte Zugriffsrichtlinie auf. Sie können diesen Gruppen in der **Office 365-Verwaltungskonsole**konfigurieren. Diese Gruppen werden Ziel oder ausgenommenen Benutzer von der Richtlinie verwendet werden. Wenn ein Benutzer von einer Richtlinie vorgesehen ist, muss jedes Gerät, mit denen sie den Zugriff auf Ressourcen kompatibel sein.

Sie können zwei Arten von zur Verwendung für die Richtlinie Dynamics CRM angeben:
* **Gezielte Gruppen** – enthält Gruppen von Benutzern, die die Richtlinie angewendet wird.
* **Exempted Gruppen** – enthält Gruppen von Benutzern, die von der Richtlinie ausgenommen sind.

Wenn ein Benutzer in beiden Gruppen ist, werden sie von der Richtlinie ausgenommen.

### Schritt 2: Konfigurieren und Bereitstellen einer Richtlinie compliance
[Erstellen](create-a-device-compliance-policy-in-microsoft-intune.md) und [Bereitstellen](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) einer Compliance-Richtlinie an alle Geräte, die von der Richtlinie beeinflusst. Diese wäre alle Geräte, die von den Benutzern in den Gruppen gezielte verwendet werden.

> [!NOTE]
> Während der Compliance-Richtlinien für Microsoft Intune-Gruppen bereitgestellt werden, sind bedingte Richtlinien auf Azure-Active Directory-Sicherheitsgruppen abgestimmt.

> [!IMPORTANT]
> Wenn Sie eine Richtlinie Compliance nicht bereitgestellt haben, werden die Geräte als kompatibel angesehen.

Wenn Sie bereit sind, fahren Sie mit Schritt 3 fort.
### Schritt 3: Konfigurieren Sie die Richtlinie Dynamics CRM
Konfigurieren Sie anschließend die Richtlinie, um festzulegen, dass nur verwaltete und kompatible Geräte Dynamics CRM zugreifen können. Kann ich diese Richtlinie wird in Azure Active Directory gespeichert werden.

1.  Wählen Sie in der Microsoft-Intune-Verwaltungskonsole **Richtlinie > bedingten Zugriff > Dynamics CRM Online Richtlinie**.

  ![Screenshot der Seite Richtlinie Dynamics CRM Online bedingten Zugriff](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Wählen Sie Richtlinie **bedingten Zugriff aktivieren** .
3.  Wählen Sie unter **Zugriff auf die Anwendung**können Sie bedingte Access Richtlinie angewendet werden soll:
  * **iOS**
  * **Android**
4.  Wählen Sie unter **Gruppen als Ziel**aus **Ändern** , um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die die Richtlinie angewendet wird. Sie können dies für alle Benutzer oder nur einer ausgewählten Gruppe von Benutzern als Ziel auswählen.
5.  Wählen Sie unter **Gruppen ausgenommen**optional **Ändern** , um die Azure Active Directory-Sicherheitsgruppen auszuwählen, die von dieser Richtlinie ausgenommen sind.
6.  Wenn Sie fertig sind, wählen Sie **Speichern**aus.

Jetzt haben Sie bedingte Zugriff für Dynamics CRM konfiguriert. Sie verfügen nicht über die bedingte Zugriffsrichtlinie bereitstellen, wird sofort wirksam.
##  Überwachen Sie die Einhaltung von Vorschriften und bedingte Richtlinien

Klicken Sie im Arbeitsbereich **Gruppen** können Sie den bedingten Zugriffsstatus Ihrer Geräte anzeigen.

Wählen Sie eine Gruppe mobilen Gerät aus, und klicken Sie dann auf die Registerkarte **Geräte** , wählen Sie eine der folgenden **Filter**:
* **Geräte, die nicht mit AAD registriert sind** – diese Geräte sind Dynamics CRM blockiert.
* **Geräte, die nicht kompatibel sind** – diese Geräte sind Dynamics CRM blockiert.
* **Geräte, die mit AAD und kompatible registriert** – diese Geräte Dynamics CRM zugreifen können.

##  Nächste Schritte
[Einschränken des Zugriffs auf Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)

[Einschränken des Zugriffs auf Exchange lokalen](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
[Einschränken des Zugriffs auf SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Einschränken des Zugriffs auf Skype für Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
