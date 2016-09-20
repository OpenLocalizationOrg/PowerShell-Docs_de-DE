---
title: Windows Phone 8.1 Richtlinieneinstellungen | Microsoft Intune
description: "Intune stellt einen Zellbereich integrierte Allgemeine Einstellungen, die Sie, klicken Sie auf Windows Phone 8.1 Geräte konfigurieren können. Darüber hinaus können Sie angeben, OMA-URI-Werte, um benutzerdefinierte Einstellungen zu erstellen, die nicht von Intune verfügbar sind."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 315e492b301387c2030440e7188dfdb35a99ddd9
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Windows Phone 8.1 Richtlinieneinstellungen in Microsoft Intune

Intune stellt einen Bereich von integrierten Allgemeine Einstellungen, die Sie, klicken Sie auf Windows Phone 8.1 Geräte konfigurieren können. Darüber hinaus können Sie angeben, geöffneten Mobile Alliance Uniform Resource Identifier (URI-OMA) Werte, um benutzerdefinierte Einstellungen zu erstellen, die nicht von Intune verfügbar sind.

## Konfiguration von allgemeinen Einstellungen

Verwenden Sie die Microsoft Intune **Windows Phone-Konfiguration von allgemeinen Richtlinie (Windows Phone, 8.1 und höher)** so konfigurieren Sie die folgenden Einstellungen für Windows Phone 8.1 Geräte aus:

-   **Mobile gerätesicherheitseinstellungen** – auswählen aus einer Liste von vordefinierten Einstellungen, mit die Sie einen Zellbereich Features und Funktionen auf dem Gerät steuern können.

-   **Compliance-gerecht und nicht kompatible apps** - Geben Sie eine Liste der apps, die kompatibel oder in Ihrem Unternehmen nicht kompatibel sind. Windows Phone-Geräten können blockieren oder zulassen Installation von dieser apps.

### Anwendungsmöglichkeiten Einstellungen

|Name der Einstellung|Details|
|----------------|----------------------------------|
|**Alle Konfigurationen für Windows 10 anwenden**|Aktiviert die Einstellungen in dieser Richtlinie 10 unter Windows Mobile Geräte sowie Windows Phone 8.1 Geräte angewendet werden.|

### Kennworteinstellungen

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|------|-----|------------------------------|
|**Anfordern eines Kennworts zum Entsperren von mobiler Geräten**|Gibt an, ob Benutzer ein Kennwort zum Zugreifen auf ihre Geräte eingeben müssen.|Ja|Ja|
|**Kennwort geben erforderlich**|Gibt den Typ des Kennworts, die erforderlich sind, wie z. B. alphanumerischen oder numerischen nur bilden soll.|Ja|Ja|
|**Geben Sie erforderliche Kennwort – minimale Anzahl von Zeichensätzen**|Gibt an, wie viele verschiedene Zeichen Datensätze im Kennwort enthalten sein müssen. Es gibt vier Zeichensätzen: Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole. Für iOS-Geräte gibt diese jedoch die Anzahl der Symbole, die in das Kennwort enthalten sein müssen.|Ja|Ja|
|**Mindestlänge des Kennworts**|Gibt die minimale Anzahl von Zeichen, die erforderlich sind im Kennwort an.|Ja|Ja|
|**Einfache Kennwörter zulassen**|Gibt an, wie z. B. '0000' und '1234' einfache Kennwörter verwendet werden können.|Ja|Ja|
|**Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird**|Gibt die Anzahl der Häufigkeit, mit die ein falschen Kennwort eingegeben werden kann, bevor das Gerät bereinigt wird.|Ja|Ja|
|**Minuten nach der letzten, bevor der Bildschirm ausgeschaltet**|Gibt den Zeitraum an, die ein Gerät im Leerlauf bleiben muss, bevor der Bildschirm automatisch gesperrt ist.|Ja|Ja|
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage, bevor das Gerätekennwort geändert werden muss.|Ja|Ja|
|**Denken Sie daran Kennwortverlauf**|Gibt an, ob die zuvor verwendete Kennwörter erinnert werden, um zu verhindern, dass den Benutzer erneut zu verwenden.|Ja|Ja|
|**Speichern Kennwortverlauf** – **verhindern, dass Wiederverwendung von vorherigen Kennwörtern**|Gibt an, wie viele zuvor verwendete Kennwörter erinnert werden.|Ja|Ja|

### Einstellungen für Verschlüsselung

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|------|------|-----------------------------|
|**Vorschreiben von Verschlüsselung auf mobilen Geräten**|Erfordert, dass die Daten auf unterstützten mobilen Geräten verschlüsselt werden.<br>Für Windows Phone 8-Geräte müssen Sie diese auf **Ja**festgelegt.|Ja|Ja|

### Systemeinstellungen

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|------|------------------------------|
|**Einen Bildschirmausschnitt zulassen**|Kann der Benutzer den Inhalt des Bildschirms als Bilddatei zu erfassen.|Nein|Ja|
|**Senden von Diagnoseprotokollen Daten zulassen**|Ermöglicht das Gerät Diagnoseinformationen an Microsoft senden.|Nein|Ja|

### Einstellungen der Cloud – Konten und Synchronisierung

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|------|-----|------------------------------|
|**Zulassen von Microsoft-Konto**|Können ein Microsoft-Konto, das Gerät verknüpft werden soll.|Nein|Ja|

### E-Mail-Einstellungen

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|-----|-------------------------------|
|**Zulassen von benutzerdefinierten e-Mail-Konten**|Aktiviert das Gerät für die Verbindung zu Microsoft-fremden e-Mail-Konten.|Nein|Ja|

### Anwendungseinstellungen - Browser

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|-----|-------------------------------|
|**Webbrowser zulassen**|Ermöglicht wird oder den integrierten Webbrowser auf Geräte blockiert.|Nein|Ja|

### Anwendungseinstellungen - apps

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|------|------------------------------|
|**Anwendungsspeicher zulassen**|Ermöglicht Benutzern, die vom Gerät zum app Store zu verbinden.|Nein|Ja|

### Funktionen des Audiogeräts - hardware

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|----|--------------------------------|
|**Kamera zulassen**|Aktiviert oder des Geräts Kamera blockiert.|Nein|Ja|
|**Wechselmedien zulassen**|Ermöglicht das Gerät Wechselmedien wie SD-Karten verwenden.|Ja|Ja|
|**Wi-Fi zulassen**|Aktiviert oder deaktiviert die Wi-Fi-Funktionalität des Geräts.|Nein|Ja|
|**Wi-Fi tethering zulassen**|Ermöglicht die Verwendung von WLAN-tethering auf dem Gerät.|Nein|Ja
|**Zulassen Sie automatische Verbindung mit Wi-Fi-Hotspots frei**|Aktiviert das Gerät automatisch eine Verbindung herstellen, um frei Wi-Fi-Hotspots und alle Nutzungsbedingungen automatisch akzeptieren.|Nein|Ja|
|**Wi-Fi-Hotspot reporting zulassen**|Sendet Informationen über WLAN-Verbindungen mit Hilfe den Benutzer in der Nähe Verbindungen zu ermitteln.|Nein|Ja|
|**Geografischen Standort zulassen**|Aktiviert das Gerät Standortinformationen nutzen.|Nein|Ja|
|**NFK zulassen**|Ermöglicht die Vorgänge, die in der Nähe Feld Kommunikation verwenden.|Nein|Ja|
|**Bluetooth zulassen**|Aktiviert oder deaktiviert die Bluetooth-Funktionalität des Geräts.|Nein|Ja|

### Funktionen des Audiogeräts - features

|Name der Einstellung|Details|Windows Phone 8|Windows Phone 8.1|
|----------------|----|------|-------------------------------|
|**Zulassen von kopieren und einfügen**|Ermöglicht kopieren und Einfügen von Funktionen auf Geräten.|Nein|Ja|

### Einstellungen für den zugelassenen und blockierten apps
Geben Sie in der Liste **zulässige und blockierte apps** eine Liste der apps, die Sie zulassen oder sperren, indem Sie die folgenden Informationen möchten:

> [!NOTE]
> Eine einzelne Richtlinie kann nur eine Liste der zulässigen oder geblockten apps enthalten. Sie können keine beide in der gleichen Richtlinie angeben.

|Name der Einstellung|Details|
|----------------|--------------------|
|**Blockieren von Geräten Öffnens der aufgeführten apps**|Listen der apps, die nicht von Intune verwaltet werden und die Benutzer sind nicht, zulässig, installieren und ausführen.|
|**Ermöglichen Sie so installieren Sie nur die aufgelisteten apps Geräten**|Listet die apps, die Benutzer dürfen, zu installieren. Benutzer können keine anderen apps installieren. Apps, die vom Intune verwaltet werden sind automatisch zulässig.|
|**Hinzufügen**|Der ausgewählten Liste hinzugefügt eine app. Geben Sie einen Namen Ihrer Wahl, die URL der app im app Store, und die app Publisher (optional) ein. Weitere Hilfe finden Sie unter So URLs auf app-Speicher weiter unten in diesem Thema angeben.
|**Importieren von Apps**|Importiert eine Liste der apps, die Sie in eine CSV-Datei angegeben haben. Verwenden Sie das Format, Name der Anwendung, Publisher und app-URL in der Datei ein.|
|**Bearbeiten**|Können Sie die Namen, die Publisher sowie die URL der ausgewählten app bearbeiten.|
|**Löschen**|Löscht die ausgewählte app aus der Liste an.|
> [!IMPORTANT]
> Wenn Sie eine Liste der zulässigen apps für Windows Phone 8.1 Geräte angeben möchten, müssen Sie die app Unternehmen-Portal zu dieser Liste hinzufügen oder es blockiert werden.


### Referenzinformationen zu zulässig und blockierte apps

#### So URLs auf app-Speicher angeben.
Um eine app-URL in der Liste der zugelassenen und blockierten apps angeben möchten, verwenden Sie das folgende Format ein:

Suchen Sie auf der Seite [Für Windows Phone Apps + Spiele](http://www.windowsphone.com/en-us/store/overview) für die app, die Sie verwenden möchten.

Öffnen Sie des app Seite, und kopieren Sie die URL in die Zwischenablage. Jetzt können diese als die URL in einem die zulässigen oder geblockten apps-Liste.

**Beispiel:** Suchen Sie im Store für die Skype-app. Die URL, die Sie verwenden, werden **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## Benutzerdefinierte Richtlinieneinstellungen
Verwenden Sie die Microsoft Intune- **Richtlinie für Windows Phone benutzerdefinierte Konfiguration** OMA-URI-Einstellungen bereitstellen, die mit Funktionen auf **Windows Phone 8.1 Geräten**gesteuert werden kann. Dies sind die Standardeinstellungen, mit denen viele Mobilgerät Hersteller Features des Geräts steuern.

Diese Funktion können Sie Windows Phone-Einstellungen bereitstellen, die nicht mit einer Intune allgemeine Konfigurationsrichtlinie konfiguriert werden. Informationen über die Einstellungen, die Sie mit diesen Richtlinien konfigurieren können, finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Hilfe zum Erstellen von OMA-URI-Einstellungen für Windows Phone-Geräten finden Sie unter [Windows Phone 8.1 MDM Protokoll Dokumentation](http://technet.microsoft.com/library/dn499787.aspx).

### Allgemeine Einstellungen

|Name der Einstellung|Details|
|----------------|--------------------|
|**Namen**|Geben Sie einen eindeutigen Namen für die Richtlinie in der Verwaltungskonsole Intune erkennbar.|
|**Beschreibung**|Geben Sie eine Beschreibung, die bietet einen Überblick über die Richtlinie und weitere relevante Informationen, die Sie danach zu suchen kann.|

### OMA-URI-Einstellungen

Klicken Sie im Bereich **OMA-URI-Einstellungen** auf **Hinzufügen** , um eine Einstellung hinzugefügt. Sie können auch bearbeiten oder löschen eine vorhandene Einstellung.

Geben Sie im Dialogfeld **Hinzufügen oder Bearbeiten von OMA-URI-Einstellung** die folgenden Informationen ein:

|Name der Einstellung|Details|
    |--------|--------------------|
    |**Name der Einstellung**|Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung für die in der Liste der Einstellungen erkennbar.|
    |**Beschreibung der Einstellung**|Geben Sie eine Beschreibung, die bietet einen Überblick über die Einstellung und weitere relevante Informationen helfen Sie danach zu suchen.|
    |**Datentyp**|Wählen Sie den Datentyp, in dem Sie diese Einstellung OMA-URI angeben werden. Wählen Sie aus:<br /><br />-   **Zeichenfolge**<br />-   **Zeichenfolge (XML)**<br />-   **Datum und Uhrzeit**<br />-   **Ganze Zahl**<br />-   **Gleitkommazahl**<br />-   **Boolesch**|
    |**OMA-URI (Groß-/Kleinschreibung wird beachtet)**|Geben Sie den OMA-URI aus, für die Sie eine Einstellung angeben möchten.|
    |**Wert**|Geben Sie den Wert, mit dem OMA-URI zugeordnet werden soll, die Sie zuvor angegeben haben.|

### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
