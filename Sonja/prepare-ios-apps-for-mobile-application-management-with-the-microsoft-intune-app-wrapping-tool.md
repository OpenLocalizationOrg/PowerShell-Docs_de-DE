---
title: "Umbrechen von iOS-apps mit dem Tool für die App-umbrechen | Microsoft Intune"
description: "Verwenden Sie die Informationen in diesem Artikel erfahren Sie, wie Ihre iOS-apps umbrochen ohne Ändern des Codes der App ähneln. Bereiten Sie die apps, damit Sie mobile-app Informationsverwaltungsrichtlinien anwenden können."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
ms.openlocfilehash: a07958d58d037545630fcfda749ee0e58b84c69d
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Vorbereiten der iOS-apps für mobile anwendungsverwaltung mit dem Intune App umbrechen-Tool
Verwenden Sie das **Microsoft Intune App umbrechen Tool für iOS** das Verhalten für iOS-Apps ändern, indem Sie den Features der app ohne Ändern des Codes der App ähneln.

Das Tool ist eine Befehlszeile unter Mac OS-Anwendung, die einen Wrapper um eine app erstellt wird. Nachdem Sie eine app verarbeitet wird, können Sie dann ändern des app Funktionen, die mit [mobilen Anwendung Informationsverwaltungsrichtlinien](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) , die Sie konfigurieren.

Wenn Sie das Tool herunterladen möchten, finden Sie unter [Umbrechen Tool von Microsoft Intune App für iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

>[!IMPORTANT]
>Die Version der app umbrechen Tool, mit dem Geräte nicht registriert Intune unterstützt, steht für public Preview-Version. Wenn Sie in der Vorschau öffentlichen teilnehmen möchten, können Sie das Tool von [dieser Seite Github](https://github.com/msintuneappsdk/intune-app-wrapper-ios-preview) für iOS herunterladen.

>Das Szenario wird im Thema [schützen LOB apps auf Geräten, die nicht in Intune registriert](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md) beschrieben.

## Schritt 1 erfüllen die Voraussetzung für die Verwendung der app umbrechen tool
Lesen Sie weitere Informationen zu erforderlichen Komponenten und wie Sie diese festlegen [Dieser Blogbeitrag](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) .

|Anforderung|Weitere Informationen|
|---------------|--------------------------------|
|Unterstütztes Betriebssystem und das empfohlene Toolkit|Führen Sie die app Tool auf einem Mac OS X 10.8.5 ausgeführt wird, die umbrechen oder höher, die die Toolsetversion XCode 5 oder höher installiert wurde.|
|Signaturzertifikat und provisioning Profil|Sie müssen eine Apple Signaturzertifikat und Profil bereitgestellt. Finden Sie in Ihrem [Apple-Dokumentation für Entwickler](https://developer.apple.com/).|
|Eine app mit der App umbrechen Tool Verarbeitung|Apps müssen entwickelt und von Ihrem Unternehmen oder eine unabhängige Software Softwareanbietern () signiert werden. Sie können keine dieses Tool verwenden, um apps im Apple Store zu verarbeiten. Apps müssen für iOS 8.0 oder höher geschrieben werden. Apps müssen auch im Format Position unabhängige ausführbare Datei (Kreis). Weitere Informationen über das Kreis-Format finden Sie unter Ihrem Apple-Dokumentation für Entwickler. Schließlich müssen die app die Erweiterung **.app**oder **.ipa** Format.|
|Apps das Tool Textumbruch kann nicht verarbeitet werden.|Verschlüsselte apps, ohne Vorzeichen apps und apps mit erweiterten Dateiattributen.|
|Festlegen von Berechtigungen für Ihre app|Sie müssen Ansprüche, geben Sie die app zusätzliche Berechtigungen und Funktionen über die in der Regel gewährt werden, bevor Sie die app umbrechen hinausgehen festlegen. Weitere Informationen finden Sie in der [app-Berechtigungen festlegen](#setting-app-entitlements) .|

## Schritt 2 installieren die app Tool umbrechen

1.  Laden Sie die Installationsdatei für die app Umbruch Tool auf einem Mac-Computer, von der Seite **Umbrechen Tool von Microsoft Intune App für iOS** im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=45218).

2.  Klicken Sie auf dem Mac-Computer Doppelklicken Sie auf die Installation **Microsoft Intune App umbrechen Tool für iOS.dmg**.

3.  Wählen Sie **Ich stimme zu** , um den Endbenutzer-Lizenzvertrag (EULA) zu akzeptieren. Das Installationsprogramm ist bereitgestellt, und klicken Sie auf dem Computer Mac angezeigt.

4.  Öffnen Sie das Installationsprogramm aus, und kopieren Sie die angezeigten Dateien in einen neuen Ordner auf dem Computer Mac. Sie können jetzt das Installationsprogramm bereitgestellten Laufwerk trennen.

    Sie können nun die app umbrechen Tool ausführen.

## Schritt 3 Führen Sie die app Tool umbrechen
* Klicken Sie auf dem Computer Mac öffnen Sie ein Terminal-Fenster zu, und navigieren Sie zu dem Ordner, in dem Sie die Dateien gespeichert. Da die ausführbare Datei in der Packung befindet, müssen Sie den Befehl wie folgt ausführen:
```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|Eigenschaft|Weitere Informationen|
  |------------|--------------------|
  |**-h**|Zeigt die Befehlszeilen verfügbaren Eigenschaften für die app umbrechen Tool an.|
  |**i -**|Gibt den Pfad und den Dateinamen Namen der Eingabewerte app.|
  |**-o**|Gibt den Pfad, in dem die verarbeitete app gespeichert.|
  |**-p**|Gibt den Pfad zu Ihrem provisioning Profil für iOS-apps.|
  |**-c**|Gibt den SHA1-Hash des Signaturzertifikats an.|
  |**-v**|Die Ausgabe ausführliche Meldungen an die Konsole (Optional).|
  |f- |Optional) <Path to a plist file specifying arguments>  |
  |-b|(Optional) Geben Sie Argument für diese Kennzeichnung nicht an, wenn Sie möchten, dass die Umgebrochene app müssen dieselbe Paketversion als die Eingabewerte app (nicht empfohlen). Verwenden Sie "-b <custom bundle version>", wenn Sie, dass eine benutzerdefinierte CFBundleVersion die Umgebrochene app möchten. Es empfiehlt sich, Erhöhen der systemeigenen app CFBundleVersion von der am wenigsten signifikanten Komponente z. b. 1.0.0 -> 1.0.1 |

>[!IMPORTANT]
>F - und -b Kennzeichnungen werden nur in der public Preview-Version des Tools App umbrechen unterstützt, die MAM auf Geräten unterstützt, die nicht in Intune registriert sind.


Eine Möglichkeit zum Ausführen des Tools für die App-umbrechen besteht darin alle Befehlsargumente in einer Datei [Plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) setzen. Plist ist, dass ein Dateiformat XML, die uns helfen können ähnlich wie unsere Befehlszeilenargumente in eine Schnittstelle Schlüsselwert Eingabemethoden.

Öffnen Sie mit einem Text-Editor oder Xcode Parameters.plist, eine leere Plist Vorlage ein.
Geben Sie Ihre Argumente für die Eingabewerte Pfad, Ausgabepfad, Profilpfad, SHA1 Zertifikatshash, bereitgestellt und ausführliche aktiviert.
Führen Sie schließlich die IntuneMAMPackager mit der Plist, als einziges Argument:
```
./IntuneMAMPackager –f Parameters.plist
```

* Nach dem Aufbereiten, wird die Nachricht, **die Anwendung wurde erfolgreich umschlossen** angezeigt.

    Falls ein Fehler auftritt, finden Sie unter [Fehlermeldungen](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) Hilfe.

*   Die Umgebrochene app wird in der Ausgabeordner gespeichert, die Sie zuvor angegeben haben. Sie können jetzt hochladen die app in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] und einer mobilen Anwendung zur Dokumentverwaltungsrichtlinie zugeordnet wird.

    > [!IMPORTANT]
    > Laden Sie die app als neue app hoch. Eine ältere, allein stehenden Version der app kann nicht aktualisiert werden.

    Sie können nun die app Bereitstellen Ihrer [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Gruppen und die app wird jetzt ausgeführt, auf dem Gerät mithilfe der app-Einschränkungen, die Sie angeben.

## Fehlermeldungen und der Protokolldateien
Verwenden Sie die folgende Informationen von Problemen, die Sie mit der app umbrechen Tool haben.

### Fehlermeldungen
Wenn das app Umbruch Tool nicht erfolgreich abgeschlossen, wird eine der folgenden Fehlermeldungen angezeigt:

|Fehlermeldung|Weitere Informationen|
|-----------------|--------------------|
|Geben Sie eine gültige iOS provisioning Profil ein.|Ihr Profil provisioning möglicherweise nicht gültig. Aktivieren Sie sicherstellen, dass Sie die geeigneten Berechtigungen für Geräte haben und, dass Ihr Profil ordnungsgemäß entweder Entwicklung oder Verteilerliste verwendet wird. Ihr Profil provisioning möglicherweise auch überschritten werden.|
|Geben Sie einen gültigen Eingabewerte Anwendung an.|Stellen Sie sicher, dass die Eingabewerte angegebene Anwendungsname korrekt ist.|
|Geben Sie einen gültigen Pfad mit der Anwendung Ausgabe an.|Stellen Sie sicher, dass der Pfad zu der Ausgabe-Anwendung, die Sie angegeben haben vorhanden ist, und richtig ist.|
|Geben Sie eine gültige Eingabe provisioning Profil an.|Stellen Sie sicher, dass Sie einen gültigen provisioning Profilname und Erweiterung angegeben. Ihr Profil provisioning Ansprüche fehlen, oder Sie möglicherweise nicht die Befehlszeilenoption **– p** enthalten.|
|Die Eingabewerte Anwendung die angegebene wurde nicht gefunden. Geben Sie eine gültige Eingabewerte Anwendungsnamen und den Pfad ein.|Vergewissern Sie sich Ihre Eingabe app-Pfad gültig und vorhanden ist. Stellen Sie sicher, dass die Eingabewerte app an einer Position befindet.|
|Die Eingabewerte provisioning die angegebene Profildatei wurde nicht gefunden. Geben Sie eine gültige Eingabewerte provisioning Profildatei an.|Stellen Sie sicher, dass der Pfad für die Eingabe provisioning Datei gültig ist und die angegebene Datei vorhanden ist.|
|Der angegebene Ausgabe Anwendungsordner wurde nicht gefunden. Geben Sie einen gültigen Pfad mit der Anwendung Ausgabe an.|Stellen Sie sicher, dass der von Ihnen angegebene Ausgabepfad gültig und vorhanden ist.|
|Die Ausgabe app keinen .ipa Erweiterung.|Nur apps mit der Erweiterung **.app** und **.ipa** werden von der app umbrechen Tool akzeptiert. Stellen Sie sicher, dass die Ausgabedatei eine gültige Erweiterung enthält.|
|Ein ungültiges Signaturzertifikat wurde angegeben. Geben Sie ein gültiges Signaturzertifikat Apple an.|Stellen Sie sicher, dass Sie das richtige Signaturzertifikat aus der Apple-Entwicklerportal heruntergeladen haben. Das Zertifikat ist möglicherweise auch abgelaufen. Wenn Ihr Apple Zertifikats- und provisioning Profil eine app innerhalb Xcode ordnungsgemäß anmelden verwendet werden kann, sind sie für die app umbrechen Tool gültig.|
|Die Eingabewerte Anwendung, die Sie angegeben haben, ist ungültig. Geben Sie eine gültige Anwendung an.|Stellen Sie sicher, dass Sie über eine gültige iOS-Anwendung verfügen, die als .app oder .ipa-Datei kompiliert wurde.|
|Die Eingabewerte Anwendung, die Sie angegeben haben, ist verschlüsselt. Geben Sie eine gültige unverschlüsselter Anwendung an.|Das app-Umbruch-Tool unterstützt verschlüsselte apps nicht. Geben Sie eine app unverschlüsselter an.|
|Die Eingabewerte Anwendung, die Sie angegeben haben, ist nicht in einem Format Position unabhängige ausführbare Datei (Kreis). Geben Sie eine gültige Anwendung in Kreis-Format ein.|Position unabhängige ausführbare Datei (Kreis) apps können an einer Zufallszahl Speicheradresse beim Ausführen der Rente verfügen, können geladen werden. Weitere Informationen hierzu finden Sie unter Ihrer Apple Entwicklertools an.|
|Die Eingabewerte app die angegebene wurde bereits umgebrochen. Geben Sie eine gültige allein stehenden Anwendung an.|Eine app, die bereits durch das Tool verarbeitet wurden, können nicht verarbeitet werden. Wenn Sie eine app erneut verarbeiten möchten, führen Sie das Tool, die die ursprüngliche Version der app zu verwenden.|
|Die Eingabewerte Anwendung, die Sie angegeben haben, ist nicht angemeldet. Geben Sie eine gültige signierten Anwendung an.|Das app Umbruch Tool erfordert apps signiert werden. Wenden Sie sich an Ihre Entwicklertools Dokumentation erfahren Sie, wie sich eine app der Umgebrochene.|
|Die Eingabewerte Anwendung, die Sie angegeben haben, müssen im Format .ipa oder .app.|Von der app umbrechen Tool werden nur die Erweiterungen .app und .ipa akzeptiert. Vergewissern Sie sich die Eingabewerte Datei verfügt über eine gültige Erweiterung als Datei .app oder .ipa kompiliert wurde.|
|Die Eingabewerte app die angegebene wurde bereits eingeschlossen, und klicken Sie auf die neueste Version der Richtlinie Vorlage ist.|Das app Umbruch Tool wird keine vorhandene Umgebrochene app mit der neuesten Version der Richtlinie Vorlage umbrechen.|
|Warnung: Sie haben ein Zertifikatshash SHA1 nicht angegeben. Stellen Sie sicher, dass vor der Bereitstellung Ihrer Anwendung Umgebrochene angemeldet ist.|Stellen Sie sicher, dass Sie einen gültigen SHA Hash (mithilfe der **– C** Befehlszeile-Eigenschaft) angeben.|

### Protokolldateien für die app Tool umbrechen
Apps, die mit dem Tool der app Umbruch umbrochen wurde wurden generieren Protokolle, die in der iOS-Client-Gerät Konsole geschrieben werden. Diese Informationen sind nützlich in Situationen, wo Sie Probleme mit der Anwendung und müssen diagnostizieren, wenn das Problem mit der app umbrechen Tool verknüpft ist. Wenn Sie diese Informationen abrufen möchten, gehen Sie folgendermaßen vor:

1.  Reproduzieren Sie das Problem, indem Sie die app ausführen.

2.  Sammeln der Konsole ausgeben anhand von Apple-Anweisungen für das [Debuggen bereitgestellt iOS-Apps](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3.  Filtern Sie die gespeicherte Protokolle für die App Einschränkungen Ausgabe durch das folgende Skript in die Konsole eingeben:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Sie können die gefilterten Protokolle an Microsoft senden.

    > [!NOTE]
    > In der Protokolldatei, das Element 'Buildversion' stellt die Buildversion von Xcode dar.

    Umgebrochene apps werden präsentieren Benutzer auch die Möglichkeit, die Protokolle direkt vom Gerät per e-Mail zu versenden, nachdem die app stürzt ab. Benutzer können das Protokoll senden, zu überprüfen und an Microsoft weiterleiten, falls erforderlich.


### Zertifikat, authentifizierungsanforderungen und provisioning Profil

|Anforderung|Details|
|---------------|-----------|
|Profil bereitgestellt|**Sicherstellen, dass das provisioning Profil gültig ist, bevor Sie es aufnehmen** – das app Umbruch Tool wird nicht überprüft, ob das provisioning Profil bei der Verarbeitung von einer app für iOS abgelaufen ist. Wenn eine abgelaufene provisioning Profil angegeben wird, das app-Umbruch-Tool wird das abgelaufene provisioning Profil enthalten, und Sie werden nicht wissen, dass ein Problem vorliegt, bis die app nicht mehr auf einem iOS-Gerät installieren.|
|Zertifikat|**Sicherstellen, dass das Zertifikat gültig ist, bevor Sie es angeben** – das Tool wird nicht überprüft, ob ein Zertifikat abgelaufen ist, bei der Verarbeitung von iOS-apps. Wenn der Hashwert für ein abgelaufenen Zertifikat bereitgestellt wird, das Tool verarbeitet und melden Sie sich die app, aber es tritt ein Fehler auf Geräten installieren.<br /><br />**Vergewissern Sie sich, dass das Zertifikat zum Signieren der Anwendungs bereitgestellten eine Übereinstimmung im Profil provisioning weist** - das Tool überprüft nicht bei das Bereitstellung Profil eine Übereinstimmung für das Zertifikat zum Signieren der Umgebrochene Anwendungs bereitgestellt.|
|Authentifizierung|Ein Gerät müssen eine Pin für die Verschlüsselung entwickelt festlegen. Geräte, dem Sie eine Umgebrochene Anwendung bereitgestellt haben, klicken Sie auf die Statusleiste auf dem Gerät berühren, dass der Benutzer mit neu authentifiziert wird [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Die Standardrichtlinie in eine Anwendung Umgebrochene ist *Authentifizierung auf neu starten*. iOS übernimmt alle externen Benachrichtigung (beispielsweise einen Anruf) als Beenden der Anwendung, und klicken Sie dann neu zu starten.<br /><br />Für Umgebrochene apps ist der erste Benutzer, der in eine beliebige Umgebrochene app vom gleichen Herausgeber signiert zwischengespeichert. Nach diesem Zeitpunkt kann nur von diesem Benutzer die app zugreifen. Zum Zurücksetzen des Benutzers muss das Gerät unenrolled, und klicken Sie dann basierendes.|


## Festlegen der app-Berechtigungen
Vor dem umbrechen Ihre app, können Sie **Ansprüche** verleihen Weitere app-Berechtigungen und Fähigkeiten, die app in der Regel Möglichkeiten überschreiten, erteilen.  Eine **Datei Anspruch** wird während Code signieren können Sie spezielle Berechtigungen in der app (beispielsweise des Zugriffs auf eine Schlüsselbund) festlegen verwendet. Bestimmte app-Dienste- **Funktionen**, werden während der app-Entwicklung innerhalb Xcode aktiviert. Nach der Aktivierung werden die Funktionen in Ihre Ansprüche Datei angezeigt. Weitere Informationen zu Berechtigungen und Fähigkeiten finden Sie unter [Hinzufügen von Funktionen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) in den iOS Entwicklertools Bibliothek. Eine vollständige Liste der unterstützten Funktionen finden Sie unter [unterstützte Funktionen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### Unterstützte Funktionen für die App umbrechen Tool für iOS

|Funktion|Beschreibung|Empfohlene Anleitungen|
|--------------|---------------|------------------------|
|App-Gruppen|Verwenden Sie app Gruppen an, damit mehrere apps freigegebenen Container zugreifen und zusätzliche zwischen Prozessen Kommunikation zwischen apps zulassen.<br /><br />Um Gruppen von app zu aktivieren, öffnen Sie den Bereich **Funktionen** , und klicken Sie auf den Schalter " **auf** " im Abschnitt **App Gruppen** . Sie können Gruppen für app hinzufügen oder vorhandene zu markieren.|Verwenden Sie bei Verwendung von App-Gruppen, reverse-DNS-Notation:<br /><br />*group.com.companyName.AppGroup*|
|Hintergrund Modi|Durch das Aktivieren Hintergrund Modi können Ihre app iOS weiterhin im Hintergrund ausführen.||
|Datenschutz|Datenschutz Fügt eine Sicherheitsebene Dateien von Ihrem iOS-app auf einem Datenträger gespeichert. Datenschutz nutzt die integrierten Verschlüsselung Hardware präsentieren auf bestimmte Geräte, zum Speichern von Dateien in einem verschlüsselten Format auf dem Datenträger. Ihre app muss bereitgestellt werden, um den Datenschutz zu verwenden.||
|Kauf von in-App|In-App erwerben eingebettet einer Store direkt an Ihre app ermöglicht es Ihnen Verbinden mit dem Store und sichere Weise verarbeitet Zahlungen vom Benutzer. In der App kaufen können zum Sammeln von der app Zahlung für erweiterte Funktionen oder zusätzlichen Inhalten verwendet werden.||
|Schlüsselbundfreigabe|Bei aktiviertem schlüsselbundfreigabe kann Ihre app im Schlüsselbund Kennwörter für andere apps entwickelt von Ihrem Team freigeben.|Bei Verwendung von Schlüsselbundfreigabe, verwenden Sie reverse-DNS-Notation:<br /><br />*com.companyName.KeychainGroup*|
|Persönliche VPN|Aktivieren Sie persönliche VPN an, damit Ihre app zu erstellen und eine benutzerdefinierte VPN Systemkonfiguration mit dem Netzwerk Erweiterung Framework steuern.||
|Pushbenachrichtigungen|Apple Pushbenachrichtigungen Benachrichtigungsdienst (APNs) ermöglicht eine app, die im Vordergrund dem Benutzer benachrichtigt, dass er Informationen für den Benutzer ist nicht ausgeführt wird.|Für Pushbenachrichtigungen entwickelt müssen Sie ein app-spezifische provisioning Profil zu verwenden.<br /><br />Führen Sie die Schritte in der [Dokumentation für Apple-Entwickler](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)aus.|
|Wireless Zubehör-Konfiguration|Aktivieren der drahtlosen Zubehör Konfiguration das externen Zubehör Framework zum Projekt hinzugefügt und Ihre app MFi Wi-Fi Zubehör konfigurieren kann.||

### Schritte zum Aktivieren von Berechtigungen

1.  Funktionen in Ihre app zu aktivieren:

    1.  Navigieren Sie in Xcode zu Ihrer app Ziel, und klicken Sie im Bereich **Funktionen** auf.

    2.  Aktivieren Sie die entsprechenden Funktionen. Ausführliche Informationen zu jede Funktion und die richtigen Werte feststellen finden Sie unter [Hinzufügen von Funktionen, die](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) in den iOS Entwicklertools Bibliothek.

    3.  Beachten Sie alle IDs, die Sie während des Prozesses erstellt.

    4.  Erstellen, und melden Sie sich Ihre app umbrochen werden.

2.  Aktivieren Sie in Ihrem Profil provisioning Ansprüche:

    1.  Melden Sie sich bei der Apple-Entwicklercenter Mitglied.

    2.  Erstellen Sie ein provisioning Profil für Ihre app ein. Anweisungen finden Sie unter [So erhalten Sie die erforderlichen Komponenten Intune App umbrechen Tools für iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/).

    3.  Aktivieren Sie in Ihrem Profil provisioning dieselben Berechtigungen, die Sie in Ihrer app aufweisen. Sie müssen die gleichen IDs angeben, die Sie bei der Entwicklung Ihrer App angegeben haben.

    4.  Schließen Sie der Bereitstellung Profil-Assistent ab, und Laden Sie die Datei.

3.  Stellen Sie sicher, dass Sie alle erforderlichen Komponenten haben erfüllt, und klicken Sie dann die app umbrochen.

### Problembehandlung bei häufigen mit Berechtigungen
Wenn die App umbrechen Tool für iOS einen Anspruch Fehler angezeigt wird, versuchen Sie die folgenden Schritte zur Problembehandlung aus.

|Problem|Ursache|Auflösung|
|---------|---------|--------------|
|Fehler beim Analysieren der Ansprüche aus der Eingabewerte Anwendung generiert.|Das Tool für die App-umbrechen kann nicht die Ansprüche Datei lesen, die aus der app extrahiert wurde. Die Datei Ansprüche möglicherweise falsch formatiert.|Prüfen Sie die Datei Berechtigungen für Ihre app ein. Führen Sie hierzu die Anweisungen unter detaillierte aus. Wenn die Datei Ansprüche zu prüfen, aktivieren Sie für alle fehlerhafte Syntax. Die Datei sollte in XML-Format.|
|Ansprüche fehlen im Profil provisioning (fehlende Ansprüche aufgelisteten). Verpacken der app mit einem provisioning Profil, das diese Ansprüche enthält.|Es ist ein Konflikt zwischen den Ansprüchen im provisioning Profil aktiviert und die Funktionen, die in der app aktiviert. Dies gilt auch für die IDs bestimmter Funktionen (d. h., App Gruppen, Schlüsselbund Access usw.) zugeordnet.|Im Allgemeinen können Sie ein neues Profil für die Bereitstellung erstellen, das die gleiche Funktionalität wie der app ermöglicht. Wenn IDs zwischen dem Profil und die app nicht entsprechen, wird die App-Tool Textumbruch die IDs ersetzen, wenn es kann. Wenn Sie nach dem Erstellen eines neuen provisioning Profils weiterhin dieser Fehler zurückgegeben, können Sie versuchen, Ansprüche aus der app zu entfernen, indem Sie mit dem Parameter **– e** (siehe "verwenden den Parameter – e So entfernen Sie Ansprüche aus einer app Abschnitt unten).|

### Suchen die vorhandenen Ansprüchen einer signierten App
So überprüfen Sie vorhandenen Berechtigungen für eine app signierte und provisioning Profil

1.  Suchen nach der Datei .ipa und hat die Erweiterung in ZIP ändern.

2.  Erweitern Sie die ZIP-Datei aus. Dies erzeugt einen Nutzlast Ordner, der Ihre .app-Paket enthält.

3.  Verwenden Sie das Tool Codesign So überprüfen Sie die Berechtigungen auf das Paket .app wie folgt aus:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    wo `YourApp.app` ist der tatsächliche Name der .app-Paket.

4.  Verwenden Sie das Sicherheitstool überprüfen, dass die Berechtigungen für der app provisioning Profil eingebettet:

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    wo `YourApp.app` ist der tatsächliche Name der .app-Paket.

### Verwenden den Parameter – e Ansprüche aus einer app zu entfernen
Dieser Befehl entfernt alle aktivierten Funktionen, die in der app, die nicht in der Datei Ansprüche sind. Wenn Sie Funktionen entfernen möchten, die von der app verwendet werden, können sie Ihre app aufgehoben werden. Beispiel, in dem Sie fehlende Funktionen entfernen Möglicherweise ist, wenn Sie eine app Hersteller erstellte verfügen, die alle Funktionen standardmäßig enthält.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Sicherheit und Datenschutz für die app Tool umbrechen
Verwenden Sie die folgenden bewährten Methoden Sicherheit und Datenschutz, wenn Sie die Tool umbrechen app verwenden.

-   Das Signaturzertifikat provisioning Profil und die Line-of-Business-app, die Sie angeben, dass Sie verwenden, um das Tool umbrechen ausführen auf demselben Computer Mac sein muss. Wenn die Dateien auf einen FERNEN Pfad befinden, stellen Sie sicher, dass diese aus dem Mac-Computer zugegriffen werden kann. Der Pfad muss über IPsec oder SMB Signieren geschützt werden.

    In die Umgebrochene Anwendung importiert die [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Console sollten auf dem gleichen Computer, die das Tool ausgeführt werden. Wenn die Datei auf einen FERNEN Pfad ist, stellen Sie sicher, dass auf dem Computer mit zugegriffen der [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Console. Der Pfad muss über IPsec oder SMB Signieren geschützt werden.

-   Die Stelle, an der das app Umbruch Tool vom Microsoft Download Center-Website heruntergeladen wurde Umgebung muss über IPsec oder SMB Signieren geschützt werden.

-   Die app, die Sie verarbeiten muss aus einer Quelle trust-worthy, um sicherzustellen, dass Schutz vor Angriffen stammen.

-   Stellen Sie sicher, dass der Ausgabeordner im Tool Umbruch app angegebenen geschützt werden, insbesondere dann, wenn es sich um einen remote-Ordner ist.

-   iOS-apps, die Sie im Dialogfeld eine Datei hochladen enthalten können Benutzerberechtigungen zum umgehen Ausschneiden, kopieren und Einfügen von Einschränkungen bei der app angewendet. Beispielsweise kann ein Benutzer im Dialogfeld Datei hochladen verwenden, ein Bildschirmabbild des app-Daten hochladen.

-   Wenn Benutzer Dokumentordners Geräts aus innerhalb einer Umgebrochene app überwachen, möglicherweise einen Ordner namens **.msftintuneapplauncher**angezeigt. Wenn diesen Ordner geändert oder gelöscht wird, kann dies beeinträchtigt werden das richtige Funktionieren des eingeschränkten apps.

### Siehe auch
- [Entscheiden Sie, wie apps für mobile anwendungsverwaltung mit Microsoft Intune vorbereiten](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Verwenden Sie das SDK apps für mobile anwendungsverwaltung aktivieren](use-the-sdk-to-enable-apps-for-mobile-application-management.md)
