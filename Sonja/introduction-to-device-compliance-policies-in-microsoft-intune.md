---
title: "Gerät Compliance-Richtlinien | Microsoft Intune"
description: "In diesem Thema wird erläutert, die Konzepte, die müssen Sie wissen, welche Gerät Compliance-Richtlinien sind und wie sie funktionieren."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 476f44df54fbea5c0fcfe8cf0e3ce4a61bd7c0a0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Compliance-Richtlinien in Microsoft Intune Gerät
## Was ist eine Compliance-Richtlinie?
Um Unternehmensdaten schützen möchten, müssen Sie sicherstellen, dass die Geräte verwendet, um apps für Unternehmen und Daten zugreifen einhalten bestimmter Regeln wie mit einer PIN Zugriff auf das Gerät und Verschlüsselung von Daten auf dem Gerät gespeichert. Ein Regelsatzes wird als eine Compliance-Richtlinie bezeichnet.

## Wie verwende ich Compliance-Richtlinien?
Können Compliance-Richtlinien mit bedingten Zugriff auf nur Geräten ermöglichen, die gesetzlichen Vorschriften Richtlinienregeln auf e-Mail und andere Dienste zugreifen. Lesen Sie den Artikel [Einschränken des Zugriffs auf e-Mail- und Office 365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) , um zu verstehen, wie die beiden Richtlinien zusammen verwendet werden können.

Sie können auch Compliance-Richtlinien unabhängig von bedingten Access verwenden. Wenn unabhängig voneinander verwendet, werden die gezielte Geräte ausgewertet und mit ihrem Compliance-Status gemeldet. Angenommen, möchten Sie Bericht über wie viele Geräte nicht verschlüsselt sind oder welche Geräte Jailbroken sind oder deren Stamm. Treten allerdings unabhängig voneinander verwendet, keine zugriffseinschränkungen zu Unternehmensressourcen angeordnet.

Sie bereitstellen Compliance-Richtlinien für Benutzer. Wenn eine Compliance-Richtlinien für einen Benutzer bereitgestellt wird, werden Geräte des Benutzers überprüft.

Die folgende Tabelle enthält das Gerät von Compliance-Richtlinien und wie nicht kompatible Einstellungen unterstützte Typen verwaltet werden, wenn die Richtlinie mit einem bedingten Zugriffsrichtlinie verwendet wird.

-----------------------------

|Einstellung der Richtlinie| Windows 8.1 und höher| Windows Phone 8.1 und höher| iOS 8.0 und höher|Android 4.0 und höher<br/>Samsung KNOX Standard 4.0 und höher|
|-----|----|----|----|----|
|**PIN oder mein Kennwort Konfiguration** |Diese beseitigt|Diese beseitigt|Diese beseitigt|Unter Quarantäne gestellt|
|**Gerät-Verschlüsselung**|N/V|Diese beseitigt|Diese beseitigt (durch Festlegen PIN)|Unter Quarantäne gestellt|
|**Jailbroken oder Stamm-Gerät**|N/V|N/V|Isoliert (keine Einstellung)|Isoliert (keine Einstellung)|
|**E-Mail-Profil**|N/V|N/V|Unter Quarantäne gestellt|N/V|
|**Mindestversion OS**|Unter Quarantäne gestellt|Unter Quarantäne gestellt|Unter Quarantäne gestellt|Unter Quarantäne gestellt|
|**Maximale Version des Betriebssystems**|Unter Quarantäne gestellt| Unter Quarantäne gestellt| Unter Quarantäne gestellt| Unter Quarantäne gestellt|
|**Windows Bescheinigung**|Windows 10 und 10 unter Windows Mobile isoliert werden.<br /><br />Die Einstellung gilt nicht für Windows 8.1|N/V|N/V|N/V|

------------------------------

**Remediated** = Compliance wird vom Betriebssystem Geräts erzwungen (beispielsweise ist der Benutzer eine PIN festgelegt wird).  Es kommt nie vor, wenn die Einstellung nicht kompatibel ist.

**Isoliert** das Gerät = Betriebssystem erzwingt keine Compliance (z. B. Android-Geräten nicht erzwingen, dass den Benutzer auf das Gerät verschlüsseln). Wenn Sie die Geräte nicht kompatibel ist, werden die folgenden Aktionen ausgeführt:

-   Das Gerät werden blockiert, wenn der Benutzer durch eine bedingte Zugriffsrichtlinie vorgesehen ist.

-   Im Portal Unternehmen werden benachrichtigt, dass den Benutzer über alle Kompatibilitätsprobleme.

## Nächste Schritte
[Erstellen einer Richtlinie für Geräte compliance](create-a-device-compliance-policy-in-microsoft-intune.md)

[Bereitstellen Sie und überwachen Sie Ihrer Geräterichtlinie](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Siehe auch
[Beschränken Sie den Zugriff auf e-Mail und Office 365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
