---
title: Was kommt | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
ms.openlocfilehash: 0949172a7b8517b12fb46e8fd1f8a3cd70d93099
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# In Microsoft Intune - August in Kürze
Diese Informationen werden auf der Grundlage extrem eingeschränkte unter NDA bereitgestellt und Ankündigung geändert wird. Einige der hier aufgeführten Features sind gefährdet Verzicht auf die Datumsvorgaben und bis zu einer späteren Version verzögert werden können. Weitere Features werden in eines Pilotprojekts (flighting) aus, um sicherzustellen, dass sie die Kunden bereiten befinden überprüft wird. Bitte erreichen Sie können mit Ihrem Intune/PM Kontakt Wenn Sie Fragen oder Bedenken haben.

Diese Seite wird regelmäßig aktualisiert. Sehen Sie regelmäßig nach neu, was Updates kommt.

Die folgenden Änderungen werden in der Entwicklung für Intune. All diese Funktionen werden später Hybrid Kunden Bereitstellungen (Konfigurations-Manager mit Intune) unterstützt werden. Weitere Informationen zu neuen Features von Hybrid schauen Sie sich unsere [Hybrid Neuigkeiten auf neue Seite](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## App-Verwaltung
### Ein- und ausgeblendete apps für iOS 9.3
Für Kontrolle Geräte dem iOS 9,3 oder höher ausgeführt wird werden Sie ein- und ausgeblendete apps-Liste in der iOS Konfiguration von allgemeinen Richtlinie verwenden können:
- Geben Sie eine Liste der apps, die von Benutzern ausgeblendet wird. Benutzer können nicht anzeigen oder diese apps zu starten.
- Geben Sie eine Liste der apps, die Benutzer anzeigen und starten können. Keine anderen apps können angezeigte oder gestartet wird.

Die apps, die Sie angeben können, enthalten beide apps, die Sie bereitgestellt haben, und der integrierten iOS-apps wie Nachrichten und Notizen.
<!---TFS 1279009--->

### Zugelassenen und blockierten apps Richtlinie für Samsung KNOX Geräte

Sie können nun eine benutzerdefinierte Richtlinie für Samsung KNOX Geräte konfigurieren, die Ihnen ermöglicht, erstellen eine der folgenden Aktionen aus:
- Eine Liste der apps, die auf dem Gerät ausführen gesperrt sind. Selbst wenn installiert ist, kann eine app, die in der Liste der blockierten definiert auf dem Gerät aktiviert werden.
- Eine Liste der apps, die Benutzer des Geräts zulässig sind, aus dem Google Play Store zu installieren. Keine anderen apps können aus dem Store installiert sein.

Diese Einstellungen können nur von Geräten verwendet werden, die Samsung KNOX ausgeführt werden.
<!--- For details, see [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md)--->
<!---TFS 1311629 --->

### Neue apps kompatibel mit mobilen Anwendung Informationsverwaltungsrichtlinien (MAM)
Die Yammer-app für [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) und [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) ist [Intune mobilen Anwendung Informationsverwaltungsrichtlinien (MAM)](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)kompatibel, und zwar unabhängig davon, ob das Gerät registriert ist.

Eine vollständige Liste der MAM kompatibel apps, finden Sie unter der Website [Microsoft Intune Anwendungspartnern](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) .
<!--- TFS 1252335 & 1252336--->

## Gerät-Verwaltung
### Android 7.0-Unterstützung
Im August werden Intune "Day 0" das demnächst Android 7.0 Betriebssystem für mobile Geräte unterstützen.
<!---TFS 1262053--->
### Google Entfernen des remote-Kennung zurücksetzen Videofunktionen auf 7.0 Android-Geräten
Google ist die Möglichkeit für IT-Administratoren und Endbenutzer, die Kennung Android 7.0 Geräte per Remotezugriff zurücksetzen entfernen. IT-Administratoren konnte zuvor, Remote Kenncode des Benutzers, und Endbenutzer konnte ihre die Kennungen von der Website des Unternehmens Portal zurückgesetzt.

## Verwaltung von Gruppen
### Wechselt zum Anfang der Azure-Active Directory-Gruppen in September 2016 Intune-Gruppen
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

## Dienst veraltete Objekte
### Unternehmen Portal apps für Windows 8 und Windows Phone 8 werden nicht mehr unterstützt wird in September 2016 starten
Starten in Oktober 2016, wird Microsoft Intune Unterstützung für Windows 8 und Windows Phone 8 Unternehmen Portal apps deaktivieren. Unterstützung für Windows Phone 8-Plattform wird von Microsoft Intune auch deaktivieren. Daher werden Sie nicht möglicherweise registrieren oder aktualisieren alle Windows Phone 8-Geräte. Sie können weiterhin zum Verwalten von Windows Phone 8 und Windows 8-Geräten, die bereits registriert sind. Aktualisieren von Windows Phone 8 und Windows 8-Geräte mit Windows 8.1 und Windows Phone 8.1, und verwenden Sie die entsprechenden Windows 8.1 und Windows Phone 8.1 Unternehmen Portal apps Verteilen von apps für diese Geräte ohne Ausbluten fortsetzen.
<!---TFS 1255391--->

### Benutzerdefinierte Gruppe als Ziel der Benachrichtigung Regeln freistellen
Definieren Sie Intune Benachrichtigungsregeln, die eine e-Mail-Benachrichtigung zu von Intune gesendet werden soll. Derzeit können Sie konfigurieren Benachrichtigungsregeln zum Senden von e-Mails an alle Benutzer der Geräte in einer Intune Gerätegruppe, die Sie erstellt haben. Ab Juni 2016, wird als Ziel Benutzern erstellten Gruppen nicht mehr unterstützt werden.

Zeitachse für diese Änderung über der vorläufigen sieht wie folgt aus:
- In September 2016 werden die neue Mandanten nicht Schritt des Assistenten zum Erstellen einer Benachrichtigung Regel angezeigt. Vorhandene Mandanten sind nicht betroffen.
- Um Oktober 2016 werden einige vorhandenen Mandanten "Gruppen Gerät auswählen" im Assistenten nicht angezeigt wird.
- Zu einem späteren Zeitpunkt erwarten wir, dass alle Mandanten "Gruppen Gerät auswählen" im Assistenten nicht angezeigt werden.

<!---   TFS 1278864--->
### Änderungen für die Unternehmen Portal-app für iOS-Support
Im September werden alle Benutzer der Microsoft Intune Unternehmen Portal-app für iOS müssen Sie die neueste Version zu verwenden. Neue Benutzer werden nur die neueste Version herunterzuladen, und aktuellen Benutzer muss zu aktualisieren. Die neueste Version benötigt iOS 8.0 oder höher, daher Geräte mit älteren Versionen von iOS können nicht im Portal Unternehmen oder bis sie Geräts zu iOS 8.0 oder höher aktualisieren und dann auf die neueste Version die app Unternehmens-Portal aktualisieren zu registrieren. Registrierten Geräte Versionen unter iOS 8.0 ausgeführt werden weiterhin verwaltet werden und in der Administrator Intune-Verwaltungskonsole aufgeführt.

<!---TFS 1283165--->


### Intune-Viewer-apps
Mit der Veröffentlichung von den neuen RMS app freigeben werden wir die folgenden Intune-Viewer-apps in August 2016 entfernt:
- Intune AV-Viewer
- Intune PDF-Viewer
- Android aus Google Play Intune-Image-Viewer

Anstatt mithilfe der Intune-Viewer-apps, empfehlen wir die neue app-Verwaltung von Informationsrechten (RMS Freigabe) für Android, dem Sie eine app anstelle von drei separate apps sicher corporate Dateien auf Android-Geräten anzeigen bereitstellen kann. Weitere Informationen zu den [RMS-app freigeben](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app).
<!--- goes in 1608 What's New--->


### Siehe auch
Weitere Informationen über die zuletzt verwendete Entwicklung finden Sie unter [Neuigkeiten in Microsoft Intune](whats-new-in-microsoft-intune.md) .
