---
title: "Lookout für Arbeit app bereitstellen | Microsoft Intune"
description: "Konfigurieren und Bereitstellen von Lookout für Arbeit apps für Android."
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: c43104ff199e1800bfded35154d2be0cfd0c40f3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren und Lookout für Arbeit apps bereitstellen
In dieser Version achten app Android 4.1-Geräten arbeiten und höher unterstützt.
## Android
In diesem Abschnitt wird erläutert, wie konfigurieren und Bereitstellen von Ausschau für Arbeit Anwendung für Android-Geräten für Intune registriert wird.  
* Schritt 1: In der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), rufen Sie **Apps** , und wählen Sie **Apps hinzufügen**.   
* Schritt 2: Auf der Seite **Software einrichten** des Herausgebers wählen Sie **externer Link**aus, und geben Sie den folgenden URL: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Klicken Sie auf das Feld einrichten, dass einen verwalteten Browser nicht.

* Schritt 3: Klicken Sie auf die **Beschreibung der Software** Seite Füllung in die folgenden Informationen:
  * **Publisher:** Lookout Mobile Sicherheit
  * **Name:**   Sucht generell nach Arbeit
  * **Beschreibung:**  Lookout bietet die beste Schutzes mobile auf Ihrem Gerät zu schützen. Wenn die app Lookout auf dem Gerät installiert ist, wird die app Loss von Ihrem Gerät aus Risiken und wird Sie und Ihre Unternehmensadministratoren gewarnt werden, wenn diese gefunden werden.
  * **Kategorie:** Verwaltung von Computern
* Schritt 4: Nach dem erfolgreichen Abschluss wird eine Meldung **Hochladen von Daten an Microsoft Intune erfolgreich abgeschlossen wurde**.

Klicken Sie auf die Intune-Verwaltungskonsole beim Klicken auf die **Apps** Sie sehen nun für Arbeit app in der Liste Ausschau ![Screenshot Intune Console apps-Verwaltungskonsole mit Ausschau für Arbeit apps in der Liste](../media/mtp/lookout-app-listed-intune-console.png)

Schritt 5: An diesem Punkt Intune weiß, wie Sie Ausschau für Arbeit android app bereitstellen.   Sie können die app für Benutzer, bereitstellen, indem Sie Ausschau für Arbeit app im Bildschirm oben und Auswählen eines **Bereitstellung verwalten**gezeigt auswählen.

Wählen Sie die gleichen Benutzer der Registrierung Verwaltungsoption in der Verwaltungskonsole Lookout MTP hinzugefügt.  [Konfigurieren Sie Ihr Abonnement mit Lookout MTP Abschnitt](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) Informationen zum Hinzufügen von Benutzergruppen zur Lookout MTP finden Sie in Schritt 3.
>[!IMPORTANT]
> Die app-Bereitstellung von Intune Assistenten ist keine bekannt die Benutzergruppen Azure AD- und die Benutzergruppen Intune stattdessen verwendet. Daher müssen Sie eine Intune Benutzergruppe basierend auf Azure AD-Benutzergruppe, die in der Verwaltungskonsole Lookout MTP registriert ist, wie in [diesem](plan-your-user-and-device-groups.md)Artikel beschrieben erstellen.

Schritt 6: Wählen Sie die Option **Installieren erforderlich** , um festzulegen, dass die app Lookout installiert werden, auf dem Gerät des Benutzers aus.

### Gerät Aktivierung
Mit der Option für die **Installation erforderlich** für die Bereitstellung ausgewählten wird Intune Ausschau für Arbeit Anwendung auf dem Gerät drücken.   

Wenn der Benutzer auf dem Gerät für die Arbeit Ausschau öffnet werden sie aufgefordert, die app zu aktivieren, und wählen Sie die melden Sie sich mit Azure Active Directory-Option. Eine ausführliche exemplarische mit dem Endbenutzer Flow finden Sie in den folgenden Themen:

* [Sie werden aufgefordert, achten Arbeit auf Ihrem Android-Gerät installieren](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Sie müssen ein darstellen zu beheben, die dafür Arbeit auf Ihrem Android-Gerät finden](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Nächste Schritte
* [Aktivieren Sie Gerät Bedrohung Schutzregel in die Compliance-Richtlinien](enable-device-threat-protection-rule-in-compliance-policy.md)
