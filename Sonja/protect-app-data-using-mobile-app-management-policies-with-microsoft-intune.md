---
title: "Schützen von app-Daten mithilfe von MAM | Microsoft Intune"
description: "In diesem Thema wird erläutert, wie mobile app Management Richtlinien helfen können, Ihre Firmendaten schützen, verhindern Datenverlust und trennen persönliche und geschäftlichen Informationen."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: a3b6cb54c5b6c7bee084482f5c73c250574b182f
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Schützen von app-Daten, die mithilfe von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune

## Wie Sie die app-Daten schützen können
Ihre Mitarbeiter verwenden mobile Geräten für persönliche und geschäftlichen Aufgaben an.  Während Ihre Mitarbeiter sicherzustellen produktiv werden kann, möchten Sie auch Datenverlust, beabsichtigten und unbeabsichtigte zu verhindern.  Darüber hinaus möchten Sie haben die Möglichkeit zum Schutz von Unternehmensdaten auf der Geräte über auch den Fall, in dem sie nicht von Ihnen verwaltet werden.

Intune mobile-app Informationsverwaltungsrichtlinien (MAM) können Sie die um Daten Ihres Unternehmens zu schützen. Da Intune MAM Richtlinien verwendeten **unabhängig von eines mobilen Geräts Management (MDM) Lösung**sein können, können Sie es zum Schutz Ihres Unternehmens Daten mit oder ohne registrieren Geräte in einer Lösung Gerät verwenden. Durch die Implementierung **appebene Richtlinien**, können Sie einschränken des Zugriffs auf Unternehmensressourcen und strukturieren Sie Daten innerhalb Ihrer IT-Abteilung Bereichs übertragen.

MAM Richtlinien können konfiguriert werden, für die app auf Geräten, die sind ausgeführt:

- **In Microsoft Intune registriert:** Die Geräte in dieser Kategorie sind in der Regel corporate im Besitz der Geräte.

-   **Für eine Lösung für Mobilgerät Drittanbieters (MDM) registriert:**   Die Geräte in dieser Kategorie sind in der Regel corporate im Besitz der Geräte.

  > [!NOTE]
  > Mobile-app Informationsverwaltungsrichtlinien sollte nicht mit Drittanbieter mobile-app Management oder sicheren Container Lösungen verwendet werden.

-   **Nicht in einem beliebigen Mobilgerät Management-Lösung registriert:**  Die Geräte in dieser Kategorie sind in der Regel Mitarbeiter im Besitz Geräten, die nicht verwaltet oder Intune oder andere MDM-Lösungen für registriert.

> [!IMPORTANT]
> Sie können mobile-app Informationsverwaltungsrichtlinien für Office mobile-apps erstellen, die mit Office 365-Webdiensten herstellen. MAM Richtlinien sind apps nicht unterstützt, die mit lokalen Exchange, Skype for Business- oder SharePoint Services herstellen.

**Sind die wichtigen Vorteile von MAM Richtlinien**

-   Zum Schutz Ihrer Unternehmensdaten Ebene der app aus.  Da mobile-app Management nicht Gerät verwaltet werden müssen, können Sie die Unternehmensdaten in verwalteten und nicht verwalteten Geräte schützen. Die Verwaltung ist zentriert auf die Identität des Benutzers, die die Anforderung für Device Management entfernt.

-   Endbenutzer Produktivität wird nicht beeinträchtigt, und die Richtlinien werden nicht angewendet werden, wenn die app in einem persönlichen Kontext zu verwenden.  Die Richtlinien werden nur in einem Arbeitskontext somit was Ihnen die Möglichkeit, Unternehmensdaten zu schützen, ohne Sie zu berühren persönliche Daten angewendet.

Es gibt weitere Vorteile bei der Verwendung von MDM mit MAM Richtlinien, und Unternehmen können beide MAM mit und ohne MDM zur gleichen Zeit. Beispielsweise möglicherweise ein Mitarbeiters ausgestellt von das Unternehmen ebenso wie eine persönliche Tablet Telefon verwenden.  In diesem Fall die Telefonnummer des Unternehmens in MDM registriert und durch MAM Richtlinien geschützt ist, und das persönliche Gerät, die nur MAM Richtlinien geschützt ist.

- **MDM wird sichergestellt, dass das Gerät geschützt ist**.  Beispielsweise können Sie eine PIN zum Zugreifen auf des Geräts benötigen, oder Sie können verwaltete apps auf dem Gerät bereitstellen. Sie können auch apps für Geräte über Ihre MDM-Lösung, um mehr Kontrolle über die app-Verwaltung zu verleihen bereitstellen.

- **MAM Richtlinien wird sichergestellt, dass die app-Layer Schutzmechanismen vorhanden sind**. Sie können beispielsweise eine PIN zum Öffnen einer app in einem Arbeitskontext erforderlich app-Daten auf einen Speicherort für persönliche verhindert des Unternehmens oder wenn Daten zwischen apps freigegebenen oder verhindert werden können.


### MAM Richtlinien werden derzeit unterstützt auf:
-   iOS 8.1 oder höher

-   Android 4 oder höher

Windows-Geräten werden derzeit nicht unterstützt.
##  Wie schützen MAM Richtlinien für app-Daten

####  Apps ohne MAM Richtlinien:

![Bild, das zeigt Daten kann frei bewegen zwischen apps, wenn es keine MAM-Richtlinien angeordnet sind](../media/Apps_without_MAM_policies.png)

Wenn Sie apps ohne Einschränkungen verwendet werden, Firmenname und Ihre persönlichen Daten können gemischt auftreten erhalten.  Unternehmensdaten an Orten wie persönliche Speicher einhandeln konnte oder auf apps außerhalb Ihrer fällt, wodurch Datenverlust übertragen. Die Pfeile im Diagramm anzeigen Verschieben von uneingeschränkte Daten zwischen apps (Firmen- oder persönlichen) und Speicherorte

### Datenschutz mit MAM Richtlinien:

![Bild, das zeigt, wie Unternehmensdaten schützen ist, wenn MAM Richtlinien angewendet werden ](../media/Apps_with_mobile_app_policies.png)

Sie können Sie verwenden MAM Richtlinien zum Speichern auf den lokalen Speicher des Geräts Unternehmensdaten verhindern und Einschränken der Verlagerung von Daten an andere apps, die durch MAM Richtlinien nicht geschützt werden. MAM Richtlinieneinstellungen umfassen:
- Daten Verlagerung Richtlinien wie **Verhindern, dass speichern unter**, **einschränken Ausschneiden, kopieren und Einfügen**.
- Richtlinie Bedienung wie **einfache PIN für den Zugriff erfordern**, **Blockieren verwaltete apps Ausführung auf Jailbroken oder ab dem Stammverzeichnis Geräte**.

### Datenschutz mit MAM Richtlinien auf Geräten, die von einer Lösung MDM verwaltet:

![Bild, das zeigt, wie MAM Richtlinien auf BYOD Geräte funktionieren](../media/MAM_BYOD_November.png)

**Für Geräte, die für eine Lösung MDM registriert**-

Die obige Abbildung zeigt die Ebenen der Schutz die MDM und MAM Richtlinien zusammen anbieten.

Die MDM-Lösung:

-   Registriert wird das Gerät

-   Der apps bereitgestellt für das Gerät.

-   Stellt laufenden Gerät Compliance und management

**MAM Richtlinien fügen Sie nach Wert hinzu:**

-   Schutz Ihrer Unternehmensdaten aus Verluste im Consumer apps und Dienste

-   Anwenden von Einschränkungen (Speichern-als Zwischenablage, PIN, usw.) zu mobilen apps

-   Wischen Sie Unternehmensdaten von apps, ohne diese apps vom Gerät entfernen


### Schutz von Daten mit MAM Richtlinien für Geräte ohne Registrierung

![Bild, das zeigt, wie Richtlinien MAM auf verwaltete Geräte funktionieren](../media/MAM_ManagedDevices_November.png)

Die Abbildung zeigt, wie die Datenschutzrichtlinien Ebene der app ohne MDM arbeiten

Für BYOD Geräte in einer beliebigen MDM Lösung nicht registriert können MAM Richtlinien schützen Unternehmensdaten Ebene der app.
Es gibt jedoch einige Einschränkungen, wie berücksichtigen:

-   Sie können keine apps auf dem Gerät bereitstellen.  Der Endbenutzer muss die apps aus dem Speicher zu erhalten.

-   Sie können keine Zertifikatsprofile auf folgenden Geräten bereitstellen.

-   Sie können keine Firma Wi-Fi und VPN-Einstellungen auf folgenden Geräten bereitstellen.


## Mehrere Identität

Apps, die mehrere Identität unterstützen bietet Ihnen die Möglichkeit, unterschiedliche Konten verwenden – arbeiten und persönliche, für den Zugriff auf den gleichen apps während MAM Richtlinien werden angewendet, klicken Sie auf Wenn die apps im Arbeitskontext verwendet werden.  

Wenn der Endbenutzer ihr Konto für die Arbeit mit die OneDrive-app gestartet wird, können nicht sie die Dateien an einen Speicherort für persönliche verschoben. Wenn der Endbenutzer OneDrive mit ihrem persönlichen Konto verwendet wird, können sie jedoch kopieren und Verschieben von Daten von deren persönliche OneDrive ohne Einschränkungen.  

Eine ausführliche Erläuterung von der Erfahrung mit apps, die MAM Richtlinien und wie support-apps mit mehreren Identität zugeordnet sind aktivieren Sie MAM Richtlinien nur in Arbeitskontext lesen, [Verwendung von apps mit Unterstützung für mehrere](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md#using-apps-with-multi-identity-support) anwenden

Alle Office mobile-apps unterstützt mehrere Identität.

##  Nächste Schritte
[Bereiten Sie sich zum Konfigurieren von Informationsverwaltungsrichtlinien für mobile-app](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien mit Microsoft Intune mobile-app](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
