---
title: "Vorbereiten von apps für mobile anwendungsverwaltung | Microsoft Intune"
description: "Die Informationen in diesem Thema hilft Ihnen bei der Entscheidung, wenn die App-Tool und das App-SDK umbrechen verwendet werden sollen, aktivieren Sie Ihre benutzerdefinierten Textzeile Geschäfts-apps, die Informationsverwaltungsrichtlinien mobile-app verwenden."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
ms.openlocfilehash: 0e5761859f4c0c30f1bd818c968bba3a3c6c60b6
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Entscheiden Sie, wie apps für mobile anwendungsverwaltung mit Microsoft Intune vorbereiten
Sie können Ihre apps mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) verwenden, mithilfe des Intune App umbrechen oder das Intune App SDK aktivieren. Mithilfe dieser Informationen um über diese beiden Methoden und ihrer Verwendung zu erfahren.

## Die App Umbruch Intune-Tool
Das Tool für die App-umbrechen wird hauptsächlich für interne Linie-von-branchenspezifische apps verwendet. Das Tool ist eine Befehlszeile-Anwendung, die einen Wrapper für die app erstellt wird, der dann die app von einer Richtlinie Intune mobilen Anwendung Verwaltung verwaltet werden können. Sie benötigen keine Quellcode mit das Tool zum, jedoch benötigen Sie Anmeldeinformationen bei der Anmeldung.  Weitere Informationen zum Signieren von Anmeldeinformationen finden Sie im [Blog Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Der App-Tool Textumbruch Dokumentation finden Sie unter [Android App umbrechen Tool](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) und [iOS-App-Tool Textumbruch](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

Die App-Tool Textumbruch unterstützt keine Apps in der App oder Play Store oder Features, die Entwicklung Uhrzeit Integration erforderlich (siehe die folgenden Features Vergleichstabelle).

Sie sollten die App-Tool Textumbruch, anstatt die SDK verwenden, wenn die app bereits geschrieben wurde oder der Quellcode nicht verfügbar ist.

**Der App umbrechen Tool für MAM auf Geräten, die nicht in Intune registriert sind, wird momentan in public Preview-Version unterstützt. Weitere Informationen hierzu finden Sie unter [schützen LOB apps auf Geräten, die nicht in Intune registriert](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md) Thema**.

### Unterstützte Plattformen

|**App Umbruch Tool** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Ja|Ja|
|**Android**| Nein |Ja|
## Intune App SDK
Die App SDK ist hauptsächlich für Kunden entwickelt, die apps in der App oder Wiedergabe speichern und Sie möchten die apps mit Intune verwalten können. Allerdings kann eine beliebige app, Integration das SDK nutzen, auch wenn es sich um eine LOB-app ist.

Weitere Informationen zu den SDK finden Sie unter [Übersicht über](/intune/develop/intune-app-sdk)die. Um mit dem SDK anzufangen, finden Sie unter [Erste Schritte mit der Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started).

### Unterstützte Plattformen
|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Arbeiten mit Ja – der Intune App SDK Xamarin-Komponente|Ja – verwenden der Intune App SDK Cordova-Plug-Ins|
|**Android**| Ja – verwenden der Intune App SDK Xamarin-Komponente|Ja – verwenden der Intune App SDK Cordova-Plug-Ins|

## Vergleich der Features
Diese Tabelle listet die Einstellungen, die Sie für die App SDK und App Tool Textumbruch verwenden können.

> [!NOTE]
> Die App-Tool Textumbruch können mit Intune Standalone oder Intune mit Konfigurations-Manager verwendet werden.

|Feature|App-SDK|App Umbruch Tool|
|-----------|---------------------|-----------|
|Einschränken von Webinhalten in einem corporate verwalteten Browser angezeigt werden.|X|X|
|Verhindern, dass Android, iTunes oder iCloud Sicherungskopien|X|X|
|Zulassen der app, Daten in anderen apps übertragen|X|X|
|Zulassen Sie app zum Empfangen von Daten aus anderen apps|X|X|
|Einschränken der Ausschneiden, kopieren und Einfügen mit anderen apps|X|X|
|Einfache PIN für den Zugriff erfordern|X|X|
|Ersetzen von integrierten app PIN mit Intune-PIN|X||
|Geben Sie die Anzahl der Versuche vor dem Zurücksetzen der PIN|X|X|
|Fingerabdruck statt PIN (nur iOS) erforderlich<br></br>**Hinweis:** Nur in MAM nur Umgebungen verfügbar.|X||
|Corporate Anmeldeinformationen für den Zugriff erfordern|X|X|
|Blockieren verwaltete apps Ausführung auf Jailbroken oder ab dem Stammverzeichnis Geräten|X|X|
|Verschlüsseln Sie die app-Daten|X|X|
|Überprüfen Sie die Access-Anforderungen nach einer bestimmten Anzahl von Minuten|X|X|
|Angeben der offline Nachfrist|X|X|
|Blockieren Bildschirmaufnahme (nur Android)|X|X|
|Vollständige zurücksetzen|X|X|
|Selektives zurücksetzen <br></br>**Hinweis:** Wenn das Management-Profil entfernt wird, wird die app für iOS ebenfalls entfernt.|X||
|Verhindern, dass "Speichern unter" |X||
|Unterstützung für mehrere Identität|X||
### Siehe auch

[Android-app Umbruch tool](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS-app Umbruch tool](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Verwenden Sie das SDK apps für mobile anwendungsverwaltung aktivieren](use-the-sdk-to-enable-apps-for-mobile-application-management.md)
