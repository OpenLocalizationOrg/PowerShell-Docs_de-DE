---
title: Erstellen und Bereitstellen von MAM | Microsoft Intune
description: "Verwenden Sie eine schrittweise Anleitung zum Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien für mobile-app in diesem Thema."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 686610249b35f81e9ad7a87fe20d736a32eafb43
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien mit Microsoft Intune mobile-app
Informationsverwaltungsrichtlinien (MAM) für Mobile-app können angewendet werden, um apps für Geräte, können möglicherweise nicht vom Intune verwaltet ausgeführt. MAM Richtlinien Arbeit und den Szenarien von Intune MAM Richtlinien unterstützt finden Sie eine ausführlichere Beschreibung wie Thema [app-Daten, die mithilfe von Informationsverwaltungsrichtlinien für mobile-app zu schützen](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) .

In diesem Thema werden die Vorgehensweise zum Erstellen einer Richtlinie MAM im **Azure-Portal**an. Azure-Portal ist die neue Administratorkonsole zum Erstellen von MAM, und es wird empfohlen, dass Sie mithilfe dieser Portal um MAM Richtlinien zu erstellen. Azure-Portal unterstützt die folgenden MAM Szenarien:
- Geräte in Intune registriert
- Durch die Lösung eines Drittanbieters MDM verwaltete Geräte
- Geräte, die nicht von einem beliebigen MDM Lösung (BYOD) verwaltet werden.

>[!IMPORTANT]
Wenn Sie zum Verwalten Ihrer Geräte derzeit die **Intune-Verwaltungskonsole** verwenden, wird berücksichtigen Sie Folgendes:

> * Sie können eine Richtlinie MAM erstellen, die die apps für Geräte in Intune mithilfe der [Verwaltungskonsole Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)registriert unterstützt.
> * In der Verwaltungskonsole Intune erstellte MAM-Richtlinien können nicht Azure-Portal importiert werden.  Die Richtlinien MAM müssen im Azure-Portal neu erstellt werden.

> * Alle MAM Richtlinieneinstellungen in der Administrator Intune-Verwaltungskonsole möglicherweise nicht angezeigt. Das Azure Portal ist die neue Administratorkonsole zum Erstellen von MAM.

> * Bereitzustellende apps verwalten, müssen Sie eine Richtlinie MAM erstellen, in der die Intune-Verwaltungskonsole. Sie möchten in diesem Fall MAM Richtlinien in der Intune-Verwaltungskonsole und Azure-Portal zu erstellen: Intune-Verwaltungskonsole, um sicherzustellen, dass Sie die Möglichkeit, verwaltete apps, Azure-Portal bereitstellen, da es sich um die neue Administratorkonsole handelt, die alle MAM Richtlinieneinstellungen enthält.

> * Wenn Sie sowohl Intune-Verwaltungskonsole und Azure-Portal MAM Richtlinien erstellt haben, ist die Richtlinie, die in Azure-Portal erstellt wird auf der apps angewendet.

Um eine Liste der Einstellungen für die Informationsverwaltungsrichtlinie unterstützte Plattformen für Android und iOS anzuzeigen, wählen Sie eine der folgenden Aktionen aus:

> [!div class="op_single_selector"]
- [Richtlinien für iOS](ios-mam-policy-settings.md)
- [Android-Richtlinien](android-mam-policy-settings.md)

##  Erstellen einer Richtlinie MAM
Vor dem Erstellen einer Richtlinie MAM, überprüfen Sie die [erforderlichen Komponenten und Support](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) -Informationen.
1.  Wählen Sie **Intune mobilen anwendungsverwaltung &gt; Einstellungen** um das Blade **Einstellungen** zu öffnen.

    ![Screenshot des Intune mobilen Anwendung Management Blades](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Ist dies das erste Mal verwenden Sie das Azure-Portal [Azure-Portal für Microsoft Intune MAM Richtlinien](azure-portal-for-microsoft-intune-mam-policies.md) zuerst lesen auf dem Portal kennenzulernen.

2.  Wählen Sie das Blade **Einstellungen** **-App-Richtlinie**aus.  Dadurch wird das **App-Richtlinie** Blade, wo Sie neue Richtlinien erstellen und Bearbeiten von vorhandenen Richtlinien werden, geöffnet. Wählen Sie **Hinzufügen einer Richtlinie**aus.

    ![Screenshot des App-Richtlinie Blades mit der hervorgehobenen eine Menüoption Richtlinie hinzufügen ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  Geben Sie einen Namen für die Richtlinie, fügen Sie eine kurze Beschreibung hinzu, und wählen Sie den Plattformtyp eine Richtlinie für iOS oder Android zu erstellen.  Sie können mehr als eine Richtlinie für jede Plattform erstellen.

    ![Screenshot der Hinzufügen einer Richtlinie blade](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  Wählen Sie **Apps** , um das **Blade Apps** zu öffnen, in dem eine Liste der verfügbaren apps angezeigt wird. Sie können eine oder mehrere apps aus der Liste auswählen, die Sie der Richtlinie zuordnen, die Sie erstellen möchten. Sie die apps ausgewählt haben, wählen Sie die Schaltfläche **Wählen Sie** am unteren Rand der Blade **Apps** , um Ihre Auswahl zu speichern.

    > [!IMPORTANT]
    > Sie müssen mindestens eine app zum Erstellen einer Richtlinie auswählen.

5.  Klicken Sie auf das **Hinzufügen einer Richtlinie Blade**wählen Sie zum Öffnen des Richtlinie Einstellungen Blades **Konfigurieren erforderlich Einstellungen** aus.

    Es gibt zwei Feldkategorien für Richtlinieneinstellungen,**Daten Verlagerung** und **Access**ein.  Daten Verlagerung Richtlinien gelten für das Verschieben von Daten in die und aus der apps, während der Access-Richtlinien bestimmen, wie die Endbenutzer der apps in einem Arbeitskontext greift auf.
    Fangen Sie haben die Richtlinieneinstellungen Standardwerte.  Sie müssen keine Änderungen vornehmen, wenn die Standardwerte Ihren Anforderungen entsprechen.

    > [!TIP]
    > Nur bei Verwendung von apps im Arbeitskontext, werden diese Richtlinieneinstellungen erzwungen.  Wenn der Endbenutzer die app verwendet, um eine persönliche Aufgabe zu erledigen, werden sie durch diese Richtlinien nicht betroffen.

    ![Screenshot des Blades Einstellungen sowie das Hinzufügen einer Richtlinie blade](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  Wählen Sie **OK** , um diese Konfiguration speichern aus.  Sie können jetzt wieder in das **Hinzufügen einer Richtlinie** Blade. Wählen Sie **Erstellen** , um die Richtlinie erstellen und speichern Ihre Einstellungen aus.

    ![Screenshot der Hinzufügen einer Richtlinie Blade mit, dass die Einstellungen und Apps konfiguriert wurden](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)



Nach dem Erstellen einer Richtlinie wie im vorangehenden Verfahren beschrieben, wird es nicht für alle Benutzer bereitgestellt.  Folgen Sie den Schritten unter die Richtlinie bereitstellen.

> [!IMPORTANT]
> Wenn Sie eine Richtlinie MAM für eine app mithilfe der Verwaltungskonsole Intune und einer MAM Richtlinie über das Azure-Portal erstellen, hat die Richtlinie, die Sie erstellt haben, über das Azure-Portal Vorrang vor. Die Berichte in der Verwaltungskonsole Intune oder Konfigurations-Manager wird jedoch die Richtlinieneinstellungen Dokumentvorlagen Azure-Portal melden. Beispiel:
>
> -   Sie erstellt eine mobile Anwendung zur Dokumentverwaltungsrichtlinie in der Intune Admin-Verwaltungskonsole, die Blöcke aus einer app zu kopieren.
> -   Eine mobile-app zur Dokumentverwaltungsrichtlinie in der Azure-Verwaltungskonsole, die Kopie aus einer app ermöglicht erstellten
> -   Sie ordnen Sie beide mit der gleichen Richtlinien.
> -   Das Ergebnis ist, dass die Richtlinie, die Sie von der Azure-Konsole erstellt Vorrang hat, und Kopieren zulässig ist.
> -   Allerdings werden Status und Berichte in der Intune Verwaltungskonsole falsch darauf hinzuweisen, dass kopieren blockiert wird.

## Bereitstellen einer Richtlinie für Benutzer

1.  Wählen Sie die **Richtlinie** Blade **Benutzergruppen**, die das **Benutzergruppen** Blade wird geöffnet. Wählen Sie in die **Benutzergruppen** Blade So öffnen Sie das Blade **Benutzergruppe hinzufügen** **Benutzergruppe hinzufügen** aus.

    ![Screenshot des Blades Gruppen Benutzer mit der Benutzer Gruppe Menüoption hinzufügen hervorgehoben](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  Klicken Sie auf das Blade **Benutzergruppe hinzufügen** wird eine Liste von Benutzergruppen angezeigt. Dies ist eine Liste der Sicherheitsgruppen in Ihrem **Azure Active Directory**.  Sie können die Benutzergruppen auswählen, die Sie dieser Richtlinie gelten soll, und wählen Sie **auswählen**möchten. **Wählen Sie**auswählen, wird die Richtlinie für Benutzer bereitgestellt.

    ![Screenshot des hinzufügen Benutzer Gruppe Blades mit der Liste der Azure-Active Directory-Benutzer](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    Sie haben nun eine Richtlinie erstellt und es für Benutzer bereitgestellt.

Nur Benutzer mit [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Lizenzen zugewiesen werden von der Richtlinie betroffen.  Benutzer, die in der Sicherheitsgruppe sind, dass Sie die Option aktiviert verfügen Sie nicht über eine [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Lizenz, die ihnen zugewiesenen sind hiervon nicht betroffen.

>[!IMPORTANT]
> Wenn Sie Intune mit Konfigurations-Manager verwenden, um Ihre iOS und Android-Geräten verwaltet, wird die Richtlinie nur an die Benutzer direkt in der Gruppe angewendet, die Sie ausgewählt haben.  Mitglieder von untergeordneten Gruppen verschachtelt in der Gruppe, die Sie ausgewählt haben, sind nicht betroffen.

Die Endbenutzer können die apps aus dem App Store oder Google Play herunterladen. Eine ausführliche exemplarische wie MAM Unternehmen geschützt finden Sie unter Daten auf dem Gerät [Endbenutzer mit MAM aktiviert apps](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md) Thema.

##  Ändern Sie die vorhandene Richtlinien
Sie können eine vorhandene Richtlinie bearbeiten und wenden Sie sie auf den Benutzer. Jedoch, wenn Sie vorhandene Richtlinien ändern, wird nicht Benutzer, die bereits in der apps angemeldet sind die Änderungen über einen Zeitraum 8 Stunden angezeigt.

Anzeigen des Effekts über die Änderungen der Endbenutzer haben sofort zum Abmelden von der app, und melden Sie sich wieder einzuchecken.

### So ändern Sie die Liste der apps, die mit der Richtlinie verbunden ist

1.  Wählen Sie das **App-Richtlinie** Blade die Richtlinie, die Sie ändern möchten. Eine bestimmte auf die soeben ausgewählte Richtlinie Blade wird geöffnet.

    ![Screenshot einer vorhandenen Richtlinie, die in einem separaten Blade geöffnet](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Wählen Sie die Richtlinie Blade **gezielte apps** , um die Liste der apps zu öffnen.

3.  Entfernen Sie oder fügen Sie apps aus der Liste hinzu, und wählen Sie das **Symbol zum Speichern** in die Änderungen zu speichern.

### So ändern Sie die Liste der Benutzergruppen

1.  Wählen Sie das **App-Richtlinie** Blade die Richtlinie, die Sie ändern möchten. Daraufhin wird das Blade speziell für die Richtlinie, die Sie ausgewählt haben.

2.  Wählen Sie die Richtlinie Blade **Benutzergruppen** , um das Blade **Benutzergruppe** zu öffnen, das die Liste der aktuellen Benutzergruppen anzeigt, die dieser Richtlinie haben.

3.  **Fügen Sie eine neue Benutzergruppe hinzu** , die Richtlinie wählen Sie **Benutzergruppe hinzufügen**, und wählen Sie die Benutzergruppe aus. Wählen Sie aus, **Wählen Sie aus** , um die Richtlinie für die Gruppe bereitstellen, die Sie ausgewählt haben.

    ![Screenshot des mit zwei Benutzern ausgewählt Blades Gruppe Benutzer hinzufügen](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  So **Löschen Sie eine Benutzergruppe**markieren Sie die Benutzergruppe aus, die Sie entfernen, wählen Sie die drei Punkte (...), und wählen Sie dann **Löschen** , um die Benutzergruppe entfernen möchten.

    ![Screenshot mit eine Löschoption ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### Zum Ändern der Richtlinieneinstellungen

1.  Wählen Sie das **App-Richtlinie** Blade die Richtlinie, die Sie ändern möchten. Eine bestimmte auf die soeben ausgewählte Richtlinie Blade wird geöffnet.

    ![Screenshot einer vorhandenen Richtlinie in einem separaten Blade öffnen ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Wählen Sie **Richtlinieneinstellungen** , um das Blade **Richtlinieneinstellungen** zu öffnen.

3.  Ändern der Einstellungen, und wählen Sie das **Symbol zum Speichern** in die Änderungen zu speichern.

    ![Screenshot der Richtlinie Einstellungen Blade mit speichern Menüoption oben](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## Richtlinieneinstellungen
Um eine vollständige Liste der die richtlinieneinstellung für iOS und Android anzuzeigen, wählen Sie eine der folgenden Aktionen aus:

> [!div class="op_single_selector"]
- [Richtlinien für iOS](ios-mam-policy-settings.md)
- [Android-Richtlinien](android-mam-policy-settings.md)

## Nächste Schritte
[Überwachen von Compliance und Benutzer status](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### Siehe auch
[Endbenutzer für MAM aktiviert apps](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md)
