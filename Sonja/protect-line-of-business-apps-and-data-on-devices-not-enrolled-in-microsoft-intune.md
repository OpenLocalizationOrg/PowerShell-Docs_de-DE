---
title: "Schützen von LOB-apps auf Geräten nicht registriert | Microsoft Intune"
description: "In diesem Thema wird beschrieben, wie Sie Ihre benutzerdefinierten Textzeile Geschäfts-apps, damit Sie mobile-app Informationsverwaltungsrichtlinien anwenden können, die verhindern Datenverlust vorbereiten können."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 05b7755798963005a894a9f4a72442672bbe0a68
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Schützen von Zeile des Geschäfts-apps und Daten auf Geräten, die nicht in Microsoft Intune registriert

Mobile-app Informationsverwaltungsrichtlinien (MAM) Schutz Ihrer Unternehmensdaten verschieben wie Kopieren und Einfügen von Daten einschränken oder verhindern, dass Benutzer Dokumente des Unternehmens auf einen Speicherort für persönliche zu speichern.   Um MAM Richtlinien für iOS und oder Android Textzeile Geschäfts-apps übernehmen möchten, müssen Sie zuerst die app mit Werkzeug Microsoft Intune App Wrapping umbrechen.  App Umbruch versteht mobile-app ohne Änderungen an der zugrunde liegenden Anwendung Management-Layer zuweisen.  Sobald die app umschlossen ist, können Sie MAM Richtlinien darauf anwenden und an die Endbenutzer verteilen.  

In diesem Thema wird erläutert, die erforderlichen Schritte zum Anwenden von MAM Richtlinien für apps, die für **Mitarbeiter im Besitz Geräte, die nicht verwaltet werden,**zugegriffen werden und Geräte, die von einer **Drittanbieter - Mobilgerät Management (MDM) Lösung**verwaltet werden.  Um Ihre Textzeile Geschäfts-apps vorzubereiten, die auf **Geräten, die Intune registriert sind,**ausgeführt werden, finden Sie unter [entscheiden, wie apps für mobile anwendungsverwaltung mit Microsoft Intune vorbereiten](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).
##  Schritt 1: Vorbereiten der app
Bevor Sie eine app MAM Richtlinien zuordnen können, müssen Sie zuerst die app mit dem Tool Microsoft Intune App Wrapping umbrechen.  Der Download beinhaltet die Anweisungen zum Installieren und Verwenden des app Umbruch Tools.  
>[!IMPORTANT]  
>Diese Version des app Umbruch Tools, die nicht registriert Geräte in Intune unterstützt steht in public Preview-Version zur Verfügung. Wenn Sie in der Vorschau öffentlichen teilnehmen möchten, können Sie das Tool aus [dieser Seite Github](https://github.com/msintuneappsdk/intune-app-wrapper-ios-preview) für iOS und [diese Website Github](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview) für Android herunterladen.

## Schritt 2: Hinzufügen der app

Wenn Ihre app Branchen MAM Richtlinien zuordnen möchten, müssen Sie die app-Details zu Ihrem Intune Abonnement/Mandanten mithilfe der folgenden Schritte hinzufügen:

1. Wechseln Sie zu der [Azure-Portal](https://portal.azure.com/) **mobile anwendungsverwaltung Intune > Einstellungen**, und wählen Sie **Branchen apps**.

  ![Screenshot des Blades Einstellungen mit Business-option](../media/mam-azure-portal-lob-on-settings.png)

2. Wählen Sie in der **Zeile des Business apps** Blade **Hinzufügen einer benutzerdefinierten app**aus.

  ![Screenshot der Zeile des Business apps Blade mit der Hinzufügen benutzerdefinierter app-Schaltfläche im Kopfbereich](../media/mam-azure-portal-add-lob-app-action.png)
3.  Geben Sie einen Namen für die app, die Paket-ID in das Feld App-ID und die Plattform (iOS oder Android).

  ![Screenshot zum Hinzufügen einer benutzerdefinierten app Blade ](../media/mam-azure-portal-add-app-details.png) in diesem Schritt können eine eindeutige Auflistung der app zu erstellen.  Die app wird auch in der Liste der gezielte apps für eine MAM Richtlinie für Ihren Mandanten, wie im nächsten Schritt beschrieben angezeigt werden.

## Schritt 3: Anwenden von MAM Richtlinien
Sobald die app-Metadaten zum Dienst hochgeladen wird, wird die app in der Liste der apps angezeigt.  Sie können nun [eine neue Richtlinie oder einer vorhandenen Richtlinie erstellen](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) und auf die Zeile des Business-app, die Sie in Schritt 2 hinzugefügten anzuwenden.

>[!IMPORTANT]
>Sie müssen die Richtlinie MAM an die Benutzer adressieren, wer die Umgebrochene app verwenden möchten.  Benutzer, die dieser Richtlinie zu bereitgestellt haben möglich, verwenden Sie die app nicht.


  ![Screenshot der gezielte Liste der apps Blade mit der neuen Zeile von Business-app angezeigt](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## Schritt 4: Verteilen der app
Sie können Ihre Endbenutzer auf folgende Weise apps bereitstellen:
* Für Geräte, die in der Lösung eines Drittanbieters MDM registriert können Sie die apps durch Ihre Lösung MDM verteilen.
* Für Geräte, die nicht von einem beliebigen MDM Lösung verwaltet werden benötigen Sie eine benutzerdefinierte Lösung. Endbenutzer haben zum Herunterladen und installieren Sie die app auf ihrem Gerät.

## Ändern die Metadaten
Wenn Sie die app-Details wie den Namen der app oder der Bezeichner Paket ändern müssen, müssen Sie [die app entfernen](#remove-apps), und [Fügen Sie es hinzu](#step-2-add-the-app) , mit der neuen Metadaten.

##  Entfernen von apps
Sie können eine Zeile Business-app in der app-Liste entfernen.  Dies wird die app aus der Liste entfernen und die Verknüpfung mit MAM Richtlinien, aber wird nicht entfernen oder deinstallieren die app aus der Endbenutzer-Gerät.  

1.  Wechseln Sie auf der [Azure-Portal](https://portal.azure.com/)zu **Intune mobile-app Management > Einstellungen**.  Wählen Sie in den **Einstellungen** Blade, **Branchen** , um der Liste der vorhandenen apps zu öffnen.  
2.  Wählen Sie die app, die Sie entfernen möchten, und wählen Sie im **Kontextmenü (...)** aus.

  ![Screenshot der Zeile des Business apps Blade mit den drei Punkte](../media/mam-azure-portal-lob-context-menu.png)
3.  Wählen Sie die **Anwendung löschen** , um die app zu löschen.

  ![Screenshot der Zeile des Business Blade mit der Anwendung Löschoption](../media/mam-azure-portal-delete-app.png)

  Dies entfernt apps aus der Liste der Zeile des Geschäfts-apps und der gezielte-Liste der apps in die Richtlinie MAM.
