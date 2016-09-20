---
title: "Verwalten von Daten zwischen iOS-apps übertragen | Microsoft Intune"
description: "Verwenden Sie dieses Thema um zu verstehen, wie die iOS öffnen in Feature und mobile-app Informationsverwaltungsrichtlinien Datenübertragung zwischen apps verwalten."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 1d212dddc1d5665b7badf6cc27b41e012f74d96c
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwalten von Daten zwischen iOS-apps mit Microsoft Intune übertragen
## Verwalten von apps für iOS
Schützen von Daten des Unternehmens enthält, und stellen Sie sicher, dass die Übertragung von Dateien auf apps beschränkt sind, die von Ihnen verwaltet werden.  Sie können auf folgende Weise iOS-apps verwalten:

-   Verhindern der Anzeige Unternehmen Datenverlust durch Konfigurieren einer Richtlinie MAM von den apps, die wir als **Richtlinie verwaltet** apps bezeichnet werden.

-   Sie können auch bereitstellen und Verwalten von apps über den **MDM Channel**.  Setzt die Geräte in die Lösung MDM registriert sind. Diese **Richtlinie verwaltet** apps oder andere verwaltete apps möglich.

Das **Öffnen in Management** Feature für iOS-Geräte kann die Übertragung von Dateien zwischen apps einschränken, die über den **MDM Channel**bereitgestellt werden. Öffnen in Management Einschränkungen in der Konfiguration Einstellungen festgelegt sind und Ihre Lösung MDM mit bereitgestellt.  Wenn der Benutzer die app bereitgestellte Installationen angewendet werden die Einschränkungen, die Sie festlegen.
##  Verwenden MAM mit iOS-apps
Mobile-app Informationsverwaltungsrichtlinien (MAM) können mit dem **Öffnen in Management** iOS-Feature für Unternehmen-Datenschutz auf folgende Weise verwendet werden:

-   **Mitarbeiter im Besitz Geräte, die nicht von einem beliebigen MDM Lösung verwaltet:** Sie können die Richtlinieneinstellungen MAM **Zulassen-app, Daten zu übertragen**verwaltet nur apps festlegen. Wenn der Endbenutzer eine geschützte Datei in einer app geöffnet, die nicht Richtlinie verwaltet wird wird, ist die Datei nicht gelesen werden.

-   **Geräte von Intune verwaltet:** Für Geräte in Intune registriert übertragen von Daten zwischen apps mit MAM Richtlinien, und andere verwaltete iOS-apps durch Intune bereitgestellt automatisch zulässig ist. Aktivieren Sie die Einstellung **Zulassen app zum Übertragen von Daten, die nur verwaltete apps** Datenübertragung zwischen apps mit MAM Richtlinien um zu ermöglichen. Das Feature **in Management öffnen** können Sie die um Übertragung von Daten zwischen apps zu steuern, die durch Intune bereitgestellt werden.   

-   **Geräte verwaltet, indem der Lösung eines Drittanbieters MDM:** Sie können die Datenübertragung auf nur verwaltete apps beschränken, mit dem **Öffnen in Management** iOS-Feature.
Um sicherzustellen, dass apps, die Sie die Bereitstellung Ihrer Drittanbieter MDM-Lösung mit auch die Richtlinien MAM zugeordnet sind, die Sie in Intune konfiguriert haben, müssen Sie die Einstellung des Benutzers Benutzerprinzipalnamen konfigurieren, wie in der exemplarische Vorgehensweise [Konfigurieren Sie die Einstellung für Benutzer Benutzerprinzipalnamen](#configure-user-upn-setting) beschrieben.  Wenn apps mit der Einstellung des Benutzers Benutzerprinzipalnamen bereitgestellt werden, werden die MAM Richtlinien zur app angewendet, wenn der Endbenutzer Vorzeichen-sich mit ihrer Arbeit-Konto.

> [!IMPORTANT]
> Die Einstellung des Benutzers Benutzerprinzipalnamen steht nur für apps auf Geräten, die von einem Drittanbieter-MDM verwaltet bereitgestellt, die erforderlich ist  Diese Einstellung ist für verwaltete Intune Geräte nicht erforderlich.

## Konfigurieren Sie die Einstellung für Benutzer Benutzerprinzipalnamen
Diese Konfiguration ist erforderlich für Geräte, die von der Lösung eines Drittanbieters MDM verwaltet werden. Das folgende Verfahren ist eine allgemeine Fluss zum Implementieren der Einstellung Benutzerprinzipalnamen und die resultierende Endbenutzer:


1.  Im Azure-Portal für iOS-Plattform [Konfigurieren eines mobilen app zur Dokumentverwaltungsrichtlinie](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) . Konfigurieren von Einstellungen für die Informationsverwaltungsrichtlinie pro Ihren Anforderungen Unternehmen, und wählen Sie die apps, die dieser Richtlinie sein soll.

2.  Bereitstellen der apps und der verwalteten **durch Ihre Drittanbieter - MDM-Lösung** mit der Einstellung beschrieben, die in Schritt 3 und 4 die gewünschte e-Mail-Profil.

3.  Bereitstellen die app mit den folgenden Einstellungen der app-Konfiguration: Key IntuneMAMUPN, Wert =<username@company.com> = [Beispiel: 'IntuneMAMUPN', 'jondoe@microsoft.com']

4.  Stellen Sie die in zur Dokumentverwaltungsrichtlinie öffnen in registrierten Geräte.

### Beispiel für Endbenutzer

1.  Endbenutzer installiert Microsoft Word-app auf dem Gerät.

2.  Endbenutzer startet die verwalteten systemeigenen-e-Mail-app um auf ihre e-Mails zuzugreifen.

3.  Endbenutzer versucht, Dokument aus einer systemeigenen Mail in Microsoft Word zu öffnen.

4.  Wenn die app für Word startet, wird der Endbenutzer aufgefordert, zum Melden Sie sich mit ihrem Konto Arbeit.  Dieses Konto Arbeit, die den Endbenutzer eingibt, wenn Sie aufgefordert werden, sollten Konto übereinstimmen, die Sie in den konfigurierten in der app-Konfiguration-Einstellungen für Microsoft Word app angegeben haben.

    > [!NOTE]
    > Endbenutzer können anderen persönlichen Konten bei Word ihre privaten und nicht durch die Richtlinien MAM betroffen, wenn Sie mit Word app in einem persönlichen Kontext hinzufügen.

5.  Wenn die Anmeldung erfolgreich ist, werden die Einstellungen für die app-Richtlinie auf Word app angewendet.

6.  Jetzt die Datenübertragung erfolgreich ist und das Dokument als corporate Identität in der app markiert ist. Darüber hinaus ist die Daten in einem Arbeitskontext behandelt und entsprechend die Richtlinieneinstellungen angewendet.

### Siehe auch
[Schützen von app-Daten, die mithilfe von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
