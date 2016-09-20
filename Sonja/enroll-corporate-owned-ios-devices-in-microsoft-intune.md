---
title: "Registrieren Ihres Unternehmens im Besitz iOS-Geräte | Microsoft Intune"
description: "Registrierung von corporate im Besitz iOS-Geräte mithilfe des Apple-Gerät Registrierungs-Programm (DEP) oder Apple-Konfiguration"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 7fb28509d78159fa9bec8d12a1cab534a039f328
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Registrieren Sie Ihres Unternehmens im Besitz eines iOS-Geräte in Microsoft Intune
Microsoft Intune unterstützt die Registrierung von corporate im Besitz iOS-Geräte über die Apple-Gerät Registrierungs-Programm (DEP) oder das [Apple-Konfiguration](http://go.microsoft.com/fwlink/?LinkId=518017) Tool auf einem Mac-Computer ausgeführt werden.

**Vorbereitende:** Ein [Apple Pushbenachrichtigungen Benachrichtigung Dienstzertifikat](set-up-ios-and-mac-management-with-microsoft-intune.md) ist erforderlich.

Corporate registriert iOS-Geräte auf drei Arten registriert werden kann: mithilfe von Apple-Konfiguration, DEP oder im Portal Unternehmen.

## Verwenden von Apple-Konfiguration

Sie können die iOS-Geräte registrieren, indem Corporate Registrierung Profile exportieren und verbinden dann diese mobile Geräte mit einem Mac, die Apple-Konfiguration ausgeführt wird. Apple-Konfiguration unterstützt zwei Formen der Registrierung:

- **Setup-Assistenten Registrierung**: setzt das Gerät zu Factory-Einstellungen und für die Ausführung von Setup durch die neuen Benutzer des Geräts vorbereitet. Diese Methode erfordert der Administrator das iOS-Gerät über USB mit einem Mac-Computer, die mit [Apple-Konfiguration](http://go.microsoft.com/fwlink/?LinkId=518017) die Registrierung vorkonfiguriert verbinden. Geräte sind dann für ihre Benutzer, übermittelt, die den Setup-Assistenten Prozess ausführen. Dieses Verfahren konfiguriert das Gerät mit ihrer Arbeit oder Schule Anmeldeinformationen und schließt den Registrierungsprozess. Weitere Informationen finden Sie unter [Registrieren iOS-Geräte mit Apple-Konfiguration und Setup-Assistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **Direkte Registrierung**: erstellt eine Apple-Konfiguration – kompatible Datei zur Verwendung während der Vorbereitung Gerät. Das Gerät registrierte Factory Zurücksetzen nicht zur Verfügung, aber es wurde keine Benutzer Zugehörigkeit. Diese Methode erfordert der Administrator Verbindung iOS-Gerät über USB mit einem Mac-Computer, die mit [Apple-Konfiguration](http://go.microsoft.com/fwlink/?LinkId=518017) , um das Gerät zu registrieren. Weitere Informationen finden Sie unter [Verwenden der Apple Konfiguration direkte Registrierung registrieren iOS-Geräte](ios-direct-enrollment-in-microsoft-intune.md).

## Verwenden Sie das Gerät Registrierungs-Programm (DEP)
DEP bereitstellen ein Registrierungs-Profils "über die Luft", auf Geräten, die durch die Datenausführungsverhinderung erworben werden Wenn ein Benutzer auf dem Gerät Setup-Assistenten ausgeführt wird, ist das Gerät Intune registriert.  Durch die Datenausführungsverhinderung registrierte Geräten können nicht von Benutzern unenrolled werden. Weitere Informationen finden Sie unter [Gerät Registrierungs-Programm registrieren iOS-Geräte](ios-device-enrollment-program-in-microsoft-intune.md).

## Verwenden von Unternehmens-Portal auf DEP registriert oder Apple-Konfiguration registriert Geräten

Geräte, die mit Zugehörigkeit Benutzer konfiguriert werden können installieren und Ausführen die Firma Portal-app, um apps herunterladen und Verwalten von Geräten. Nachdem die Benutzer ihre Geräte erhalten, müssen sie eine Anzahl von zusätzliche Schritte zum Abschließen des Setup-Assistenten und installieren Sie die app Unternehmen Portal ausführen.

Benutzer Zugehörigkeit ist erforderlich, um Folgendes zu unterstützen:
  - Mobile Anwendung Management (MAM) apps
  - Bedingte Zugriff auf e-Mail und Firmennamen Daten
  - Unternehmen Portal-app

**Wie Benutzer Ihres Unternehmens im Besitz iOS-Geräte mit Zugehörigkeit Benutzer anmelden**
1. Wenn ihr Gerät Benutzer aktivieren, werden sie aufgefordert, um den Setup-Assistenten auszuführen. Während der Installation werden Benutzer zur Eingabe ihrer Anmeldeinformationen aufgefordert. Sie müssen die Anmeldeinformationen (d. h. eindeutigen persönlichen Namen oder Benutzerprinzipalnamen) verwenden, die mit ihrem Abonnement in Intune verknüpft sind.

2. Während der Installation werden Benutzer für einen Apple-ID aufgefordert. Sie müssen eine Apple-ID, um das Gerät das Unternehmen Portal installieren zulassen bereitstellen. Sie können auch die ID über das Menü iOS-Einstellungen bereitstellen, nachdem Setup abgeschlossen ist.

3. Nach Abschluss der Installation muss das iOS-Gerät die Firma Portal app aus dem App Store installieren.

4. Der Benutzer kann jetzt anmelden Unternehmen-Portal an, mit dem UPN, die sie beim Einrichten des Geräts verwendet.

5. Nach der Anmeldung wird der Benutzer aufgefordert, ihr Gerät zu registrieren. Der erste Schritt besteht ihr Gerät zu identifizieren. Die app bietet eine Liste der iOS-Geräte, die bereits im Unternehmen wurden registriert und Intune-Konto des Benutzers zugewiesen. Sie sollten das passende Gerät auswählen.

  Wenn dieses Gerät noch nicht corporate registriert ist, sollten sie **neue Geräte** mit dem standard Registrierungs-Flow fortsetzen auswählen.

6. Klicken Sie auf dem nächsten Bildschirm muss der Benutzer die fortlaufende Zahl des neuen Geräts bestätigen. Der Benutzer kann die Link **bestätigen Sie die fortlaufende Zahl** um die Einstellungen-app, um zu überprüfen, ob die fortlaufende Zahl starten tippen. Der Benutzer muss die letzten vier Zeichen der Seriennummer klicken Sie dann in der app Unternehmen Portal eingeben.

  Dieser Schritt überprüft, ob das Gerät das corporate Gerät in Intune registriert ist. Wenn die fortlaufende Zahl auf dem Gerät nicht übereinstimmt, wurde das falsche Gerät ausgewählt. Der Benutzer sollte kehren Sie zum vorherigen Bildschirm, und wählen Sie ein anderes Gerät aus.

7. Nachdem die fortlaufende Zahl überprüft wurde, leitet die Unternehmen Portal-app auf die Website Unternehmen Portal zum Fertigstellen der Registrierung. Klicken Sie dann Aufforderung die Website der, an die app zurückzugeben.

8. Registrierung ist abgeschlossen. Der Benutzer kann nun dieses Gerät mit dem vollständigen Satz von Funktionen verwenden.

### Informationen zum corporate im Besitz eines verwaltete Geräte mit keine Zugehörigkeit Benutzer

Das Unternehmen Portal Geräte, die mit keine Zugehörigkeit Benutzer konfiguriert werden nicht unterstützt und sollte nicht die app installiert haben. Das Unternehmen Portal wurde für Benutzer entwickelt, die corporate Anmeldeinformationen verfügen und erfordern den Zugriff auf individuelle Ihres Unternehmens Ressourcen (z. B. e-Mail). Geräte, die mit keine Zugehörigkeit Benutzer registriert sind sind nicht vorgesehen, einen dedizierten Benutzer anmelden können. Kiosk, Punkt Verkauf (POS) oder freigegebene Programm Geräte sind typische Nutzung Fällen für Geräte, die mit keine Zugehörigkeit Benutzer registriert sind.

Wenn Benutzer Zugehörigkeit erforderlich ist, müssen Sie unbedingt des Geräts Registrierungs-Profil **Benutzer Zugehörigkeit** ausgewählt ist, bevor Sie das Gerät registrieren verfügt. Um die Zugehörigkeit Status auf einem Gerät zu ändern, müssen Sie das Gerät zurückziehen und neu registrieren, es.



### Siehe auch
[Fertigstellen Sie Geräte in Microsoft Intune registrieren.](get-ready-to-enroll-devices-in-microsoft-intune.md)
