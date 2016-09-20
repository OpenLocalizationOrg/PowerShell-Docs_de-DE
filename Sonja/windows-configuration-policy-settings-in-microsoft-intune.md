---
title: Windows-Richtlinieneinstellungen | Microsoft Intune
description: "Verwenden Sie die Richtlinie für Intune Windows-Konfiguration von allgemeinen (Windows 8.1 und höher), um Einstellungen für registrierten Windows 8 und Windows 8.1-Geräte konfigurieren."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: b02804f933f8c259ea12efefd0353a7d5ceda25c
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Richtlinieneinstellungen Windows Intune Microsoft
Verwenden Sie die Microsoft Intune **Windows allgemeine Konfigurationsrichtlinie (Windows 8.1 und höher)** so konfigurieren Sie die folgenden Einstellungen für registrierten Windows 8 und Windows 8.1 Geräte aus:

## Anwendungsmöglichkeiten Einstellungen

|Name der Einstellung|Details|
|----------------|----------------------------------|
|**Alle Konfigurationen für Windows 10 anwenden**|Aktiviert die Einstellungen in dieser Richtlinie Windows 10 Geräten zusätzlich zu Windows 8 und Windows 8.1-Geräten angewendet werden.|

## Sicherheitseinstellungen

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**Kennwort geben erforderlich**|Gibt den Typ des Kennworts, die erforderlich ist, wie z. B. alphanumerischen oder numerischen nur an.|Ja|Ja|
|**Geben Sie erforderliche Kennwort – minimale Anzahl von Zeichensätzen**|Gibt an, wie viele verschiedene Zeichen Datensätze im Kennwort enthalten sein müssen. Es gibt vier Zeichensätzen: Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole. Für iOS-Geräte gibt diese Einstellung jedoch die Anzahl der Symbole, die in das Kennwort enthalten sein müssen.|Ja|Ja|
|**Mindestlänge**<sup>1</sup>|Konfiguriert die erforderliche Mindestlänge (in Zeichen) für das Kennwort ein.|Ja|Ja|
|**Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird**|Löscht das Gerät an, wenn die Anmeldung Versuche, diese Anzahl, wie oft fehl.|Ja|Ja|
|**Minuten nach der letzten, bevor der Bildschirm ausgeschaltet**|Gibt die Anzahl der Minuten, die ein Gerät im Leerlauf sein muss, bevor ein Kennwort zum Entsperren erforderlich ist.| Ja|Ja|
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage, bevor das Gerätekennwort geändert werden muss.|Ja|Ja|
|**Denken Sie daran Kennwortverlauf**|Gibt an, ob der Benutzer zuvor verwendete Kennwörter konfigurieren kann.|Ja|Ja|
|**Speichern Kennwortverlauf** – **verhindern, dass Wiederverwendung von vorherigen Kennwörtern**|Gibt die Anzahl der zuvor verwendeten Kennwörter, die vom Gerät gedacht sind.|Ja|Ja|
|**Bild Kennwort und eine PIN zulassen**|Ermöglicht die Verwendung eines Bilds Kennwort und PIN. Ein Bild Kennwort ermöglicht den Benutzer melden Sie sich mit Gesten auf ein Bild. Eine PIN ermöglicht Benutzern, schnell mit einer vierstelligen Code signieren.|Ja|Ja|
<sup>1</sup> beim Bereitstellen einer Länge Kennwortrichtlinien für Geräte, die Windows RT ausgeführt werden, Benutzer werden zwangsweise ihre Kennwörter zurücksetzen, auch wenn die Richtlinie Vorschriften das aktuelle Kennwort erfüllt.

## Einstellungen für Verschlüsselung

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Vorschreiben von Verschlüsselung auf mobilen Geräten**<sup>1</sup>|Erfordert, dass Dateien auf dem Gerät verschlüsselt werden.<br>Für Windows Phone 8-Geräte müssen Sie diese auf **Ja**festgelegt.|Ja|Nein|
<sup>1</sup> zusätzliche Informationen für Geräte, die Windows 8.1 ausgeführt werden.

-   Enforce Verschlüsselung auf Geräten, die Windows 8.1 ausgeführt werden, müssen Sie Installieren der [Dezember 2014 MDM-Updates für Windows](http://support.microsoft.com/kb/3013816) auf jedem Gerät.

-   Wenn Sie diese Einstellung für Windows 8.1-Geräte aktivieren, müssen alle Benutzer des Geräts ein Microsoft-Konto.

-   Für die Verschlüsselung entwickelt muss das Gerät die Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) Hardware Zertifizierung erfüllen.

-   Wenn Sie die Verschlüsselung auf einem Gerät erzwingen, ist die Taste Wiederherstellung nur verfügbare des Benutzers Microsoft-Konto, das aus ihrem OneDrive-Konto zugegriffen werden kann. Dieser Taste im Auftrag eines Benutzers können nicht wiederhergestellt werden.

## Schadsoftware-Einstellungen

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Netzwerk-Firewall erforderlich**|Erfordert, dass die Windows-Firewall aktiviert ist.|Ja|Nein|
|**Aktivieren Sie SmartScreen**|Erfordert die Verwendung von Windows SmartScreen.|Ja|Nein|

## Systemeinstellungen

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|-------|---------------------------|--------------|
|**Automatische Updates erforderlich**|Aktiviert die automatische Updates auf Geräten festlegen.|Ja|Nein|
|**Vorschreiben von automatischen Updates – Minimum Klassifizierung von Updates automatisch installieren.**|Wählt die Klassifizierung von Updates, die automatisch installiert werden:<br /><br />-   **Wichtig** – installiert alle Updates, die als wichtig klassifiziert werden.<br />-   **Empfohlen** – installiert alle Updates, die als wichtig eingestuft sind oder empfohlen.|Ja|Nein|
|**Benutzerkontensteuerung**|Erfordert die Verwendung der Benutzerkontensteuerung (UAC) auf Geräten.|Ja|Nein|
|**Senden von Diagnoseprotokollen Daten zulassen**|Ermöglicht das Gerät Diagnoseinformationen an Microsoft senden.|Ja|Nein|


## Cloud-Einstellungen – Dokumente und Daten

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**Arbeit Ordner URL**|Legt die URL des Ordners Arbeit an, damit Dokumente auf Geräten synchronisiert werden.|Ja|Nein|

## E-Mail-Einstellungen

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Stellen Sie die Microsoft-Konto in Windows Mail Anwendung optional**|Ermöglicht den Zugriff auf die Windows Mail-Anwendung, ohne ein Microsoft-Konto.|Ja|Nein|

## Anwendungseinstellungen - Browser

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Zulassen von AutoAusfüllen**|Ermöglicht Benutzern das AutoVervollständigen-Einstellungen im Browser zu ändern.|Ja|Nein|
|**Popupblocker zulassen**|Aktiviert oder deaktiviert den Popupblocker des Browsers.|Ja|Nein|
|**Zulassen-Plug-ins**|Ermöglicht Benutzern, die Internet Explorer-Plug-ins hinzufügen.|Ja|Nein|
|**Active scripting zulassen**|Ermöglicht Browser Skripts, wie ActiveX-Skripts ausführen.|Ja|Nein|
|**Betrug Warnung zulassen**|Aktiviert oder deaktiviert Warnungen für potenzielle gefälschte Websites.|Ja|Nein|
|**Intranetwebsite für einzelnes Wort Eintrag zulassen**|Aktiviert die Verwendung von ein einzelnes Wort in Internet Explorer zu einer Website, wie z. B. Bing direkte.|Ja|Nein|
|**Automatische Erkennung von Intranetnetzwerk zulassen**|Hilft, Sicherheit für Intranet-Websites in Internet Explorer zu konfigurieren.|Ja|Nein|
|**Sicherheitsstufe für Internet**|Legt die Sicherheitsstufe von Internet Explorer für Internetsites an.|Ja|Nein|
|**Sicherheitsstufe für intranet**|Legt die Sicherheitsstufe von Internet Explorer für Intranet-Websites.|Ja|Nein|
|**Sicherheitsstufe für vertrauenswürdige sites**|Konfiguriert die Sicherheitsstufe für die Zone vertrauenswürdige Sites.|Ja|Nein|
|**Sicherheitsstufe für eingeschränkte sites**|Konfiguriert die Sicherheitsstufe für eingeschränkte Sites.|Ja|Nein|
|**Senden Sie die Kopfzeile nicht nachverfolgen**|Führen Sie eine sendet Kopfzeile besuchten Websites in Internet Explorer nicht nachverfolgen.|Ja|Nein|
|**Enterprise-Modus Menüzugriff zulassen**|Ermöglicht Benutzern, die Menüoptionen für die Enterprise-Modus von Internet Explorer zugreifen.<br>Wenn Sie diese Einstellung auswählen, können Sie auch eine **Protokollierung Speicherort des Berichts**, angeben, die eine URL zu einem Bericht, die Websites anzeigt enthält, für die Enterprise-Modus Access Benutzer aktiviert haben.|Ja|Nein|
|**Enterprise-Modus Website Listenspeicherort**|Gibt den Speicherort der Liste der Websites, für die Enterprise-Modus verwendet wird, wenn es aktiv ist.|Ja|Nein|

## Funktionen des Audiogeräts - Mobile

|Name der Einstellung|Details|Windows 8.1 und Windows RT 8.1|Windows RT|
|----------------|----|------------------------------|--------------|
|**Daten roaming zulassen**|Ermöglicht das roaming, wenn das Gerät in einem Netzwerk Mobile Daten.|Ja|Nein|



### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
