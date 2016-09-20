---
title: "Planen Ihrer Benutzer und Gerät Gruppen | Microsoft Intune"
description: Planen von Gruppen an Ihre Organisation Anforderungen anpassen.
keywords: 
author: sanchusa
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ms.reviewer: lpatha
ms.suite: ems
ms.openlocfilehash: dc76ed0c368f616f8533c42b298f40bd18b22fce
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Planen Sie Ihrer Benutzer und Geräte-Gruppen
Gruppen in Intune bieten Ihnen große Flexibilität beim Verwalten von Ihrer Geräte und Benutzer. Sie können die Gruppen einrichten, um den Bedürfnissen Ihrer Organisation entsprechend:

- geografische Position
- Abteilung
- Hardware-Eigenschaften
- Betriebssystem
- Gibt an, ob das Gerät im Besitz eines Benutzers oder im Besitz eines Unternehmens wird


## Wie funktionieren Intune-Gruppen


Dies ist der Standardansicht den Knoten **Gruppen** in der Administrator Intune-Verwaltungskonsole:

![Screenshot der Standardansicht der Gruppen-Knoten in der Intune-Verwaltungskonsole](../media/Intune_Planning_Groups_Default_small.png)

Richtlinien werden auf Gruppen bereitgestellt, damit Gruppenhierarchie eines Ihrer Key gibt ist. Es ist wichtig zu wissen, dass Sie die übergeordnete Gruppe eine Gruppe nicht ändern können, nachdem Sie die Gruppe erstellt haben. Es ist entscheidend, ab dem Zeitpunkt, den Sie beginnen, mit dem Intune-Dienst, wie Sie Ihre Gruppen entwerfen. Einige empfohlen, dass Methoden zum Entwerfen einer Gruppenhierarchie entsprechend Ihren Anforderungen organisationsinterne hier beschrieben werden.

## Regeln für Gruppenmitgliedschaft

- Eine Gruppe kann Benutzer oder Geräte, jedoch nicht beide enthalten.

    * **Device-Gruppen**. Dies umfasst Computern und mobile Geräte. Bevor Sie einen Computer zu einer Gruppe hinzufügen können, müssen sie registriert sein. Bevor Sie ein mobiles Gerät zu einer Gruppe hinzufügen können, Ihre Umgebung muss konfiguriert werden, um die Unterstützung von mobilen Geräten und das Gerät muss registriert sein oder entdeckt in Exchange ActiveSync.

    * Die **Benutzergruppen**. Eine Gruppe kann Benutzer Sicherheitsgruppen verfügen. Sicherheit Gruppen synchronisieren mit Ihrem Instanz von Active Directory. Wenn Sie nicht mit Active Directory synchronisieren, können Sie manuell diesen Gruppen erstellen.

- Ein Gerät oder ein Benutzer kann mehr als einer Gruppe angehören.

- Eine Gruppe kann umfassen und Ausschließen von Elementen basierend auf den folgenden Mitgliedschaftsregeln:

    * **Mitgliedschaft Kriterien**. Hierbei handelt es sich um dynamische Regeln, die Intune ausgeführt wird, um ein- oder auszuschließen Mitglieder. Verwenden Sie diese Kriterien Sicherheitsgruppen und andere Informationen, die mit Ihrem lokalen Instanz von Active Directory synchronisiert. Sobald die Sicherheitsgruppe oder Daten geändert hat, wird die Gruppenmitgliedschaft beim Synchronisieren mit Active Directory.

    * **Direkte Mitgliedschaft**. Hierbei handelt es sich um statische Regeln, die explizit hinzufügen oder Mitglieder ausschließen. Die Liste der Mitglieder ist statisch.

-   Active Directory-Domänendiensten (AD DS) ist nicht erforderlich, beim Erstellen von Benutzergruppen oder Gerätegruppen, die Benutzer oder Computer enthalten. Aber für Gerätegruppen mobile Geräte aufnehmen möchten, muss Ihre Umgebung zur Unterstützung von mobiler Geräten konfiguriert werden.

    Darüber hinaus müssen die Geräte erkannt und Intune hinzugefügt werden.

## Gruppe Beziehung Regeln

- Jede Gruppe, die Sie erstellen, müssen in der übergeordneten Gruppe. Nachdem Sie die Gruppe erstellt haben, können Sie eine Gruppe übergeordnete Gruppe nicht ändern.

- Wenn Sie Benutzer oder Geräte einer untergeordneten Gruppe hinzufügen:

    * Die untergeordneten Gruppe ist immer eine Teilmenge der übergeordneten Gruppe.

    * Mitglieder, die Sie einer Gruppe untergeordnetes Element hinzufügen, werden automatisch in der Gruppe übergeordnete Gruppe hinzugefügt.

    * Sie können nicht Mitglied einer untergeordneten Gruppe hinzufügen, wenn die Mitglied von der übergeordneten Gruppe ausgeschlossen wird.

- Die Zugehörigkeit zu einer übergeordneten Gruppe definiert die verfügbare Mitgliedschaft für die Gruppe untergeordneten.

- Wenn Sie in der übergeordneten Gruppe löschen, werden alle untergeordneten Gruppen gelöscht.

- Sie können jedoch Bereitstellen von Inhalt und Richtlinien für eine übergeordnete Gruppe, die Bereitstellung auf untergeordneten Gruppen ausschließen.

- Sie können einen bestimmten Benutzer oder Gerät zu einer untergeordneten Gruppe hinzufügen, wenn der Benutzer oder das Gerät nicht bereits Mitglied der übergeordneten Gruppe ist. Wenn Sie dies tun, wird das neue Mitglied der Gruppe untergeordneten zur übergeordneten Gruppe hinzugefügt.

    Sie können jedoch Mitglied einer untergeordneten Gruppe hinzufügen, wenn das Mitglied aus der übergeordneten Gruppe ausgeschlossen wird.

- Die Mitgliedschaft ist rekursive. Beispiel:

    * **Pat** ist ein Mitglied der Sicherheitsgruppe **Laptopbenutzer** nur eine Gruppe.

    * Die Gruppe **Laptop-Benutzer** ist ein Mitglied der Sicherheitsgruppe **Benutzer genehmigt** .

    * Sie erstellen eine Gruppe Intune, die eine dynamische Mitgliedschaft Abfrage verwendet, die die Mitglieder der Gruppe **Benutzer genehmigt** enthält. Das Ergebnis ist, dass der Benutzergruppe Intune **Pat**enthält.

> [!TIP]
> Denken Sie an, wenn Sie Gruppen erstellen, wie Sie die Richtlinie angewendet werden. Angenommen, haben Sie Richtlinien, die speziell für Gerätebetriebssysteme, sind oder Richtlinien, die speziell für unterschiedliche Rollen sind oder organisationsinterne Einheiten, die Sie bereits in Ihrem Active Directory-Dienst definiert haben. Einige Administratoren hilfreich Gerätegruppen erstellen, die speziell für iOS, Android und Windows sind. Dies gilt zusätzlich zum Erstellen von Benutzergruppen für jede Organisationseinheit Rolle.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## Integrierte Gruppen
Intune weist neun vordefinierte Gruppen, die Sie bearbeiten oder löschen können: <!--maybe a screen shot would be best?-->

-   **Alle Benutzer**
    -   Benutzer aufgehobener Gruppierung
-   **Alle Geräte**
    -   Alle Computer
    -   Auf allen mobilen Geräten
        -   Alle direkten verwalteten Geräte
        -   Alle Exchange ActiveSync verwaltete Geräte
    -   Alle Corporate im Besitz Geräte
    -   Aufgehobener Gruppierung Geräte

> [!NOTE]
> Lassen Sie Ihre Motto werden: *die Würze*. Wenn Ihre Organisation keinen Bedürfnisse wie in den folgenden Abschnitten beschriebenen, halten Sie es einfach, und wechseln Sie mit der Struktur der standardmäßigen Gruppen und Richtlinien. Dadurch wird den Dienst langfristig überschaubarer. Wartung werden einfacher, wenn Ihre Benutzer einheitlich behandelt werden können. Mit kleinen Unterscheidung nach Gruppen müssen Sie weniger Richtlinien zu verwalten.


### Alle Benutzer und Geräte in Ihrer Organisation
Definieren einer übergeordneten Gruppe für alle Benutzer und Geräte in Ihrer Organisation an. Sie sind wahrscheinlich Richtlinien einsetzen, die für alle gelten soll. Sie können für diesen Zweck Intune **Alle Benutzer** und **alle Geräte** Standardgruppen verwenden. Untergruppen, die Geräte indem Sie Besonderheiten, wie eine Gruppe organisieren schalten Sie Ihr eigenes Gerät (BYOD) und eine für corporate Besitzer (CO) Geräte untergeordneten Gruppen der **Alle Benutzer** und **Geräte aller** übergeordneten Gruppen sein kann.

## Anpassen von Gruppen für Ihre Organisation

### BYOD und Geräte im Unternehmen im Besitz
Wenn Ihre Organisation Mitarbeiter auf ihren eigenen Geräten verwenden kann, Geräte im Besitz eines Unternehmens bietet oder verfügt über eine Kombination aus beiden, empfehlen wir, dass Sie separate Richtlinien für diese Kategorien von Geräten anwenden.

Achten Sie bei BYOD oder eine Mischung Richtlinien planen, die nicht auf dem lokalen für Verbraucher zu verstoßen verletzt. Erstellen Sie eine übergeordnete Gruppe für alle Benutzer, die ihren eigenen Geräten verbringen. Dieser Gruppe können Sie Richtlinien anwenden, die für alle Benutzer in dieser Kategorie verfügbar sind.

![Erstellen einer BYOD übergeordneten Gruppe](../media/Intune_Planning_Groups_BYOD_small.png)

Auf ähnliche Weise können Sie eine Gruppe für die CO Gerätebenutzer in Ihrer Organisation erstellen:

![Nebengeordneten Benutzergruppen für BYOD und CO-Geräte](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### Gruppen für geographischen Regionen
Wenn Ihre Organisation Richtlinien für bestimmte Regionen benötigt, können Sie auf der Grundlage geografische Region Gruppen erstellen. Sie können diese basieren, auf Landes-/ Gruppen, die Sie möglicherweise bereits in der Active Directory-Instanz erstellt haben, und synchronisieren Sie diese mit Ihrem Azure Active Directory-Dienst. Sie können auch direkt in Azure Active Directory regionale Gruppen erstellen.

Die nächsten Screenshots gezeigt, wie basierte auf Gruppen mit Ihrem lokalen Active Directory-Instanz synchronisiert Intune-Gruppen erstellen. In diesen Beispielen wird davon ausgegangen, dass Sie eine Active Directory-Sicherheitsgruppe **US-Benutzergruppe**aufgerufen haben.

Geben Sie zuerst allgemeine Informationen ein.

![Screenshot des Bereichs Gruppe "Bearbeiten"](../media/Intune_Planning_Groups_AD_General_small.png)

Wählen Sie unter **Kriterien für die Mitgliedschaft** **US Benutzergruppe**mit Active Directory synchronisiert werden, als der Sicherheitsgruppe unter Mitgliedschaftsregeln für die verwenden.

![Screenshot des Dialogfelds Gruppe "Bearbeiten"](../media/Intune_Planning_Groups_AD_Criteria_small.png)

Überprüfen Sie Ihre Eingaben, und wählen Sie dann auf **Fertig stellen** , um die Gruppe zu erstellen.

![Screenshot des Dialogfelds Gruppe "Bearbeiten"](../media/Intune_Planning_Groups_AD_Summary_small.png)

In diesem Beispiel haben wir auch eine Gruppe namens **MEA**, für die Nahost und Asien erstellt haben.

> [!NOTE]
> Wenn Gruppenmitgliedschaft nicht basierend auf Sicherheitsgruppen-Mitgliedschaft gefüllt wird, stellen Sie sicher, dass Sie Gruppenmitglieder Intune Lizenzen zugewiesen haben.

### Gruppen für bestimmte hardware
Wenn Ihre Organisation Richtlinien erfordert, die bestimmte Hardware Projekttypen betreffen, können Sie diese Anforderung ausgehend von Gruppen erstellen. Sie können als Grundlage für die Richtlinien bestimmten Gruppen, die Sie bereits in Ihrem lokalen Instanz von Active Directory erstellt haben, und klicken Sie dann mit Azure Active Directory synchronisieren. Sie können auch direkt in Azure Active Directory Gruppen erstellen. In diesem Beispiel verwenden wir **US-Benutzergruppe** als die übergeordnete Gruppe für die Gruppe **Laptop-Benutzer** .

![Sicherheitsgruppe wählen Sie im Dialogfeld](../media/Intune_Planning_Groups_Laptop_small.png)

An diesem Punkt sollte die Gruppe der Hierarchie in den nächsten Screenshot ähneln. Sie können sehen, dass Sie in der Gruppe Intune **Laptop-Benutzer**jetzt Mitglieder sind. Alle Richtlinien, die dieser Gruppe angewendet werden BYOD Laptop-Benutzern aus einer zweiten Region US angewendet werden.

![Anzeigen der Laptop Benutzergruppe](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### Gruppen für bestimmte Betriebssysteme
Wenn Ihre Organisation Richtlinien, die auf bestimmte Betriebssysteme wie Android, iOS oder Windows anwenden erfordert, können Sie diese Anforderung ausgehend von Gruppen erstellen. Wie in den vorherigen Beispielen können Sie diese als Grundlage für ein bestimmtes Betriebssystem Gruppen, die Sie bereits in Ihrem lokalen Instanz von Active Directory erstellt haben und mit Azure Active Directory zu synchronisieren. Sie können auch direkt in der Azure-Active Directory-Instanz erstellen.

Sie können mithilfe der gleichen Methode aus früheren Beispielen Gruppen basierend auf Benutzer erstellen <!--devices?--> , die das Betriebssystem von bestimmten Plattformen verwenden.

> [!NOTE]
> Oder, wenn Sie Benutzer zum Verwenden von mehreren mobiler Plattformen Betriebssysteme und Sie verfügen nicht über eine automatisierte Möglichkeit zum Kategorisieren von Benutzern als Android-Benutzer, iOS-Benutzer oder Windows-Benutzer erwägen Sie das Anwenden von Richtlinien für das Gerät festzulegen. Dadurch erhalten Sie eine größere Flexibilität beim Anwenden von Richtlinien, die zu einem Betriebssystem spezifisch sind.
>
> Sie können keine Gruppen dynamisch basierend auf das Betriebssystem des Geräts bereitstellen. Führen Sie stattdessen Folgendes mithilfe von Active Directory oder Azure Active Directory-Sicherheitsgruppen.

![Benutzergruppe Laptops](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

Nachdem alle sollte des Benutzers, die Gruppen basierend auf Ihren Anforderungen organisationsinterne ausgefüllt werden, die Gruppenhierarchie ungefähr wie folgt aussehen:

![Hierarchie Gruppenansicht](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Diese Hierarchie können Sie die Richtlinien der Organisation anwenden.

### Device-Gruppen
Sie können auch ähnliche Gruppen für Geräte erstellen, wie hier gezeigt, beginnend mit einer allgemeinen Gruppe, die alle im Besitz eines Mitarbeiters Geräten für das BYOD Szenario enthält.

![Klicken Sie im Dialogfeld Gruppe erstellen](../media/Intune_Planning_Groups_Device_General_small.png)

Stellen Sie sicher, dass Sie **alle Geräte (Computer und Mobile)** auswählen, damit die Gruppe alle BYO-Geräte enthalten sein sollen:

![Seite ' Kriterien ' Mitgliedschaft definieren](../media/Intune_Planning_Groups_Device_Criteria_small.png)

Überprüfen Sie Ihre Eingaben, und wählen Sie dann auf **Fertig stellen** , zum Erstellen der Gruppe BYOD.

![Klicken Sie im Dialogfeld Gruppe erstellen](../media/Intune_Planning_Groups_Device_Summary_small.png)

Fahren Sie mit Device-Gruppen erstellen, bis Sie eine Gerät Gruppenhierarchie verfügen, die ähnlich wie der Hierarchie der Gruppe ist. Ihre Gruppenknoten in der Intune-Verwaltungskonsole sieht in etwa wie folgt aus:

![Intune Hierarchie Gruppenansicht](../media/Intune_Groups_Hierarchy_Final_Small.png)

## Gruppe Hierarchien und Benennungskonventionen
Es wird empfohlen, benennen Sie jede Richtlinie entsprechend den Zweck, Plattform und Umfang auf denen Sie anwenden, um Gruppenrichtlinien-Verwaltungskonsole zu erleichtern. Verwenden Sie einen naming Standard, der die Gruppenstruktur, die Sie erstellt haben folgt, wenn Sie Ihre Richtlinien anwenden vorbereitet.

Beispielsweise könnten Sie für eine Android-Richtlinie, die für alle corporate, Android, mobile Geräte auf der regionalen US-Ebene gilt, die Richtlinie **CO_US_Mob_Android_General**nennen.

![Erstellen Sie die Richtlinie für Android](../media/Intune_planning_policy_android_small.png)

Wenn Sie auf diese Weise Ihre Richtlinien benennen, können Sie schnell erkennen, Richtlinien und ihres Verwendungszwecks und Bereich in den Knoten **Richtlinien** wie folgt:

![Liste der Intune-Richtlinie](../media/Intune_planning_policy_view_small.png)

## Nächste Schritte
[Erstellen von Gruppen](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
