---
title: Aktivieren von Lookout MTP in Intune | Microsoft Intune
description: "Aktivieren des Schutzes von Lookout für Mobilgeräte in der Administrator Intune-Verwaltungskonsole."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: 4ae7d6c571f69c0cc51dc15355e50325afb88694
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Aktivieren von Lookout MTP Verbindung in der Administrator Intune-Verwaltungskonsole
In diesem Thema wird gezeigt, wie die Verbindung Lookout MTP in Intune aktivieren. Sie sollten bereits der Intune Verbinder in der Verwaltungskonsole Lookout MTP konfiguriert haben vor dem Durchführen dieses Schritts.  Wenn Sie dies nicht bereits getan haben, führen Sie im [Richten Sie Ihr Abonnement mit Lookout für Mobilgeräte Schutz](set-up-your-subscription-with-lookout-mtp.md)beschriebenen Schritte.

Wählen Sie zum Aktivieren der Verbindungs Lookout MTP in Intune, klicken Sie auf der Seite " **Suchverwaltung** " in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), **Integration von Drittanbieter-Dienst**aus. Wählen Sie **Lookout Status** , und aktivieren Sie die **Synchronisierung mit MTP** mithilfe der Umschaltfläche.

![Screenshot der Seite Lookout Synchronisierung mit hervorgehobener Schaltfläche den Schalter Protokollierung aktivieren](../media/mtp/lookout-intune-synchronization.png)

Damit ist die Einrichtung der Lookout und Intune Integration in der Intune-Verwaltungskonsole abgeschlossen.  Die nächsten Schritte zur Implementierung dieser Lösung umfassen die [dafür Arbeit apps](configure-and-deploy-lookout-for-work-apps.md) bereitstellen und die [Compliance](enable-device-threat-protection-rule-in-compliance-policy.md) -Richtlinien einrichten.

>[!IMPORTANT]
> Sie **müssen** konfigurieren, halten Sie die Augen Arbeit app vor Compliance-Richtlinienregeln erstellen und Konfigurieren von bedingten Zugriff. Dadurch wird sichergestellt, dass die app bereit und Endbenutzer installieren, bevor sie Zugriff auf e-Mail- oder anderen Unternehmensressourcen werden können.
## Nächste Schritte
[Konfigurieren von Lookout für die Arbeit-app ](configure-and-deploy-lookout-for-work-apps.md)
