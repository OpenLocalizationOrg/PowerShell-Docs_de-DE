---
title: Konfigurieren von Richtlinien MAM in der Intune-Verwaltungskonsole | Microsoft Intune
description: "Informationsverwaltungsrichtlinien in Microsoft Intune mobilen Anwendung können Sie die Funktionalität der apps zu ändern, die Sie bereitstellen, um Ihnen helfen, diese mit Compliance und Sicherheitsrichtlinien Ihres Unternehmens auszurichten."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 1584022db4b312919f88ef39dd3912c47b859099
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren und Bereitstellen von mobilen Anwendung Informationsverwaltungsrichtlinien in der Microsoft-Intune-Verwaltungskonsole
Mobile-Anwendung (MAM) Informationsverwaltungsrichtlinien in Intune Microsoft können Sie die Funktionalität der apps ändern, die Sie bereitstellen, um Ihnen helfen ihnen mit Ihres Unternehmens Compliance- und auszurichten. Sie können beispielsweise Ausschneiden, kopieren und von Einfügeoperationen innerhalb einer verwalteten app einschränken oder konfigurieren eine app aus, um alle Weblinks innerhalb einer verwalteten Browser zu öffnen.

Unterstützung für Mobile Anwendung Management Richtlinien:

-   Geräte, die Android 4 und höher ausgeführt werden.

-   Geräte, die iOS 8.0 und höher ausgeführt werden.

> [!TIP]
> Informationsverwaltungsrichtlinien mobilen Anwendung unterstützen Geräten, die mit Intune registriert sind.
>
> Wenn Sie Informationen dazu, wie Sie die app Informationsverwaltungsrichtlinien für Geräte erstellen, die Intune verwalten nicht gefunden werden, finden Sie unter [Verwenden von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune schützen app-Daten](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

Im Gegensatz zu anderen Intune-Richtlinien Sie eine mobile Anwendung zur Dokumentverwaltungsrichtlinie nicht direkt bereitstellen. In diesem Fall ordnen Sie die Richtlinie die app, die Sie einschränken möchten. Wenn die app bereitgestellt und auf Geräten installiert ist, werden die Einstellungen, die Sie angeben wirksam werden.

Um Einschränkungen zu einer app anwenden möchten, muss die app Microsoft Intune App SDK einbinden. Es gibt drei Methoden zum Abrufen von diesem Typ der app aus:

-   **Verwenden Sie eine app Richtlinie verwaltet**. Eine Richtlinie verwalteten app hat die App SDK in erstellt wurde. Wenn diese Art von app hinzufügen möchten, geben Sie eine Verknüpfung mit der eine app Store wie Google Play iTunes-Store. Keine weitere Verarbeitung ist für diese Art von app erforderlich. Weitere Informationen finden Sie in der [Liste der apps, die mit Microsoft Intune mobilen Anwendung Informationsverwaltungsrichtlinien verwendet werden können](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

-   **Verwenden einer Umgebrochene app**. Eine Umgebrochene app handelt es sich um eine app, die Sie erneut Verpacken, um die App SDK mithilfe des Microsoft Intune App umbrechen Tools enthalten. Dieses Tool wird in der Regel zum Unternehmen apps zu verarbeiten, die im Haus erstellt wurden. Sie können sie um apps zu verarbeiten, die aus dem app Store heruntergeladen wurden. Weitere Informationen finden Sie unter [Vorbereiten iOS-apps für mobile anwendungsverwaltung mit dem Microsoft Intune App umbrechen Tool](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) und [Android vorbereiten apps für mobile anwendungsverwaltung mit dem Microsoft Intune App umbrechen Tool](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

- **Schreiben Sie Ihre eigenen app, die das Intune App SDK übernimmt**. Das Intune App SDK können Sie die app Verwaltungsfunktionen in einer app integrieren, während Sie geschrieben werden. Weitere Informationen finden Sie unter [Intune App SDK Übersicht](/intune/develop/intune-app-sdk).

Hilfe bei der Auswahl zwischen der App-Tool Textumbruch und das Intune App SDK finden Sie unter [entscheiden, wie apps für mobile anwendungsverwaltung mit Microsoft Intune vorbereiten](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

Einige verwaltete apps, wie die Outlook-app für iOS und Android unterstützt *mehrere Identität*. Dies bedeutet, dass Intune Management Einstellungen auf corporate Konten oder Daten in der app eingrenzen.

Verwenden beispielsweise die Outlook-app:

-   Wenn der Benutzer ein Ihres Unternehmens-e-Mail-Konto und ein persönliches e-Mail-Konto konfiguriert hat, Intune betrifft nur das Konto Ihres Unternehmens Einstellungen für, und verwaltet das persönliche Konto nicht.

-   Wenn das Gerät Rente oder unenrolled, werden nur die Outlook-Unternehmensdaten vom Gerät entfernt.

-   Das Konto Ihres Unternehmens müssen dasselbe Konto, das verwendet wurde, um das Gerät mit Intune registrieren.

> [!TIP]
> Wenn Sie Intune mit Konfigurations-Manager, verwenden, finden Sie unter [Steuerelement Apps verwenden Mobile Anwendung Informationsverwaltungsrichtlinien im Konfigurations-Manager](https://technet.microsoft.com/library/mt131414.aspx).

## Erstellen und Bereitstellen einer app mit einem mobilen Anwendung zur Dokumentverwaltungsrichtlinie

-   **Schritt 1:** Erhalten Sie den Link zu einer Richtlinie verwalteten app, erstellen Sie eine app Umgebrochene, oder verwenden Sie das Intune App SDK zum Schreiben einer app MAM aktiviert.

-   **Schritt 2:** Veröffentlichen Sie die app in Speicherplatz verschwendet Cloud.

-   **Schritt 3:** Erstellen einer mobilen Anwendung zur Dokumentverwaltungsrichtlinie.

-   **Schritt 4:** Ordnen Sie die app einer mobilen Anwendung zur Dokumentverwaltungsrichtlinie, und klicken Sie dann bereitstellen Sie die app.

-   **Schritt 5:** Überwachen der app-bereitstellungs.

## Schritt 1: Abrufen der Link zu einer verwalteten Richtlinie-app, eine Umgebrochene app erstellen, oder verwenden Sie das Intune App SDK, schreiben eine app MAM aktiviert

Suchen Sie aus dem app Store, und notieren Sie die URL der Richtlinie verwalteten app, die Sie bereitstellen möchten. Die URL für die Microsoft Word für iPad-app beträgt beispielsweise **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.


## Schritt 2: Veröffentlichen der app in der Cloud-Speicherplatz
Wenn Sie eine verwaltete app veröffentlichen, unterscheiden sich die Verfahren je nachdem, ob Sie Veröffentlichen einer Richtlinie verwaltet app oder eine app, die mithilfe von verarbeitet wurde die Microsoft Intune App umbrechen Tool für iOS.

#### Wenn Sie eine Richtlinie veröffentlichen verwaltete app

1.  Wenn Sie die app in der Cloud Speicherplatz hochladen bereit sind, folgen Sie den Anweisungen in [Hinzufügen von apps für mobile Geräte in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  IOS-apps wählen Sie **aus dem App Store-App für iOS von verwaltete** unter **Wählen Sie aus, wie diese Software Geräte zur Verfügung gestellt werden**.

    Wählen Sie für Android-apps **externer Link**aus.

3.  Geben Sie unter **angeben die URL**die URL, mit der Richtlinie verwalteten, die Sie zuvor notiert haben.

Nach Beendigung des Uploads sehen **Ja** für **App Informationsverwaltungsrichtlinien** Sie auf der Seite **Eigenschaften der Software** für die app hochgeladene.

Nachdem Sie überprüft haben, dass die app erfolgreich hochgeladen wird, fahren Sie mit Schritt 3 fort.

#### So veröffentlichen Sie eine app, die über die Microsoft Intune App umbrechen Tool verarbeitet wurde

1.  Wenn Sie die app in der Cloud Speicherplatz hochladen bereit sind, folgen Sie den Anweisungen in [Hinzufügen von apps für mobile Geräte in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Wählen Sie die **Software Installer** klicken Sie unter **Wählen Sie aus, wie diese Software Geräte zur Verfügung gestellt werden**.

3.  Wählen Sie die App-Pakets **für iOS (& #42;. IPA-Datei)** klicken Sie unter **Software Installer-Dateityp**.

Nach Beendigung des Uploads wird **Ja** für **App-Informationsverwaltungsrichtlinien** auf der Seite **Eigenschaften der Software** für die hochgeladene app angezeigt.

Nachdem Sie überprüft haben, dass die app erfolgreich hochgeladen wird, fahren Sie mit Schritt 3 fort.

## Schritt 3: Erstellen einer mobilen Anwendung zur Dokumentverwaltungsrichtlinie

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** &gt; **Übersicht** &gt; **Richtlinie hinzufügen**.

2.  Konfigurieren Sie und Bereitstellen Sie einer der **folgenden Richtlinien, je nach Typ des Geräts, dem Sie apps für konfigurieren möchten** :

    -   **Mobile Anwendung zur Dokumentverwaltungsrichtlinie (Android 4 und höher)**

    -   **Mobile Anwendung zur Dokumentverwaltungsrichtlinie (iOS 8.0 und höher)**

    Sie können empfohlene Einstellungen verwenden oder Anpassen der Einstellungen. Details finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Konfigurieren Sie die folgenden Einstellungen je nach Bedarf an. Die Optionen möglicherweise je nach Typ des Geräts abweichen, für die Sie die Richtlinie konfigurieren.

|Name der Einstellung|Details|
    |---------|--------------------|
    |**Namen**|Geben Sie einen Namen für diese Richtlinie ein.|
    |**Beschreibung**|Geben Sie optional eine Beschreibung für diese Richtlinie ein.|
    |**Einschränken von Webinhalten in einem corporate verwalteten Browser angezeigt werden.**|Wenn diese Einstellung aktiviert ist, werden alle Links in der app im verwalteten Browser geöffnet werden. Für diese Option entwickelt müssen Sie diese app zu Geräte bereitgestellt haben.|
    |**Verhindern, dass Android Sicherungskopien** oder **iTunes und iCloud Sicherungen verhindern**|Diese Einstellung deaktiviert die Sicherung von Informationen aus der app.|
    |**Zulassen der app, Daten in anderen apps übertragen**|Diese Einstellung gibt an, die apps, denen diese app Daten senden können. Datenübertragung an eine beliebige app, nicht zulassen ausgewählt werden können nur für andere verwaltete apps durchstellen zulassen oder Übergabe an eine beliebige app zulassen. <br /><br />Beispielsweise, wenn Sie keine Datenübertragung zulassen, schränken Sie Datenübertragung auf Dienste wie SMS messaging, Zuweisen von Bildern für Kontakte und Veröffentlichen von Beiträgen in Facebook oder Twitter.<br /><br />Für iOS-Geräte zwischen verwalteten und nicht verwalteten apps zu übertragende Dokument nicht verloren geht muss auch konfigurieren und Bereitstellen eine Richtlinie für mobile Geräte Sicherheit, die die Einstellung **Zulassen verwaltete Dokumente in andere apps nicht verwalteten**deaktiviert. Wenn Sie nur für andere verwaltete apps durchstellen zulassen, werden die Viewer Intune PDF- und Bild (falls bereitgestellt) zum Öffnen von Inhalt der jeweiligen verwendet werden.<br /><br />Darüber hinaus, wenn Sie diese Option **Richtlinie verwaltet Apps** oder **keiner**festlegen, die iOS 9-Funktion, die Spotlight suchen zum Durchsuchen von Daten in apps ermöglicht, blockiert.<br><br>Diese Einstellung steuert die Verwendung der Funktion öffnen In auf mobilen Geräten nicht. Zum Verwalten von öffnen In finden Sie unter [Verwalten von Datenübertragung zwischen iOS-apps mit Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).|
    |**Zulassen Sie app zum Empfangen von Daten aus anderen apps**|Diese Einstellung gibt an, die apps, denen diese app Daten empfangen kann. Datenübertragung von einem beliebigen app nicht zulassen ausgewählt werden können nur von anderen verwalteten apps durchstellen zulassen oder Übergabe aus einem beliebigen app zulassen.<br /><br />Wenn ein Benutzer Daten aus einer app greift auf, die nicht von einem mobilen Anwendung zur Dokumentverwaltungsrichtlinie verwaltet wird, werden die Daten als Unternehmensdaten und durch die Richtlinie geschützt ist. Dies gilt für iOS-apps dieser Support mit mehreren Identität (wo Intune Einstellungen für nur für corporate Konten oder Daten in der app angewendet wird). Oder dies gilt für ein Gerät registrierten mit einem mobilen Anwendung zur Dokumentverwaltungsrichtlinie angewendet.|
    |**Verhindern, dass "Speichern unter"**|Diese Einstellung deaktiviert die Verwendung der Option **Speichern unter** zum Speichern von Daten zu persönlichen Cloud-Speicherorte (wie etwa OneDrive oder Dropbox) in eine beliebige app, die dieser Richtlinie verwendet.|
    |**Einschränken der Ausschneiden, kopieren und Einfügen mit anderen apps**|Diese Einstellung gibt an, wie Ausschneiden, kopieren und Einfügen von Vorgängen mit der app verwendet werden können. Wählen Sie aus:<br /><br />**Blockiert**. Lassen Sie nicht ausschneiden, kopieren und von Einfügeoperationen zwischen dieser app und andere apps.<br /><br />Die **Richtlinie verwaltet Apps**. Zulassen Sie, Ausschneiden, kopieren und von Einfügeoperationen nur zwischen dieser app und andere verwaltete apps.<br /><br />Die **Richtlinie verwaltet-Apps mit Einfügen In**. Können Sie Daten ausgeschnittenes oder kopiertes aus dieser app nur in anderen verwalteten apps eingefügt werden. Zulassen von Daten des ausgeschnittenen oder kopierten aus einem beliebigen app in diese app eingefügt werden.<br /><br />**Eine beliebige App**. Setzen Sie keine Einschränkungen auf Ausschneiden, kopieren und Einfügen von Vorgängen zu oder, aus dieser app.<br /><br />Zum Kopieren und Einfügen von Daten zwischen verwalteten apps, müssen beide apps der **Richtlinie verwaltet Apps** oder **Richtlinie verwaltet Apps mit Einfügen In** Einstellung konfiguriert.|
    |**Einfache PIN für den Zugriff erfordern**|Diese Einstellung muss der Benutzer eine PIN eingeben, die sie angeben, dass diese app zu verwenden. Der Benutzer werden aufgefordert, dies das erste Mal eingerichtet werden, die sie die app ausgeführt werden.|
    |**Anzahl der Versuche vor dem Zurücksetzen der PIN**|Geben Sie die Anzahl der PIN-Eintrag Versuche, die bereitgestellt werden kann, bevor der Benutzer die PIN zurücksetzen muss.|
    |**Corporate Anmeldeinformationen für den Zugriff erfordern**|Diese Einstellung muss der Benutzer ihre corporate Anmeldeinformationen eingeben, bevor sie die app zugreifen können.|
    |**Gerät Konformität mit Richtlinien des Unternehmens für den Zugriff benötigen**|Diese Einstellung ermöglicht die app verwendet werden, nur wenn das Gerät nicht Jailbroken ist oder als Stamm.|
    |**Überprüfen Sie die Access-Anforderungen nach (Minuten)**|Geben Sie im Feld **Timeout** an den Zeitraum, bevor Sie die Access-Anforderungen für die app erneut geprüft werden, nachdem die app geöffnet wird.|
    |**Offline Nachfrist**|Wenn das Gerät offline ist, geben Sie den Zeitraum, bevor Sie die Access-Anforderungen für die app erneut geprüft werden.|
    |**Verschlüsseln Sie die app-Daten**|Diese Einstellung gibt an, dass alle Daten, die diese app zugeordnet werden verschlüsselt werden. Dies umfasst Daten extern gespeicherte, z. B. SD-Karten.<br /><br />**Verschlüsselung für iOS**<br /><br />Für apps, die eine Intune mobilen Anwendung zur Dokumentverwaltungsrichtlinie zugeordnet sind, werden die Daten statisch sind durch Verschlüsselung Gerät Ebene verschlüsselt, die das Betriebssystem bereitstellt. Dies wird über ein Gerät PIN-Richtlinie aktiviert, die der IT-Administrator festlegt. Wenn Sie eine PIN erforderlich ist, werden die Daten entsprechend den in der mobilen Anwendung zur Dokumentverwaltungsrichtlinie verschlüsselt werden. Wie in [den Modulen iOS-Verwendungen FIPS 140-2, die zertifiziert sind](http://support.apple.com/en-us/HT202739)Apple-Dokumentation erwähnt wird.<br /><br />**Verschlüsselung für Android**<br /><br />Für apps, die eine Intune mobilen Anwendung zur Dokumentverwaltungsrichtlinie zugeordnet sind, stellt Microsoft Verschlüsselung. Daten werden während der Datei e/a-Vorgänge synchron verschlüsselt werden.  Inhalt auf dem Gerätespeicher wird immer verschlüsselt werden. Die Verschlüsselungsmethode ist nicht FIPS 140-2 zertifiziert.|
    |**Blockieren Bildschirmaufnahme** (Nur android-Geräten)|Diese Einstellung gibt an, dass die Bildschirm Erfassungsfunktionen des Geräts blockiert werden, wenn jemand diese app verwendet wird.|
    
4. Wenn Sie fertig sind, wählen Sie die **Richtlinie speichern**.

Die neue Richtlinie wird in den Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt.

## Schritt 4: Zuordnen der app zu einer mobilen Anwendung zur Dokumentverwaltungsrichtlinie, und klicken Sie dann die app bereitstellen
Stellen Sie sicher, dass Sie wählen Sie aus der mobilen Anwendung zur Dokumentverwaltungsrichtlinie auf der Seite **Mobile App Management** im Dialogfeld **Bereitstellung verwalten** , die Richtlinie mit der app zugeordnet werden soll.

Details finden Sie unter [Bereitstellen von apps im Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> Wenn Sie das Gerät aus Intune unenrolled ist, Richtlinien werden aus der apps nicht entfernt. Alle apps, die angewendeten Richtlinien aufwiesen behält die Richtlinieneinstellungen aus, nach die app deinstalliert und neu installiert ist.

### Was zu tun ist, wenn eine app bereits auf Geräten bereitgestellt wird
Möglicherweise gibt es Situationen, in dem Sie eine app und dann eine der gezielte Benutzer bereitstellen oder Geräte bereits eine nicht verwaltete Version der app installiert ist. Zum Beispiel der Benutzer möglicherweise Microsoft Word aus dem app Store installiert haben.

In diesem Fall müssen Sie bitten Sie den Benutzer, die nicht verwaltete Version manuell zu deinstallieren, damit die verwaltete Version, die so konfiguriert, Sie dass installiert werden kann.

Jedoch für Geräte ausführen, die iOS 9 und höher Intune wird automatisch bitten Sie den Benutzer für die Berechtigung zum Übernehmen der Verwaltung von der vorhandenen app. Wenn sie einverstanden sind, werden die app von Intune verwaltet werden, und alle mobilen Anwendung Informationsverwaltungsrichtlinien, die Sie mit der app verknüpft werden auch angewendet werden.

> [!TIP]
> Ist das Gerät im Modus Kontrolle dauert Intune über die Verwaltung von der vorhandenen app ohne Erlaubnis des Benutzers.

## Schritt 5: Überwachen der app-bereitstellungs
Nachdem Sie eine app, die eine mobile Anwendung zur Dokumentverwaltungsrichtlinie zugeordnet ist bereitgestellt und erstellt haben, gehen Sie folgendermaßen vor, die app überwachen und Richtlinie Konflikte lösen.

#### Anzeigen des Status der Bereitstellung

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), **Gruppen** &gt; **Übersicht**.

2.  Führen Sie eine der folgenden Schritte aus:

    -   Wählen Sie **Alle Benutzer**aus, und doppelklicken Sie dann auf den Benutzer, dessen Gerät, das Sie auswerten möchten. Eine der Seite **Benutzereigenschaften** wählen Sie **Geräte**aus, und doppelklicken Sie dann auf das Gerät, das Sie auswerten möchten.

    -   Wählen Sie **alle Geräte** &gt; **auf allen mobilen Geräten**. Klicken Sie auf der Seite **Eigenschaften von Gerät Gruppe** wählen Sie **Geräte**aus, und doppelklicken Sie dann auf das Gerät, das Sie auswerten möchten.

3.  Wählen Sie von der Seite **Eigenschaften für Mobile Geräte** **Richtlinie** , um eine Liste von der mobilen Anwendung Informationsverwaltungsrichtlinien anzuzeigen, die mit dem Gerät bereitgestellt wurden.

4.  Wählen Sie die mobile Anwendung zur Dokumentverwaltungsrichtlinie, deren Status Sie anzeigen möchten. Sie können Details der Richtlinie im unteren Bereich anzeigen und erweitern Sie dessen Knoten, um die zugehörigen Einstellungen anzeigen.

5.  Unter den **Status** wird die Spalte mit den einzelnen von der mobilen Anwendung Informationsverwaltungsrichtlinien, **Conforms**, **entspricht (Ausstehend)**oder **Fehler** angezeigt. Wenn die ausgewählte Richtlinie ein oder mehrere Einstellungen in Konflikt aufweist, wird der **Fehler** in diesem Feld angezeigt.

6.  Nachdem Sie einen Konflikt festgestellt haben, können Sie in Konflikt stehende Richtlinieneinstellungen, wenn Sie diese Einstellung verwenden überarbeiten oder können Sie nur eine Richtlinie zu der app und die Benutzer bereitstellen.

### Wie Richtlinie Konflikte gelöst werden
Bei ein mobilen Anwendung Management Richtlinienkonflikt auf der ersten Bereitstellung an den Benutzer oder Gerät, werden der Einstellungswert bestimmte in Konflikt aus die Richtlinie bei der app bereitgestellt entfernt. Die app wird einen integrierte Konflikt Wert verwendet.

Bei ein mobilen app Management Richtlinienkonflikt auf spätere Bereitstellungen app oder dem Benutzer, wird der Wert bestimmte Einstellung in Konflikt auf die mobile-app zur Dokumentverwaltungsrichtlinie bereitgestellt, die bei der app nicht aktualisiert werden. Die app wird den vorhandenen Wert für diese Einstellung verwenden.

In Fällen, in denen das Gerät oder der Benutzer zwei in Konflikt stehenden Richtlinien erhält, gilt folgende Verhalten:

-   Wenn Sie eine Richtlinie bereits auf dem Gerät bereitgestellt wurde, werden die vorhandenen Richtlinieneinstellungen für die nicht überschrieben.

-   Wenn keine Richtlinie bereits auf dem Gerät bereitgestellt und zwei widersprüchliche Einstellungen bereitgestellt werden, ist die Standardeinstellung für das Gerät integriert verwendet.
