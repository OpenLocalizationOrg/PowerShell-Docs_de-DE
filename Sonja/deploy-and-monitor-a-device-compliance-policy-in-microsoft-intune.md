---
title: "Bereitstellen und Überwachen Ihrer Richtlinie | Microsoft Intune"
description: "Verwenden Sie die schrittweisen Anweisungen in diesem Thema Bereitstellen und Überwachen Ihrer Geräterichtlinie."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 8658df1fb9932fb2cab984a13557aad684569df5
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Bereitstellen und Überwachen einer Richtlinie für Geräte Compliance in Microsoft Intune
## Bereitstellen einer Richtlinie compliance
Die Compliance-Richtlinien bereitstellen Sie für eine oder mehrere Gruppen von Benutzern in Ihrer Organisation [erstellt](create-a-device-compliance-policy-in-microsoft-intune.md) . Wenn eine Compliance-Richtlinien für einen Benutzer bereitgestellt wird, werden Geräte des Benutzers überprüft.

1.  Wählen Sie die Richtlinie, die Sie bereitstellen, und wählen **Bereitstellung verwalten**möchten, klicken Sie im Arbeitsbereich **Richtlinie** .
![Screenshot der Seite Richtlinie Konformität mit der Menüoption Bereitstellung verwalten oben](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  Wählen Sie eine oder mehrere Gruppen, Sie möchten die Richtlinie bereitstellen, und wählen Sie dann, im Dialogfeld **Bereitstellung verwalten** **Hinzufügen > OK**.
![Screenshot des Dialogfelds verwalten Bereitstellung](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) können Sie eine Compliance-Richtlinien für Benutzer bereitstellen. Verwenden von Active Directory-Gruppen, die Sie bereits erstellt und auf Intune synchronisiert haben, oder erstellen Sie diesen Gruppen manuell in die Intune-Verwaltungskonsole. Weitere Informationen zum Bereitstellen von Richtlinien Informationen finden Sie unter [Bereitstellen eine Konfigurationsrichtlinie](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Anhand der Status Zusammenfassung und Benachrichtigungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie** Erkennen von Problemen mit der Richtlinie, die Ihre Aufmerksamkeit erfordern. Außerdem wird ein Zusammenfassung Status im **Dashboard** -Arbeitsbereich ein.

> [!IMPORTANT]
> Wenn Sie keine Compliance-Richtlinie bereitgestellt haben und dann eine bedingte Zugriffsrichtlinie Exchange aktivieren, werden alle gezielte Geräte Zugriff gewährt werden.

## Wie Intune Richtlinie Konflikte gelöst werden
Konflikte Richtlinie können auftreten, Fälligkeitsdatum Wenn mehrere Intune-Richtlinien auf einem Gerät angewendet werden. Wenn die Richtlinieneinstellungen überlappen, aufgelöst Intune Konflikte mit den folgenden Regeln:

-   Wenn die in Konflikt stehenden Einstellungen aus einer Intune Konfigurationsrichtlinie und Compliance-Richtlinien sind, Vorrang die Einstellungen für die Compliance-Richtlinien der Einstellungen für die Richtlinie-Konfiguration, selbst wenn die Einstellungen für die Konfigurationsrichtlinie sicherer sind.

-   Wenn Sie mehrere Compliance-Richtlinien bereitgestellt haben, wird die sicherste diese Richtlinien verwendet werden.

## Überwachen Sie die Compliance-Richtlinien

#### Geräte anzeigen möchten, die nicht zu einer Richtlinie Vorschriften entsprechen

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), **Gruppen > alle Geräte**.

2.  Doppelklicken Sie auf den Namen des Geräts in der Liste der Geräte.

3.  Wählen Sie die Registerkarte **Richtlinie** , um eine Liste der Richtlinien für das Gerät anzuzeigen.

4.  Wählen Sie aus der Dropdownliste **Filter** **Compliance-Richtlinien nicht entsprechen**.
![Screenshot mit der Liste der Optionen in der Filterliste](./media/intune-sa-3e-view-device-noncompliance.png)

#### Zum Anzeigen der Bescheinigung-Berichte

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com) **Berichte**aus.

2.  Auf der Seite **Dienststatus Befähigungsnachweis Bericht - Erstellen eines neuen Berichts** können Sie einen Bericht alle 10 Windows Gesundheit Befähigungsnachweis gesammelten Daten werden von Intune anzeigen. Sie können auch einen Bericht mit einer Teilmenge der Daten mithilfe von Filtern erstellen. Die Filter können auf den Typ des Geräts, das Betriebssystem oder nur eine Teilmenge der Datenpunkte basieren.


## Nächste Schritte
Sie können jetzt die Compliance-Richtlinien mit bedingten Richtlinien verwenden, zum Steuern des Zugriffs auf Dienste in Ihrer Organisation.

[Beschränken Sie den Zugriff auf e-Mail und Office 365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


### Siehe auch
[Einführung in das Gerät Compliance Richtlinien in Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)
