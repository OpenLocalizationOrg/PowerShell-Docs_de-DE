---
title: "Einschränken der e-Mail-Zugriff auf Exchange lokalen | Microsoft Intune"
description: "Schützen Sie und steuern Sie des Zugriffs auf Unternehmens-e-Mail auf Exchange lokal mit bedingten Zugriff."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 9a6455ded35bf77fbd5da1d4f345759836f38c7f
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einschränken der e-Mail-Zugriffs auf lokale und ältere Exchange Online dedizierten mit Intune Exchange


Wenn Sie eine Exchange Online dedizierte Umgebung besitzen müssen, um herauszufinden, ob es in der neuen oder älteren Konfigurations handelt, wenden Sie sich an Ihren Account Manager.


Zur Steuerung des e-Mail-Zugriffs Exchange lokalen oder seine alte Exchange Online dedizierte Umgebung konfigurieren Sie bedingte Zugriff auf Exchange lokal in Intune aus.
Weitere Informationen zu wie bedingte Access Works Informationen hierzu im Artikel [Einschränken des Zugriffs auf e-Mail- und O365-Dienste]( restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

Überprüfen Sie Folgendes, **bevor** Sie bedingte Access konfigurieren können:

-   Die Exchange-Version muss **Exchange 2010 oder höher**. Exchange Server-Client Access Server (Zertifizierungsstellen) Array unterstützt wird.

-   Verwenden Sie den **lokalen Exchange-Connector**, der eine Verbindung herstellt [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] auf Microsoft Exchange lokalen. So können Sie die Geräte über Verwalten der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Console. Details Netzwerke finden Sie unter [Intune lokalen Exchange-Verbinder](intune-on-premises-exchange-connector.md).

    -   Der lokalen Exchange Verbinder in die Intune-Verwaltungskonsole zur Verfügung bezieht sich nur auf Ihrem Mandanten Intune und nicht mit einem beliebigen anderen Mandanten verwendet werden. Sie sollten auch sicherstellen, dass der Exchange-Connector für Ihren Mandanten installierten **auf nur von einem Computer**ist.

        Diesen Connector sollte der Administrator Intune-Verwaltungskonsole heruntergeladen werden.  Eine exemplarische Vorgehensweise zum Konfigurieren des lokalen Exchange-Connectors finden Sie unter [Konfigurieren von Exchange lokalen Connector für lokale oder gehostete Exchange](intune-on-premises-exchange-connector.md).

    -   Der Verbinder kann auf einem beliebigen Computer installiert werden, solange dieser Computer mit dem Exchange-Server kommunizieren kann.

    -   Der Verbinder unterstützt **Zertifizierungsstellen Exchange-Umgebung**. Sie können technisch den Verbinder auf dem Server Exchange Zertifizierungsstellen direkt installieren, wenn Sie möchten, aber es nicht empfohlen wird, wenn sie die Last auf dem Server erhöhen wird.
    Wenn Sie den Verbinder zu konfigurieren, müssen Sie es einrichten, für die Kommunikation mit einem der Zertifizierungsstellen Exchange Server.

-   **Exchange ActiveSync** muss mit basierendes Zertifikatauthentifizierung oder Eingabe des Benutzers Anmeldeinformationen konfiguriert sein.

Wenn bedingte-Richtlinien werden konfiguriert und dessen Ziel eines Benutzers, bevor ein Benutzer auf ihre e-Mails eine Verbindung herstellen kann, muss das **Gerät** , die sie verwenden:

-  Entweder **registriert** mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] oder ist eine Domäne beigetreten PC.

-  **Registriert in Azure-Active Directory**. Darüber hinaus den Client, die, den Exchange ActiveSync-ID bei Azure Active Directory registriert sein.

  AAD DRS wird für Intune und Office-365-Kunden automatisch aktiviert. Kunden, die bereits ADFS Gerät Registrierungsdienst bereitgestellt haben, werden nicht registriert Geräte in deren lokalen Active Directory angezeigt. **Dies gilt nicht für Windows-PCs und Windows Phone-Geräten**.

-   **Kompatibel** mit einem [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Compliance-Richtlinien, die auf dem Gerät bereitgestellt.

Das folgende Diagramm veranschaulicht den Datenfluss, der von bedingten Richtlinien für Exchange lokal für ausgewertet werden soll, ob zulassen oder Sperren von Geräten verwendet wird.

![Diagramm, das die Entscheidungspunkte, die bestimmen darstellt, ob ein Gerät ist der Zugriff auf Exchange lokalen erlaubt oder blockiert](../media/ConditionalAccess8-2.png) Wenn eine bedingte Zugriffsrichtlinie nicht erfüllt ist, wird angezeigt mit einem der folgenden angezeigt, wenn sie sich anmelden:

- Wenn das Gerät nicht registriert wird, mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], oder ist nicht registriert in Azure Active Directory, wird eine Meldung angezeigt, mit Anweisungen Informationen zum Installieren der app Unternehmen Portal, das Gerät zu registrieren, und aktivieren e-Mail. Dieses Verfahren ordnet des Geräts Exchange ActiveSync-ID auch den Eintrag Gerät in Azure Active Directory.

-   Wenn das Gerät nicht kompatibel ist, wird eine Meldung angezeigt, die den Benutzer zur weiterleitet der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Website Unternehmen Portal oder im Unternehmen Portal app, wo sie Informationen über das Problem und so beheben sie finden können.

## Unterstützung für mobile Geräte
-   Windows Phone 8 und höher

-   Systemeigene e-Mail-app für iOS.

-   Systemeigene e-Mail-app auf Android 4 oder höher
> [!NOTE]
> Microsoft Outlook-app für Android und iOS wird nicht unterstützt.

## Unterstützung für PCs

Die **E-Mail** -Anwendung unter Windows 8 oder höher (wenn mit registriert [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)])

##  Konfigurieren einer bedingten Zugriffsrichtlinie

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** > **Bedingte Access** > **Exchange lokale Richtlinie**.
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  Konfigurieren Sie die Richtlinie mit den Einstellungen, die Sie benötigen: ![Screenshot des Exchange-lokale Richtlinienseite](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **Blockieren e-Mail-apps vom Zugriff auf lokalen Exchange, ist das Gerät nicht kompatibel oder nicht an Microsoft Intune registrierten:** Wenn Sie diese Option, Geräten, die nicht von verwaltet werden auswählen [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], oder nicht kompatibel mit einer Compliance Richtlinie blockiert den Zugriff auf die Exchange-Dienste.

  - **Regel außer Kraft setzen Standard - immer zulassen registrierte und kompatible Geräten Zugriff auf Exchange:** Wenn Sie diese Option aktivieren, dürfen Geräten, die in Intune und Einhaltung der die kompatiblen Richtlinien registriert sind Exchange zugreifen.  
  Mit dieser Regel überschreibt die **Regel Standard**, d. h., auch wenn Sie festlegen, dass der **Standard-Regel** in Quarantäne stellen oder Zugriff blockieren, registriert und kompatible Geräte können weiterhin Zugriff auf Exchange.

  - **Ziel Gruppen:** Wählen Sie aus der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Benutzergruppen, die ihr Gerät mit registrieren müssen [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] bevor sie Exchange zugreifen können.

  - **Ausgenommen Gruppen:** Wählen Sie aus der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Benutzergruppen, die von der bedingten Richtlinie ausgenommen werden. In dieser Liste Benutzer ausgenommenen auch wenn sie auch in der Liste **Gruppen gerichtet** sind.

  - **Plattform Ausnahmen:** Wählen Sie **Regel hinzufügen** so konfigurieren Sie eine Regel, die definiert Zugriffsebenen für Familien angegebenen Mobilgerät und Modelle aus. Da diese Geräte eines beliebigen Typs sein können, können Sie auch Arten von Geräten, die von nicht unterstützt werden konfigurieren [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

  - **Standard Regel:** Für ein Gerät, das nicht über eine der anderen Regeln sind, können Sie auswählen, damit er Exchange zugreifen, es blockieren oder unter Quarantäne gestellt wird. Wenn Sie festlegen, dass die Regel zu Zugriff für Geräte, die registrierten Konformität und, e-Mail-automatisch für iOS, Windows und Samsung KNOX Geräte erhält Zugriff. Der Endbenutzer hat keinen, bis alle Prozess erhalten, ihre e-Mail zu gelangen.  Android-Geräten, die nicht Samsung KNOX ausgeführt werden, wird Endbenutzer eine Quarantäne-e-Mail können die enthält eine exemplarische Vorgehensweise zum Registrierung und Kompatibilität überprüfen, bevor sie e-Mails zugreifen können. Wenn Sie die Regel Zugriff blockieren oder unter Quarantäne gestellt wird festlegen, werden alle Geräte blockiert erste Zugriff auf exchange, unabhängig davon, ob diese bereits Intune oder nicht registriert werden. Um zu verhindern, dass registrierten und kompatible Geräte durch diese Regel beeinträchtigt wird, überprüfen Sie die **Standard Regel außer Kraft setzen.**
>[!TIP]
>Ist Ihre Absicht zuerst alle Geräte blockieren, bevor Sie gewähren des Zugriffs auf e-Mail, wählen Sie den Zugriff blockieren oder die Quarantäneregel aus. Die Standard-Regel gilt für alle Gerätetypen, damit Sie als Plattform Ausnahmen und die konfigurieren Arten von Geräten nicht, indem unterstützt werden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] sind auch betroffen.

  - **Benutzer Benachrichtigung:** Zusätzlich zu den e-Mail-Benachrichtigung gesendet von Microsoft Exchange sendet Intune eine e-Mail-Nachricht die Schritte aus, um das Gerät Aufheben der Blockierung enthält. Bearbeiten Sie die standardmäßige angezeigt, um ihn an Ihre Bedürfnisse anzupassen. Da die Intune Benachrichtigung e-Mail Behebung Anweisungen mit Exchange-Postfach des Benutzers, übermittelt, den Fall, dass das Gerät des Benutzers gesperrt ist, bevor sie die e-Mail-Nachricht erhalten, können sie ein Gerät freigegeben werden soll oder eine andere Methode verwenden, den Zugriff auf Exchange, und zeigen Sie die Nachricht. Dies gilt besonders, wenn die **Regel standardmäßig** blockieren oder Quarantäne eingestellt ist.  In diesem Fall wird der Endbenutzer verfügen, ihre app Store, laden Sie die app Microsoft Unternehmen Portal und Geräts registrieren. Dies gilt für iOS, Windows und Samsung KNOX Geräte.  Für Geräte, die nicht Samsung KNOX ausgeführt werden, müssen Sie die Quarantäne e-Mail senden, eine alternative e-Mail-Konto, die dann den Endbenutzer hat, auf deren gesperrten Gerät in der Registrierung und Compliance-Vorgang abschließen kopieren. |
  > [!NOTE]
  > Damit für Exchange die e-Mail-Benachrichtigung senden können müssen Sie das Konto angeben, das zum Senden der e-Mail-Benachrichtigung verwendet werden soll.
  >
  > Details finden Sie unter [Konfigurieren von Exchange lokalen Connector für lokale oder gehostete Exchange](intune-on-premises-exchange-connector.md).

3.  Wenn Sie fertig sind, wählen Sie **Speichern**aus.

-   Sie verfügen nicht über die bedingte Zugriffsrichtlinie bereitstellen, wird sofort wirksam.

-   Nachdem ein Benutzer kann eine Exchange ActiveSync-Profil festlegt, möglicherweise Optimieren von 1 bis 3 Stunden für das Gerät blockiert werden (wenn es nicht von verwaltet wird [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

-   Wenn Sie ein blockierter Benutzer dann registriert, wird das Gerät mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und behebt bei nicht-Konformität), e-Mail-Zugriff werden innerhalb von zwei Minuten freigegeben werden soll.

-   Wenn der Benutzer un-registriert wird aus [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] dauert möglicherweise von 1 bis 3 Stunden für das Gerät blockiert werden sollen.

**Einige Beispielszenarien der, wie Sie bedingte Zugriffsrichtlinie zum Einschränken des Zugriffs Gerät konfigurieren möchten, finden Sie unter [Beispielszenarien für e-Mail-Zugriff einschränken](restrict-email-access-example-scenarios.md).**

## Nächste Schritte
[Einschränken des Zugriffs auf SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Einschränken des Zugriffs auf Skype für Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
