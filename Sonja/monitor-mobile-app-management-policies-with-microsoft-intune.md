---
title: "Überwachen von MAM Richtlinien mit Microsoft Intune | Microsoft Intune"
description: Sehen Sie, wie viele Benutzer die Richtlinie, finden Sie heraus, weitere Details Drilldown haben.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: e530960268e8ef7d9c7f5419e7221bec61c0e6ef
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Überwachen von Informationsverwaltungsrichtlinien mit Microsoft Intune mobile-app
Nachdem Sie es an die Benutzer angewendet und eine Richtlinie MAM konfiguriert haben, können Sie den Status der Compliance in [Azure-Portal](https://portal.azure.com)überwachen. Azure-Portal enthält Informationen zu den Benutzern auswirken, die Richtlinie, die Compliance-Status und Probleme, die Ihre Endbenutzer unter Umständen auftreten können.
## Überblickansicht
Auf dem **mobilen anwendungsverwaltung Intune** Blade können Sie eine Zusammenfassung der Compliance-Status sehen, wie unten beschrieben:


![Zusammenfassung der Kachel auf das Intune mobilen Anwendung Management blade](../media/mam-azure-portal-user-status-summary.png)

-   **Benutzer:** Die Gesamtzahl der Benutzer in Ihrem Unternehmen, die die apps verwenden, die Richtlinie zugeordnet werden kann.

-   **Nach Richtlinie verwaltet:**-die Anzahl der Benutzer, die mindestens eines der apps im Arbeitskontext verwendet haben.

-   **Keine Richtlinie:** Die Anzahl der Benutzer, der die Richtlinie zugeordnet apps verwenden, aber nicht durch die Richtlinie gerichtet sind.  Sie sollten die Richtlinie diese Benutzer hinzufügen.

- **Benutzer gekennzeichnet:** Die Anzahl der Benutzer, die Probleme mit dem. Klicken Sie unter **gekennzeichnete Benutzer**werden aktuell nur Benutzer mit Jailbroken Geräten gemeldet.


## Detailansicht
Sie können auf die Detailansicht der Zusammenfassung, indem Sie auf die Kachel der **Benutzerstatus** und die Kachel **gekennzeichnete Benutzer** erhalten.

### Benutzerstatus
Sie können für einen einzelnen Benutzer suchen, und schauen Sie sich das Compliance-Status für diesen Benutzer. Das **App reporting** Blade zeigt die folgende Informationen für einen ausgewählten Benutzer:
- Computerlautsprecher, die das Benutzerkonto zugeordnet sind
- App(s) mit MAM Richtlinie auf dem Gerät
- Status:

  **Eingecheckt:** Dies bedeutet, dass die Richtlinie für den Benutzer bereitgestellt wurde, und die app im Arbeitskontext bereits mindestens einmal verwendet wurde.

  **Nicht eingecheckt:** Dies bedeutet die Richtlinie für den Benutzer bereitgestellt wurde, aber die app wurde nicht im Arbeitskontext seit dann verwendet.

>[!NOTE]
> Wenn der Benutzer, den, dem Sie gesucht, keinen die MAM Richtlinie zu bereitgestellt, sehen Sie eine Meldung darüber informiert werden, dass der Benutzer nicht für alle Richtlinien für die app vorgesehen ist.

Wenn die reporting für einen Benutzer anzeigen möchten, gehen Sie folgendermaßen vor:

**Schritt 1:**  Um einen Benutzer auszuwählen, klicken Sie auf die Kachel "Zusammenfassung", oder wählen Sie die Option für die **APP REPORTING durch Benutzer** in das Blade **Einstellungen** aus, wie unten dargestellt:

![App auf das Blade Einstellungen die Option reporting](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

**Schritt 2:** Das **App reporting** Blade wird geöffnet. Wählen Sie die zu suchenden Azure-Active Directory-Benutzer **Wählen Sie Benutzer** aus.

![Wählen Sie die Benutzeroption auf die App-reporting blade](../media/mam-azure-portal-app-reporting-select-user.png)

**Schritt 3:** Nach Auswahl des Benutzers aus der Liste, sehen Sie die Details des Compliance-Status für diesen Benutzer.

![App Berichten von details](../media/mam-azure-portal-app-reporting-by-user.png)
### Gekennzeichnete Benutzer
Die Detailansicht zeigt die Fehlermeldung, die app, die auf den Fehler zugegriffen wurde, die Plattform des Geräts und einen Zeitstempel.  

### Siehe auch
[Verwalten von Datenübertragung zwischen iOS-apps](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

[Endbenutzer für MAM aktiviert-app](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md)
