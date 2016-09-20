---
title: "Zurückziehen Geräte | Microsoft Intune"
description: "Intune unterstützt sowohl einer selektiven zurücksetzen und eine vollständige zurücksetzen So entfernen Sie das Gerät aus der Intune Verwaltung, indem Sie die Richtlinie und das Unternehmen Portal entfernen."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 93c8c07632c067fdb2eef221bc149fa7f6e9d495
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Zurückziehen Geräte aus der Intune-Verwaltung

Ob Geräte Ihres Unternehmens im Besitz oder persönlichen sind, kommt eine Uhrzeit, wann eine verwaltete Gerät aus der Verwaltung von Intune entfernt werden muss. Möglicherweise müssen Sie ein Gerät zu deaktivierte eine Vielzahl von Gründen:

-   Benutzer bewirkt, dass ein Unternehmen in einer geplanten Weise (Abweichung "verwaltete")
-   Benutzer plötzlich verlässt (wird ausgelöst, usw. abgebrochen.).
-   Verlust des Geräts
-   Wiederverwendung von einem Gerät (Verschieben an einen anderen Benutzer, Wiederverwendung für einen anderen Zweck usw.).

Sie können entweder eine selektiven Zurücksetzen ausführen oder eine vollständige Wischen Sie auf Geräten, die als mobile Geräte verwaltet oder ein Gerät sperren und das Kennwort zurücksetzen. Durch das Gerät Wischen freie das Abonnement des Benutzers ein anderes Gerät hinzufügen. Sie können auch mit der Intune-Clientsoftware verwaltete PCs zurückziehen.

## Wischen Sie Daten und apps von Geräten
Sowohl einer selektiven zurücksetzen und eine vollständige zurücksetzen können Sie das Gerät aus Intune Management entfernen, indem Sie die Richtlinie und im Portal Unternehmen, was bedeutet, dass das Gerät nicht mehr Unternehmensressourcen wie Microsoft SharePoint, e-Mail- oder Office 365 anmelden erforderlichen Anmeldeinformationen wurde entfernt.

[Wischen Sie selektive](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) ist die gewünschte Aktion für Mitarbeiter, die ihre eigenen Geräte in Intune registriert haben, da es nicht auf persönlichen Informationen auf dem Gerät auswirkt. Nur Unternehmensdaten werden entfernt.

Für Geräte, die verwendet werden, Sie können auch eine [vollständige zurücksetzen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)verwenden müssen, setzt die das Gerät Factory-Standardeinstellungen zurück.

## So löschen Sie Geräte in Azure Active Directory-portal

1.  Melden Sie sich mit Ihrer Organisation [http://aka.ms/accessaad](http://aka.ms/accessaad) oder [https://portal.office.com](https://portal.office.com) Anmeldeinformationen, und wählen Sie dann auf **Admin centers** &gt; **Azure AD**.

2.  Azure-Abonnement zu erstellen, wenn Sie dort noch keines besteht. Dies sollte nicht dauern eine Kreditkarte oder Zahlung, wenn Sie über ein kostenpflichtiges Konto verfügen (Wählen Sie den **Registrieren Ihrer kostenlosen Azure-Active Directory** -Abonnement-Link).

4.  Wählen Sie aus **Active Directory** , und wählen Sie dann Ihre Organisation.

5.  Wählen Sie die Registerkarte **Benutzer** .

6.  Wählen Sie den Benutzer, dessen Geräte, die Sie löschen möchten.

7.  Wählen Sie die **Geräte**aus.

8.  Wählen Sie die Geräte je nach Bedarf, und wählen Sie die **Geräte löschen**. Das Gerät wird das nächste Mal gelöscht werden, die, das Sie mit Active Directory synchronisiert. In diesem Fall in der Regel innerhalb von 4 Stunden. Nach dem synchronisieren, wird das Gerät aus der Verwaltung entfernt. Dadurch wird ein Gerät von der Beschränkung Gerät für diesen Benutzer entfernt.

## Zurückziehen verwaltete Computern
Computer verwaltet mit Intune-Clientsoftware aus der Verwaltung der Administrator Intune-Verwaltungskonsole entfernt werden kann. Dadurch auch die Clientsoftware deinstalliert und löscht Intune Richtlinie vom Computer. Zeigen Sie Informationen zu [Computern, die mit der Intune-Clientsoftware verwaltet zurückziehen](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## Zugriff blockieren ein Gerät
Wenn ein Gerät verloren oder wenn ein Gerät deaktiviert werden müssen, da ein Mitarbeiters Ihres Unternehmens ohne Eingabe eine Unternehmens Hardware nach links können Sie auch [Kenncode zurücksetzen und Remote Sperren](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) das Gerät. Auf diese Weise wird die Firmeninformationen aus verwendet werden kann, obwohl Sie möglicherweise schreiben das Gerät als Verlust deaktivieren.

Sie möchten die Lizenz des Mitarbeiters Intune Benutzerkonto widerrufen. Dadurch wird die Lizenz freigegeben, und Sie können ein neues Benutzerkonto zuweisen.

## Zurückziehen hardware
Manchmal ist es dem Gerät selbst, das das Ende seines Lebenszyklus erreicht hat. In diesem Fall mit einem vollständigen Wischen [sie Factory Einstellungen zurücksetzen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) entfernt alle Daten und das Gerät aus Intune. Klicken Sie dann können Sie die Hardware entsprechend der Richtlinie Ihres Unternehmens Zeitteil.

### Siehe auch
[Schützen von Daten mit vollständigen oder selektiven zurücksetzen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)
