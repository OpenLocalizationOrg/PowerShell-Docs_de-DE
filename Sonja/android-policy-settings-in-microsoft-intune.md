---
title: Android und Samsung KNOX Richtlinieneinstellungen | Microsoft Intune
description: "Erstellen Sie Richtlinien, die Einstellungen und Features für Android-Geräten, die mit Intune verwaltet steuern."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 870d735644f08e3eca8c72bca2b156947d798cb5
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Android und Richtlinieneinstellungen in Microsoft Intune Samsung KNOX

Intune stellt einen Bereich von integrierten Allgemeine Einstellungen, die Sie auf dem Android-Geräten konfigurieren können. Darüber hinaus können Sie angeben, geöffneten Mobile Alliance Uniform Resource Identifier (URI-OMA) Werte, um benutzerdefinierte Einstellungen zu erstellen, die nicht von Intune verfügbar sind.

## Von allgemeinen Konfigurationsrichtlinie

Verwenden Sie zum Konfigurieren der Einstellungen für Intune, **Android allgemeine Konfigurationsrichtlinie** ein:

-   **Mobile gerätesicherheitseinstellungen** - auswählen aus einer Liste von vordefinierten Einstellungen, mit denen Sie einen Zellbereich Features und Funktionen auf dem Gerät steuern können.

-   **Kiosk-Modus** Sperren Sie (für Samsung KNOX Geräte nur) – ein Gerät, um nur bestimmte Features entwickelt zulassen. Beispielsweise können Sie ein Gerät nur eine verwaltete app ausführen, die Sie angeben können, oder Sie können die Lautstärke Schaltflächen auf einem Gerät deaktivieren. Für ein Demomodell ein Gerät oder ein Gerät für die Durchführung nur eine Funktion, wie etwa ein POS-Gerät festgelegt ist, können diese Einstellungen verwendet werden.

-   **Compliance-gerecht und nicht kompatible apps** - Geben Sie eine Liste der apps, die kompatibel oder in Ihrem Unternehmen nicht kompatibel sind. Auf Android und iOS-Geräte kann **Nicht kompatible Apps Bericht** die Kompatibilität von apps anzeigen möchten, die Sie in der Liste anhand der apps angegeben haben, die Benutzer installiert haben verwendet werden. Der Bericht kann nicht die Installation von der app tatsächlich blockieren.

> [!TIP]
> Sie können die allgemeinen Geschäftsbedingungen für Benutzer, um sicherzustellen, dass sie bestätigen, dass alle apps Geräts, einschließlich persönlicher apps, ausgewertet werden und nicht kompatible apps entweder blockiert oder gemeldet werden als nicht kompatible konfigurieren. Benutzer müssen diese allgemeinen Geschäftsbedingungen zustimmen, bevor sie können Geräts zu registrieren und das Unternehmen Portal um apps zu erhalten. Weitere Informationen zur Verwendung von allgemeinen Geschäftsbedingungen finden Sie unter [Ausdrücke und Richtlinieneinstellungen in Microsoft Intune Bedingung](terms-and-condition-policy-settings-in-microsoft-intune.md).

Wenn Sie die Einstellung für gesuchte in diesem Thema nicht angezeigt wird, können Sie möglicherweise erstellen sie mithilfe einer Android benutzerdefinierten Richtlinie, in dem Sie die OMA-URI-Einstellungen verwenden, um das Gerät zu steuern kann. Weitere Informationen finden Sie auf [benutzerdefinierte Richtlinieneinstellungen](#custom-policy-settings) weiter unten in diesem Thema.

### Kennworteinstellungen

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Anfordern eines Kennworts zum Entsperren von mobiler Geräten**|Gibt an, ob ein Kennwort auf unterstützten Geräten erforderlich ist.|Ja|Ja|
|**Mindestlänge des Kennworts**|Gibt die Mindestlänge des Kennworts an.|Ja|Ja|
|**Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird**|Gibt die Anzahl der Anmeldung Fehler an, bevor das Gerät bereinigt wird.|Ja|Ja|
|**Minuten nach der letzten, bevor der Bildschirm ausgeschaltet**|Gibt die Anzahl der Minuten nach der letzten an, bevor Sie das Gerät automatisch gesperrt wurde.|Ja|Ja|
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage, bis ein Kennwort geändert werden muss.|Ja|Ja|
|**Denken Sie daran Kennwortverlauf**|Gibt die Anzahl der zuvor verwendete Kennwörter an.|Ja|Ja|
|**Denken Sie daran Kennwortverlauf** - **zu verhindern, dass Wiederverwendung von vorherigen Kennwörtern**|Verhindert, dass Wiederverwendung von vorherigen Kennwörtern.|Ja|Ja|
|**Kennwort Qualität**|Gibt das Kennwort Komplexität Ebene, die erforderlich ist und ob biometrische Geräte verwendet werden können.|Ja|Ja|
|**Zulassen von Fingerabdrucks Aufheben der Sperre**|Ermöglicht die Verwendung eines Fingerabdrucks zum Entsperren des Geräts an.|Nein|Ja|
|**Intelligentes sperren und andere Trust-Agents zulassen**<br>(Android-5 und höher)|Können Sie das Feature SmartArt Sperren mit kompatiblen Android-Geräten steuern. Diese Telefon-Funktion, manchmal bekannt als Agent vertrauen, können Sie die deaktivieren oder das Kennwort für das Gerät sperren Bildschirm umgehen, ist das Gerät an einem vertrauenswürdigen Speicherort (z. B. wenn er mit einem bestimmten Bluetooth-Gerät angeschlossen ist oder wenn es in der Nähe einer Kategorie NFK ist.) Sie können diese Einstellung verwenden, verhindern, dass Benutzer konfigurieren Smart sperren.|Ja|Nein|

### Einstellungen für Verschlüsselung

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|---|-------------|----------------|
|**Vorschreiben von Verschlüsselung auf mobilen Geräten**|Ist erforderlich, dass Dateien auf dem mobilen Gerät verschlüsselt werden.|Ja|Ja|
|**Vorschreiben von Verschlüsselung Speicherkarten**|Gibt an, ob die Karte Gerät Speicher verschlüsselt werden muss.|Nein|Ja|

### Systemeinstellungen

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|---|-------------|----------------|
|**Einen Bildschirmausschnitt zulassen**|Kann der Benutzer den Bildschirminhalt als Bild aufzeichnen.|Nein|Ja|
|**Senden von Diagnoseprotokollen Daten zulassen**|Ermöglicht das Gerät Diagnoseinformationen zu Google übermitteln.|Nein|Ja|
|**Zulassen von Factory zurücksetzen**|Ermöglicht dem Benutzer auszuführenden Factory auf dem Gerät zurücksetzen.|Nein|Ja|

### Cloud-Einstellungen - Dokumente und Daten

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|----|------------------------|----------------|
|**Zulassen von Google-Sicherung**|Ermöglicht die Verwendung von Google sichern.|Nein|Ja|

### Cloud-Einstellungen - Konten und Synchronisierung

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|-----|-----------|----------------|
|**Synchronisieren von Google-Konto automatisch zulassen**|Diese Berechtigung ermöglicht Gmail-Konten-Einstellungen automatisch synchronisiert werden.|Nein|Ja|

### Anwendungseinstellungen - Browser

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|-----|-----------|----------------|
|**Webbrowser zulassen**|Gibt an, ob der Standardwebbrowser des Geräts verwendet werden kann.|Nein|Ja|
|**Zulassen von AutoAusfüllen**|Ermöglicht die AutoAusfüllen-Funktion des Webbrowsers verwendet werden.|Nein|Ja|
|**Popupblocker zulassen**|Ermöglicht die Verwendung von den Popupblocker in einem Webbrowser.|Nein|Ja|
|**Zulassen von cookies**|Ermöglicht den Gerät Webbrowser Cookies verwendet.|Nein|Ja|
|**Active scripting zulassen**|Ermöglicht den Gerät Webbrowser active scripting verwenden.|Nein|Ja|

### Anwendungseinstellungen - apps

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|----|------------|----------------|
|**Zulassen von Google Play store**|Ermöglicht dem Benutzer den Google Play Store auf dem Gerät zugreifen.|Nein|Ja|

### Funktionen des Audiogeräts - hardware

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|-----|-----------|----------------|
|**Kamera zulassen**|Ermöglicht die Verwendung der Kamera Gerät.|Ja|Ja|
|**Wechselmedien zulassen**|Ermöglicht das Gerät Wechselmedien wie einer SD-Karte zu verwenden.|Nein|Ja|
|**Wi-Fi zulassen**|Ermöglicht die Verwendung der Wi-Fi-Funktionen des Geräts.|Nein|Ja|
|**Wi-Fi tethering zulassen**|Ermöglicht die Verwendung von WLAN-tethering auf dem Gerät.|Nein|Ja|
|**Geografischen Standort zulassen**|Ermöglicht das Gerät Standortinformationen nutzen.|Nein|Ja|
|**NFK zulassen**|Ermöglicht die Vorgänge, die in der Nähe Feld Kommunikation verwenden, wenn das Gerät unterstützt.|Nein|Ja|
|**Bluetooth zulassen**|Ermöglicht die Verwendung von Bluetooth auf dem Gerät.|Nein|Ja|
|**Zulassen von Power deaktivieren**|Ermöglicht es dem Benutzer zu schalten Sie das Gerät aus.<br /><br />Wenn diese Einstellung deaktiviert ist, ist die Einstellung **Anzahl der wiederholten anmelden Fehler an, bevor das Gerät bereinigt ist** für Samsung KNOX Geräte nicht funktionsfähig.|Nein|Ja|

### Funktionen des Audiogeräts - Mobile

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|---|-------------|----------------|
|**VoIP roaming zulassen**|Diese Berechtigung ermöglicht VoIP roaming, wenn das Gerät in einem Netzwerk Mobile ist.|Nein|Ja|
|**Daten roaming zulassen**|Können Daten roaming, wenn das Gerät in einem Netzwerk Mobile ist.|Nein|Ja|
|**Per SMS/MMS zulassen**|Ermöglicht die Verwendung von SMS und MMS messaging auf dem Gerät.|Nein|Ja|

### Funktionen des Audiogeräts - features

|Name der Einstellung|Details|Android 4.0 +|Samsung KNOX|
|----------------|----|------------|----------------|
|**VoIP-Assistent zulassen**|Ermöglicht die Verwendung von VoIP-Assistent-Software auf dem Gerät.|Nein|Ja|
|**VoIP einwählen zulassen**|Aktiviert oder deaktiviert die Voicemail DFÜ-Funktion auf dem Gerät.|Nein|Ja|
|**Zulassen von kopieren und einfügen**|Mit der kopieren und Einfügen von Funktionen auf dem Gerät.|Nein|Ja|
|**Freigeben der Zwischenablage zwischen Clientanwendungen zulassen**|Ermöglicht die Verwendung der Zwischenablage kopieren und Einfügen zwischen apps.|Nein|Ja|
|**Zulassen von YouTube**|Ermöglicht die Verwendung von YouTube auf dem Gerät.|Nein|Ja|

### Einstellungen für kompatible und nicht kompatible apps
In der **kompatibel &amp; nicht kompatible Apps** Liste, geben Sie eine Liste der kompatiblen oder nicht kompatibel apps, die die folgende Informationen verwenden:

> [!NOTE]
> Eine einzelne Richtlinie kann nur eine Liste der kompatiblen apps oder eine Liste der nicht kompatiblen apps enthalten. Sie können keine beide in der gleichen Richtlinie angeben.

|Name der Einstellung|Details|
|----------------|--------------------|
|**Melden Sie bei nicht-Konformität, wenn der Benutzer der aufgeführten apps installieren**|Listet die apps, die nicht von Intune verwaltet werden und nicht möchten, dass Benutzer zum Installieren und ausführen. Wenn der Benutzer eine der folgenden apps installiert haben, wird es im Bericht nicht kompatible apps aufgeführt sein.|
|**Melden Sie bei der Installation von Benutzern der aufgeführten apps nicht bei nicht-Konformität**|Listet die apps, die Sie zulassen möchten. Um kompatibel bleiben, müssen Benutzer keine apps installieren, die nicht aufgelistet werden. Apps, die vom Intune verwaltet werden sind automatisch zulässig.|
|**Hinzufügen**|Der ausgewählten Liste hinzugefügt eine app. Geben Sie den Namen der app, die app Publisher (optional) und die URL der app im app Store.<br /><br />Weitere Informationen hierzu finden Sie unter [angeben URLs mit speichert](#specify-urls-to-app-stores) weiter unten in diesem Thema.|
|**Importieren von Apps**|Importiert eine Liste der apps, die Sie in eine CSV-Datei angegeben haben. Verwenden Sie das Format, Name der Anwendung, Publisher und app-URL in der Datei ein.|
|**Bearbeiten**|Können Sie die Namen, die Publisher sowie die URL der ausgewählten app bearbeiten.|
|**Löschen**|Löscht die ausgewählte app aus der Liste an.|

### Einstellungen für Kiosk-Modus
Geben Sie die folgenden Einstellungen für **Samsung KNOX Geräte**:

|Name der Einstellung|Details|
|----------------|--------------------|
|**Wählen Sie eine verwaltete app, die ausgeführt werden kann, wenn das Gerät im Kioskmodus ist.**|Wählen Sie **Durchsuchen**, und wählen Sie dann auf die verwaltete app, die ausgeführt werden kann, wenn das Gerät befindet sich im Kioskmodus (apps, wie Sie ein Link zu den Store werden derzeit nicht unterstützt angegeben). Keine andere apps dürfen auf dem Gerät ausgeführt werden.|
|**Schaltflächen zum Zulassen**|Aktiviert oder deaktiviert die Verwendung der Schaltflächen Lautstärke auf dem Gerät.|
|**Bildschirm Standby-Aktivierungstaste zulassen**|Aktiviert oder deaktiviert die Bildschirm Standby Aktivierung-Taste auf dem Gerät.|

### Referenzinformationen für kompatible und nicht kompatible apps

#### Überwachen der apps kompatible und nicht kompatible
**Nicht kompatible Apps Bericht** können die Kompatibilität der anzeigen zulässig und apps blockiert.

###### Zum Ausführen des Berichts für nicht kompatible Apps

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), **Berichte** &gt; **Nicht kompatible Apps Bericht**.

2.  Wählen Sie die Gerätegruppen, die Sie überprüfen möchten. Wählen Sie, ob Sie kompatible apps, apps nicht kompatible oder beides prüfen möchten. Wählen Sie schließlich **Bericht anzeigen**aus.

#### Geben Sie die URLs auf app-Speicher
Wenn Sie eine app-URL in der Liste kompatible und nicht kompatible apps angeben, gehen Sie folgendermaßen vor:

Suchen Sie im [Abschnitt Google Play Apps](https://play.google.com/store/apps)für die app, die Sie verwenden möchten.

Öffnen Sie die Installationsseite für die app, und klicken Sie dann kopieren Sie die URL in die Zwischenablage. Jetzt können diese als die URL übertragen kompatibel oder nicht kompatibel apps-Liste.

Beispiel: Suche Google Play für Microsoft Office Mobile. Die URL, die Sie verwenden werden **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## Benutzerdefinierte Richtlinieneinstellungen
Verwenden Sie Microsoft Intune, **Android benutzerdefinierte Konfigurationsrichtlinie** OMA-URI-Einstellungen bereitstellen, die zur Steuerung der Funktionen Android-Geräten verwendet werden können. Dies sind die Standardeinstellungen, mit denen viele Mobilgerät Hersteller Features des Geräts steuern.

Diese Funktion soll ermöglichen es Ihnen, Android Einstellungen bereitstellen, die nicht mit Intune-Richtlinien konfiguriert sind.

> [!NOTE]
> Derzeit unterstützt Android benutzerdefinierte Richtlinien nur Konfigurieren von WLAN-Einstellungen für Android-Geräten, die einen vorinstallierten Schlüssel enthalten.

### Allgemeine Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Namen**|Geben Sie einen eindeutigen Namen für die benutzerdefinierte Android Richtlinie in der Verwaltungskonsole Intune erkennbar.|
    |**Beschreibung**|Stellen Sie eine Beschreibung, die bietet einen Überblick über die Android benutzerdefinierte Richtlinie und weitere relevante Informationen, die Sie danach zu suchen kann.|

### OMA-URI-Einstellungen

   |Name der Einstellung|Details|
    |--------|--------------------|
    |**Name der Einstellung**|Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung für die in der Liste der Einstellungen erkennbar.|
    |**Beschreibung der Einstellung**|Geben Sie eine Beschreibung, die bietet einen Überblick über die Einstellung und weitere relevante Informationen helfen Sie danach zu suchen.|
    |**Datentyp**|Wählen Sie den Datentyp, in dem Sie diese Einstellung OMA-URI angeben werden. Wählen Sie aus der **Zeichenfolge, Zeichenfolge (XML), Datum und Uhrzeit, ganze Zahl, Gleitkommazahl**oder **Boolean**.|
    |**OMA-URI (Groß-/Kleinschreibung wird beachtet)**|Geben Sie den OMA-URI-eine Einstellung für bereitstellen möchten.|
    |**Wert**|Geben Sie den Wert, mit dem OMA-URI zugeordnet werden soll, die Sie zuvor angegeben haben.|

### Beispiele

- [Erstellen Sie Wi-Fi Profil mit einem vorinstallierten Schlüssel](pre-shared-key-wi-fi-profile.md)
- [Verwenden einer benutzerdefinierten Richtlinie zum Erstellen eines pro-app VPN Profils für Android-Geräten](per-app-vpn-for-android-pulse-secure.md)
- [Verwenden Sie benutzerdefinierte Richtlinien zum Zulassen oder apps für Samsung KNOX Geräte blockieren](custom-policy-to-allow-and-block-samsung-knox-apps.md)

### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
