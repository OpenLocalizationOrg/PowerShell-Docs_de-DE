---
title: "Mobiles Gerät Richtlinie Sicherheitseinstellungen | Microsoft Intune"
description: "Verwenden von Intune eine Vielzahl von Einstellungen konfiguriert werden, die Sie bereitstellen können verwaltete Geräte in Ihrer Organisation."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 04dec6046a54550070b4fec4622d134ec9ff94b3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Mobiles Gerät Richtlinie Sicherheitseinstellungen in Microsoft Intune
> [!IMPORTANT]
> Microsoft Intune jetzt Funktionen Konfigurationsrichtlinien für jede Geräteplattform zu trennen. Diese Richtlinien enthalten die aktuellsten Einstellungen, die Sie verwenden können. Sie können weiterhin die Sicherheitsrichtlinie mobiles Gerät verwenden, und einer beliebigen vorhandenen Bereitstellung funktionieren weiterhin. Jedoch sollten Sie planen, um die neue Konfigurationsrichtlinien so früh wie möglich migrieren, da die Richtlinie für mobile Geräte Sicherheit in Zukunft entfernt werden.

Intune Mobilgerät Sicherheitsrichtlinien können eine Vielzahl von Einstellungen konfiguriert werden, die auf verwalteten Geräte in Ihrer Organisation bereitgestellt werden kann. Diese Einstellungen werden verwendet, um die Funktionalität und Sicherheit Ihrer Geräte kontrollieren.

Sie können erstellen und Bereitstellen von mobilen Geräten Sicherheitsrichtlinien für die folgenden Gerätetypen:

-   Windows RT 8.1 und registrierten Windows 8.1-Geräte

-   Windows RT

-   Windows Phone 8 und Windows Phone 8.1

-   iOS

-   Android und Samsung KNOX

> [!NOTE]
> Einige Einstellungen sind nicht anwendbar auf einigen Geräten. Finden Sie unter den folgenden Tabellen eine vollständige Liste der Einstellungen, die Sie konfigurieren können.

## Sicherheitseinstellungen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Anfordern eines Kennworts zum Entsperren von mobiler Geräten**|Nein|Nein|Ja|Ja|Ja|
|**Kennwort geben erforderlich**<br /><br />Diese Einstellung gibt das Kennwort ein, die erforderlich sind, wie z. B. numerisch nur oder alphanumerische können.|Ja|Ja|Ja|Ja|Nein|
|**Geben Sie erforderliche Kennwort – minimale Anzahl von Zeichensätzen**<br /><br />Es gibt vier Zeichensätzen: Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole. Diese Einstellung gibt an, wie viele verschiedene Zeichen Datensätze im Kennwort enthalten sein müssen. Für iOS-Geräte gibt diese jedoch die Anzahl der Symbolzeichen, die im Kennwort enthalten sein müssen.|Ja|Ja|Ja|Ja|Nein|
|**Mindestlänge des Kennworts**|Ja|Ja|Ja|Ja|Ja|
|**Einfache Kennwörter zulassen**<br /><br />Einfache Kennwörter gehören '0000' und '1234'.|Nein|Nein|Ja|Ja|Nein|
|**Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird**|Ja|Ja|Ja|Ja|Ja|
|**Minuten nach der letzten, bevor der Bildschirm ausgeschaltet**<sup>1</sup>|Ja|Ja|Ja|Ja|Ja|
|**Kennwortablauf (Tage)**|Ja|Ja|Ja|Ja|Ja|
|**Denken Sie daran Kennwortverlauf**|Ja|Ja|Ja|Ja|Ja|
|**Speichern Kennwortverlauf** – **verhindern, dass Wiederverwendung von vorherigen Kennwörtern**|Ja|Ja|Ja|Ja|Ja|
|**Kennwort Qualität**|Nein|Nein|Nein|Nein|Ja|
|**Bild Kennwort und eine PIN zulassen**|Ja|Ja|Nein|Nein|Nein|
|**Minuten nach der letzten vor dem Kennwort erforderlich ist.**|Nein|Nein|Nein|Ja|Nein|
|**Zulassen von Fingerabdrucks Aufheben der Sperre**|Nein|Nein|Nein|iOS 7 und höher|Nein|
<sup>1</sup>für iOS-Geräte, wenn Sie die Einstellungen **inaktiv, bevor der Bildschirm ausgeschaltet** und **Minuten nach der letzten vor dem Kennwort erforderlich ist**, konfigurieren sie angewendet werden nacheinander. Beispielsweise wenn Sie den Wert für beide Einstellungen **5** Minuten festlegen, wird der Bildschirm automatisch nach 5 Minuten deaktivieren und das Gerät wird gesperrt nach einen zusätzlichen 5 Minuten. Wenn der Benutzer den Bildschirm manuell deaktiviert, wird die zweite Einstellung jedoch sofort angewendet. In diesem Beispiel Sperren des Geräts nach dem Bildschirm der Benutzer deaktiviert später 5 Minuten.

Wenn Sie eine Länge Kennwortrichtlinien Geräte, die Windows RT ausgeführt werden bereitstellen, werden Benutzer zum Zurücksetzen ihres Kennworts wird – selbst wenn das aktuelle Kennwort die Richtlinie Vorschriften erfüllt.

## Einstellungen für Verschlüsselung

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Vorschreiben von Verschlüsselung auf mobilen Geräten**<sup>1</sup><br /><br />Für Windows Phone 8-Geräte müssen Sie diese auf **Ja**festgelegt.<br /><br />Aktivieren Sie zum Aktivieren der Verschlüsselung auf iOS-Geräte die Einstellung **Anfordern eines Kennworts zum Entsperren von mobiler Geräten**aus.|Ja|Nein|Ja|Nein|Ja|
|**Verschlüsselung Speicherkarten erfordern**<br /><br />Diese Einstellung gilt für Geräte, die ebenfalls über Exchange ActiveSync verwaltet werden.|n/v|n/v|n/v <br />Apps und die zugeordneten Daten werden automatisch verschlüsselt.|n/v|Ja|
<sup>1</sup>Hier finden Sie zusätzliche Informationen für Geräte, die Windows 8.1 ausgeführt werden:

-   Enforce Verschlüsselung auf Geräten, die Windows 8.1 ausgeführt werden, installieren Sie die [Dezember 2014 MDM-Updates für Windows](http://support.microsoft.com/kb/3013816) auf jedem Gerät.

-   Wenn Sie diese Einstellung für Windows 8.1-Geräte aktivieren, müssen alle Benutzer des Geräts ein Microsoft-Konto.

-   Für die Verschlüsselung entwickelt muss das Gerät die Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) Hardware Zertifizierung erfüllen.

-   Wenn Sie die Verschlüsselung auf einem Gerät erzwingen, ist die Taste Wiederherstellung nur verfügbare des Benutzers Microsoft-Konto, das aus ihrem OneDrive-Konto zugegriffen werden kann. Dieser Taste im Auftrag eines Benutzers können nicht wiederhergestellt werden.

## Schadsoftware-Einstellungen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Netzwerk-Firewall erforderlich**|Ja|Nein|Nein|Nein|Nein|
|**Aktivieren Sie SmartScreen**|Ja|Nein|Nein|Nein|Nein|

## Systemeinstellungen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Vorschreiben von automatischen updates**|Ja|Nein|Nein|Nein|Nein|
|**Vorschreiben von automatischen Updates – Minimum Klassifizierung von Updates automatisch installieren.**<br /><br />Wählen Sie aus der Klassifizierung von Updates, die automatisch installiert werden:<br /><br />- **Wichtige**. Installiert alle Updates, die als wichtig klassifiziert werden.<br /><br />- **Empfohlen**. Installiert alle Updates, die als wichtig eingestuft sind oder empfohlen.|Ja|Nein|Nein|Nein|Nein|
|**Einen Bildschirmausschnitt zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja|Ja (Samsung KNOX nur)|
|**Neue Steuerzentrum in Sperrbildschirm zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Benachrichtigung anzeigen in Sperrbildschirm zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Zulassen von Sperrbildschirm Today anzeigen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Benutzerkontensteuerung**|Ja|Nein|Nein|Nein|Nein|
|**Senden von Diagnoseprotokollen Daten zulassen**|Ja|Nein|Nur Windows Phone 8.1|Ja|Ja (Samsung KNOX nur)|
|**Nicht vertrauenswürdige TLS-Zertifikate zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Zulassen von persönlichen Wallet Software während gesperrt**|Nein|Nein|Nein|Ja|Nein|
|**Zulassen von Factory zurücksetzen**|Nein|Nein|Nein|Nein|Ja (Samsung KNOX nur)|


## Cloud-Einstellungen – Dokumente und Daten

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Sicherung an einem iCloud zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Dokument-Synchronisierung mit iCloud zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Foto Stream Synchronisierung mit iCloud zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Verschlüsselte Sicherung erforderlich**|Nein|Nein|Nein|Ja|Nein|
|**Arbeit Ordner URL**<br /><br />Diese Einstellung legt die URL des Ordners Arbeit an, damit Dokumente auf Geräten synchronisiert werden.|Ja|Nein|Nein|Nein|Nein|
|**Zulassen von Google Sicherung**|Nein|Nein|Nein|Nein|Ja (Samsung KNOX nur)|

## Einstellungen der Cloud – Konten und Synchronisierung

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Zulassen von Microsoft-Konto**|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|
|**Synchronisieren von Google-Konto automatisch zulassen**|Nein|Nein|Nein|Nein|Ja (Samsung KNOX nur)|

## E-Mail-Einstellungen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Benutzerberechtigungen zum Herunterladen von e-Mail-Anlagen**<sup>1</sup>|n/v|n/v|n/v|n/v|n/v|
|**E-Mail-Synchronisierung Periode zurück** <br /><br />Diese Einstellung gilt für Geräte, die ebenfalls über Exchange ActiveSync verwaltet werden.|n/v|n/v|n/v|n/v|n/v|
|**Zulassen von mobilen Geräten, die nicht vollständig mit diesen Einstellungen für die Synchronisierung mit Exchange (Exchange ActiveSync) unterstützen** <br /><br />Diese Einstellung gilt für Geräte, die ebenfalls über Exchange ActiveSync verwaltet werden.|n/v|n/v|n/v|n/v|n/v|
|**Stellen Sie die Microsoft-Konto in Windows Mail Anwendung optional**|Ja|Nein|Nein|Nein|Nein|
|**Zulassen von benutzerdefinierten e-Mail-Konten**|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|

## Anwendungseinstellungen - Browser

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Webbrowser zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja|Ja (Samsung KNOX nur)|
|**Zulassen von AutoAusfüllen**|Ja|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Popupblocker zulassen**|Ja|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Zulassen von cookies**|Nein|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Zulassen-Plug-ins**|Ja|Nein|Nein|Nein|Nein|
|**Active scripting zulassen**|Ja|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Betrug Warnung zulassen**|Ja|Nein|Nein|Ja|Nein|
|**Intranetwebsite für einzelnes Wort Eintrag zulassen**<br /><br />(Diese Einstellung ermöglicht die Verwendung von Internet Explorer zu einer Website zu leiten ein einzelnes Wort – beispielsweise 'Bing'.)|Ja|Nein|Nein|Nein|Nein|
|**Automatische Erkennung von Intranetnetzwerk zulassen**|Ja|Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für Internet**|Ja|Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für intranet**|Ja|Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für vertrauenswürdige sites**|Ja|Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für eingeschränkte sites**|Ja|Nein|Nein|Nein|Nein|
|**Senden Sie nicht nachverfolgen Kopfzeile**|Ja|Nein|Nein|Nein|Nein|
|**Enterprise-Modus Menüzugriff zulassen**|Ja|Nein|Nein|Nein|Nein|
|**Enterprise-Modus Website Listenspeicherort**|Ja|Nein|Nein|Nein|Nein|

## Anwendungseinstellungen - apps

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Anwendungsspeicher zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja|Ja (Samsung KNOX nur)|
|**Festlegen eines Kennworts für Anwendungsspeicher zugreifen**|Nein|Nein|Nein|Ja|Nein|
|**In der app Einkäufe zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Verwaltete Dokumente in andere apps nicht verwalteten zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Ermöglicht es nicht verwalteten Dokumente in anderen verwalteten apps**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Videokonferenzen zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Medien Store für Erwachsene zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Zulassen der app-installation**|Nein|Nein|Nein|iOS 6 und höher|Nein|

## Anwendungseinstellungen - Spiele

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Spiel Center Freunde zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Spielen zulassen**|Nein|Nein|Nein|Ja|Nein|

## Funktionen des Audiogeräts - hardware

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kamera zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja|Ja|
|**Wechselmedien zulassen**|Nein|Nein|Ja|Nein|Ja (Samsung KNOX nur)|
|**Wi-Fi zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (Samsung KNOX nur)|
|**Wi-Fi tethering zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (Samsung KNOX nur)|
|**Zulassen Sie automatische Verbindung mit Wi-Fi-Hotspots frei**|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|
|**Wi-Fi-Hotspot reporting zulassen**<br /><br />Diese Einstellung sendet Informationen über WLAN-Verbindungen mit Hilfe der Umgebung Verbindungen zu ermitteln.|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|
|**Geografischen Standort zulassen**<br /><br />Diese Einstellung kann das Gerät Standortinformationen nutzen.|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (Samsung KNOX nur)|
|**NFK zulassen**<br /><br />Mit dieser Einstellung können Vorgänge, die in der Nähe Feld Kommunikation verwenden.|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (Samsung KNOX nur)|
|**Bluetooth zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (Samsung KNOX nur)|
|**Zulassen von Power deaktivieren**<br>Wenn diese Einstellung deaktiviert ist, ist die Einstellung **Anzahl wiederholten anmelden Fehler an, bevor das Gerät bereinigt ist** für Samsung KNOX Geräte nicht funktionsfähig.|Nein|Nein|Nein|Nein|Ja (Samsung KNOX nur)|

## Funktionen des Audiogeräts - Mobile

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**VoIP-roaming zulassen**|Nein|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Daten roaming zulassen**|Ja|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Automatische Synchronisierung beim roaming zulassen**|Nein|Nein|Nein|Ja|Nein|
|**Per SMS/MMS zulassen**|Nein|Nein|Nein|Nein|Ja (Samsung KNOX nur)|

## Funktionen des Audiogeräts - features

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**VoIP-Assistent zulassen**|Nein|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Zulassen Sie VoIP-Assistent, während das Gerät gesperrt ist**|Nein|Nein|Nein|Ja|Nein|
|**VoIP einwählen zulassen**|Nein|Nein|Nein|Ja|Ja (Samsung KNOX nur)|
|**Zulassen von kopieren und einfügen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (Samsung KNOX nur)|
|**Freigeben der Zwischenablage zwischen Clientanwendungen zulassen**|Nein|Nein|Nein|Nein|Ja (Samsung KNOX nur)|
|**YouTube zulassen**|Nein|Nein|Nein|Nein|Ja (Samsung KNOX nur)|

### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
