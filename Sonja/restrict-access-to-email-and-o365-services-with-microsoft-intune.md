---
title: "Beschränken Sie den Zugriff auf e-Mail und Office 365-Dienste | Microsoft Intune"
description: "In diesem Thema wird beschrieben, wie bedingte verwendet werden kann, damit nur kompatible Geräte Unternehmen Zugriff auf e-Mail und Firmennamen Daten auf SharePoint Online und andere Dienste können."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 9e64ab7f9955f72e9d47a0282820ebdcba0db00b
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Beschränken Sie den Zugriff auf e-Mail, Office 365 und andere Dienste mit Microsoft Intune
Sie können den Zugriff zu Unternehmen e-Mail und Office 365-Diensten mit Intunes bedingten Zugriff einschränken. Intune des bedingten Access-Funktion können Sie sicherstellen, dass der Zugriff auf Ihre e-Mail Unternehmen, und Office 365-Dienste ist eingeschränkt Geräte, mit der Regeln kompatibel sind, die Sie festlegen.
## Wie funktioniert die bedingte zugreifen?
Compliance-Richtlinien werden verwendet, für die Kompatibilität des Geräts ausgewertet werden soll. Bedingte Zugriffsrichtlinie verwendet die Auswertung einschränken oder den Zugriff auf einen bestimmten Dienst an. Wenn eine bedingte Zugriffsrichtlinie in Kombination mit einer Richtlinie Compliance verwendet wird, werden nur kompatible Geräte gewährt werden, auf den Dienst zuzugreifen. Die Compliance-Richtlinien und die bedingte Zugriffsrichtlinie sind für den Benutzer bereitgestellt. Jedem Gerät, die der Benutzer Zugriff auf die Dienste verwendet, die für die Einhaltung der Richtlinien aktiviert ist.

Denken Sie daran, die der Benutzer, der das Gerät verwendet eine Compliance-Richtlinie können bereitgestellt werden, damit das Gerät auszuwertende für Compliance benötigen beibehalten.
Wenn keine Compliance-Richtlinie für den Benutzer bereitgestellt wird das Gerät wird als kompatibel behandelt, und keine zugriffseinschränkungen angewendet werden.

Wenn Geräte die Vorschriften in die Richtlinien nicht erfüllen, ist der Endbenutzer geleitet, obwohl die Vorgehensweise zum Registrieren des Geräts und das Problem zu beheben, die das Gerät verhindert kompatibel.

Einer standardmäßigen Ablauf von bedingten Access:

![Das Diagramm zeigt die Entscheidungspunkte verwendet, um zu bestimmen, ob ein Gerät Zugriff auf einen Dienst zulässig ist oder ist gesperrt](../media/ConditionalAccess4.png)

## So konfigurieren Sie bedingte Access?
Verwenden von bedingten Access den Zugriff auf Microsoft **Exchange lokalen**, **Exchange Online**, **Exchange Online dedizierte**, **SharePoint Online** und **Skype für Business Online**verwalten.

Zum Einrichten von bedingten Zugriff konfigurieren einer Richtlinie für Geräte Compliance und einer bedingten Zugriffsrichtlinie.

Die Compliance-Richtlinien enthält Einstellungen wie Kenncode, Verschlüsselung und ob ein Gerät ist Jailbroken. Das Gerät muss diese Regeln erfüllen, damit kompatibel sein.

Zum Einschränken des Zugriffs auf der Grundlage eine bedingten Zugriffsrichtlinie können Sie Folgendes festlegen:
- Der Status des Geräts Compliance.
- Die Plattform auf dem Gerät ausgeführt wird.
- Die Art des apps verwendet, um die Dienste zuzugreifen.

Im Gegensatz zu anderen Intune-Richtlinien Sie bedingte Richtlinien nicht bereitstellen. Nachdem Sie die Richtlinie konfigurieren, und wählen Sie die Benutzer, die die Richtlinie sein soll, wird stattdessen die Richtlinie für alle zielgerichteten Benutzer angewendet. Wenn ein Benutzer durch eine Richtlinie vorgesehen ist, muss jedem Gerät, mit denen sie den Zugriff auf Ressourcen kompatibel sein.


## Nächste Schritte
1. [Erfahren Sie mehr über das Compliance-Geräterichtlinie und deren Funktionsweise ](introduction-to-device-compliance-policies-in-microsoft-intune.md)

2. [Erstellen einer Richtlinie compliance](create-a-device-compliance-policy-in-microsoft-intune.md)

2.  Erstellen einer bedingten Zugriffsrichtlinie für eine der folgenden Aktionen aus:
> [!div class="op_single_selector"]
  - [Erstellen einer bedingten Zugriffsrichtlinie für Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Erstellen einer bedingten Zugriffsrichtlinie für Exchange lokal](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Erstellen einer bedingten Zugriffsrichtlinie für neuer Exchange Online dedizierter](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Erstellen einer bedingten Zugriffsrichtlinie für legacy Exchange Online dedizierter](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Erstellen von bedingten Zugriffsrichtlinie für SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Erstellen von bedingten Zugriffsrichtlinie für Skype für Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Erstellen von bedingten Zugriffsrichtlinie für Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
