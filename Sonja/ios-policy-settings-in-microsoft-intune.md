---
title: iOS Richtlinieneinstellungen | Microsoft Intune
description: "Erstellen Sie Richtlinien, die Einstellungen und Funktionen, die mit Intune verwaltet iOS-Geräte steuern."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 24540a74ce98adbf3f908cbea401328f027867ca
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# iOS-Richtlinieneinstellungen in Microsoft Intune

Intune stellt einen Bereich von integrierten Allgemeine Einstellungen, die Sie, klicken Sie auf iOS-Geräte konfigurieren können. Darüber hinaus können Sie das Tool Apple-Konfiguration zum Erstellen von benutzerdefinierter Einstellungen, die nicht von Intune verfügbar sind.

## Allgemeine Konfiguration Richtlinieneinstellungen

Verwenden Sie die Microsoft Intune **iOS allgemeine Konfigurationsrichtlinie** zum Konfigurieren der Einstellungen für ein:

-   **Allgemeine Gerät und Sicherheitseinstellungen**. Wählen Sie aus einer Liste von vordefinierten Einstellungen, mit die Sie eine Reihe von Features und Funktionen auf dem Gerät steuern können.

-   **Kiosk-Modus**. Sperren Sie ein Gerät aus, um nur bestimmte Features arbeiten zu ermöglichen. Beispielsweise können Sie ein Gerät nur eine verwaltete app ausführen, die Sie angeben können, oder Sie können die Lautstärke Schaltflächen auf einem Gerät deaktivieren. Für ein Demomodell ein Gerät oder ein Gerät für die Durchführung nur eine Funktion, wie etwa ein POS-Gerät festgelegt ist, können diese Einstellungen verwendet werden.

-   **Compliance-gerecht und apps nicht kompatibel**. Geben Sie eine Liste der apps, die kompatibel oder in Ihrem Unternehmen nicht kompatibel sind. Auf Android und iOS-Geräte kann **Nicht kompatible Apps Bericht** die Kompatibilität von apps anzeigen möchten, die Sie in der Liste anhand der apps angegeben, die Benutzer installiert haben haben (aber nicht möglich tatsächlich Blockieren der Installation der app) verwendet werden.

> [!TIP]
> Sie können die allgemeinen Geschäftsbedingungen für Benutzer, um sicherzustellen, dass sie bestätigen, dass apps auf ihrem Gerät (einschließlich persönliche apps) ausgewertet werden konfigurieren und nicht kompatible apps entweder blockiert oder als nicht kompatible gemeldet werden. Benutzer müssen diese allgemeinen Geschäftsbedingungen zustimmen, bevor sie können Geräts zu registrieren und das Unternehmen Portal um apps zu erhalten. Weitere Informationen zur Verwendung von allgemeinen Geschäftsbedingungen finden Sie unter [Microsoft Intune allgemeinen Geschäftsbedingungen Richtlinieneinstellungen](terms-and-condition-policy-settings-in-microsoft-intune.md).

Wenn die von Ihnen gesuchte Einstellung in diesem Thema nicht angezeigt wird, können Sie möglicherweise erstellen sie mithilfe einer benutzerdefinierten iOS-Richtlinie, die Sie können importieren, die Sie erstellt haben, mit dem [Tool Apple-Konfiguration](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Weitere Informationen finden Sie unter "Benutzerdefinierte Richtlinieneinstellungen" weiter unten in diesem Thema.

### Sicherheitseinstellungen
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Anfordern eines Kennworts zum Entsperren von mobiler Geräten**|Geben Sie an, ob der Benutzer zur Eingabe eines Kennworts zum Zugreifen auf ihr Geräts erforderlich ist.|
|**Kennwort geben erforderlich**|Geben Sie das Kennwort ein, die erforderlich sind, wie z. B. numerisch nur oder alphanumerische können.|
|**Anzahl der komplexe Zeichen im Feld Kennwort erforderlich**|Geben Sie die Anzahl der Symbolzeichen (wie **#** oder **@**), die in das Kennwort enthalten sein müssen.|
|**Mindestlänge des Kennworts**|Geben Sie die minimale Anzahl von Zeichen in das Kennwort ein.|
|**Einfache Kennwörter zulassen**|Einfache Kennwörter wie **0000** und **1234**zulassen.|
|**Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird**|Geben Sie die Anzahl der fehlgeschlagener Login-Versuche, bevor diese Einstellung das Gerät löscht.|
|**Minuten nach der letzten vor dem Kennwort erforderlich ist**<sup>1</sup>|Geben Sie an, wie lange das Gerät im Leerlauf bleiben kann, bevor der Benutzer das Kennwort erneut eingeben muss.|
|**Kennwortablauf (Tage)**|Geben Sie die Anzahl der Tage, bevor das Gerätekennwort geändert werden muss.|
|**Denken Sie daran Kennwortverlauf**|Geben Sie an, ob der Benutzer Kennwörter verwenden kann, die sie zuvor verwendet haben.|
|**Speichern Kennwortverlauf** – **verhindern, dass Wiederverwendung von vorherigen Kennwörtern**|Geben Sie die Anzahl der zuvor verwendete Kennwörter, die das Gerät merkt sich ein.|
|**Minuten nach der letzten, bevor der Bildschirm ausgeschaltet**<sup>1</sup>|Geben Sie die Anzahl der Minuten, bevor Sie die Anzeige des Geräts deaktiviert ist.|
|**Zulassen von Fingerabdrucks Aufheben der Sperre**|Zulassen Sie verwenden zum Entsperren des Geräts einen Fingerabdruck|
<sup>1</sup> für iOS-Geräte, wenn Sie die Einstellungen **inaktiv, bevor der Bildschirm ausgeschaltet** und **Minuten nach der letzten vor dem Kennwort erforderlich ist**, konfigurieren sie angewendet werden nacheinander. Wenn Sie den Wert für beide Einstellungen **5** Minuten festlegen, wird im Bildschirm automatisch nach 5 Minuten deaktivieren ein, und das Gerät wird gesperrt nach ein weiteres 5 Minuten. Wenn der Benutzer den Bildschirm manuell deaktiviert, wird die zweite Einstellung jedoch sofort angewendet. In diesem Beispiel Sperren des Geräts nach dem Bildschirm der Benutzer deaktiviert später 5 Minuten.

### Systemeinstellungen
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Screenshot zulassen**|Kann der Benutzer den Inhalt des Bildschirms als Bild erfassen.|
|**Neue Steuerzentrum in Sperrbildschirm zulassen**|Kann der Benutzer die app Steuerelement Center zugreifen, wenn das Gerät gesperrt ist.|
|**Benachrichtigung anzeigen in Sperrbildschirm zulassen**|Kann der Benutzer auf die Benachrichtigungen-Ansicht zugreifen können, ohne das Gerät entsperren.|
|**Zulassen von Sperrbildschirm Today anzeigen**|Kann der Benutzer zum Anzeigen von Benachrichtigungen, wenn das Gerät gesperrt ist.|
|**Nicht vertrauenswürdige TLS-Zertifikate zulassen**|Nicht vertrauenswürdige Transport Layer Security Zertifikate auf dem Gerät zulassen.|
|**Senden von Diagnoseprotokollen Daten zulassen**|Zulassen Sie oder Sperren Sie das Gerät aus Senden von Diagnoseprotokollen Daten an Apple.|
|**Zulassen von Passbook während gesperrt**|Zulassen der Benutzers auf die app Passbook zugreifen, während das Gerät gesperrt ist.|

### Cloud-Einstellungen für Dokumente und Daten
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Sicherung an einem iCloud zulassen**|Kann der Benutzer das Gerät zu iCloud sichern.|
|**Dokument-Synchronisierung mit iCloud zulassen**|Dokument- und Schlüsselwert Synchronisierung zu Speicherplatz verschwendet iCloud ermöglicht.|
|**Foto Stream Synchronisierung mit iCloud zulassen**|Erlauben Sie Fotos auf dem Gerät, der mit iCloud synchronisiert.|
|**Verschlüsselte Sicherung erforderlich**|Erfordern Sie Gerät Sicherungskopien verschlüsselt werden.|
|**Zulassen Sie verwaltete apps zum Synchronisieren von Daten mit iCloud**|Erlauben Sie apps, die Sie zum Synchronisieren von Daten mit iCloud-Konto des Benutzers mit Intune verwalten.|
|**Zulassen Sie Übergabe Aktivitäten auf ein anderes Gerät weiterhin**|Ermöglicht dem Benutzer Arbeit fortsetzen, die sie auf einem iOS-Gerät auf einem anderen iOS oder Mac OS X-Gerät gestartet haben.|
|**Zulassen von iCloud Freigabe von Fotos**|Lassen Sie die Verwendung des Features iOS freigegebene Fotos Stream.|
|**ICloud Fotobibliothek zulassen**|Kann der Benutzer zum Speichern von Fotos auf iCloud. Wenn deaktiviert, werden alle bereits auf iCloud gespeicherten Fotos entfernt.|

### Anwendungseinstellungen für den browser
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Safari zulassen**|Geben Sie an, ob der Safari-Browser auf dem Gerät verwendet werden kann.|
|**Zulassen von AutoAusfüllen**|Kann der Benutzer zum Ändern der AutoVervollständigen-Einstellungen im Browser.|
|**Popupblocker zulassen**|Aktivieren oder Deaktivieren des Popupblockers des Browsers.|
|**Zulassen von cookies**|Lassen Sie im Browser Cookies verwendet.|
|**Java scripting zulassen**|Erlauben Sie Java-Skripts auf im Browser ausgeführt werden.|
|**Betrug Warnung zulassen**|Zulassen von Betrug Warnungen im Browser.|

### Anwendungseinstellungen für apps
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Zulassen der Installation von apps**|Lassen Sie das Gerät zum app Store zugreifen und Installieren von apps.|
|**Anfordern eines Kennworts zum Anwendungsspeicher zugreifen**|Muss der Benutzer ein Kennwort eingeben, bevor sie den app Store besuchen können.|
|**In der app Einkäufe zulassen**|Zulassen von Store Einkäufe innerhalb einer laufenden app aus vorgenommen werden.|
|**Verwaltete Dokumente in andere apps nicht verwalteten zulassen**|Zulassen von corporate Dokumente auf eine beliebige app angezeigt werden.<br>**Beispiel:** Um zu verhindern, dass Benutzer das Speichern von Dateien mit der OneDrive-app zu Dropbox werden soll. Konfigurieren Sie diese Einstellung als Nein aus. Nachdem das Gerät (beispielsweise nach einem Neustart) die Richtlinie empfangen, ermöglichen es nicht mehr speichern.|
|**Ermöglicht es nicht verwalteten Dokumente in anderen verwalteten apps**|Lassen Sie jedes Dokument auf corporate verwalteten apps angezeigt werden.|
|**Videokonferenzen zulassen**|Zulassen von Videokonferenzen apps wie FaceTime auf dem Gerät.|
|**Ermöglicht dem Benutzer, Autoren von neuen Enterprise-app zu vertrauen**|Kann der Benutzer wählen Sie apps zu vertrauen, die nicht aus dem app Store heruntergeladen wurden.|


### Anwendungseinstellungen für Spiele
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Zulassen Sie Hinzufügen von Freunden Spiel Center**|Zulassen des Benutzers Freunde Spiel Center hinzufügen.|
|**Spielen zulassen**|Kann des Benutzers mehrere Spieler spielen auf dem Gerät.|

### Anwendungseinstellungen für Medieninhalten
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Bewertungen region**|Wählen Sie einen Bereich aus, und wählen Sie dann die maximale Bewertung, die Benutzer für **Filme**, **Fernsehsendungen** und **Apps**herunterladen können.|
|**Medien Store für Erwachsene zulassen**|Lassen Sie das Gerät Zugriff auf die Inhalte als oben im Store bewertet.|
|**Ermöglicht dem Benutzer Inhalt herunterladen, aus dem iBook Store gekennzeichnet als erotisches 'Material'**|Kann der Benutzer mit der Kategorie "erotisches Material" Bücher herunterladen.|


### Funktionen des Audiogeräts für hardware
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Kamera zulassen**|Geben Sie an, ob die Kamera auf dem Gerät verwendet werden kann.|
|**Erzwingen Sie für Apple Überwachungen Handgelenk Erkennung verwenden**|Wenn aktiviert, werden im Apple Watch Benachrichtigungen nicht angezeigt, wenn es nicht ist beschädigt wird.|
|**Festlegen eines pairing Kennworts für ausgehende AirPlay Anfragen**|Pairing Kennwort erforderlich, wenn der Benutzer zum Streaming von Inhalten von anderen Geräten Apple AirPlay verwendet.|

### Funktionen des Audiogeräts für Mobiltelefone
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**VoIP roaming zulassen**|Zulassen von VoIP roaming, wenn das Gerät in einem Netzwerk Mobile ist.|
|**Daten roaming zulassen**|Können Sie Daten roaming, wenn das Gerät auf einem Mobilfunknetz ist.|
|**Globale Hintergrund Abruf beim roaming zulassen**|Lassen Sie das Gerät zum Abrufen von Daten wie e-Mail, während Sie es auf einem Mobilfunknetz roaming ist.|

### Funktionen des Audiogeräts für features
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Siri zulassen**|Lassen Sie die Verwendung des Siri VoIP-Assistenten auf dem Gerät.|
|**Zulassen Sie Siri, während das Gerät gesperrt ist**|Lassen Sie Verwendung von des Siri VoIP-Assistenten auf dem Gerät zu, solange sie gesperrt ist.|
|**VoIP einwählen zulassen**|Lassen Sie die Verwendung der Funktion VoIP Einwählen auf dem Gerät.|
|**Airdrop aus verwalteten apps nicht zulassen**|Stopps verwaltet apps daran hindern, Daten über zu senden. Airdrop.|


### Einstellungen für kompatible und nicht kompatible apps
In der **kompatibel &amp; nicht kompatible Apps** Liste, eine Liste der kompatiblen oder nicht kompatibel apps mithilfe der folgenden Informationen angeben.

> [!NOTE]
> Eine einzelne Richtlinie kann nur eine Liste der kompatiblen apps oder eine Liste der nicht kompatiblen apps enthalten. Sie können keine beide in der gleichen Richtlinie angeben.

|Name der Einstellung|Details|
|----------------|--------------------|
|**Melden Sie bei nicht-Konformität, wenn der Benutzer der aufgeführten apps installieren**|Liste der apps (nicht von Intune verwaltet), dass Benutzer nicht unterstützt werden, installieren und ausführen.|
|**Melden Sie bei nicht-Konformität, wenn Benutzer apps installieren, die nicht aufgeführt sind**|Liste der apps, die Benutzer dürfen, zu installieren. Um kompatibel bleiben, müssen Benutzer nicht apps installieren, die nicht aufgelistet werden. Apps, die vom Intune verwaltet werden sind automatisch zulässig.|
|**Hinzufügen**|Hinzufügen einer app der ausgewählten Liste an. Geben Sie einen Namen Ihrer Wahl, optional die app Publisher und die URL der app im app Store. Lesen Sie "How to URLs zu app Stores angeben" weiter unten in diesem Thema weitere Hilfe.|
|**Importieren von Apps**|Importieren Sie eine Liste der apps, die Sie in eine CSV-Datei angegeben haben. Verwenden Sie dieses Format in der Datei: Name der Anwendung, Publisher, app-URL.|
|**Bearbeiten**|Bearbeiten Sie Name, Publisher und der ausgewählten app-URL ein.|
|**Löschen**|Löschen der ausgewählten app aus der Liste aus.|

### Einstellungen für Kiosk-Modus

|Name der Einstellung|Details|
|----------------|--------------------|
|**Wählen Sie eine verwaltete app, die zur Ausführung beim Kiosk-Modus das Gerät wird gewährt werden soll**|Wählen Sie **Durchsuchen**, und geben Sie dann die verwaltete app oder die app aus einem Speicher, der zur Ausführung beim Kiosk-Modus das Gerät wird gewährt werden soll. Keine andere apps dürfen auf dem Gerät ausgeführt werden. Weitere Hilfe finden Sie unter "How to URLs zu app Stores angeben" weiter unten in diesem Thema.|
|**Fingereingabe zulassen**|Aktivieren Sie oder deaktivieren Sie der Touchscreen auf dem Gerät.|
|**Drehung des Bildschirms zulassen**|Aktivieren Sie oder deaktivieren Sie die Bildschirm Ausrichtung ändern, wenn der Benutzer das Gerät dreht.|
|**Schaltflächen zum Zulassen**|Aktivieren oder Deaktivieren der Verwendung der Schaltflächen auf dem Gerät.|
|**Zulassen von Ringer wechseln**|Aktivieren Sie oder deaktivieren Sie den Schalter Ringer (stumm schalten) auf dem Gerät.|
|**Bildschirm Standby-Aktivierungstaste zulassen**|Aktivieren Sie oder deaktivieren Sie die Bildschirm Standby Aktivierung-Taste auf dem Gerät.|
|**Automatische Sperren zulassen**|Aktivieren Sie oder deaktivieren Sie der automatischen Sperren des Geräts.|
|**Audio Schwarzweiß aktivieren**|Aktivieren Sie oder deaktivieren Sie den Zugriff auf **Schwarzweiß Audio**festlegen.|
|**VoIP über aktivieren**|Aktivieren oder Deaktivieren der Eingabehilfen **VoiceOver**, die vorgelesen Text bei der Anzeige des Geräts festlegen.|
|**VoIP über Anpassungen aktivieren**|Aktivieren oder Deaktivieren von Voiceover Anpassungen, mit die den Benutzer die Funktion VoiceOver (beispielsweise, wie schnell auf dem Bildschirm Text laut gelesen wird) anpassen können.|
|**Zoom aktivieren**|Aktivieren oder Deaktivieren der **Zoom** Accessibility Einstellung, die der Benutzer Touch verwenden, um die Anzeige des Geräts vergrößern.|
|**Aktivieren Sie Zoom Anpassungen**|Aktivieren oder Deaktivieren von Zoom-Anpassungen, mit die den Benutzer die Zoomfunktion anpassen können.|
|**Aktivieren Sie Farben umkehren**|Aktivieren Sie oder deaktivieren Sie die **Farben umkehren** Accessibility-Einstellung, die die Anzeige, um Benutzer mit eingeschränkter Sehkraft Hilfe passt.|
|**Umkehren Farben Anpassungen aktivieren**|Aktivieren oder Deaktivieren von umkehren Farben Anpassungen, mit die den Benutzer die Farben umkehren-Funktion anpassen können.|
|**Aktivieren Sie hilfstechnologien touch**|Aktivieren oder Deaktivieren von **Hilfstechnologien berühren** Accessibility Einstellung der, die den Benutzer auf dem Bildschirm ausführen kann Gesten, die möglicherweise schwierig bis ausführen.|
|**Aktivieren Sie hilfstechnologien Touch Anpassungen**|Aktivieren oder Deaktivieren von hilfstechnologien Touch Anpassungen, mit die den Benutzer, die hilfstechnologien Touch-Funktion anpassen können.|
|**Aktivieren einer Sprache Auswahl**|Aktivieren oder Deaktivieren der **Auswahl vorlesen** Eingabehilfen erhalten Sie, die welche laut den Text lesen können, den der Benutzer auswählt.|
> [!NOTE]
> Die folgenden Hinweise gelten für Kiosk-Modus Einstellungen für iOS-Geräte:
>
> -   Bevor Sie einem iOS-Gerät für Kiosk-Modus konfigurieren können, müssen Sie das [Tool Apple-Konfiguration](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) oder [Apple Gerät Registrierungs-Programm](ios-device-enrollment-program-in-microsoft-intune) verwenden, auf das Gerät in Kontrolle versetzt werden soll. Weitere Informationen über das Tool Apple-Konfiguration finden Sie unter Ihrem Apple-Dokumentation.
> -   Wenn die iOS-app, die Sie angeben, nach der Bereitstellung von der Konfigurationsrichtlinie installiert wurde, wird das Gerät nicht Kioskmodus bis Geben Sie nach dem Neustart ist.

### Referenzinformationen für kompatible und nicht kompatible apps

**Nicht kompatible Apps Bericht** können die Kompatibilität der anzeigen zulässig und apps blockiert.

##### Zum Ausführen des Berichts für nicht kompatible Apps

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), **Berichte** &gt; **Nicht kompatible Apps Bericht**.

2.  Wählen Sie die Gerätegruppen, die Sie überprüfen, ob Sie soll kompatiblen apps, apps nicht kompatible oder beides gesucht werden soll, und wählen Sie dann auf **Bericht anzeigen**möchten.

#### So URLs auf app-Speicher angeben.
Geben Sie eine app-URL in der Liste kompatible und nicht kompatible apps oder die Option **Wählen Sie eine verwaltete app, die ausgeführt werden, wenn das Gerät in Kioskmodus ist gewährt werden soll** (nur iOS) verwenden das folgende Format:

1. Verwenden ein Suchmodul, finden Sie die app, die Sie verwenden möchten, verwenden Sie im iTunes App Store, und öffnen Sie die Seite für die app.

2. Kopieren Sie die URL der Seite, und verwenden Sie diese als die URL zum Konfigurieren der Liste der kompatiblen oder nicht kompatibel apps oder die app, die im Kioskmodus ausgeführt werden soll.

**Beispiel:** Suchen Sie nach **Microsoft Word für iPad**. Die URL, die verwendet, werden **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Sie können auch die iTunes-Software verwenden, suchen Sie die app, und verwenden Sie den Befehl **Link kopieren** können Sie um die app-URL zu gelangen.

### Registrierungs-Einstellungen
Alle Einstellungen gelten für iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|--------------------|
|**Zulassen Sie Sperren der Aktivierung, wenn das Gerät im Kontrolle ausgeführt wird**|Aktivieren Sie Aktivierung Sperren auf Kontrolle iOS-Geräte.|

### Einstellungen für Kontrolle Modus
Sie können die folgenden Einstellungen auf Geräten unter iOS 8.0 und höher, die im Modus Kontrolle sind konfigurieren.

### Einstellungen für Gerät Einschränkungen Kontrolle Modus

|Name der Einstellung|Details|
|----------------|--------------------|
|**Konto Änderung zulassen**|Zulassen von Benutzern, wie z. B. Konfigurationen für e-Mail-Konten-Einstellungen zu ändern.|
|**Zulassen von Änderungen an app-Einstellungen für die Verwendung von Datenverbindung**|Gestatten Sie den Benutzer, zu steuern, welche apps Mobile Daten verwenden dürfen.|
|**Der Verwendung von den Löschvorgang alle Inhalte und Option "Einstellungen" auf dem Gerät zulassen**|Ermöglicht dem Benutzer die Möglichkeit, löschen alle Inhalte und Einstellungen auf dem Gerät verwenden.|
|**Ermöglicht dem Benutzer in den Einstellungen für Audiogeräte Einschränkungen aktivieren**|Zulassen von Gerät Einschränkungen (jugendschutzeinstellungen) auf dem Gerät zu konfigurieren.|
|**Verbindung zum Steuern der Geräte, die, denen mit einem iOS-Gerät gepaart kann, Host zulassen**|Zulassen von Host paarweise Zuordnung, wenn der Administrator steuern können, welche Geräte mit einem iOS-Gerät verbinden kann.|
|**Ermöglicht dem Benutzer, Konfiguration von Benutzerprofilen und Zertifikate zu installieren.**|Ermöglicht dem Benutzer, Konfiguration von Benutzerprofilen und Zertifikate zu installieren.|
|**Namensänderung Gerät zulassen**|Zulassen Sie so ändern Sie den Namen des Geräts Benutzer.|
|**Kenncode Änderung zulassen**|Lassen Sie das Kennwort für das Gerät zu hinzugefügt, geändert oder entfernt werden soll.|
|**Apple Watch Verbindung zulassen**|Lassen Sie das Gerät mit einer Apple Watch ein.|
|**Benachrichtigung Einstellungen Änderung zulassen**|Zulassen Sie so ändern Sie die Benachrichtigung des Audiogeräts Benutzer.|
|**Hintergrundbild Änderung zulassen**|Zulassen Sie so ändern Sie das Gerät Hintergrundbild Benutzer.|

### Einstellungen für das Feature Einschränkungen Kontrolle Modus

|Name der Einstellung|Details|
|----------------|--------------------|
|**AirDrop zulassen**|Lassen Sie die Verwendung der Funktion "AirDrop" zum Austauschen von Inhalten mit benachbarten Geräte.|
|**Siri auf benutzerseitig generierte Abfrage-Inhalte aus dem Internet zulassen**|Lassen Sie Siri den Zugriff auf Websites, um Fragen zu beantworten.|
|**Verwenden Sie Siri für anstößige filter**|Verhindert, dass Siri von diktieren und sprechen Bitte beachten.|
|**Zulassen Sie Spotlight Suche zurückzugebenden Ergebnisse aus dem Internet**|Zulassen, dass eine Verbindung mit dem Internet Ergebnisse genauer Spotlight-Suche.|
|**Word Definition Nachschlagen zulassen**|Erlauben Sie das iOS-Feature, mit dem Sie markieren Sie ein Wort, und suchen sie die Definition.|
|**Vorhersage Tastaturen zulassen**|Lassen Sie die Verwendung von Vorhersage Bildschirmtastaturen, die Wörter vorschlagen, die der Benutzer vielleicht zu.|
|**AutoKorrektur zulassen**|Ermöglicht das Gerät falsch geschriebene Wörter automatisch korrigiert.|
|**Tastatur-Rechtschreibprüfung zulassen**|Ermöglicht das Gerät Rechtschreibprüfung verwendet werden soll.|
|**Zulassen von Tastenkombinationen**|Ermöglicht die Verwendung der Tastenkombinationen.|

### Einstellungen für die app Einschränkungen Kontrolle Modus

|Name der Einstellung|Details|
|----------------|--------------------|
|**Enterprise-app Trust Einstellungen Änderung zulassen**|Ermöglicht Benutzern das Ändern der Einstellungen für das Trust für Enterprise-apps.|
|**Zulassen Sie Installieren von apps mit Apple-Konfiguration und iTunes nur**|Aktiviert oder deaktiviert im App Store vom Startbildschirm Gerät. Benutzer können weiterhin iTunes, oder auf das Tool Apple-Konfiguration für das Installieren und Aktualisieren von apps verwenden.|
|**Automatische app Downloads zulassen**|Zulassen von apps auf anderen Geräten automatisch mit diesem Gerät herunterladen erworben haben. Diese Einstellung wirkt sich nicht auf app-Updates aus.|
|**Zulassen von Änderungen an den app-Einstellungen meine Freunde suchen**|Kann der Benutzer zum Ändern der Einstellungen für die app meine Freunde suchen.|
|**Zugriff auf die iBooks Store zulassen**|Gestatten Sie den Benutzer, zu durchsuchen und Bücher aus dem iBooks Speicher kaufen.|
|**Lassen Sie die Verwendung der app Nachrichten auf dem Gerät**|Lassen Sie die Verwendung der app Nachrichten, Textnachrichten zu senden.|
|**Verwendung von Podcasts zulassen**|Lassen Sie die Verwendung der app Podcasts.|
|**Verwendung von Musikdienst zulassen**|Lassen Sie die Verwendung der Musik Apple-app.|
|**ITunes Optionsfeld-Dienst zulassen**|Lassen Sie die Verwendung der iTunes Optionsfeld-app.|
|**Apple News zulassen**|Lassen Sie die Verwendung der app Apple News.|
|**Spiel Center zulassen**|Lassen Sie die Verwendung der app Spiel Center.|


### Ein- oder Ausblenden von Apps

Verwenden Sie die **ausgeblendet und angezeigte apps-Liste** so steuern Sie die folgenden auf Kontrolle Geräten iOS 9,3 oder höher ausgeführt:

- Geben Sie eine Liste der apps, die von Benutzern ausgeblendet wird. Benutzer können nicht anzeigen oder diese apps zu starten.
- Geben Sie eine Liste der apps, die Benutzer anzeigen und starten können. Keine anderen apps können angezeigte oder gestartet wird.


#### So erstellen Sie eine ausgeblendete oder angezeigte app-Liste

Geben Sie die folgenden Einstellungen:

|Name der Einstellung|Details|
|-|-|
|**Ein- und ausgeblendete apps-Liste**|Aktivieren Sie diese Einstellung, wenn Sie eine ausgeblendete oder angezeigte apps-Liste erstellen möchten.|
|**Ausblenden der aufgeführten apps von Benutzern**|Wählen Sie diese Option, wenn Sie eine Liste der apps, die ausgeblendet wird von Benutzern erstellen möchten.|
|**Zeigen Sie nur der aufgeführten apps für Benutzer an**|Wählen Sie diese Option, wenn Sie eine Liste der apps erstellen, die für Benutzer angezeigt werden soll.<br>Wenn Sie diese Art von Liste erstellen, werden alle anderen apps eine Ausnahme bilden jedoch die iOS- **Einstellungen** und **Telefon** (für iPhones) apps ausgeblendet.<br>Sie müssen außerdem im Portal Unternehmen und apps, die Sie bereitgestellt haben, die und mit Intune verwalten, um der Liste hinzufügen.|
|**Hinzufügen**|Der ausgewählten Liste hinzugefügt eine app.<br>Für die ausgeblendete Liste müssen Sie angeben, der **Name**, **Publisher**und **App-URL oder Paket-ID** der einzelnen app, die Sie ausblenden möchten.<br>Für die angezeigte Liste können Sie entweder **Wählen Sie eine verwaltete app aus** der Sie eine Liste der apps können Sie verwalten mit Intune Auswahl aus, oder wählen Sie eine Store-app, nach der Sie angeben müssen, der **Name**, **Publisher**und **App-URL oder Paket-ID** der einzelnen app, die angezeigt werden soll.|
|**Importieren von Apps**|Importiert eine Liste der apps, die Sie in eine CSV-Datei angegeben haben. Verwenden Sie das Format, Name der Anwendung, Publisher, app-URL in der Datei ein.|
|**Bearbeiten**|Lassen Sie uns bearbeiten Sie Name, Publisher und der ausgewählten app-URL.|
|**Löschen**|Löscht die ausgewählte app aus der Liste an.|

#### Informationen zu App für integrierte iOS-apps

Verwenden Sie die Informationen in dieser Liste, um den Namen, identifizieren Publisher und Paket-ID der integrierten iOS-apps, die Sie vielleicht ein- oder ausblenden möchten. Wenn Sie ein- oder Ausblenden aller der in der Liste apps möchten, können Sie die nachfolgenden Daten in eine Textdatei mit der Erweiterung **CSV**kopieren und dann verwenden die Option **Importieren Apps** , um alle der apps gleichzeitig importieren.

```
App Store,Apple,com.apple.AppStore
Calculator,Apple,com.apple.calculator
Calendar,Apple,com.apple.mobilecal
Camera,Apple,com.apple.camera
Clock,Apple,com.apple.mobiletimer
Compass,Apple,com.apple.compass
Contacts,Apple,com.apple.MobileAddressBook
FaceTime,Apple,com.apple.facetime
Find Friends,Apple,com.apple.mobileme.fmf1
Find iPhone,Apple,com.apple.mobileme.fmip1
Game Center,Apple,com.apple.gamecenter
GarageBand,Apple,com.apple.mobilegarageband
Health,Apple,com.apple.Health
iBooks,Apple,com.apple.iBooks
iTunes Store,Apple,com.apple.MobileStore
iTunes U,Apple,com.apple.itunesu
Keynote,Apple,com.apple.Keynote
Mail,Apple,com.apple.mobilemail
Maps,Apple,com.apple.Maps
Messages,Apple,com.apple.MobileSMS
Music,Apple,com.apple.Music
News,Apple,com.apple.news
Notes,Apple,com.apple.mobilenotes
Numbers,Apple,com.apple.Numbers
Pages,Apple,com.apple.Pages
Photo Booth,Apple,com.apple.Photo-Booth
Photos,Apple,com.apple.mobileslideshow
Podcasts,Apple,com.apple.podcasts
Reminders,Apple,com.apple.reminders
Safari,Apple,com.apple.mobilesafari
Settings,Apple,com.apple.Preferences
Stocks,Apple,com.apple.stocks
Tips,Apple,com.apple.tips
Videos,Apple,com.apple.videos
VoiceMemos,Apple,com.apple.VoiceMemos
Wallet,Apple,com.apple.Passbook
Watch,Apple,com.apple.Bridge
Weather,Apple,com.apple.weather


```




## Benutzerdefinierte Richtlinieneinstellungen

Verwenden Sie die Microsoft Intune **iOS benutzerdefinierte Richtlinie** Einstellungen bereitstellen, die Sie erstellt haben, indem Sie mit dem [Tool Apple-Konfiguration](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) iOS-Geräte. Diese-Tool können Sie viele Einstellungen erstellen, die Steuerung des Betriebs dieser Geräte und einem Konfiguration Profil zu exportieren. Dann können Sie dieses Konfigurationsprofil in einer benutzerdefinierten Intune iOS-Richtlinie importieren und die Einstellungen für Benutzer und Geräte in Ihrer Organisation bereitstellen.

Diese Funktion können Sie iOS-Einstellungen bereitstellen, die nicht mit Intune allgemeine Konfigurationsrichtlinien konfiguriert sind.

### Erforderliche Komponenten
Bevor Sie beginnen, müssen Sie die Apple-Konfiguration installiert und eine Konfigurationsdatei, die Einstellungen enthält, die Sie für Benutzer oder Geräte bereitstellen möchten, erstellt haben. Sie können herunterladen und erfahren Sie mehr über die Apple-Konfiguration aus [Dem Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> Intune meldet die Kompatibilität der einzelnen Einstellungen in einer benutzerdefinierten iOS-Richtlinie nicht. Jedoch ist die allgemeinen Vorschriften der Richtlinie gemeldet.

### Allgemeine Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Namen**|Geben Sie einen eindeutigen Namen für die benutzerdefinierte Richtlinie iOS in der Intune Verwaltungskonsole erkennbar.|
    |**Beschreibung**|Stellen Sie eine Beschreibung, die einen Überblick über die iOS benutzerdefinierte Richtlinie bietet und weitere relevante Informationen, die Sie danach zu suchen kann.|

### Benutzerdefinierte Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
|**Benutzerdefinierte Konfiguration Profilname (für Benutzer angezeigt)**|Geben Sie einen Namen für die Richtlinie aus, wie er auf dem Gerät, und klicken Sie in Berichten Intune angezeigt werden.|
|**Konfigurationsdatei-Profil**|Wählen Sie **Importieren**aus, und wechseln Sie dann zu der Konfigurationsprofil, das Sie mithilfe der Apple-Konfiguration erstellt haben. **Hinweis:** Stellen Sie sicher, dass die Einstellungen, die Sie auf das Tool Apple-Konfiguration exportieren mit der Version von iOS auf Geräten kompatibel sind, dem Sie die benutzerdefinierte iOS-Richtlinie bereitstellen. Für Informationen wie inkompatiblen Einstellungen gelöst werden, auf der Website [Apple Developer](https://developer.apple.com/) nach **Konfiguration Profil Bezug** und **Mobile Geräte Management Protokoll verweisen** suchen.|
    |**Konfiguration von Profildetails**|Anzeigen des XML-Codes für das Konfigurationsprofil, das Sie importiert haben.|

### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
