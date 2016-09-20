---
title: "Verwalten von iOS Aktivierung Sperren auf Geräten | Microsoft Intune"
description: "Microsoft Intune helfen Ihnen die iOS Aktivierung sperren, eine Funktion der Suche mit meinem iPhone-app für iOS 7.1 oder höher verwalten."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 5cc03b724f8b9b00feb6bf693bd9b420c02e4ed3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Schützen Sie iOS, Geräte mit Aktivierung Sperren für Microsoft Intune umgehen
Microsoft-Intune helfen Ihnen die iOS Aktivierung sperren, eine Funktion der Suche mit meinem iPhone-app für iOS 8.0 oder höher verwalten. Aktivierung Sperren wird automatisch aktiviert, wenn ein Benutzer meine iPhone-app auf einem Gerät suchen wird geöffnet. Nachdem sie aktiviert ist, müssen Apple-ID und das Kennwort des Benutzers eingegeben werden, bevor Sie jeder kann: 

-   Suchen nach meinem iPhone deaktivieren

-   Löschen Sie das Gerät

-   Reaktivieren des Geräts

## Wie wirkt sich auf Aktivierung Sperren Sie
Während der Aktivierung Sperren hilft secure iOS-Geräte und erhöht die Chancen für ein Gerät Verlust oder Diebstahl wiederherstellen, kann diese Funktion, als IT-Administrator mit einer Reihe von Problemen präsentieren. Beispiel:

-   Ein Benutzer richtet Aktivierung Sperren auf einem Gerät. Der Benutzer dann bewirkt, dass das Unternehmen und das Gerät gibt. Ohne Apple-ID und das Kennwort des Benutzers gibt es Möglichkeit keine, das Gerät zu reaktivieren.

-   Sie benötigen einen Bericht zu allen Geräten, die Aktivierung Sperren aktiviert haben.

-   Einige Geräte in eine andere Abteilung während einer Aktualisierung Gerät in Ihrer Organisation neu zuweisen möchten. Sie können nur Geräte zuweisen, die keine Aktivierung Sperren aktiviert ist.

Um diese Probleme zu lösen, eingeführt Apple Aktivierung Sperren umgehen in iOS 7.1. So können Sie die Sperre für die Aktivierung von Kontrolle Geräte ohne Apple-ID und das Kennwort des Benutzers zu entfernen. Kontrolle Geräte können einen Geräte-spezifischen Aktivierung Sperren umgehen-Code generieren das auf Apple Aktivierungsserver gespeichert ist.

> [!TIP]
> Kontrolle Modus für iOS-Geräte können Sie die Apple-Konfiguration auf einem Gerät und Grenzwert Funktionen für die bestimmte geschäftliche Zwecke Sperren verwenden. Kontrolle Modus ist im Allgemeinen nur für Geräte Ihres Unternehmens gehören.

## Schutzmechanismen Intune Sie die Aktivierung Sperren verwalten
Intune kann die Aktivierung Sperrstatus Kontrolle und unbeaufsichtigt Geräte anfordern, die iOS 8.0 und höher ausgeführt werden. Für Kontrolle Geräte Intune rufen Sie den Code der Aktivierung Sperren umgehen, und es direkt mit dem Gerät ausgeben. Wenn das Gerät bereinigt wurde, können Sie das Gerät direkt mithilfe des Codes als den Benutzernamen und ein leeres Kennwort zugreifen.

**Sind die Vorteile von dies**:

-   Der Benutzer erhält Vorteile für die Sicherheit von meinem iPhone-app suchen.

-   Sie können die Benutzer ihre Arbeit und wissen, wenn Sie neue Aufgaben verwendet werden, können Sie zurückziehen oder Entsperren muss ein Gerät aktivieren.

## So umgehen der Aktivierung Sperren der Administrator Intune-Verwaltungskonsole verwenden
> [!IMPORTANT]
> Nachdem Sie die Aktivierung Sperre auf einem Gerät umgehen, wird automatisch eine neue Aktivierung Sperre angewendet, wenn das Suchen meinem iPhone-app geöffnet wird. Da dieser, **Sie sollten tatsächlich über das Gerät, bevor Sie dieses Verfahren ausführen**.

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), **Gruppen** &gt; **Alle Geräte** &gt; **Alle Corporate im Besitz Geräte**.

2.  Wählen Sie das Gerät, dessen Aktivierung Sperren umgehen soll. Wählen Sie die **Aktivierung Sperren umgehen**aus.

3.  Lesen Sie die Warnung angezeigt. Wählen Sie **Ja,** um den Vorgang fortzusetzen.

Sie können den Status der Anfrage entsperren auf der Detailseite für das Gerät überprüfen.

## Wie Sie sehen, welche Geräte Aktivierung Sperren verwenden
Sie können sehen, welche Geräte Aktivierung Sperren auf zwei Arten verwenden:

-   Führen Sie die **Mobilgerät Inventory Berichte**. Dieser Bericht zeigt die **Aktivierung Sperrstatus** und **Supervised** -Spalten, um den Status der Geräte an. Die Werte für **Supervised** **Ja** oder **Nein**, und die Werte für die **Aktivierung Sperrstatus** sind:

    -   Mit Umgehung Code aktiviert

    -   Ohne Code umgehen aktiviert (Gerät wird nicht überwacht.)

    -   Ohne Code umgehen aktiviert (Gerät nicht erreicht werden kann)

    -   Nicht aktiviert

    Das Feld **Sperren Aktivierungsstatus** ist leer für Geräte, die nicht iOS 8.0 oder höher ausgeführt werden.

-   Wählen Sie in einer Gruppenansicht, um die Aktivierung Sperrstatus im Detailbereich Gerät finden Sie unter ein Gerät.

    Wenn Sie ein Gerät im **Corporate alle im Besitz eines Geräte** -Knoten auswählen und Aktivierung Sperren für das Gerät aktiviert ist, können Sie auch den Umgehung Code anzeigen. Dieser Code kann verwendet werden, um manuell eine Aktivierung Sperre umgehen Problem.

    > [!IMPORTANT]
    >Intune nimmt eine Bestandsaufnahme von Geräten für die Aktivierung Sperren alle sieben Tage. Aus diesem Grund möglicherweise Geräte nicht sofort mit ihren Aktivierung Sperrstatus in der Intune Verwaltungskonsole angezeigt werden.


### Siehe auch
[Zurückziehen Geräte](retire-devices-from-microsoft-intune-management.md)
[Schützen Ihrer Geräte mit entfernten sperren und Kenncodes zurücksetzen](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)
