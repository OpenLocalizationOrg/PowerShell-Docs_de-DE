---
title: "Früheren Versionen | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
ms.openlocfilehash: 8d8ef81d5051af5ef8f81e2a8b0c784282a8ade4
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Intune Vorversionen
## August 2016
## August 2016
## App-Verwaltung
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### Ein- und ausgeblendete apps für iOS 9.3
Für Kontrolle Geräte dem iOS 9,3 oder höher ausgeführt wird können Sie in den iOS allgemeine Konfigurationsrichtlinien und ausgeblendete apps-Liste:
- Geben Sie eine Liste der apps, die von Benutzern ausgeblendet wird. Benutzer können nicht anzeigen oder diese apps zu starten.
- Geben Sie eine Liste der apps, die Benutzer anzeigen und starten können. Keine anderen apps können angezeigte oder gestartet wird.

Die apps, die Sie angeben können, enthalten beide apps, die Sie bereitgestellt haben, und der integrierten iOS-apps wie Nachrichten und Notizen. Details finden Sie unter [Microsoft Intune iOS Richtlinieneinstellungen]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
### Zugelassenen und blockierten apps Richtlinie für Samsung KNOX Geräte
Sie können nun eine benutzerdefinierte Richtlinie für Samsung KNOX Geräte konfigurieren, die Ihnen ermöglicht, erstellen eine der folgenden Aktionen aus:
- Eine Liste der apps, die auf dem Gerät ausführen gesperrt sind. Selbst wenn installiert ist, kann eine app, die in der Liste der blockierten definiert auf dem Gerät aktiviert werden.
- Eine Liste der apps, die Benutzer des Geräts zulässig sind, aus dem Google Play Store zu installieren. Keine anderen apps können aus dem Store installiert sein.

Diese Einstellungen können nur von Geräten verwendet werden, die Samsung KNOX ausgeführt werden.
Details finden Sie unter [Verwenden von benutzerdefinierten Richtlinien zum Zulassen oder apps für Samsung KNOX Geräte blockieren]( custom-policy-to-allow-and-block-samsung-knox-apps.md).
<!---TFS 1311629 checked --->
### Neue apps kompatibel mit mobilen Anwendung Informationsverwaltungsrichtlinien (MAM)
Die Yammer-app für [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) und [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) ist nun mit [Intune mobilen Anwendung Informationsverwaltungsrichtlinien (MAM)](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)kompatibel, unabhängig davon, ob das Gerät registriert ist.

Eine vollständige Liste der kompatiblen apps MAM finden Sie auf der Website [Microsoft Intune Anwendungspartnern](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) .
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Intune-Viewer-apps
Mit der Veröffentlichung von der app Freigabe neue RMS sind wir der folgenden Intune-Viewer-apps, zu Anfang in August 2016 entfernen:
- Intune AV-Viewer
- Intune PDF-Viewer
- Android aus Google Play Intune-Image-Viewer

Es wird empfohlen, anstelle der Intune-Viewer-apps mithilfe der neuen [app-Verwaltung von Informationsrechten (RMS Freigabe) für Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), dem Sie eine app anstelle von drei separate apps sicher corporate Dateien auf Android-Geräten anzeigen bereitstellen können. Wenn die Intune-Viewer-app nicht mehr unterstützt wird, aus dem Google-Speicher entfernt werden und nicht zur Verfügung für eine zukünftige Verwendung.

## Gerät-Verwaltung
### Android 7.0-Unterstützung
Intune bietet "Day 0"-Unterstützung für das demnächst Android 7.0 Betriebssystem für mobile Geräte.
<!---TFS 1262053--->
### Google Entfernen des remote-Kennung zurücksetzen Videofunktionen auf 7.0 Android-Geräten
Google ist die Möglichkeit für IT-Administratoren und Endbenutzer, die Kennung Android 7.0 Geräte per Remotezugriff zurücksetzen entfernen. IT-Administratoren konnte zuvor, Remote Kenncode des Benutzers, und Endbenutzer konnte ihre die Kennungen von der Website des Unternehmens Portal zurückgesetzt.



## Unternehmen Portal updates
### Unternehmen Portal-website
- **Feedback links vom Unternehmen-Portal an Microsoft** <br/>
Die Website Unternehmen Portal ermöglicht Endbenutzern, tippen Sie am unteren Rand der Seite, um Feedback an Microsoft senden, ihre Meinung zu der Website einen neuen "Feedback" Link. Das zusammengestellten, anonymes Feedback hilft Microsoft, das Unternehmen Portal-Website für Benutzer zu verbessern.
<!--- TFS 1313657 checked--->

### iOS
- **Minimalen iOS verwaltete Browserversion ans 8.0**<br/>
Die Microsoft Intune verwaltet Browser-app für iOS wurde aktualisiert, um Unterstützung für Geräte dem iOS 8.0 oder höher ausgeführt wird. Während 7.1-iOS-Geräte weiterhin die vorhandene verwaltete Browser-app verwenden können, sollten Sie die Benutzer zu iOS 8.0 oder höher für den Zugriff auf Aktualisieren und neue verwaltete Browser-Features vollständig nutzen.  
<!---TFS 1313253 checked--->

## Was wird in Kürze

### iOS-10-support
IOS 10 unterstützt Intune vollständig. Weitere Informationen wird der Veröffentlichung iOS 10 folgen.

### Wechselt zum Anfang der Azure-Active Directory-Gruppen in September 2016 Intune-Gruppen
Intune ist die Erstellung einer neuen Gruppe Verwaltungsoption, der als Benutzer und Gerät Gruppen in Intune Sicherheitsgruppen Azure Active Directory (AAD) verwendet wird. Diesen Gruppen werden für alle Verwaltung von Gruppen, Richtlinie Bereitstellung und Profil Bereitstellung **, wenn eine Einführung in die neue Azure-basierten Intune Administratorportal**verwendet werden.

Diese neue Erfahrung wird verhindert, dass Sie Gruppen zwischen Diensten, **zulassen, dass Sie Zugriff auf einige neue Features von Azure Active Directory Premium (AADP) Gruppe**, duplizieren müssen und Erweiterung mit PowerShell und Graph bereitstellen. Dies wird auch der Gruppe Verwaltungsoption über Enterprise Mobilität Management zusammengeführt werden.

Um den Wechsel zu Sicherheitsgruppen aktivieren, wird der Benutzeroberfläche in der **aktuellen Administrator Console** einigen Änderungen werden. **Diese Änderungen, und die Verwendung von AAD Sicherheitsgruppen enthalten, werden in der Dokumentation Intune aufgezeichnet**.

Kunden, die mit Intune nicht vertraut sind, werden die **Führen Sie einige der Sicherheit Gruppe Änderungen vor dem aktuellen Mandanten**angezeigt.

Zusätzlich zu den Änderungen in der Gruppe Verwaltung, **die folgende Funktionen werden nicht mehr unterstützt werden**:
- Ausschließen von Mitgliedern oder Gruppen beim Erstellen einer neuen Gruppe
- Gruppen **Aufgehobener Gruppierung Benutzer** und **Geräte aufgehobener Gruppierung**
- **Verwalten von Gruppen** in der Rolle Dienstadministrator
- Benutzerdefinierte Gruppe-basierte Alarme für Benachrichtigungsregeln
- Pivotieren mit Gruppen in Berichten
<!--- TFS 1295329--->

### Hinzufügen von 'Benachrichtigungen' Unternehmen-Portal für Android
Ein Update auf das Portal Unternehmen veröffentlicht für Android im September, in denen ein neues **Benachrichtigungen** -Symbol auf der Homepage vermittelt werden. Auf das Symbol tippen wird die **Benachrichtigungen** Seite zugreifen, die Ihre Endbenutzer alle Elemente angezeigt wird, die in der app-Portal Unternehmen wie Gerät Verstoßes, Registrierung aktualisieren und Registrierungs-Aktivierung Aufmerksamkeit erfordern. Wenn Sie auch Unternehmen Portal iOS-app verwenden, sehen Sie bereits die Benachrichtigungen auftreten. Mit der Einführung der Seite **Benachrichtigungen** sehen nicht die **Unternehmen Access** Einrichtungsseite Sie jedes Mal, wenn Sie starten oder das Unternehmen Portal für Android fortsetzen, solange das Gerät bereits registriert ist. Wir hören viele von Ihnen Endbenutzer Anleitungen erstellt haben und erweiterte Mitteilung schätzen, wenn Ihre Anleitungen/Screenshots aktualisieren möglicherweise erforderlich ist. Aktualisieren Sie Ihre Dokumentation die Anstehende Änderung in Erfahrung entsprechend. Suchen nach aktualisierten Screenshots hier: https://aka.ms/androidcpupdate.  

### Verbesserte wie iOS-Endbenutzer ihrer apps zu erhalten
Die folgenden Änderungen werden auf apps Kacheln in der Firma Portal-app für iOS verweisen Benutzer zu verschiedenen Sichten in einem einzigen Speicherort, der Website Unternehmen Portal für alle ihre apps im September bereitgestellt. Derzeit Apple Einschränkungen verbieten Line-of-Business, und verwalteten app apps von aufgeführt wird, in der app-Portal Unternehmen speichern und festlegen, dass Benutzer besuchen Sie die verschiedene Ansichten, um alle ihre apps zu finden.

- Der **Firma Apps** Kachel aktuell interessante zu einer Liste alle apps auf der Registerkarte alle die Unternehmen Portal-Website, und es auf die gleiche Weise funktionieren weiterhin. Der Name der Kachel ändert sich in **Alle Apps**.
- Die **Anderen Apps** Kachel derzeit für verweist auf eine Ansicht, in der app-Portal Unternehmen, die alle apps Listen, die Apple, dass die app Unternehmen Portal anzeigen ermöglicht. Der Kachelnamen ändert sich in **Bereitgestellte Apps**, und Tippen auf die Kachel Benutzer zur Registerkarte empfohlen der Website Unternehmen Portal dauert.
-  Die Kachel " **Kategorien** " verweist aktuell zu einer Ansicht, in der app-Portal Unternehmen, die Kategorien von apps listet. Der Kachel Name wird nicht geändert, aber es wird jetzt zeigen Sie auf der Registerkarte Kategorien im Unternehmen Portal-Website. Aktualisierte Screenshots finden Sie [hier](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Cloud-Wegweiser
Über anstehende Entwicklung für Intune mit der [Cloud-Plattform Wegweiser](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)informiert.

### Service veraltete Objekte
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Änderungen für die Unternehmen Portal-app für iOS-Support**<br/>
Im September werden alle Benutzer der Microsoft Intune Unternehmen Portal-app für iOS müssen Sie die neueste Version zu verwenden. Neue Benutzer werden nur die neueste Version herunterzuladen, und aktuellen Benutzer muss zu aktualisieren. Die neueste Version benötigt iOS 8.0 oder höher, daher Geräte mit älteren Versionen von iOS können nicht im Portal Unternehmen oder bis sie Geräts zu iOS 8.0 oder höher aktualisieren und dann auf die neueste Version die app-Portal Unternehmen aktualisieren zu registrieren. Registrierten Geräte Versionen unter iOS 8.0 ausgeführt werden weiterhin verwaltet werden und in der Administrator Intune-Verwaltungskonsole aufgeführt.  

- **Minimalen iOS verwaltete Browserversion ans 8.0**<br/>
Im August wird Intune eine aktualisierte Microsoft Intune verwaltet Browser-app für iOS freigeben, die unterstützt nur Geräte dem iOS 8.0 oder höher ausgeführt wird. Während iOS 7.1 Geräte weiterhin die vorhandene verwaltete Browser-app verwenden können, wenden Sie sich bitte sollten Sie die Benutzer auf iOS 8.0 aktualisieren oder höher zugreifen und neue verwaltete Browser-Features vollständig nutzen.  
<!---TFS 1313253--->

- **Unternehmen Portal apps für Windows 8 und Windows Phone 8 werden nicht mehr unterstützt wird** <br/>
Starten in Oktober 2016, wird Microsoft Intune Unterstützung für Windows 8 und Windows Phone 8 Unternehmen Portal apps deaktivieren. Unterstützung für Windows Phone 8-Plattform wird von Microsoft Intune auch deaktivieren. Daher werden Sie nicht möglicherweise registrieren oder aktualisieren alle Windows Phone 8-Geräte. Sie können weiterhin zum Verwalten von Windows Phone 8 und Windows 8-Geräten, die bereits registriert sind. Aktualisieren von Windows Phone 8 und Windows 8-Geräte mit Windows 8.1 und Windows Phone 8.1, und verwenden Sie die entsprechenden apps für Windows 8.1 und Windows Phone 8.1 Unternehmen Portal Verteilen von apps für diese Geräte ohne Ausbluten fortsetzen.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## Juli 2016
### App-Verwaltung
#### Verbessern der app bereitgestellt Profil aktualisieren-Benutzeroberfläche
Apple iOS Zeile des Business erstellte mobile-apps mit einem provisioning Profil enthalten und Code mit einem Zertifikat signiert. Wenn die app auf einem iOS-Gerät ausgeführt wird, wird iOS bestätigt die Integrität des iOS-app und erzwingt Richtlinien, die durch die Bereitstellung Profil definiert.

Signaturzertifikat aus, die Sie verwenden, um apps normalerweise melden Unternehmen dauert für 3 Jahre. Jedoch läuft ab das provisioning Profil nach einem Jahr ein. Mit diesem Update bietet Intune Tools, um die vorausschauende eine neue provisioning Profil Richtlinie Geräte bereitstellen, die apps, die in der Nähe Ablauf sind aufweisen, während das Zertifikat noch gültig ist. Weitere Informationen finden Sie unter [verwenden iOS mobilen provisioning Profil Richtlinien Ihrer Textzeile Geschäfts-apps auf dem neuesten Stand zu bleiben](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
#### Xamarin SDK für Intune apps steht.
Die Komponente Intune App SDK Xamarin können Sie die Intune Verwaltungsfunktionen für mobile-app auf Ihren mobilen iOS und Android-apps mit Xamarin erstellte aktivieren. Sie können die Komponente in der [Xamarin speichern](https://components.xamarin.com/view/Microsoft.Intune.MAM) , oder klicken Sie auf der [Seite Microsoft Intune Github](https://github.com/msintuneappsdk)suchen.
<!--- TFS 1061478 --->

### Gerät-Verwaltung
#### Höhere Gerät Registrierungs-Grenzwerte
Intune erhöht die maximale konfigurierbare Geräte Registrierung hinsichtlich von 5 15 Geräte pro Benutzer.
<!---TFS 1289896 --->

#### TeamViewer Integration für Computer mit Windows Intune-Clientsoftware ausgeführt
Remoteunterstützungssitzungen mit Windows-PCs unterstützen Endbenutzer Helpdesk Abteilungen herstellen kann [TeamViewer](https://www.teamviewer.com) Integration für Windows-PCs, die den Intune-Client ausgeführt werden. Windows 7, 8, 8.1 und Windows 10 umfasst. Details finden Sie unter [Allgemeine Windows-PC-Verwaltungsaufgaben mit dem Microsoft Intune Computer Client](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).
<!---TFS 1284856--->

### Unternehmen Portal updates
#### Unternehmen Portal-website
- **Verbesserte Endbenutzer bei der Registrierung von Windows-Geräten**<br/>
Wenn Sie bedingte Access verwenden, haben die Registrierung Schritte für Windows 8.1 und Windows-10-Desktop 10 unter Windows Mobile auf der Website des Unternehmens Portal erläutert wurde. Benutzer sehen nun separate "Gerät-Registrierung" und "Arbeitsplatz teilnehmen" Schritte, denen es einfacher für sie den Status des Geräts anzeigen und den Prozess abzuschließen, wenn eines Fehlers Arbeitsplatz teilnehmen (WPJ eintreten). Die getrennten Schritten werden auch zur Problembehandlung für IT-Administratoren vereinfacht das erwartet. Zuvor, würde beim Endbenutzer versucht zu registrieren, und alle Registrierungs-Schritte erfolgreich verlaufen, eine Ausnahme bilden jedoch WPJ ist, registrierte Gerät nicht in der Liste der Geräte für Benutzer zu identifizieren, angezeigt Verwirrung, die für Benutzer.

#### Android
- **Portal Unternehmen Android-app**<br/>
Wenn Android Endbenutzer angezeigt wird, dass eine Fehlermeldung angezeigt, die besagt Geräts ein erforderliches Zertifikat nicht angezeigt wird, können sie eine Schaltfläche "How to dieses Verhalten zu beheben", um [Schritte](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) zum Installieren des fehlende Zertifikats erhalten tippen. Wenn Benutzer führen Sie die Schritte aus, aber ein zusätzliches "fehlende Zertifikat" finden Sie unter Fehlermeldung angezeigt, sie werden aufgefordert, wenden Sie sich an ihre IT-Administrator, und geben Sie diesen [Link](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), die Schritte, die IT-Administratoren verwenden können enthält, um das Zertifikat Problem zu beheben.

- **Seite geladen app-Installationen auf registrierten Geräte einschränken**<br/>
Android-Geräten können nicht mehr Applikationen über die Website Unternehmen Portal installieren, es sei denn, Sie die Geräte mithilfe der app Intune Unternehmen Portal für Android in Intune registriert wurden.
<!---TFS 1299082--->

#### iOS
- **Ändert sich in Device Registrierungs-Managers Konten in der Firma Portal-app für iOS**<br/>
Zum Verbessern der Leistung und Skalierung zeigt Intune nicht mehr alle Gerät Registrierungs-Manager (DEM) Geräte im Bereich **Meine Geräte** des Unternehmens Portal iOS-app. Nur die lokale Geräte mit der app angezeigten, wird und nur dann, wenn sie über die app Unternehmen Portal registriert ist.

Der von DEM Benutzer möglicherweise Aktionen auf dem lokalen Gerät ausführen, aber remote-Verwaltung von anderen Geräten registrierten kann nur der Administrator Intune-Verwaltungskonsole ausgeführt werden. Darüber hinaus ist Intune mit DEM Konten mithilfe des Apple-Gerät Registrierungs-Programms oder das Tool Apple-Konfiguration veralteter. Beide Registrierungsmethoden folgenden unterstützen bereits Benutzer zugängliche Registrierung für freigegebene iOS-Geräte.

Verwenden Sie nur von DEM Konten auf, wenn Benutzer zugängliche Registrierung für freigegebene Geräte nicht verfügbar ist. Weitere Informationen finden Sie unter [Registrieren Ihres Unternehmens im Besitz eines Geräte mit dem Gerät Registrierungs-Manager in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### Ändern der Namen für die Windows-features
- [Microsoft Passport für Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) wird jetzt als **Windows Hallo für Unternehmen**bezeichnet.
- [Enterprise-Datenschutz](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) ist jetzt als **Windows Schutz von Informationen**bezeichnet.

## Juni 2016
### Intune-Dienststatus
Service-Dienststatus-Informationen für Intune wurde an einem zentralen Speicherort mit anderen Microsoft-Diensten verschoben. Sie finden diese Informationen jetzt im Verwaltungsportal Office 365 unter Dienststatus. Weitere Informationen finden Sie unter [diesen Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### App-Verwaltung
- **Erweiterte Windows 10 Enterprise Daten Richtlinienkonfiguration erzielen.** Wir haben Verbesserungen an der Windows-10 Enterprise Daten Schutz Richtlinienkonfiguration auftreten, um das Erstellen von Regeln für die app Netzwerk Begrenzungslinie Definition und andere Einstellungen für Enterprise-Schutz angeben. Weitere Informationen finden Sie unter [erstellen eine Enterprise Daten (EDP) Schutzrichtlinie Microsoft Intune verwenden](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### Gerät-Verwaltung
- **Windows Defender Richtlinie zum Schutz vor potenziell unerwünschte apps einrichten.** Eine neue Einstellung für Windows Defender mit dem Namen **Potenziell unerwünschte Anwendung Erkennung** wurde auf die Richtlinie allgemeine Konfiguration für Windows 10 Desktop- und Mobile hinzugefügt. Verwenden Sie diese Einstellung zum Schutz für Windows Desktopcomputern gegen das Ausführen von Software klassifiziert von Windows Defender als potenziell unerwünschte registriert. Sie können schützen Sie sich vor diesen Anwendungen ausgeführt, oder verwenden Audit Modus Bericht aus, wenn eine potenziell unerwünschte Anwendung installiert ist. Weitere Informationen finden Sie unter [Richtlinieneinstellungen 10 Windows Intune Microsoft](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune) .
<!---TFS 1244478--->

### Bedingte access
- **Cisco ISE Netzwerkzugriffsrichtlinie Intune.**  Kunden, verwenden Sie die Cisco Identität Dienst Engine 2.1 (ISE) und auch Microsoft Intune, können eine Zugriffsrichtlinie Steuerelement Netzwerk in ISE festlegen.

    Diese Richtlinie verwenden, müssen der Geräte über WiFi oder VPN mit dem Netzwerk eine Verbindung herstellen müssen folgenden Bedingungen erfüllen, bevor sie zugreifen dürfen:

    * Müssen von Intune verwaltet werden
    * Mit einem beliebigen bereitgestellten Intune Compliance-Richtlinien werden müssen

 Endbenutzer nicht kompatible Geräte werden aufgefordert, registrieren, und beheben alle Kompatibilitätsprobleme um Zugriff zu erhalten.
- **Bedingte Zugriff für Browser.** Sie können eine bedingte Zugriffsrichtlinie für [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) und [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) festlegen, dass sie nur aus den unterstützten Webbrowsern auf verwalteten und kompatible iOS und Android zugegriffen werden kann. Endbenutzer, die Anmeldung bei Outlook Web Access (OWA) und SharePoint-Websites mit iOS und Android-Geräten versuchen Sie werden aufgefordert, registrieren Geräts mit Intune auch unter ', um alle Kompatibilitätsprobleme zu beheben, bevor die Anmeldung abgeschlossen werden kann.
<!---TFS 1175844--->

- **Dynamics CRM Online unterstützt bedingten Zugriff.** Sie können eine bedingte Zugriffsrichtlinie für [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) festlegen, damit nur von verwalteten und kompatible iOS und Android zugegriffen werden kann. Ende-Benutzer, die versuchen, melden Sie sich bei der Dynamics CRM mobile-app für iOS und Android werden aufgefordert, mit Intune registrieren als auch alle Kompatibilitätsprobleme zu beheben, bevor Anmeldung abschließen zu kann.
<!---TFS1295358--->

##E Unternehmen Portal updates

#### Portal Unternehmen Android-app

- Beim Anwenden von IT-Administratoren der neuen "Erfordern, dass Geräte Installation von apps von unbekannten Quellen (Android 4.0 +) verbieten"-Richtlinie, Endbenutzer mit Android 4.0 oder höher werden die Meldung angezeigt wird, "Installation von unbekannten Quellen muss deaktiviert werden." Benutzer, wechseln Sie zu **Einstellungen**müssen > **Sicherheit**und deaktivieren Sie **unbekannten Quellen**. Ein Link in der Nachricht Compliance ermöglicht Benutzern das Anzeigen weiterer [Informationen](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) zu der Nachricht und warum benötigt wird sind die Einstellung zu deaktivieren.

- Wenn IT-Administratoren die neue "Erfordern, dass Geräte aktiviert haben, Scannen von apps für Sicherheitsrisiken (Android 4.0 +)" Richtlinie anwenden möchten, wird der Endbenutzer mit Android 4.0 oder höher die Nachricht "Gerät für Sicherheitsrisiken scannen." angezeigt. Müssen Benutzer wechseln Sie zu **Einstellungen** > **Google** > **Sicherheit**und **Gerät für Sicherheitsrisiken Scannen**aktivieren. Ein Link in der Nachricht Compliance kann Benutzer erhalten Sie weitere [Informationen](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) über die Meldung und warum sie erforderlich werden sind, um die Einstellung zu aktivieren.

- Beim Anwenden von IT-Administratoren das neue "erfordern, dass USB-Debuggen deaktiviert ist (Android 4.2 +)" Richtlinie, Endbenutzer mit Android 4.2 oder höher wird die Meldung angezeigt, "USB-Debuggen muss deaktiviert werden." Müssen Benutzer wechseln Sie zu **Einstellungen** > **Entwicklertools Optionen**, und deaktivieren Sie **USB Debuggen**. " Ein Link in der Nachricht Compliance ermöglicht Benutzern das Anzeigen weiterer [Informationen](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) zu der Nachricht und warum benötigt wird sind die Einstellung zu deaktivieren.

- Beim Anwenden von IT-Administratoren der neue "Android Sicherheit Minimum patch Level (Android 6.0 +)"-Richtlinie, Endbenutzer mit Android 6.0 oder höher werden die Meldung angezeigt wird, "dieses Gerät erfüllt nicht die minimalen Android Patch Sicherheitsstufe." Benutzer müssen den erforderlichen Sicherheits-Patch installieren. Ein Links in der Nachricht Compliance ermöglicht dem Benutzer erhalten [Informationen](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) dazu, wie Sie den erforderlichen Sicherheits-Patch installieren und die Sicherheitspatch sehen sie aktuell installiert haben.

#### Unternehmen Portal-app für iOS

- Wenn Endbenutzer Branchen apps installieren, wird jetzt eine verbesserte app-Installation integriertes Feature angezeigt. Wenn die app-Installation sehr lange dauert, können Benutzer ihr Gerät zum Erzwingen des Synchronisierung Prozess fortgesetzt manuell synchronisieren. Um den Endbenutzer Anweisungen finden Sie unter [Ihrem iOS-Gerät manuell synchronisieren](/Intune/EndUser/sync-your-device-manually-ios).

- Die Microsoft Intune Unternehmen Portal-app für iOS wurde aktualisiert, iOS Version 8.0 und höher unterstützt. Dieses Update bedeutet, dass Endbenutzer kann die app Unternehmen Portal installieren und neue Geräte in Intune registrieren, nur dann, wenn das Gerät iOS Version 8.0 oder höher ausgeführt wird. Benutzer, die bereits Geräte registriert haben, die auf eine nicht unterstützte Version von iOS ausgeführt werden können weiterhin im Unternehmen Portal app zu verwenden, die auf ihrem Gerät ist.


## Mai 2016

Alle diese Features werden auch für hybridbereitstellungen (Konfigurations-Manager mit Intune) unterstützt werden. Weitere Informationen zu neuen Features von Hybrid schauen Sie sich die Seite [Hybrid, was neu ist](https://technet.microsoft.com/en-us/library/mt718155.aspx) .

### Dokumentation
Willkommen Sie bei der Preview-Version von [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Dies ist eine vollständig neue, moderne Inhalt Plattform ausgelegt, damit es einfacher für Sie, unsere Kunden zu verstehen und Intune verwenden.
Weitere Informationen über alle neuen Funktionen finden Sie unter [Einführung in docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Intune-Dienststatus
Service-Dienststatus-Informationen für Intune wurde an einem zentralen Speicherort mit anderen Microsoft-Diensten verschoben. Sie finden diese Informationen jetzt im [Verwaltungsportal von Office 365](https://portal.office.com/Admin/Default.aspx) unter **Dienststatus**.
Weitere Informationen finden Sie [in diesem Blogbeitrag](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)aus.


### App-Verwaltung
- **MAM SDK: Unterstützung PIN Länge Konfiguration.** Sie werden können die Länge der die PIN für MAM apps ähnlich wie mit einem Gerät PIN angeben. Dieser Vorgang erfordert Endbenutzern, zu der neuen Einschränkungen einhalten, die Sie festgelegt werden. Einen leicht abgewandelte PIN-Bildschirm, um mehr Eingabewerte berücksichtigen wird angezeigt. Details finden Sie unter [MAM Richtlinieneinstellungen für Android](android-mam-policy-settings.md)und [MAM Richtlinieneinstellungen für iOS](ios-mam-policy-settings.md).

- **Skype for Business für iOS und Android.** Sie können jetzt Skype for Business mit eigenständiger [MAM ohne Registrierungsrichtlinien](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)Zielgruppen ausrichten. Nachdem die Benutzer angemeldet haben, werden die MAM Richtlinien angewendet werden.

- **Neue apps für die Verwaltung von mit MAM Richtlinien zur Verfügung.** Der Microsoft Word, Excel und PowerPoint-apps für Android können nun MAM Richtlinien auf Geräten zugeordnet werden, die nicht mit Intune registriert sind. Eine vollständige Liste der unterstützten apps finden Sie auf der Seite [Microsoft Intune Anwendungspartnern](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) der mobilen Microsoft Intune Galerie.


### Unternehmen Portal updates

#### Portal Unternehmen Android-app
- **Endbenutzer Spruch Benachrichtigungen**: Endbenutzer sehen nun Spruch Benachrichtigungen aus der app Android Unternehmen Portal aus, wenn diese aktivierten Geräte registrieren oder Entfernen von aktivierten Geräte vom Unternehmen-Portal.

- **Ändert sich in Device Registrierungs-Managers Konten in der app Android Unternehmen Portal aus.** Zum Verbessern der Leistung und Skalierung ist Intune nicht mehr alle Gerät Registrierungs-Manager (DEM) Geräte im Bereich Meine Geräte der app Android Unternehmen Portal angezeigt. Nur die lokale Geräte mit der app angezeigten, wird und nur dann, wenn sie über die app Unternehmen Portal registriert ist. Der von DEM Benutzer möglicherweise Aktionen auf dem lokalen Gerät ausführen, aber remote-Verwaltung von anderen Geräten registrierten kann nur der Administrator Intune-Verwaltungskonsole ausgeführt werden.

#### Unternehmen Portal-website
- **Unternehmen Portal Website: Gerät Kennung Banner enthält weitere Informationen für den Endbenutzer.** Endbenutzer können jetzt vereinfacht das Gerät identifizieren, die, das Sie ausgewählt haben, wenn die Website Unternehmen Portal verwendeten. Wenn das falsche Gerät ausgewählt ist, werden sie das richtige Gerät auswählen, indem Sie auf den Link **hier tippen Sie auf** der Startseite Banner tippen.

## Was wird in Kürze
- **Nachricht Center Benutzeroberfläche Onboarding**. Als Teil der Migration von Intune in im [Verwaltungsportal von Office 365](https://portal.office.com/)beginnt wir nutzen ihre Nachrichtencenter, um die neuen Features und anderen Benachrichtigungen kommunizieren. Auch nach der Installation der Companion mobilen-app für Office 365-Administrator können lassen Sie sich auf Ihrem Mobiltelefon und einfach alle Nachrichten an Benutzer oder einer Verteilung Alias weiterleiten.
Beginnen wir mit unseren Mai das Nachrichtencenter mit Version, um Sie zu benachrichtigen, wenn Updates abgeschlossen werden und Informationen zu den neuen und verbesserten Features von Intune enthalten. Schauen Sie sich das Nachrichtencenter heute, indem Sie im [Verwaltungsportal von Office 365](https://portal.office.com/) anmelden und die Option NACHRICHTENCENTER im linken Navigationsbereich auswählen.

- **Änderungen an Gerät Registrierungs-Manager-Konten**. Zum Verbessern der Leistung und Skalierung ist Intune nicht mehr mit **allen** Gerät Registrierungs-Manager (DEM) Geräte im Bereich **Meine Geräte** des Unternehmens Portal iOS-app. Nur die lokale Geräte mit der app angezeigten, wird und nur dann, wenn sie über die app Unternehmen Portal registriert ist. Der von DEM Benutzer möglicherweise Aktionen auf dem lokalen Gerät ausführen, aber remote-Verwaltung von anderen Geräten registrierten kann nur der Administrator Intune-Verwaltungskonsole ausgeführt werden. Darüber hinaus ist Intune mit DEM Konten mithilfe des Apple-Gerät Registrierungs-Programms oder das Tool Apple-Konfiguration veralteter. Beide Registrierungsmethoden folgenden unterstützen bereits Benutzer zugängliche Registrierung für freigegebene iOS-Geräte. Verwenden Sie nur von DEM Konten auf, wenn Benutzer zugängliche Registrierung für freigegebene Geräte nicht verfügbar ist.

### Cloud-Wegweiser
Über anstehende Entwicklung für Intune mit der [Cloud-Plattform Wegweiser](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)informiert.

### Service veraltete Objekte
- **Intune-Viewer-apps.** Mit der Veröffentlichung von den neuen RMS app freigeben sind wir die folgenden Intune-Viewer-apps, Anfang August 2016 zu entfernen:
    - Intune AV-Viewer
    - Intune PDF-Viewer
    - Android aus Google Play Intune-Image-Viewer

  Statt der Intune-Viewer-apps zu verwenden, empfiehlt es sich mit neuen Verwaltung von Informationsrechten (RMS-Freigaben) app für Android, dem Sie eine app anstelle von drei separate apps sicher corporate Dateien auf Android-Geräten anzeigen bereitstellen kann. Weitere Informationen zu den RMS app (mit dem Link zu Dokumentation) freigeben.

- **Benutzerdefinierte Gruppe als Ziel der Benachrichtigung Regeln entfernen.**
Definieren Sie Intune Benachrichtigungsregeln, die eine e-Mail-Benachrichtigung zu von Intune gesendet werden soll. Aktuell, können Sie konfigurieren Benachrichtigungsregeln zum Senden von e-Mails für alle Benutzer der Geräte in einer Intune Gerätegruppe, die Sie erstellt haben. Von wird um Juni 1st 2016 weiterleiten, Verschieben von Benutzern erstellte Gruppen verwendet, nicht mehr unterstützt werden.

    Heute, würden Sie zum Adressieren einer Benachrichtigungsregel zu einer Gruppe, dass Sie über die Microsoft Intune-Verwaltungskonsole erstellt haben, die folgenden Schritte durchführen:

    Klicken Sie im Arbeitsbereich **Administrator** klicken Sie auf **Regeln Benachrichtigung** > **Neue Regel erstellen**

    Wählen Sie in Schritt 2 des Assistenten zum Erstellen einer Benachrichtigung Regel Device-Gruppen die Regel konzipiert ist. Dieser Schritt, "Gerät auswählen Gruppen", der Intune Verwaltungskonsole entfernt wird.

    Zeitachse für diese Änderung über der vorläufigen sieht wie folgt aus:
    - Im Juni 2016 werden die neue Mandanten nicht Schritt des Assistenten zum Erstellen einer Benachrichtigung Regel angezeigt. Vorhandene Mandanten sind nicht betroffen.
    - Um August 2016 werden einige vorhandenen Mandanten "Gruppen Gerät auswählen" im Assistenten nicht angezeigt wird.
    - Um Oktober 2016 erwarten wir, dass alle Mandanten "Gruppen Gerät auswählen" im Assistenten nicht angezeigt werden.


- **Änderungen in Unterstützung für iOS Unternehmen Portal app**. In den kommenden Monaten wird ein Update für die Microsoft Intune Unternehmen Portal-app für iOS, die unterstützt nur Geräte iOS 8.0 oder höher ausgeführt werden. Benutzer können keine registrieren neue Geräte Versionen unter iOS 8.0 ausgeführt werden. Registrierten Geräte mit Versionen unter iOS 8.0 weiterhin verwaltet werden und, für eine begrenzte Zeit, werden weiterhin mithilfe der app-Portal Unternehmen. Allerdings muss Geräten unter iOS 8.0 oder höher, um die neuesten Versionen der app Unternehmen Portal zugreifen. Wir empfehlen Ihnen, um Benutzer auf iOS 8.0 aktualisieren oder höher der neuen Intune-Features vollständig nutzen zu benachrichtigen.  


## April 2016
Alle diese Features sind für Kunden Hybrid ebenfalls unterstützt (Konfigurations-Manager integriert mit Intune).
### App-Verwaltung
- **MAM Benutzer Richtlinientreue.**
Sie können nun den [Status](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) Ihrer Anwendung Informationsverwaltungsrichtlinien für alle Benutzer in Ihrem Mandanten Azure Active Directory (AAD) anzeigen. Dies umfasst:
   - Geräte
   - Apps auf dem Gerät

   Statuswerte:

   **Checked in**: Zeigt an, die Richtlinie für den Benutzer bereitgestellt wurde, und die app wurde im Arbeitskontext verwendet und erfolgreich die Richtlinie empfangen.

    **Nicht eingecheckt**: Zeigt an, die Richtlinie für den Benutzer bereitgestellt wurde, aber die app wurde nicht im Arbeitskontext seit dann verwendet.


- **MAM-Steuerelemente, um Outlook-Kontakte synchronisieren (Android) zu verhindern.**
Eine neue Einstellung steht für [mobile anwendungsverwaltung](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) ohne Registrierung Gerät. Mit dieser Einstellung können Sie verhindern, dass eine Anwendung von Synchronisieren von Kontakten auf dem systemeigenen Adressbuch auf Android-Geräten. Wenn diese Einstellung aktiviert ist, werden zielgerichtete Applikationen mehr Kontakte zu einer systemeigenen Adressbuch gespeichert sein. Wenn diese Einstellung deaktiviert ist, werden zielgerichtete Applikationen Kontakte zum systemeigenen Adressbuch speichern können. Wenn Sie [Remote Wischen Sie ein Gerät oder eine app](wipe-managed-company-app-data-with-Microsoft-Intune.md), Kontakte, die bereits, in die native Adressbuch gespeichert wurden werden entfernt. Diese neue Einstellung wird zunächst von der Outlook-Anwendung auf dem Android-Geräten unterstützt.

### Gerät-Verwaltung
- **Telefon Zahl Kennung für Geräte Ihres Unternehmens gehören.** Telefone, die als "Unternehmen" kategorisiert werden werden jetzt mit ihren vollständigen Telefonnummer identifiziert beim, beispielsweise einen mobilen Gerät Inventory Bericht ausführen. Telefonnummern BYOD mit maskierte werden weiterhin ***, mit der nur die letzten 4 Ziffern angezeigt.


### Portal Updates für Unternehmen
**Android Unternehmen Portal-app** Benutzer, die nicht Geräts in Intune registriert haben und die nicht über das richtige Zertifikat installiert, werden nicht in der Lage, melden Sie sich bei der app Android Unternehmen Portal und werden die Meldung angezeigt, die "Kann nicht anmelden, da Ihr Gerät ein erforderliches Zertifikat fehlt." Die Nachricht enthält, die Benutzer tippen können, um Anweisungen zum Installieren des Zertifikats finden Sie unter "How to dieses Verhalten zu beheben" Link. Wenn Sie die einzelnen Schritte anzeigen, die Endbenutzer folgen, um das Problem zu beheben, finden Sie unter [Ihrem Gerät fehlt ein erforderliches Zertifikat](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Unternehmen Portal-app für iOS** Unterstützung für die Aktion Abruf-zu-aktualisieren des Inhalts auf der Startseite aktualisieren, wozu auch aufgelisteten apps, aufgelisteten Geräte sowie IT-Kontakt hinzugefügt wurde Informationen. Compliance oder Richtlinieninformationen, die ausgeführt werden kann, indem Sie die Kachel für Ihre aktuelle Gerät, und Tippen auf die Schaltfläche **Synchronisieren** , werden die Aktion Abruf-zu-aktualisieren nicht überprüft.

**App für Windows 10 Mobile und Windows Phone 8.1 Unternehmen-Portal** Wenn Endbenutzer Branchen apps installieren, wird jetzt eine verbesserte app-Installation integriertes Feature angezeigt. Wenn die app-Installation sehr lange dauert, können Benutzer ihr Gerät zum Erzwingen des Synchronisierung Prozess fortgesetzt manuell synchronisieren. Den Endbenutzer Anweisungen finden Sie unter [Synchronisieren von Ihrem Gerät manuell zum Beschleunigen der app-Installationen](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Unternehmen Portal-website** Wenn 10 unter Windows Mobile und Windows Phone 8.1 Branchen apps installiert werden, wird nun die folgenden neuen Status, angezeigt, die Sie weitere Details zu den Status ihrer Installation bereitstellen:

* **Warten auf Geräten für die Synchronisierung** – der Benutzer "Installieren" tippen weist und das Gerät jetzt versucht, mit der Infrastruktur Intune synchronisieren. Die Synchronisierung ist erforderlich, bevor die Installation abschließen können. Die Meldung "Wartet Gerät synchronisieren" ist ebenfalls ein Link, den Benutzer tippen können, um [Anweisungen](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) zum Geräts mit Intune manuell zu synchronisieren, wenn die Synchronisierung viel Zeit sehr oder angehalten wird angezeigt.
* **Herunterladen** – Download-Anforderung des Benutzers verarbeitet wird und das Gerät herunterladen und installieren die app.

Bevor diese Status hinzugefügt wurden, haben Benutzer verwechselt werden, wenn eine app-Installation langem, erstellen, da sie nur einen "Installieren" Status gesehen haben, die auf dem Bildschirm für Stunden bleiben möglicherweise. Hinzufügen der neuen Status bedeutet, dass Benutzer anstelle des Supports, jetzt der "Warten auf Gerät synchronisieren" tippen können verknüpfen Sie und folgen Sie den Anweisungen zum Erzwingen des Synchronisierung Prozess fortgesetzt.


## März 2016
### Was ist neu seit 29 März 2016
Mit Ausnahme der Update auf die Windows-10-Konfiguration von allgemeinen Richtlinie werden alle Features auf 29 März 2016, freigeben auch für Kunden Hybrid unterstützt (Konfigurations-Manager integriert mit Intune). Hybrid-Unterstützung für die Aktualisierung der Windows-10-allgemeine Konfiguration-Richtlinie ist in Kürze zur Verfügung. Bitte beachten Sie, dass einige dieser Features möglicherweise, dass der neuesten Version des Konfigurations-Manager erfordert.

### App-Verwaltung
- **MAM Steuerelemente zu verhindern, dass Outlook-Kontakten synchronisieren (iOS).** Eine neue Einstellung steht für mobile anwendungsverwaltung ohne Registrierung Gerät. Mit dieser Einstellung können Sie verhindern, dass eine Anwendung von Synchronisieren von Kontakten auf dem systemeigenen Adressbuch auf iOS-Geräte. Wenn diese Einstellung aktiviert ist, wird die app nicht mehr Kontakte zum systemeigenen Adressbuch speichern können. Wenn diese Einstellung deaktiviert ist, wird die app Kontakte zum systemeigenen Adressbuch speichern können. Wenn Sie ein Gerät Selektives zurücksetzen aus, werden alle Kontakte, die bereits, in die native Adressbuch gespeichert wurden entfernt. Diese neue Einstellung wird von der Outlook-Anwendung auf iOS-Geräte unterstützt. Weitere Details zu diesem und anderen Einstellungen finden Sie unter [Erstellen und Bereitstellen von MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Steuerung des Benutzerzugriffs
- **Skype für Business Online unterstützt bedingte Zugriff.** Sie können eine bedingte Zugriffsrichtlinie für Skype für Business Online festlegen, damit nur von verwalteten und kompatible iOS und Android zugegriffen werden kann. Ende-Benutzer, die Anmeldung bei der Skype for Business-mobile-app für iOS und Android versuchen Sie werden aufgefordert, mit Intune registrieren sowie alle Kompatibilitätsprobleme zu beheben, bevor Anmeldung abschließen zu kann. Weitere Informationen finden Sie unter [Verwalten Zugriff auf Skype für Business Online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Gerät-Verwaltung
- **Intune-Support für iOS 9.3.** Am Montag März 21. vorgestellt Apple die Verfügbarkeit von iOS 9.3. Wir wurden daran arbeiten, um sicherzustellen, dass Microsoft Intune mit der neuesten Version von Apple für mobile Betriebssystem, und [Wir sind zufrieden zu können, dass Intune verwalten von iOS 9.3 Geräte unterstützt](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)kompatibel ist ausgelastet.

  Alle vorhandenen Intune aktuell verfügbaren Features für die Verwaltung von iOS-Geräte weiterhin arbeiten nahtlos, wie Benutzer aktivierten Geräte auf iOS 9.3 aktualisieren. Darüber hinaus wird iOS 9.3 auch heute Hybrid Kunden unterstützt (Konfigurations-Manager integriert mit Intune).

- **Die Windows-10-Konfiguration von allgemeinen Richtlinie enthält jetzt Einstellungen zum Verwalten von Windows Defender unter registrierten Windows 10 PC.** Details finden Sie unter [Windows-10-Konfiguration Richtlinieneinstellungen in Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Unternehmen-portal

- **Windows-app-Paketen direkt von der Website des Unternehmens-Portal zur Verfügung.** Benutzer von Windows 8, Windows 8.1 und Windows RT-PCs können jetzt Windows-app-Paketen (mit der Erweiterung .appx) direkt von der Website des Unternehmens Portal installieren. In früheren Versionen waren bereitstellen oder Mitglieder der Gruppe zum Installieren des Unternehmens Portal-app auf ihren Geräten, apps zu installieren.

- **Benutzer können Remote Geräts von der Website des Unternehmens Portal sperren.** Eine neue Remote Sperren Option wurde zur Website Unternehmen Portal, damit Benutzer sperren Remote Geräts vom Portal aus, wenn ihr Gerät verloren geht oder gestohlen hinzugefügt. Lesen Sie die [Anweisungen Endbenutzer](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). Die folgende Tabelle enthält die Plattform Unterstützung für Remote Sperren für Intune Standalone und Intune mit Konfigurations-Manager.

|Plattform | Details zur Unterstützung|
|---------|----------------|
|Android |Unterstützt|
|iOS |Unterstützt|
|Windows 10 Mobile |Unterstützt nur dann, wenn das Telefon einen Kenncode festlegen|
|Windows-10-Desktop |Nicht unterstützt|
|Windows Phone 8.1 |Unterstützt nur dann, wenn das Telefon einen Kenncode festlegen|
|Windows Phone 8.0 |Nicht unterstützt|
|PC (Windows 8.0 und frühere Versionen) |Nicht unterstützt|
|PC (Windows 8.1) |Nicht unterstützt|

### Was ist neu seit 10 März 2016

### App-Verwaltung

- **Nutzen von iOS "Öffnen in" Management für Geräte, die Lösung eines Drittanbieters MDM registriert sind** Den Hersteller Ihrer Mobilgerät Drittanbieters Management (MDM) können Sie iOS "Öffnen In" Management nutzen. Die Einschränkungen in der Konfiguration für Profil festgelegt können und die app verwenden [Verwalten Datenübertragung zwischen iOS-apps](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)bereitstellen.

     Dieser Ansatz weist zwei Hauptvorteile:

     1. Benutzer mit ihrem Konto Arbeit anmelden, bevor sie Zugriff auf alle Unternehmensdaten aus Cloud Services oder andere apps werden müssen. Dadurch wird sichergestellt, dass mobile-app Informationsverwaltungsrichtlinien (MAM) beim Zugriff auf die Daten vorhanden sind.

     2. Verwaltete e-Mail-Profile und andere verwaltete apps bereitgestellt, bis der Lösung eines Drittanbieters MDM können Dateien und Daten mit den apps freigeben, die Intune MAM Richtlinien haben.

- **Verwalten der Microsoft Outlook-app mit MAM Richtlinien für Geräte, die nicht in Intune registriert** Sie können nun die Microsoft Outlook-app auf Geräten verwalten, die nicht mit der Intune mobilen Anwendung zur Dokumentverwaltungsrichtlinie Intune registriert sind. Die aktualisierte Microsoft Outlook-app mit den Funktionen MAM steht für [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) und [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook) -Geräten. Führen Sie die Anweisungen in der [Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien für mobile-app](https://technet.microsoft.com/library/mt627829.aspx) Thema zum Erstellen einer Richtlinie MAM.  


- **Richtlinien für Mobile-app-Konfiguration bieten Ihnen eine größere Flexibilität beim Angeben von Benutzerdetails für iOS-apps** Sie können benutzereinstellungen angeben, die eine app für iOS muss, wenn es geöffnet wird. Sie können beispielsweise einen Netzwerk-Port oder einen Benutzernamen angeben. Weitere Informationen finden Sie unter [iOS-apps mit mobile-app-Konfiguration in Microsoft Intune konfigurieren](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Bereitstellen von Adobe Reader für Microsoft Intune auf Intune verwalteten iOS-Geräte in Ihrem Unternehmen** Die Adobe Reader-app für iOS kann nun auf registrierten Geräte mit der Richtlinie Intune mobilen Anwendung Management verwaltet werden.

- **Web, die Clips in verwalteten Browser geöffnet werden bereitgestellt** Sie können den Webclips bereitstellen, die nur über den Browser verwalteten iOS und Android geöffnet werden kann. Angenommen, Sie Links zu Ihres Unternehmens Ressourcen über das Unternehmen Portal bereitstellen, und wenn Benutzer auf die Links navigieren, öffnen sie direkt in die verwaltete Browser, in dem sie nach MAM Richtlinie geschützt werden können. Weitere Informationen finden Sie unter [apps bereitstellen ](deploy-apps.md).


- **Suchen, verwalten und Verteilen von Windows Store für Geschäfts-apps für Windows 10 Geräte aus der Intune-Verwaltungskonsole** Unterstützung für Windows Store für Business steht in Intune, mit deren Hilfe Sie suchen, verwalten und Verteilen von apps für die Windows-10-Geräte, die Sie verwalten. Windows Store für Business können Sie den Prozess der Bereitstellung und Überwachung dieser apps aus der Intune-Verwaltungskonsole zu verwalten – derselben Konsole Sie mit Ihrer anderen apps verwalten. Insbesondere verwaltet Windows Store für Business Content und zur Lizenzierung von "online lizenzierte apps". Weitere Informationen finden Sie unter [Verwalten von apps, die Sie aus dem Windows Store für Unternehmen erworben haben](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Gerät-Verwaltung
- **PFX-Zertifikate-Verteilung für iOS-Geräte** Intune-Administratoren erstellen und Bereitstellen von iOS PFX Zertifikaten für Wi-Fi, e-Mail- und VPN-Authentifizierung auf iOS-Geräte. Dieses Feature ist bereits für Android und Windows-10-Geräte verfügbar. Details finden Sie unter [Aktivieren des Zugriffs auf Unternehmensressourcen Verwendung von Zertifikatsprofilen ](secure-resource-access-with-certificate-profiles.md).


- **Übernehmen apps und Richtlinien für anderes Gerätegruppen basierend auf Benutzer Kategorieauswahl** Intune-Administratoren können jetzt benutzerdefinierte Gerätekategorien für Benutzer bei der Registrierung Auswahl definieren. Beispielsweise sollten Administratoren die Benutzer angeben, wenn sie ein Gerät für die "Registrierkasse" oder "Lieferwagen" oder "Inventory Raum." verwendeten registrieren sind Die ausgewählten Kategorie bewirkt, dass das Gerät ein Mitglied der Gruppe eine Intune Gerät vorgesehen ist, die für die Bereitstellung von anderen apps und Richtlinien zum registrierten Gerät verwendet werden können. Weitere Informationen finden Sie unter [Kategorisieren Geräte mit Gerät Gruppe Zuordnung](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Änderungen und Updates an Microsoft Unternehmen Portal
Im Portal Unternehmen in dieser Version wurden die folgenden Änderungen vorgenommen.

**Portal Unternehmen Android-app**

* Wenn die Benutzer eine app, die von der mobilen Anwendungsmanagement (MAM) verwaltet wird starten, angezeigt wird eine Nachricht, die besagt, dass die app von ihrem Unternehmen verwaltet wird. Benutzer können nun Tippen Sie auf einen Link "Weitere Informationen", um [Weitere Informationen](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) zu was bedeutet "verwaltete apps" zu gelangen. Sie können auch, dass die Nachricht nicht mehr angezeigt wird, wenn sie die app starten "Nicht mehr anzeigen" tippen.
* Neue Bildschirme wurden hinzugefügt, um Benutzer durch Registrierung und enthalten weitere Informationen zu warum Benutzer registriert werden sollen, und was IT-Administratoren können und nicht auf ihren registrierten Geräten angezeigt. Finden Sie den [Registrierungs-Anweisungen](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) Details aus.
* Fehlermeldungen Registrierung werden jetzt in der app-Portal Unternehmen angezeigt. In früheren Versionen angezeigte diese Nachrichten in das Unternehmen Portal-Website ein. Bereitstellen von bedeutet, dass diese Änderung, die an einer Stelle anstelle von zwei verschiedenen Stellen jetzt alle Fehlermeldungen angezeigt werden.


**Unternehmen Portal-app für iOS**
* Wenn die Benutzer eine app, die von der mobilen Anwendungsmanagement (MAM) verwaltet wird starten, angezeigt wird eine Nachricht, die besagt, dass die app von ihrem Unternehmen verwaltet wird. Benutzer können nun Tippen Sie auf einen Link "Weitere Informationen", um [Weitere Informationen](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) zu was bedeutet "verwaltete apps" zu gelangen. Sie können auch, dass die Nachricht nicht mehr angezeigt wird, wenn sie die app starten "Nicht mehr anzeigen" tippen.
* Neue Bildschirme wurden hinzugefügt, um Benutzer durch Registrierung und Weitere Informationen zur warum Benutzer registriert werden sollen, und was IT-Administratoren können und nicht auf ihren registrierten Geräten angezeigt. Finden Sie den [Registrierungs-Anweisungen](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) Details aus.
* Registrierungs-Fehlermeldungen werden jetzt in der app-Portal Unternehmen angezeigt. In früheren Versionen angezeigte diese Nachrichten in das Unternehmen Portal-Website ein. Bereitstellen von bedeutet, dass diese Änderung, die an einer Stelle anstelle von zwei verschiedenen Stellen jetzt alle Fehlermeldungen angezeigt werden.




## Februar 2016
### Änderungen und Updates an Microsoft Unternehmen Portal

Im Portal Unternehmen in dieser Version wurden die folgenden Änderungen vorgenommen.

#### Portal Unternehmen Android-app
- Neue Bildschirme wurden hinzugefügt, um Benutzer durch Registrierung und enthalten weitere Informationen zu warum Benutzer registriert werden sollen, und was IT-Administratoren können nicht auf ihren registrierten Geräten angezeigt. Sehen Sie den [Registrierungs-Anweisungen](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) Details.
- Registrierungs-Fehlermeldungen werden jetzt in der app Unternehmen Portal angezeigt. In früheren Versionen angezeigte diese Nachrichten in das Unternehmen Portal-Website ein. Bereitstellen von bedeutet, dass diese Änderung, die an einer Stelle anstelle von zwei verschiedenen Stellen jetzt alle Fehlermeldungen angezeigt werden.

#### Unternehmen Portal-app für iOS
 - Neue Bildschirme wurden hinzugefügt, um Benutzer durch Registrierung und enthalten weitere Informationen zu warum Benutzer registriert werden sollen, und was IT-Administratoren können nicht auf ihren registrierten Geräten angezeigt. Sehen Sie den [Registrierungs-Anweisungen](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) Details.

 - Registrierungs-Fehlermeldungen werden jetzt in der app Unternehmen Portal angezeigt. In früheren Versionen angezeigte diese Nachrichten in das Unternehmen Portal-Website ein. Bereitstellen von bedeutet, dass diese Änderung, die an einer Stelle anstelle von zwei verschiedenen Stellen jetzt alle Fehlermeldungen angezeigt werden.


## Januar 2016

### Nutzen Sie die Vorteile der Windows-10-features
* **Bedingte mit Health Befähigungsnachweis Service zugreifen** Intune-Administratoren können den Status des Windows 10 Gerät Bescheinigung jetzt in der Intune Admin-Konsole anzeigen. Bescheinigung Gerät ermöglicht den Administrator diese Client Computern sicherstellen über vertrauenswürdigen BIOS, TPM, und Software-Konfigurationen zu starten. Zur Unterstützung von Gerät Bescheinigung müssen Client-Geräte Windows 10 mit TPM 2 aktiviert ausgeführt werden. Gerät Bescheinigung zeigt die Anzahl der Geräte aktiviert für jede der folgenden Aktionen aus:
    * Frühe-Launch-Modul
    * BitLocker
    * Secure Boot
    * Integrität des Codes

    Lesen [Einführung Gerät Compliance-Richtlinien für Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) detaillierte Informationen zur Integrität der Einstellung Gerät gesammelten Datenpunkte und den Dienststatus Befähigungsnachweis Bericht. Die [Dienstleistung HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) wird den Dienst – ein tieferer Einblick erläutert.

* **Windows-10-Passport für Arbeit und zertifikatverwaltung** Mit Intune können Sie die [Integration mit Microsoft Passport für die Arbeit](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), also eine alternative Anmeldung Methode für Windows 10, die Active Directory oder Azure-Active Directory-Konto wird verwendet, um ein Kennwort, Smartcard oder virtuelle Smartcard ersetzt werden. Passport können Sie eine Benutzeraktion zu verwenden, anstelle eines Kennworts anmelden. Eine Benutzeraktion möglicherweise eine einfache PIN, wie Windows Hallo biometrische Authentifizierung oder einem externen Gerät, beispielsweise einen Fingerabdruck-Reader.

* **VPN für bestimmte apps** Sie können die apps auswählen, die automatisch mit dem Unternehmensnetzwerk über VPN verbinden. Erstellen Sie die Liste der apps beim Einrichten des Profils VPN, wie in der Hilfe beschrieben, die Benutzer mit seine Arbeit mit VPN Profile mit Microsoft Intune verbinden.

* **Unterstützung für Windows 10 vollständige zurücksetzen** Sie können nun eine vollständige Remotezurücksetzung von Windows 10 ausgestellt Intune desktop Geräte über die Administrator-Konsole Intune registriert. Vollständige zurücksetzen Windows 10 unterstützt eine Fabrik Zurücksetzen des Geräts an.


### Aktualisieren von Apple Lautstärke Language Pack für-Programm (VPP)
Intune kann nun helfen, Sie [Verwalten von apps, die Sie durch Apple Lautstärke Language Pack für-Programm (VPP) für Unternehmen erworben haben](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Dies umfasst Lizenzinformationen zwischen Apfel- und Intune synchronisieren, und wie viele Kopien von jeder app verfolgen Sie bereitgestellt haben.

### Mit dem corporate im Besitz Geräte bestimmt IMEI Zahlen
Sie können jetzt [Importieren internationale mobile Geräte Identität (IMEI) Zahlen](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) für Mobilgeräteplattformen, die eine Zahl IMEI zum Identifizieren von mobilen Geräten im Unternehmen im Besitz haben. Nachdem Intune registriert, sind Geräte mit den importierten IMEI Zahlen als Corporate, markiert die verwendet werden können, für die Anwendung von Richtlinien, die als auf persönlich Besitzer Geräte angewendeten unterscheiden.

### Weitere apps sind jetzt mit Intune MAM Richtlinien kompatibel.
Weitere apps von Microsoft-Partnern sind jetzt mit Intune mobilen Anwendung (MAM) Informationsverwaltungsrichtlinien (für Geräte von Intune verwaltet) kompatibel:
* Feld für EMM (aus dem Feld Inc.) – nur iOS
* Adobe Reader (von Adobe) – nur Android
* PDF-Reader (von Foxit Unternehmen) – Foxit iOS und Android


### IE9 Support im Januar endet
Starten in Februar 2016, wird Internet Explorer 9 nicht mehr als offizielle Browser für den Zugriff auf die Website von Microsoft Intune Unternehmen Portals, Intune Kontoportal und Intune-Verwaltungskonsole unterstützt werden. Sie müssen in Internet Explorer 10 oder höher migrieren.


>[!div class="step-by-step"]

>[&larr; **Was ist neu in Intune**](whats-new-in-microsoft-intune.md)    
