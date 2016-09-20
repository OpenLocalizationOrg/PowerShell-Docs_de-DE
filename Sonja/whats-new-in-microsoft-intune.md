---
title: Was ist neu | Microsoft Intune
description: Finden Sie heraus, was neu in den Monat ist und Vergangenheit von Microsoft Intune frei
keywords: 
author: Lindavr
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
ms.openlocfilehash: 1d09e5a0adb3ecfa8f2d64f668ea7ff16bdf31fa
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Was ist neu in Microsoft Intune – September
Erfahren Sie, was ist neu in dieser Version von Microsoft Intune. Sie können auch lernen Sie anstehende Änderungen, denen Sie für die Planung werden sollen, sowie Informationen zu früheren Versionen.

All diese Funktionen werden später Hybrid Kunden Bereitstellungen (Konfigurations-Manager mit Intune) unterstützt werden. Weitere Informationen zu neuen Features von Hybrid schauen Sie sich unsere [Hybrid Neuigkeiten auf neue Seite](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT]
>Blogbeitrag - Sicherstellung mobile Geräte sind auf dem neuesten Stand mit Microsoft Intune<br>
>Aufgrund der zuletzt verwendete "Trident" Schadsoftware Angriffen auf iOS-Geräte haben wir einen neuer Blogbeitrag, mit deren Hilfe Sie Informationen zu den verschiedenen Methoden, die Intune helfen kann, Ihre Geräte sicher und auf dem neuesten Stand zu bleiben [Ensuring Mobilgeräte sind auf dem neuesten Stand mit Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) veröffentlicht.

## iOS-10-support
Vorhandene Intune MDM und MAM Szenarien sind mit iOS 10 kompatibel. Tipps finden Sie in der [Intune-Support-Teamblog](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

## App-Tool Textumbruch unterstützt MAM ohne Gerät Registrierung für Android und iOS
Die Intune App umbrechen Tool dient eine Befehlszeile verwendet, um auf Linie-von-branchenspezifische apps für iOS und Android Intune MAM zu aktivieren. Es ist die einfachste Methode zum Intune MAM SDK in Ihre app zu integrieren, damit Ihre app MAM Richtlinien über Intune bereitgestellt erzwingen kann. Mit MAM Richtlinien können Sie die folgenden Schritte ausführen:

1. Verschlüsseln Sie die app Daten ein.
2. Anfordern der Information Worker eine PIN eingeben, wenn Sie die app starten.
3. Zulassen der app zur Datenübertragung nur für andere verwaltete apps.
4. Verhindern Sie, dass die app Daten Android, iTunes und iCloud sichern.
5. Nur ermöglichen Sie Ausschneiden, kopieren und Einfügen in die und aus anderen verwalteten apps.

Die öffentliche Vorschau der aktualisierten Intune App umbrechen Tool unterstützt jetzt MAM ohne Gerät Registrierung auf interne LOB apps für iOS und Android. Dies bedeutet, dass die Endbenutzer nicht aktivierten Geräte mit Intune von MAM aktiviert LOB apps registrieren erforderlich sind.

Jeder kann public Preview-Software testen und Lesen Sie hilfreiche Dokumentation, befindet sich in der Msintuneappsdk GitHub:

http://www.github.com/msintuneappsdk/Intune-App-Wrapper-IOS-Preview

http://www.github.com/msintuneappsdk/Intune-App-Wrapper-Android-Preview

Bevor Sie installieren und Verwenden von Microsoft Intune App Wrapper für Android und iOS Sie Vorabversion müssen:

* Überprüfen Sie die Microsoft-Lizenzbedingungen für Microsoft Intune App umbrechen Tool für Android und iOS Vorabversion
* Drucken und eine Kopie der Lizenzbedingungen für Ihre Einträge beibehalten. Nach dem Herunterladen und Verwenden von Microsoft Intune App umbrechen Tool für Android Vorabversion stimmen Sie solche Lizenzbedingungen. Wenn Sie nicht akzeptieren, verwenden Sie die Software nicht.
<!---TFS 1235607--->

## Intune Gruppen beginnen Übergang zu Azure Active Directory im September
Einige neuen Intune Konten werden Azure-Active Directory-Sicherheitsgruppen statt Intune Benutzergruppen verwendet. Sie wissen, dass Sie mit Sicherheitsgruppen arbeiten, die Intune Portal Gruppen Seite einen Link zu der Azure-Verwaltungsportal zu leiten Sie wurde, sind.

## Lookout Integration schützen Android-Geräten
Microsoft ist mit der Lookout für Mobilgeräte Schutz Lösung zu schützen, Android mobile Geräte erkennen von Schadsoftware, riskante apps und mehr auf Geräten integrieren. Lookout der Lösung können Sie die Ebene Bedrohung bestimmen, die konfiguriert werden kann. Sie können in Intune Gerät Compliance anhand der risikobewertung Lookout anhand eine Compliance-Richtlinienregel erstellen. Bedingte Richtlinien können Sie zulassen oder Sperren des Zugriffs auf Unternehmensressourcen basierend auf dem Gerät Compliance-Status.

Endbenutzer nicht kompatible Geräte werden aufgefordert, registrieren, und muss, halten Sie die Augen Arbeit Anwendung auf Android-Geräten installieren die app zu aktivieren, und Behebung von Risiken Synchronisierungsfehlern Ausschau für Arbeit Anwendung zugreifen. Weitere Informationen finden Sie unter [einschränken Zugriff basierend auf dem Gerät, Netzwerk, und die Anwendung Risiko](restrict-access-based-on-device-network-app-risk.md).


## Unternehmen Portal updates

### Android

**Hinzufügen von "Benachrichtigungen" Unternehmen-Portal für Android**<br/>
Symbol für eine neues Benachrichtigungen wurde Unternehmen-Portal für Android auf der Homepage hinzugefügt. Auf das Symbol tippen greift, auf der Seite Benachrichtigungen, die Ihre Endbenutzer alle Elemente angezeigt, die in der app-Portal Unternehmen wie Gerät bei nicht-Konformität, Registrierung aktualisieren und Registrierungs-Aktivierung Aufmerksamkeit erfordern. IOS-app Unternehmen Portal hat dies bereits Benachrichtigungen auftreten. Haben Sie die neue Seite Benachrichtigungen bedeutet wird nicht diesen Benutzer der Firma Access Setup-Seite finden Sie unter jedes Mal, wenn sie starten oder das Unternehmen Portal fortsetzen, solange das Gerät bereits registriert ist. Wenn Sie Ihre eigenen Endbenutzer Anleitungen erstellt haben, empfiehlt es sich Ihre Dokumentation diese Änderung entsprechend aktualisiert. Suchen nach aktualisierten Screenshots [hier](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->


### iOS
**Änderungen für die Unternehmen Portal-app für iOS-Support**<br/>
Alle Benutzer der app für iOS Microsoft Intune Unternehmen Portal müssen jetzt die neueste Version zu verwenden. Neue Benutzer können nur die neueste Version herunterzuladen, insbesondere aktuellen Benutzer darauf aktualisieren erforderlich sind. Die neueste Version benötigt iOS 8.0 oder höher, damit Geräte mit älteren Versionen von iOS nicht des Unternehmens-Portals verwenden oder bis zum Aktualisieren des Geräts zu iOS 8.0 oder höher und dann auf die neueste Version die app-Portal Unternehmen aktualisieren zu registrieren. Registrierten Geräte Versionen unter iOS 8.0 ausgeführt werden weiterhin verwaltet werden und in der Administrator Intune-Verwaltungskonsole aufgeführt.
<!---TFS 1283165--->

**Verbesserte wie iOS-Endbenutzer ihre apps abrufen**<br/>
Die apps Kacheln in der Unternehmen Portal-app für iOS Benutzer zu verschiedenen Sichten in einem einzigen Standort, der Website Unternehmen Portal für alle ihre apps verweisen wurden folgenden Änderungen vorgenommen. Apple Einschränkungen verbieten Line-of-Business und verwaltete app speichern apps aus, die in der app-Portal Unternehmen aufgeführt wird und festlegen, dass Benutzer besuchen Sie die verschiedene Ansichten, um alle ihre apps zu finden.

- Die Kachel **Unternehmen Apps** Arbeitsordner zuvor zu einer Liste alle Apps auf der Registerkarte alle im Unternehmen Portal-Website, und es auf die gleiche Weise funktionieren weiterhin. Der Name der Kachel geändert auf **Alle Apps**.
- Die Kachel **Andere Apps** Arbeitsordner zuvor zu einer Ansicht, in der app-Portal Unternehmen, die alle apps Listen, die Apple die app Unternehmen Portal anzeigen ermöglicht. Der Kachelnamen **Bereitgestellte Apps**geändert hat, und Tippen auf die Kachel dauert Benutzer zur Registerkarte der Website Unternehmen Portal empfohlen.
-  Die Kachel " **Kategorien** " Arbeitsordner zuvor zu einer Ansicht, in der app-Portal Unternehmen, die Kategorien von apps listet. Der Kachel-Name wurde nicht geändert, aber es jetzt verweist auf die Registerkarte Kategorien im Unternehmen Portal-Website.
Aktualisierte Screenshots finden Sie [hier](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

**IOS-Browser verwaltet-app zu installieren, wenn IT Pro die Anforderung für eine app legt auffordern**<br/>
Wenn Sie einen Webclip, um nur im verwalteten Browser öffnen konfiguriert haben, und der verwaltete Browser nicht auf einem Gerät installiert ist, fordert die app-Portal Unternehmen auf dem Gerät den Benutzer auf verwalteten Browser installieren, bevor Sie der Webclip installiert werden kann. 
<!---TFS 1228570--->

### Windows
**Schaltfläche "Feedback" app für Windows Phone 8.1 Unternehmen Portal hinzugefügt**<br/>
Die app für Windows Phone 8.1 Unternehmen Portal ermöglicht Endbenutzern, Feedback zu der app mithilfe einer neuen "Feedback senden" Schaltfläche zu senden. Um die Schaltfläche zu finden, Benutzer Tippen auf das Menü "Ellipse" an der unteren rechten Ecke des Bildschirms app Unternehmen Portal, und tippen Sie dann auf **Ihr Feedback zu senden**. Das zusammengestellten, anonymes Feedback hilft Microsoft, das Unternehmen Portal-app für Benutzer zu verbessern.
<!---TFS 1317806--->


## Was wird in Kürze

### Übergang zu Azure-Active Directory-Gruppen Intune-Gruppen
Intune ist die Erstellung einer neuen Gruppe Verwaltungsoption, der als Benutzer und Gerät Gruppen in Intune Sicherheitsgruppen Azure Active Directory (AAD) verwendet wird. Diesen Gruppen werden für alle Verwaltung von Gruppen, Richtlinie Bereitstellung und Profil Bereitstellung **, wenn eine Einführung in die neue Azure-basierten Intune Administratorportal**verwendet werden.

Diese neue Benutzeroberfläche wird verhindert, dass Sie doppelte Gruppen zwischen Diensten, die **Ihnen einige neue Features von Azure Active Directory Premium (AADP) Gruppe Zugriff zulassen**, müssen und Erweiterung mit PowerShell und Graph bereitstellen. Dies wird auch der Gruppe Verwaltungsoption über Enterprise Mobilität Management zusammengeführt werden.

Klicken Sie zum Aktivieren des Wechsel zu Sicherheitsgruppen wird der Benutzeroberfläche in der **aktuellen Verwaltungskonsole** einigen Änderungen werden. **Diese Änderungen und die Verwendung von Sicherheitsgruppen AAD, werden in der Dokumentation Intune aufgezeichnet**.

Kunden, die mit Intune nicht vertraut sind werden als **Teil der Sicherheit Gruppe ändert, bevor die aktuelle Mandanten gehen Sie wie folgt**angezeigt.

Zusätzlich zu den Änderungen in der Gruppe Verwaltung, **die folgende Funktionen werden nicht mehr unterstützt werden**:
- Ausschließen von Mitgliedern oder Gruppen beim Erstellen einer neuen Gruppe
- Gruppen **Aufgehobener Gruppierung Benutzer** und **Geräte aufgehobener Gruppierung**
- **Verwalten von Gruppen** in der Rolle Dienstadministrator
- Benutzerdefinierte Gruppe-basierte Alarme für Benachrichtigungsregeln
- Pivotieren mit Gruppen in Berichten
<!--- TFS 1295329--->

### Neue bedingte Access app-Richtlinien für Exchange Online und SharePoint Online
Sie werden möglicherweise von zum Einschränken des Zugriffs mit Exchange Online und SharePoint Online, sodass Access nur von Office mobile-apps wie Outlook, Word, Excel und OneDrive stammen. Diese neue Funktion-Paare von völlig mit Intune mobile-app Informationsverwaltungsrichtlinien (MAM), wie Sie können Sperren des Zugriffs auf integrierte e-Mail-Clients oder andere apps, die nicht mit den Richtlinien Intune MAM konfiguriert wurden. Dadurch wird sichergestellt, dass die Benutzer Ihrer Organisation Daten mit apps zugreifen, die mit Intune MAM geschützt werden können. Sie können in der mobilen app-Verwaltung über das Azure-Portal Intune loslegen. Suchen Sie nach dem neuen Abschnitt bedingte Zugriff in das Blade "Einstellungen".



### Dienst veraltete Objekte

- **Unternehmen Portal apps für Windows 8 und Windows Phone 8 werden nicht mehr unterstützt wird** <br/>
Starten in Oktober 2016, wird Microsoft Intune Unterstützung für Windows 8 und Windows Phone 8 Unternehmen Portal apps deaktivieren. Unterstützung für Windows Phone 8-Plattform wird von Microsoft Intune auch deaktivieren. Daher werden Sie nicht möglicherweise registrieren oder aktualisieren alle Windows Phone 8-Geräte. Sie können weiterhin zum Verwalten von Windows Phone 8 und Windows 8-Geräten, die bereits registriert sind. Aktualisieren von Windows Phone 8 und Windows 8-Geräte mit Windows 8.1 und Windows Phone 8.1, und verwenden Sie die entsprechenden Windows 8.1 und Windows Phone 8.1 Unternehmen Portal apps Verteilen von apps für diese Geräte ohne Ausbluten fortsetzen.



### Cloud-Wegweiser
Über anstehende Entwicklung für Intune mit der [Cloud-Plattform Wegweiser](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)informiert.


## Intune Vorversionen
Wenn Sie möchten finden Sie unter was in Intune während der letzten sechs Monate freigegeben ist, werden sie in der [vorherigen Intune neu veröffentlichte](previous-intune-releases.md) Artikel aufgelistet.

### Siehe auch
* [Microsoft Intune-Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Cloud-Plattform Wegweiser](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
