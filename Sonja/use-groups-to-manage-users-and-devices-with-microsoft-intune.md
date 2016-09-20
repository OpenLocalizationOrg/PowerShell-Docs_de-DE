---
title: "Verwenden von Gruppen zum Verwalten von Benutzern und Geräten | Microsoft Intune"
description: Erstellen und Verwalten von Gruppen mithilfe des Arbeitsbereichs Gruppen.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
ms.openlocfilehash: 76b8ab90974dc258992ed8c660a04fc08872a4ec
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwenden von Gruppen zum Verwalten von Benutzern und Geräten in Microsoft Intune

In diesem Thema werden die zum Erstellen von Gruppen in Intune. Darüber hinaus Informationen wie die Verwaltung von Gruppen vertraut ist in den kommenden Monaten ändern. 

>[!IMPORTANT]
>
>Wenn Sie den Arbeitsbereich Gruppen im Portal Intune öffnen und finden Sie unter einen Link zu der Azure-active Directory-Portal (Azure AD-), und klicken Sie dann Sie den *neuen* Azure AD Sicherheit Gruppen Ansatz Gruppenmanagement bereits in Intune verwenden, beschrieben [Notice of anstehende Verbesserungen der Administrator-Benutzeroberfläche für Gruppen](#notice-of-upcoming-improvements-to-the-admin-experience-for-groups). Klicken Sie auf den Link zum Erstellen und Verwalten Ihrer Gruppen Azure AD-Portal. Informationen zum Arbeiten mit Sicherheitsgruppen Azure AD-finden Sie unter [Verwalten von Zugriff auf Ressourcen mit Azure-Active Directory-Gruppen](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
>
>Wenn Sie den Link Azure AD-Portal nicht angezeigt werden, verwenden Sie weiterhin den *aktuelle* Ansatz zur Gruppe Verwaltung [erstellen Gruppen zum Verwalten von Benutzern und Geräten mit Microsoft Intune](#Create-groups-to-manage-users-and-devices-with-Microsoft-Intune) in diesem Artikel beschrieben.


## Benachrichtigung über anstehende Verbesserungen der Administrator-Benutzeroberfläche für Gruppen

Sie haben uns mitzuteilen, eine Gruppierungs- und Erfahrung über Enterprise Mobilität + Sicherheit verwendet werden soll. Wir hören. Basierend auf Ihr Feedback, wird bald Intune Gruppen Konvertierung in Azure Active Directory-basierten Sicherheitsgruppen durchgeführt werden. Diese Änderung wird Gruppenmanagement über Intune und Azure Active Directory (Azure AD) zusammengeführt werden. Die neue Benutzeroberfläche bedeutet, dass Sie nicht zwischen Diensten Gruppen duplizieren. Außerdem wird durch die Optionen zum Verwenden von Windows PowerShell und Microsoft Graph Erweiterbarkeit zur Verfügung.

### Wie wirken sich diese mich sofort aus?
Diese Änderung auswirken nicht jetzt. Aber hier was kommt:

-   Im September 2016 werden neue Konten, die nach der Veröffentlichung der monatlichen Dienst bereitgestellt werden Azure AD-Sicherheitsgruppen anstelle Intune Benutzergruppen verwenden.   
-   Im Oktober 2016 werden neue Konten, die nach der Veröffentlichung der monatlichen Dienst bereitgestellt werden sowohl Benutzer-basierten auch Gerät-basierten Gruppen im Portal Azure AD-verwalten. Es werden keine Auswirkung auf vorhandene Kunden.
-   Im November 2016 beginnt das Produktteam Intune vorhandene Kunden in der neuen Azure AD-basierten Gruppe Verwaltungsoption migrieren. Alle Benutzer und Geräte-Gruppen, die heute in Intune vorhanden sind, werden in Azure AD-Sicherheitsgruppen migriert werden. Die Migration in Blattnamen im November 2016 beginnen möchten. Wir nicht Migration gestartet, bis wir können keine Auswirkung auf Ihre täglichen Arbeit minimieren, und wenn wir erwartet keine Auswirkung auf die Benutzer werden. Auch erhalten Sie beachten bevor wir Ihr Konto migrieren.


### Wann und wie wird kann ich mit dem neuen Gruppen migrieren?
Wir migrieren aktuelle Intune Kunden über einen Zeitraum. Wir haben den Zeitplan für die Migration Fertigstellen und aktualisieren in diesem Thema wird in einigen Wochen, um weitere Details zu verleihen. Wir geben Sie beachten, bevor Sie migriert werden. Wenn Sie alle Migrations-Fragen haben, wenden Sie sich an unser Migrationsteam am <intunegrps@microsoft.com>.

### Was geschieht mit meiner vorhandenen Benutzer und Gerätegruppen?
 Azure AD-Sicherheitsgruppen migriert Benutzergruppen und Device-Gruppen, die Sie in Intune erstellt haben. Intune Standardgruppen, wie z. B. die Gruppe alle Benutzer migriert nur, wenn Sie diese in Bereitstellungen zum Zeitpunkt der Migration verwenden. Migration möglicherweise für einige Gruppen komplexer. Wir werden benachrichtigt, wenn zusätzliche Schritte für die Migration in Ihrer Organisation erforderlich sind.

### Welche neuen Funktionen mich zur Verfügung gestellt werden?
Hier werden die neuen Funktionen, die eine Einführung mit dieser Migration von Intune auf Azure Active Directory ein:

-    Azure AD-Sicherheitsgruppen werden in Intune bei allen Typen von Bereitstellungen unterstützt werden.
-    Azure AD-Sicherheitsgruppen werden die Gruppierung von Geräten und Benutzern unterstützen.
-    Azure AD-Sicherheitsgruppen werden dynamische Gruppen unterstützt, die Intune Geräteattribute verfügen. Beispielsweise werden Sie können dynamisch Gruppe Geräte nach Plattform, wie iOS sein. Wenn Sie ein neues iOS-Gerät in Ihrer Organisation registriert ist, wird es automatisch zur Gruppe iOS-Gerät dynamische hinzugefügt.
-    Sie müssen einen freigegebenen Admin-Benutzeroberfläche für die Verwaltung über Azure AD und Intune.
- Die Rolle Intune Dienstadministrator wird Azure AD hinzugefügt werden, sodass die Dienstadministratoren Intune Gruppe Verwaltungsaufgaben in Azure AD ausführen können.

### Welche Funktionalität Intune nicht zur Verfügung?
Obwohl das Gruppen verbessern können, werden einige Intune-Funktionen, die nicht zur Verfügung nach Ihrer Organisation Azure AD-Sicherheitsgruppen aus Intune Gruppen migriert werden.

#### Verwaltung von Gruppenfunktionen

-   Nach dem Migrieren, können Sie nicht mehr Mitglieder oder Gruppen ausschließen, wenn Sie eine neue Gruppe erstellen. Mit dynamischen Azure AD-Gruppen können Sie jedoch verwenden Attribute zum Erstellen erweiterter Regeln, die Sie verwenden können, Ausschließen von Mitgliedern aus einer Gruppe basierend auf Kriterien, die Sie festlegen.
-   Aufgehobener Gruppierung Gruppen für Benutzer und Geräte aufgehobener Gruppierung wird nicht unterstützt werden. Wir werden nicht Intune diesen Gruppen in Azure AD migrieren.


#### Gruppe-abhängige Funktionen

-   Die Rolle des Administrators Dienst keinen Berechtigungen **Gruppen verwalten** .
-   Sie können keine Gruppe Exchange ActiveSync-Geräten werden. Die Gruppe alle verwalteten EAS-Geräten wird aus einer Gruppe in einer Berichtsansicht konvertiert.
-  Pivotieren mit Gruppen in Berichten nicht zur Verfügung.
-  Benutzerdefinierte Gruppe als Ziel der Benachrichtigungsregeln nicht zur Verfügung.

### Was sollte ich tun, um diese Änderung vorzubereiten?
 Wir haben Empfehlungen, die diesen Übergang für Sie einfacher machen:

- Bereinigen Sie alle gewünschte oder nicht benötigten Intune Gruppen vor der Migration.
- Auswerten der Verwendung von Ausschlusswörterbüchern in Gruppen und erwägen Sie die Umgestaltung Ihrer Gruppen aus, damit Sie nicht Ausschluss verwenden müssen.
-  Wenn Sie Administratoren, die nicht über die Berechtigungen zum Erstellen von Gruppen in Azure AD verfügen verfügen, bitten Sie Ihren Administrator Azure AD-diese Dienstadministrator Intune hinzufügen Azure AD-Rolle.


## Erstellen von Gruppen zum Verwalten von Benutzern und Geräten mit Microsoft Intune

In diesem Abschnitt beschrieben, wie Intune Gruppen in der Intune-Verwaltungskonsole zu erstellen.

Sie können erstellen und Verwalten von Gruppen in den Arbeitsbereich **Gruppen** in der Microsoft-Intune Admin-Verwaltungskonsole. Die **Gruppen** Übersichtsseite zeigt Status zusammengefasst, die Ihnen helfen können identifizieren und Priorisieren Sie Probleme, die Ihre Aufmerksamkeit erfordern. Statusübersichten behandeln diese Bereiche an:

-   Benachrichtigungen
-   Softwareupdates
-   Endpunkt Schutz
-   Richtlinie
-   Verwaltung von Software

Die Gruppenhierarchie werden auch Statusübersichten, mit deren Hilfe Sie erkennen und Beheben von Problemen für Mitglieder einer ausgewählten Gruppe.

## Erstellen von Gruppen

> [!TIP]
> Wenn Sie Gruppen erstellen, erwägen Sie, wie Sie Richtlinien angewendet werden sollen. Beispielsweise müssen Sie möglicherweise, die auf einem Gerätebetriebssystem beziehen und Richtlinien, die speziell unterschiedliche Rollen in Ihrer Organisation oder organisationsinterne Einheiten, die Sie bereits in Active Directory definiert haben. Es möglicherweise separate Gerätegruppen für iOS, Android und Windows sowie eine Benutzergruppe für jede Organisationseinheit Rolle haben hilfreich sein.
>
> Wahrscheinlich müssen Sie auch eine Standardrichtlinie erstellen, die gilt für alle Gruppen und Geräten, die grundlegende Compliance-Anforderungen Ihrer Organisation herstellen möchten. Dann können Sie weitere spezifische Richtlinien für die größten Kategorien der Benutzer und Geräte erstellen. Beispielsweise können Sie e-Mail-Richtlinien für jede der Gerätebetriebssysteme erstellen.
>
> Seien Sie vorsichtig, wenn Sie Ihre Richtlinien benennen, damit Sie sie später problemlos erkennen können. Ein Richtliniennamen für gute beschreibenden beträgt beispielsweise **WP e-Mail-Richtlinie für den gesamten Mandanten**.
>
> Bei jedem eine eingeschränkte Richtlinie erstellen, möchten Sie es den Benutzern kommunizieren. Nachdem Sie die weitere allgemeine Gruppen und Richtlinien erstellt haben, achten Sie auf wie Sie kleinere Gruppen erstellen, damit Sie nicht benötigte Kommunikation verringern können.

### So erstellen Sie eine Gerätegruppe

1.  Wählen Sie in der Verwaltungskonsole Intune **Gruppen** &gt; **Übersicht** &gt; **Gruppe erstellen**.

2.  Geben Sie einen Namen und eine Beschreibung (optional) für die Gruppe ein, und wählen Sie eine Gerätegruppe als der übergeordneten Gruppe. Wählen Sie auf **Weiter**.

3.  Wählen Sie auf der Seite **Kriterien für die Mitgliedschaft definieren** den Typ der Geräte in der Gruppe einbezogen werden sollen. Sie haben zusätzliche Gruppe Konfigurationsoptionen basierend auf den Typen der Geräte, die Sie einbeziehen möchten:

    -   **Computer**. Wählen Sie aus, ob alle Mitglieder der übergeordneten Gruppe einbezogen werden; der Organisations Einheiten, die Sie einbeziehen oder ausschließen möchten; und Domänen ein-oder ausgeschlossen werden soll. Sie können die Einheit und Domäne Organisationsinformationen für einen Computer aus dem Lager abrufen.

    -   **Mobile**. Wählen Sie aus, ob mobile Geräten, enthalten, die von Intune, mobilen Geräten verwaltet werden, die von Exchange ActiveSync oder beides verwaltet werden.

    -   **Alle Geräte**. Diese Option umfasst alle Geräte mit keine Ausschlüsse basierend auf ein beliebiges Kriterium.

4.  Wählen Sie auf der Seite **Direkte Mitgliedschaft definieren** **Durchsuchen** , um einzelne Geräte ein-oder ausschließen auszuwählen. Wenn Sie Geräte, die nicht in der übergeordneten Gruppe sind, die Sie angegeben haben auswählen, fügt Intune diese Geräte automatisch der übergeordneten Gruppe hinzu.

5.  Klicken Sie auf der Seite **Zusammenfassung** überprüfen Sie Ihre Auswahl, und wählen Sie dann auf **Fertig stellen**.

Die neu erstellte Gruppe wird in der Liste **Gruppen** , klicken Sie im Arbeitsbereich unter der übergeordneten Gruppe **Gruppen** angezeigt. Das ist auch in dem Bearbeiten oder löschen Sie die Gruppe.

### Zum Erstellen einer Benutzergruppe

1.  Wählen Sie in der Verwaltungskonsole Intune **Gruppen** &gt; **Übersicht** &gt; **Gruppe erstellen**.

2.  Geben Sie einen Namen und eine Beschreibung (optional) für die Gruppe ein, und wählen Sie dann eine Benutzergruppe als der übergeordneten Gruppe. Wählen Sie auf **Weiter**.

3.  Wählen Sie auf der Seite **Kriterien für die Mitgliedschaft definieren** aus, ob alle Mitglieder der übergeordneten Gruppe aufnehmen möchten, oder um eine leere Gruppe zu starten. Klicken Sie dann einbeziehen oder Ausschließen von Elementen basierend auf den Sicherheitsgruppen von Benutzern, die Sie entweder manuell konfigurieren im [Office 365-Verwaltungskonsole](http://go.microsoft.com/fwlink/?LinkId=698854), oder aus dem Active Directory synchronisiert. Wenn die Zugehörigkeit zu einer Sicherheitsgruppe verwandelt hat, möglicherweise auch die Zugehörigkeit zu Benutzergruppen auf der Grundlage dieser Sicherheitsgruppe ändern.

    > [!IMPORTANT]
    > Derzeit werden, wenn Ihre Gruppe Mitglieder von bestimmter Sicherheitsgruppen oder Manager Gruppen enthält und einige Gruppen Mitglieder verhindern, die Mitglieder, die Sie ursprünglich berücksichtigt entfernt. Zum Erstellen einer Gruppe, die sowohl im Lieferumfang von Mitgliedern sowie Elemente ausgeschlossen, es empfiehlt sich, zunächst in der übergeordneten Gruppe, der die darin enthaltenen Elemente zu erstellen. Erstellen Sie dann eine untergeordnete Gruppe für die übergeordnete Gruppe ein. In der Gruppe neu untergeordneten die ausgeschlossene Mitglieder aufgeführt. Klicken Sie dann verwenden dieser Gruppe untergeordneten Intune Richtlinien, Profile und Verteilung der app verwalten.

    > [!NOTE]
    > Im Portal Azure können Sie basierte auf den Managern, die Benutzer melden Gruppen erstellen. Diese Art von Gruppe ist dynamisch, und er ändert sich Mitarbeiter hinzugefügt oder aus einem Vorgesetzten Team in Azure Active Directory entfernt werden. Zum Erstellen einer Azure Gruppe basierend auf den Managernamen ist in [verwenden Attribute erstellen erweiterte Regeln](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)im Abschnitt **So konfigurieren Sie eine Gruppe als Gruppe "Manager"**beschrieben.

4.  Wählen Sie auf der Seite **Direkte Mitgliedschaft definieren** **Durchsuchen** , um einzelne Benutzer einbeziehen oder ausschließen auszuwählen. Wenn Sie Benutzer, die nicht in der übergeordneten Gruppe sind, die Sie angegeben haben auswählen, werden diese Geräte automatisch zur übergeordneten Gruppe hinzugefügt. Die Option manuell einen Benutzer hinzufügen, die sich unten im Dialogfeld **Elemente auswählen** . Dies ist hilfreich, wenn Sie einen Benutzer hinzuzufügen, der noch nicht über ein Gerät registrierten verfügt möchten.

5.  Klicken Sie auf der Seite **Zusammenfassung** überprüfen Sie Ihre Auswahl, und wählen Sie dann auf **Fertig stellen**.

Die neu erstellte Gruppe wird in der Liste **Gruppen** , klicken Sie im Arbeitsbereich unter der übergeordneten Gruppe **Gruppen** angezeigt. Das ist auch in dem Bearbeiten oder löschen Sie die Gruppe.

> [!TIP]
> Sicherheitsgruppen sind eine gute Ressource zu verwenden, wenn Sie die Benutzergruppen auffüllen. Da Sicherheitsgruppen definieren, wer welche Ressourcen zugreifen kann, können Sie Sicherheitsgruppen gut für die Benutzergruppen Intune übersetzen. Sicherheitsgruppen, die Sie aus Active Directory auf Azure Active Directory synchronisiert werden, oder die Sie direkt in Azure Active Directory über Office 365 Administrationscenter oder Azure-Portal erstellen, stehen Ihnen beim Erstellen von Benutzergruppen in Intune verwenden.

## Filter-Admin-Ansichten nach Rolle
Sie können in der gefilterten Gruppenansichten was ein IT-Administrator sehen kann, basierend auf Ihrer Rolle des Administrators anpassen. Sie können auch einschränken, welche Gruppen jeder IT-Administrator verwalten kann. Dies kann sinnvoll sein:

-   Sie möchten Ihre IT-Administratoren Elemente nur für bestimmte Benutzer und Geräte bereitstellen können
-   Sie möchten Ihre IT-Administratoren nur die Gruppen angezeigt, die zu diesem Administrator relevant sind

Sie können die gefilterten Gruppenansichten für Dienstadministratoren in der Administrator Intune-Verwaltungskonsole konfigurieren. Details finden Sie unter [Wissenswertes, bevor Sie Microsoft Intune beginnen](/intune/get-started/what-to-know-before-you-start-microsoft-intune).

Nach dem Einrichten gefilterten Gruppenansichten für eine Dienstadministrator, wenn der Administrator Software oder Richtlinien bereitstellt, oder Berichte führt, kann der Administrator anzeigen, und wählen Sie nur die Gruppen, die Sie angegeben haben. Der Administrator keine Statusinformationen außerdem auf diesen Seiten der Administratorkonsole angezeigt:

-   **Systemüberblick**
-   **Gruppen (Übersicht)**
-   **Endpunkt Schutz (Übersicht)**
-   **Benachrichtigungen (Übersicht)**
-   **Software (Übersicht)**
-   **Übersicht über die Richtlinie**

### Erstellen eine Gruppenansicht der gefilterten

1.  Wählen Sie in der Verwaltungskonsole Intune **Administrator** &gt; **Administrator Management** &gt; **Dienstadministratoren**.

2.  Wählen Sie die Dienstadministrator, denen Sie eine Gruppenansicht der gefilterten für erstellen möchten, und wählen Sie dann auf **Gruppen verwalten**.

3.  Klicken Sie im Dialogfeld **Wählen Sie die Gruppen, die für diese Dienstadministrator sichtbar,** fügen Sie die Gruppen hinzu, die die Dienstadministrator imstande sein sollen, zugreifen, und wählen Sie dann auf **OK**.

Nach dem Einrichten der gefilterten Gruppenansichten haben, wird der IT-Administrator kann anzeigen, und wählen Sie nur die Gruppen, die Sie angegeben haben.

## Verwalten Sie Ihrer Gruppen
Nachdem Sie die Gruppen erstellen, können Sie weiterhin diese entsprechend den Anforderungen Ihrer Organisation verwalten.

Sie können die Gruppe aus, um ihren Namen oder die Beschreibung ändern bearbeiten oder, die in der Gruppe gehört.

Sie können eine Gruppe löschen, die die Anforderungen Ihrer Organisation nicht mehr fungiert. Löschen einer Gruppe löschen zu dieser Gruppe gehören die Benutzer nicht.

## Nächste Schritte
Nachdem Sie Ihre Gruppen und Richtlinien eingerichtet haben, überprüfen Sie **Vorgesehen Werts** und **Status** Schritten zum Überprüfen der Auswirkung von mit Ihrem Design.

### So überprüfen Sie den Entwurf

1. Wählen Sie aus einer Gerätegruppe jedem Gerät aus, und navigieren Sie durch die Kategorien der Informationen am oberen Rand der Seite.
2. Wählen Sie die **Richtlinie**aus. Sie sehen nun wie dieser Screenshot Richtlinieneinstellungen einem Android-Gerät.

![Beispiel für die Richtlinie für Android-Einstellungen](../media/Intune-Device-Policy-v.2.jpg)

Jede Richtlinie verfügt über eine **Vorgesehen Wert** und einen **Status**. Der beabsichtigte Wert ist zu erreichen, wenn Sie die Richtlinie angewendet werden soll. Der Status lautet, was Sie erreichen, wenn Sie alle Richtlinien, die für das Gerät, als auch die Einschränkungen Anforderungen der Hardware und Betriebssystem gelten zusammen interpretiert werden. In diesem Screenshot sehen Sie zwei Beispiele für die löschen:

-   **Einfache Kennwörter zulassen** auf **Ja**festgelegt ist, wie in der Spalte **Wert vorgesehen** dargestellt, aber der **Status** lautet **nicht verfügbar**. Dies liegt daran einfache Kennwörter für Android-Geräten nicht unterstützt werden.
-   Auf ähnliche Weise wird das erweiterte Richtlinienelement **-e-Mail-Einstellungen für iOS-Geräte** mit diesem Gerät nicht angewendet, weil es auf einem Android-Gerät ist.

> [!NOTE]
> Denken Sie daran, dass die Richtlinie restriktivere Wenn zwei Richtlinien, die verschiedene Detailebenen Einschränkung aufweisen auf dem gleichen Gerät oder Benutzer anwenden möchten, in der Praxis angewendet wird.
