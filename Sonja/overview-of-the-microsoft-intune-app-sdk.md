---
title: "Übersicht über das Microsoft Intune App SDK | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 4d5e10ecc50387350eb7f1746603b7b7602190a4
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Übersicht über das Microsoft Intune App SDK
Die SDK Intune App für iOS und Android-Plattform verfügbar ist, und Verwaltungsfunktionen für mobile-app mit Microsoft Intune ermöglicht. Darüber hinaus bemüht wir Kürzen von Code Änderungen des Entwicklers erforderlich. Sie werden feststellen, dass Sie die meisten Features SDK aktivieren können, ohne Ihre app Verhalten zu ändern. Für erweiterte Endbenutzer und IT-Administrator-Benutzeroberfläche können Sie unsere APIs, um Ihre app-Verhalten für Features anzupassen, die Ihre app Teilnahme erfordern nutzen. 

Nachdem Sie Ihre app aktiviert haben, können IT-Administratoren Richtlinien für verwaltete Intune apps bereitstellen und nutzen Sie diese Funktionen, um ihre Unternehmensdaten zu schützen.

# Features
## Benutzern die Möglichkeit zum corporate Dokumente verschieben
IT-Administratoren können Datei Verlagerung der corporate Dokumente Intune verwaltet Apps steuern. Beispielsweise können sie eine Richtlinie bereitstellen, die Datei Sicherung apps von Unternehmensdaten sichern, in der Cloud deaktiviert.  

## Zwischenablage Einschränkungen konfigurieren
IT-Administratoren können das Verhalten der Zwischenablage Intune verwaltet apps konfigurieren. Beispielsweise können sie eine Richtlinie bereitstellen, damit Endbenutzern nicht mehr die Zwischenablage sind auf Ausschneiden/Kopieren aus einer app Intune verwaltet, und fügen eine app nicht verwalteten.

## Konfigurieren von Bildschirm erfassen Einschränkungen
IT-Administratoren können verhindern, dass Benutzer im Bildschirm erfassen, wenn eine app Intune verwalteten angezeigt wird. Diese Einschränkung anwenden verhindert, dass die erfassen und Freigabe von vertraulichen corporate Inhalt. Diese Funktion steht nur für android-Geräten. 

## Erzwingen der Verschlüsselung gespeicherten Daten
IT-Administratoren können eine Richtlinie erzwingen, die wird sichergestellt, dass die app auf dem Gerät gespeicherte Daten verschlüsselt sind.

## Wischen Sie Remote Unternehmensdaten
IT-Administratoren können Remote Unternehmensdaten aus einer app Intune verwalteten Wischen, wenn das Gerät aus Microsoft Intune unenrolled ist. Dieses Feature basiert auf Identität, und es werden nur die Dateien, die Bezug auf die corporate Identität des Endbenutzers gelöscht. Klicken Sie dazu erfordert das Feature des app Teilnahme an. Anhand von benutzereinstellungen die Identität, für die der Löschvorgang durchgeführt werden soll, kann die app angeben. Befindet, die Abwesenheit diese Einstellungen der angegebene Benutzer in der app das Standardverhalten um Wischen Verzeichnis der Anwendung und den Endbenutzer zu benachrichtigen, dass Unternehmen Ressource Access entfernt wurde. 

## Erzwingen der Verwendung von verwalteten browser
IT-Administratoren können die Verwendung eines verwalteten Browsers beim Öffnen von Links innerhalb Intune verwalteten apps zu erzwingen. Verwenden die Microsoft Intune verwalteten Browser wird sichergestellt, dass die Links, die in e-Mails angezeigt werden (die in einem Intune verwalteten e-Mail-Client sind) innerhalb der Domäne der Intune aufbewahrt werden, verwaltet apps.

## Erzwingen Sie eine PIN-Richtlinie
IT-Administratoren können eine PIN-Richtlinie erzwingen, wenn eine app Intune verwalteten gestartet wird. Dieser Richtlinie wird sichergestellt, dass der Endbenutzer, die für ihren Geräten mit Microsoft Intune registriert die gleichen Personen sind, die die apps auf Ihrem Computer gestartet. Wenn Endbenutzer seine PIN konfigurieren, verwendet Intune App SDK Azure Active Directory, um die Anmeldeinformationen von Endbenutzern gegen das Gerät Registrierungs-Anmeldeinformationen überprüfen. 

## Festlegen, dass Benutzer Anwendungsinformationen eingeben, bevor apps gestartet werden kann
IT-Administratoren können die Benutzer ihre Anmeldeinformationen eingeben, bevor Benutzer können eine app Intune verwalteten erforderlich. Intune App SDK verwendet Azure Active Directory, um ein einzelnes anmelden zu unterstützen, in dem die Anmeldeinformationen, einmal eingegeben haben, später wiederverwendet werden. Wir unterstützen auch die Authentifizierung der Identität Management Lösungen [Verbund mit Azure Active Directory](/active-directory/active-directory-aadconnect-federation-compatibility). 

## Kontrollkästchen-Gerät und Kompatibilität
IT-Administratoren können ein Häkchen die Integrität des Geräts und die Einhaltung von Unternehmensrichtlinien, bevor Endbenutzer Intune verwalteten apps zugreifen. Auf der iOS-Plattform überprüft dieser Richtlinie, wenn das Gerät Jailbroken wurde. Auf dem Android-Plattform überprüft dieser Richtlinie, wenn das Gerät weist Stamm wurde.  


