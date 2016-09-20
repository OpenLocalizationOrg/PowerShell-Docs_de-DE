---
title: "Access-Regeln für mobile Geräte Exchange | Microsoft Intune"
description: "Exchange ActiveSync Zugriff von Regeln zum Zulassen oder Sperren von Gerät Verbindungen mit EAS"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: c40978080967e3fb92aeb905218fd875e61e7efe
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Exchange Access Regeln für mobile Geräte
Exchange Access Regeln für mobile Geräte festlegen die Zugriffsebene, die diese Geräte mit Exchange ActiveSync aufweisen. Diese Einstellungen Einfluss auf allen mobilen Geräten, einschließlich der Empfänger, für die registriert werden nicht in Microsoft Intune. Sie können beginnen Sie damit, Definieren einer **Regel Standard**, die auf allen mobilen Geräten angewendet wird, die keine benutzerdefinierte Regel angewendet.

Die folgende Tabelle enthält die Zugriffsebenen, die von Exchange ActiveSync verwaltet werden:

|Zugriffsebene|Beschreibung|
|----------------|---------------|
|**Ermöglichen Sie die Geräte Zugriff auf Exchange**|Mobile Geräte können im Zustand *den Zugriff* über Exchange ActiveSync synchronisieren und Verbinden mit dem Exchange-Server zum Abrufen von e-Mail und Kalender, Kontakte, Aufgaben und Notizen verwalten. Dies wird fortgeführt, sofern das Gerät mit einem beliebigen Exchange ActiveSync-Postfachrichtlinie entspricht, die Sie in Exchange konfiguriert haben, wenn der Benutzer oder der bestimmten mobilen Gerät vom Exchange-Administrator blockiert wurde.|
|**Blockieren der Geräte aus den Zugriff auf Exchange**|Mobile Geräte in den Zustand *Zugriff blockieren* blockiert wurden, und sind nicht berechtigt, die Verbindung mit des Exchange-Servers. Geräte Fehlermeldung eine HTTP 403 Verboten. Der Benutzer erhält eine e-Mail-Nachricht aus dem Exchange-Server informieren, dass auf das mobile Gerät aus den Zugriff auf das Postfach gesperrt wurde. Diese Meldung kann nicht auf den blockierten Mobilgerät sein. Mithilfe der Aufgabe **Benutzer Benachrichtigung festlegen** , können Sie die angepassten Text hinzufügen, diese Nachricht Anweisungen für Benutzer bereitstellen, deren Geräte blockiert werden. |
|**Stellen Sie die Geräte in Quarantäne, damit Sie später zu blockieren oder zulassen können**|Wenn ein mobiles Gerät isoliert ist, ist das Mobilgerät Verbindung zum Exchange-Server zulässig. Es wird jedoch nur eingeschränkter Zugriff auf Daten gewährt. Der Benutzer kann Inhalte auf ihren eigenen Ordner Kalender, Kontakte, Aufgaben und Notizen hinzufügen, aber der Server ist nicht möglich das Gerät zum Abrufen von Inhalt aus dem Postfach des Benutzers. Der Benutzer erhält eine einzelne e-Mail-Nachricht, die besagt, dass das Mobilgerät isoliert wird. Diese Meldung wird das Gerät und das Postfach des Empfängers gesendet. Mithilfe der Aufgabe **Benutzer Benachrichtigung festlegen** , können Sie angepassten Text hinzufügen, um diese Meldung für die Anweisungen für Benutzer, deren Geräte in Quarantäne.|

Access-Strategie ist eine Kombination aus einer **Regel Standard** und **Plattform Ausnahmen** auf allen mobilen Geräten an, die mit Exchange verbunden sind. Der folgenden Tabelle sind einige Beispiel Access Strategien.

|Access-Strategie|Beschreibung|
|-------------------|---------------|
|Liste zulassen|Sie können eine *Liste der zugelassenen* gewähren des Zugriffs auf eine Liste der bekannten Geräte und Einschränken des Zugriffs für alle anderen Geräte. Dazu müssen Sie benutzerdefinierte Regeln für das Geräteplattformen erstellen, die auf dem Postfach eines Benutzers zugreifen dürfen. Sobald Sie eine solche Regel erstellen, müssen Sie die Regel zum Blockieren oder isolieren alle anderen Geräten Standard festlegen. Um der Zulassungsliste ein neues Gerät hinzuzufügen, erstellen Sie eine neue benutzerdefinierte Regel aus.|
|Liste blockierter Websites|Sie können eine *Sperrliste* verwenden, den Zugriff auf alle Geräte standardmäßig gewähren, sondern nur für eine Reihe von Geräten Zugriff blockieren, die nicht in Ihrer Organisation zugreifen sollen. Erstellen Sie eine Sperrliste durch Erstellen von benutzerdefinierten Regeln zum Blockieren Geräteplattformen, die nicht mit der Organisation Postfächer synchronisieren möchten. Es empfiehlt sich, Festlegen der Standard-Regel zu Zugriff auf alle Geräte, die nicht explizit von der vorhandenen Regeln blockiert werden. Um ein neues Gerät oder verschiedene Geräte Liste der blockierten hinzuzufügen, erstellen Sie eine neue benutzerdefinierte Regel.|
|Gemischte zulassen oder blockieren|Zusätzlich zur Erstellung eines zugelassene und blockierte Kontakte, Sie können neue mobile Geräte isolieren, wie sie in der Organisation eingeführt werden, während Sie diese ausgewertet werden soll. Wenn Sie eine Sperrliste für mobile Geräte, die nicht zulässig sind, innerhalb Ihrer Organisation und einer Zulassungsliste für mobile Geräte, die innerhalb der Organisation zulässig ist haben, können Sie die standardmäßigen Regel in Quarantäne stellen festlegen. Alle anderen Geräten werden automatisch unter Quarantäne gestellt. Auf diese Weise können Sie neue Geräte ermitteln, wie sie die Organisation eingeführt werden und entscheiden, ob die zulassen hinzufügen oder blockierte Kontakte.|
Das folgende Verfahren beschreibt das Erstellen einer benutzerdefinierten Regel.

## Erstellen einer Access-Standardzugriffsregel

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com), die **Richtlinie** &gt; **Exchange ActiveSync**.

2.  Wählen Sie in der Liste **Standard-Regel** die Regel, die auf allen mobilen Geräten anzuwenden, das durch eine Regel oder persönlichen steuerbefreiten abgedeckt werden nicht angezeigt werden soll. Wählen Sie **Speichern**aus.

Im folgenden wird beschrieben, wie Sie eine benutzerdefinierte Regel erstellen:

## Erstellen einer Regel benutzerspezifische

1. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com), die **Richtlinie** &gt; **Exchange ActiveSync**.

2.  In der **Plattform Ausnahmen** Liste auswählen **Regel hinzufügen**, und klicken Sie dann eine benutzerdefinierte Regel erstellen. Wählen Sie **Speichern**aus.
