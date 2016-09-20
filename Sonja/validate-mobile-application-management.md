---
title: "Überprüfen Sie Ihr Setup MAM | Microsoft Intune"
description: "Dieses Thema wird beschrieben, wie Sie überprüfen können, und überprüfen, wenn die Richtlinie MAM ordnungsgemäß eingerichtet ist und wie erwartet funktionieren."
keywords: 
author: karthikaraman
manager: angerobe
ms.date: 08/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
ms.openlocfilehash: dab40df81c26b403aa3f2ae5524ff1297e2a7963
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Überprüfen von Ihrem mobilen Anwendung Einrichtung

Dieses Thema enthält Informationen zur Prüfung Probleme nach dem Einrichten von mobilen anwendungsverwaltung (MAM) auf. Diese Anleitung bezieht sich auf MAM Richtlinien Azure-Portal.

### Prüfen auf Symptome
Benutzer sind wahrscheinlich nicht melden Sie Probleme, da MAM ein Tool zum Schutz von Daten ist. Wenn es ein Problem mit der MAM Konfiguration liegt wird des Benutzers Access uneingeschränkt haben sobald sie ohne MAM haben möchten, und nicht beachten Sie möchten, dass ein Problem vorliegt. Aus diesem Grund, wird empfohlen, überprüfen Sie Ihre MAM Konfiguration durch Testen Ihre MAM Richtlinien für eine kleine Gruppe von Benutzern, die absichtlich die Einschränkungen MAM testen können. 


### Zu überprüfen 

Wenn zeigt testen, die Verhalten der MAM-Richtlinie ist nicht wie erwartet, empfehlen wir, dass Sie Folgendes prüfen:

- Werden die Benutzer sind für die MAM lizenziert?
- Sind die Benutzer für Office 365 lizenziert?
- Der Status der einzelnen des Benutzers MAM apps. Die möglichen Status für die apps sind **Checked in** und **nicht eingecheckt**.

#### Benutzer MAM status
1. Wählen Sie im Portal Azure **Intune mobile anwendungsverwaltung** > **Einstellungen** > **app Management** > **Alle Einstellungen** > **App reporting durch Benutzer** > **Benutzer**.

2. Wählen Sie einen Benutzer aus der Liste oder suchen Sie nach Wählen Sie einen Benutzer aus, und wählen Sie aus, **Wählen Sie Benutzer**. Am oberen Rand der Spalte **reporting App** sehen Sie, ob der Benutzer eine Lizenz für MAM ist. Unten sehen Sie, ob der Benutzer eine Lizenz für Office 365 und der app-Status für alle Geräte des Benutzers ist.

![App Statuts für MAM](..\media\ts-mam-use-apps.png) 

### Was zu tun ist
Hier sind die Aktionen an, die basierend auf den Benutzerstatus ein:

- Wenn der Benutzer nicht für MAM lizenziert ist, weisen Sie eine Lizenz Intune dem Benutzer beschriebenen in [Intune verwalten von Lizenzen zu](..\get-started\start-with-a-paid-subscription-to-microsoft-intune).
- Wenn der Benutzer für Office 365 erwerben Sie eine Lizenz für den Benutzer nicht lizenziert ist.
- Wenn ein Benutzer app als **nicht eingecheckt**aufgeführt ist, überprüfen Sie, wenn Sie eine Richtlinie MAM für die app ordnungsgemäß konfiguriert haben.
- Stellen Sie sicher, dass diese Qualifikation über alle Benutzer angewendet werden, auf das MAM Richtlinien angewendet werden soll.

### Siehe auch
[Konfigurieren von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune Fertigstellen](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Schützen von app-Daten, die mithilfe von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
