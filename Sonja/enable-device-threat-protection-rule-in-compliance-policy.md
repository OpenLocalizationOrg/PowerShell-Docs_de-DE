---
title: Schutz-Regel in Compliance-Richtlinien aktivieren | Microsoft Intune
description: "Aktivieren Sie für Mobilgeräte Schutzregel in die Compliance-Richtlinien Gerät."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: 761372b2c8b81699bc2584ab1ef8d0f9d523abe9
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Aktivieren Sie Gerät Bedrohung Schutzregel in die Compliance-Richtlinien
Intune mit Lookout für Mobilgeräte Schutz gibt Ihnen die Möglichkeit, mobile Risiken erkennen, und stellen eine risikobewertung auf dem Gerät.  
Compliance-Richtlinienregel, können Sie diese risikobewertung zu verwenden, um festzustellen, ob das Gerät mit der Richtlinie kompatibel ist. Verwenden die bedingten Zugriffsrichtlinie können Sie dann zulassen oder Sperren von Exchange, SharePoint und anderen Diensten basierend auf dem Gerät Compliance.

Damit Lookout MTP Bedrohung Erkennung Einfluss auf die Compliance-Richtlinien für das Gerät:

1.  Klicken Sie auf die Compliance-Richtlinien muss die Regel **Gerät Virenschutz** aktiviert sein.

2.  **Lookout** Statusseite in der Verwaltungskonsole Intune Administrator muss **aktiven**anzeigen. Finden Sie im Thema [Aktivieren Lookout MTP Verbindung in Intune](enable-lookout-mtp-connection-in-intune.md) Weitere Details und Anweisungen zum Lookout Integration aktivieren aus.


## Konfigurieren von Gerät Bedrohung Schutzregel

Vor dem Erstellen der Regel Gerät Bedrohung Schutz in die Richtlinie Konformität, wir empfehlen, die Sie [Ihr Abonnement mit Lookout MTP einrichten](set-up-your-subscription-with-lookout-mtp.md), [Lookout Verbindung in Intune aktivieren](enable-lookout-mtp-connection-in-intune.md)und [Konfigurieren Sie Ausschau für Arbeit app](configure-and-deploy-lookout-for-work-apps.md). Die Einhaltung von Vorschriften Regel wird nur erzwungen, sobald die Einrichtung abgeschlossen ist.

Um das Gerät Bedrohung Schutzregel aktivieren, können Sie eine vorhandenen Compliance-Richtlinie verwenden oder Erstellen eines neuen Kontos.

Als Teil der Installation von Lookout MTP, in der [Lookout MTP Console](https://aad.lookout.com)haben Sie eine Richtlinie, die verschiedene Risiken in hohe, mittlere und niedrige Ebenen klassifiziert erstellt. Verwenden Sie die Ebene Bedrohung in die Intune Compliance-Richtlinien wie die maximal zulässige Bedrohung Ebene festgelegt.

In der Intune-Verwaltungskonsole, in der Seite Richtlinie Compliance wechseln Sie zu **Gesundheit Gerät** , und aktivieren Sie die **Gerät Virenschutz** Regel mit der Umschaltoption. Wählen Sie dann die maximal zulässige Bedrohung Ebene, also eine der folgenden Aktionen aus:
* **Keine (gesicherten)**: Dies ist die sicherste.  Dies bedeutet, dass das Gerät alle Risiken haben kann.  Wenn das Gerät erkannt wird, als hätten Sie beliebigen Ebenen von Risiken, wird sie als inkompatibel ausgewertet werden.  
* **Niedrig**: Gerät wird als kompatibel ausgewertet, wenn nur niedrige Ebene Risiken vorhanden sind. Nichts höheren versetzt das Gerät in ein-kompatiblen Status aus.
* **Mittel**: Gerät wird als kompatibel ausgewertet, wenn die Risiken, die auf dem Gerät vorhanden sind, Niedrig oder Mittel Ebene sind. Wenn das Gerät hohe Ebene Risiken erkannt wurde, wird es als inkompatibel bestimmt.
* **Hohe**: Dies ist die unsicherste. Im Wesentlichen auf diese Weise können alle Verfahren zum Erstellen von Ebenen, und nur vielleicht nützlich Wenn Sie bei Verwendung dieser Lösung nur für Berichtszwecke.

![Screenshot mit dem Gerät Verfahren zum Erstellen von Schutz Regel Einstellung im ](../media/mtp/mtp-compliance-policy-rule.png)

![Screenshot mit das Risiko abgleichen Option für die Bedrohung Schutz Regel-Einstellung](../media/mtp/mtp-compliance-policy-setting.png)

Wenn Sie bedingte Richtlinien für Office 365 und andere Dienste erstellen, die oben genannten Compliance Auswertung berücksichtigt wird und sind nicht kompatible Geräte blockiert zugreifen, bis das Risiko gelöst ist.

Sie können den Status Compliance ein Gerät anzuzeigen, klicken Sie auf der Seite Geräte der Intune-Verwaltungskonsole.

![Screenshot der Seite Geräte in das Compliance-Status von einem Gerät mit Intune-Verwaltungskonsole](../media/mtp/mtp-device-status-intune-console.png)

## Nächste Schritte
* Erstellen von bedingten Zugriffsrichtlinie
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange lokal](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype für Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
