---
title: "Zurücksetzen aus verwalteten app Unternehmensdaten | Microsoft Intune"
description: "Erfahren Sie, wie Sie Selektives Unternehmensdaten aus Geräte Remote entfernen können."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 111cfe66e3ee6d9238bb885e3be4025a24811369
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Wischen Sie die app-Daten mit Microsoft Intune verwalteten Unternehmen
Wenn ein Gerät verloren oder gestohlen wird oder wenn der Mitarbeiter Ihres Unternehmens lässt, Sie möchten ist sicher Unternehmensdaten app vom Gerät entfernt. Jedoch empfiehlt nicht so entfernen Sie persönliche Daten auf dem Gerät, insbesondere dann, wenn dies ein Mitarbeiter im Besitz Gerät ist.

Wenn app Unternehmensdaten Selektives entfernen möchten, erstellen Sie eine zurücksetzen Anforderung mithilfe der in diesem Abschnitt **erstellen eine Anforderung zurücksetzen** in diesem Artikel beschriebenen Schritte aus.  Sobald die Anforderung, das nächste Mal abgeschlossen ist, wenn, das die app auf dem Gerät ausgeführt wird, aus der app Unternehmensdaten entfernt.
>[!NOTE]
> Kontakte aus der app direkt auf systemeigenen Adressbuch synchronisiert werden entfernt. Kontakte aus dem Adressbuch systemeigenen eine andere externe Quelle synchronisiert mit können nicht gelöscht. Dies ist derzeit nur für die app Microsoft Outlook verfügbar.



## Erstellen Sie eine Anforderung zurücksetzen

1.  Wählen Sie die Kachel **Wischen Sie Besprechungsanfragen** in das Blade **Intune Mobile anwendungsverwaltung** aus.

    ![Screenshot der Intune mobilen Anwendung Management Blade mit Zusammenfassung Kachel](../media/AppManagement/AzurePortal_MAM_WipeRequests.png)

2.  Wählen Sie **neu zurücksetzen Anfragen aus**.

    ![Screenshot der neu zurücksetzen Anforderung Blade aus.](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

3.  Wählen Sie das Blade **neu Wischen Anforderung** **Benutzer** das Blade **Benutzer** zu öffnen, und wählen Sie den Benutzer, dessen app-Daten, die Sie zurücksetzen möchten.

4.  Wählen Sie **Gerät**aus.  Daraufhin wird das **Gerät** Blade, das alle Geräte, die dem ausgewählten Benutzer zugeordnet sind.  Wählen Sie das Gerät, die, das Sie zurücksetzen möchten.

5.  Sie können jetzt wieder in das Blade **neu zurücksetzen Anforderung aus** . Wählen Sie auf **Ok,** um eine Anforderung zurücksetzen zu gestalten. Der Dienst erstellt und verfolgt die Anforderung einer separaten zurücksetzen für jeden geschützten app auf dem Gerät.


![Screenshot der Löschvorgang anfordert Kachel ](../media/AppManagement/AzurePortal_MAM_WipeRequestsSummary.png)

## Überwachen Sie Ihre Anfragen zurücksetzen
Das **mobile anwendungsverwaltung Intune** Blade hat einen zusammengefassten Bericht auf die Kachel **Zurücksetzen Anforderung aus** .  Zeigt den allgemeinen Status, und die Anzahl der ausstehenden Anfragen und Fehlern enthält. Sie erhalten weitere Details, indem Sie die nachfolgend beschriebenen Schritte:

1.  Wählen Sie in der **mobilen anwendungsverwaltung Intune** Blade die Kachel **Zurücksetzen aus der Anforderung** zum Öffnen des **Anfrage Wischen** Blades aus.

2.  In das **Zurücksetzen aus Anforderung** Blade sehen Sie die Liste der Ihre Anfragen gruppiert nach Benutzer.  Da das System die Anforderung einer zurücksetzen für jede geschützten app ausgeführt werden, auf dem Gerät erstellt, wird möglicherweise mehrere Anforderungen für einen Benutzer angezeigt.  Der Status gibt an, ob eine Anforderung zurücksetzen noch **Ausstehend**, **fehlgeschlagen**oder **erfolgreich**ist.

### Siehe auch
[Schützen von app-Daten, die mithilfe von Informationsverwaltungsrichtlinien für mobile-app ](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Verwenden des Azure-Portals](azure-portal-for-microsoft-intune-mam-policies.md)
