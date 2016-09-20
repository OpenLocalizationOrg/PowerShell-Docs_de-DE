---
title: Exchange ActiveSync-Richtlinieneinstellungen | Microsoft Intune
description: "Verwenden Sie der Intune Exchange ActiveSync-Richtlinie zum Konfigurieren der Einstellungen, mit denen Sie die Features und Funktionen auf Geräten, die von Exchange ActiveSync verwaltet steuern können."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 21f4e16787a3f5aa1970fbf7d22214018bc8c69c
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Exchange ActiveSync-Richtlinieneinstellungen in Microsoft Intune
Verwenden Sie die Intune Microsoft **Exchange ActiveSync** -Richtlinie Einstellungen konfiguriert werden, die steuern, einen Zellbereich Features und Funktionen auf Geräten, die von Exchange ActiveSync verwaltet werden.


## Kennworteinstellungen

|Name der Einstellung|Details
|----------------|---|
|**Anfordern eines Kennworts zum Entsperren von mobiler Geräten**|Gibt an, ob Geräte mit einem Kennwort gesperrt werden müssen.<br>(gilt nicht für Geräte mit Windows RT).|
|**Kennwort geben erforderlich**|Gibt den Typ des Kennworts, die erforderlich sind, wie z. B. numerisch nur oder alphanumerische bilden soll.|
|**Mindestlänge des Kennworts**|Gibt die minimale Anzahl von Zeichen in das Kennwort für das Gerät an.|
|**Einfache Kennwörter zulassen**|Gibt an, ob Sie einfache Kennwörter verwenden können, die welche '0000' enthalten und '1234'.|
|**Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird**|Gibt an, wie oft, die ein Benutzer ein falschen Kennwort eingeben können, bevor das Gerät bereinigt wird.|
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage nach denen Kennwort für das Gerät geändert werden muss.
|**Denken Sie daran Kennwortverlauf**|Gibt an, ob die Verwendung der zuvor verwendete Kennwörter nicht zulässig.|
|**Speichern Kennwortverlauf** – **verhindern, dass Wiederverwendung von vorherigen Kennwörtern**|Gibt die Anzahl der zuvor verwendete Kennwörter, die nicht erneut verwendet werden kann.|
|**Minuten nach der letzten vor dem Kennwort erforderlich ist.**|Gibt die Zeitdauer, die ein Gerät im Leerlauf sein muss, bevor der Bildschirm gesperrt ist.

## Einstellungen für Verschlüsselung

|Name der Einstellung|Details|
|----------------|---|
|**Vorschreiben von Verschlüsselung auf mobilen Geräten**<sup>1</sup>|Erfordert die Daten auf einem Gerät verschlüsselt werden, wenn unterstützt.<br><br>Für Windows Phone 8-Geräte müssen Sie diese auf **Ja**festgelegt.<br /><br />Aktivieren Sie zum Aktivieren der Verschlüsselung auf iOS-Geräte die Einstellung **Anfordern eines Kennworts zum Entsperren von mobiler Geräten** aus.|
|**Vorschreiben von Verschlüsselung Speicherkarten**|Erfordert die Daten, die auf externen Speicher, wie etwa einer SD-Karte (auf unterstützten Geräten) verschlüsselt werden gespeichert ist.
<sup>1</sup> zusätzliche Informationen für Geräte, die Windows 8.1 ausgeführt werden.

-   Wenn Sie Verschlüsselung auf Geräten erzwingen, Ausführen von Windows 8.1 installieren müssen möchten die [Dezember 2014 MDM-Updates für Windows](http://support.microsoft.com/kb/3013816) auf jedem Gerät.

-   Wenn Sie diese Einstellung für Windows 8.1-Geräte aktivieren, müssen alle Benutzer des Geräts ein Microsoft-Konto.

-   Wenn Sie Verschlüsselung für Windows 8.1 Geräte arbeiten möchten, muss das Gerät die Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) Hardware Zertifizierung erfüllen.

-   Wenn Sie Verschlüsselung auf einem Windows 8.1-Gerät erzwingen, zugegriffen werden die Taste Wiederherstellung nur von des Benutzers Microsoft-Konto, das aus dem Benutzerkonto OneDrive zugegriffen werden kann. Dieser Taste im Auftrag eines Benutzers können nicht wiederhergestellt werden.

## E-Mail-Einstellungen

|Name der Einstellung|Details
|----------------|---|
|**Benutzerberechtigungen Sie zum Herunterladen von e-Mail-Anlagen**|Gibt an, ob der e-Mail-Anlagen auf das Gerät heruntergeladen werden können.|
|**E-Mail-Synchronisierung Periode zurück**|Gibt die Anzahl der Tage der empfangenen e-Mails, die mit dem Gerät synchronisiert werden.
|**Zulassen von mobilen Geräten, die nicht vollständig mit Exchange ActiveSync-Einstellungen für die Synchronisierung mit Exchange unterstützen**|Gibt an, ob Exchange Zugriff auf Geräten ermöglichen, die eine oder mehrere Exchange ActiveSync-Einstellungen nicht unterstützen.

## Browsereinstellungen

|Name der Einstellung|Details
|----------------|---|
|**Webbrowser zulassen**|Gibt an, ob der Webbrowser auf dem Gerät verwendet werden kann.<br>(Nicht verfügbar für Windows RT oder Windows Phone).

## Hardwareeinstellungen

|Name der Einstellung|Details
|----------------|---|
|**Kamera zulassen**|Gibt an, ob die Kamera auf dem Gerät verwendet werden kann.<br>(Nicht verfügbar für Windows RT oder Windows Phone).



### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
