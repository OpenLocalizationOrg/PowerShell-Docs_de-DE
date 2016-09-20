---
title: "Freigeben von Notizen für Microsoft Intune | Microsoft Intune"
description: Versionsinformationen Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 98b838c3bcb5401dc070da9bb37780c1365109c1
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Versionsinformationen für Microsoft Intune
Microsoft Intune ist eine integrierte, Cloud-basierte Client-Lösung, die Tools, Berichte und Upgrade auf die neueste Version von Windows-Lizenzen bereitstellt, und hält Ihre Computer auf dem neuesten Stand und sicheren. Darüber hinaus können mit Intune Sie mobile Geräte im Netzwerk über Exchange ActiveSync oder direkt über Intune verwalten. Die folgenden Versionsinformationen beschreiben wichtige Informationen und bekannte Probleme in Microsoft Intune.


## Android-Benutzer können keine e-Mail senden, wenn bedingten Zugriff für Exchange Online implementiert wird

Benutzer, die mit Samsung Android 5.1.1 und über auf ihren Geräten können keine e-Mails senden bedingten Zugriff für Exchange Online wurde konfiguriert. Samsung bestätigt, dass das Problem in ihrem integrierte e-Mail-Client in Android 5.1.1 und höher ist, und zurzeit ein Update untersucht.

**Problemumgehung 1:** Es empfiehlt sich, zu Endbenutzer verwenden die Outlook-app für Android.

**Problemumgehung 2:** Um den betroffenen Benutzer zum Senden von e-Mail zu aktivieren, können Sie die folgenden Schritte ausführen:

1. Setzen Sie den betroffenen Benutzer in einer Sicherheitsgruppe im Abschnitt "ausgenommen Gruppen" der bedingten Zugriffsrichtlinie für Exchange Online.
2. Ermöglicht dem Benutzer e-Mail auf die integrierten e-Mail-Client vorübergehend zu synchronisieren.
3. Entfernen Sie den betroffenen Benutzer aus der Gruppe ausgenommene, und überprüfen Sie, ob dieser Benutzer jetzt e-Mails senden kann.

Microsoft weiterhin eng mit Samsung eines Fix IT oder zusätzliche problemumgehungen zusammenarbeiten.



## Ändern der Ressource Access Profile zwischen Gruppen für iOS und Android kann ein Fehler auftreten
**Problem:** Wenn Sie die e-Mail- oder einfachen Registrierung SCEP (Certificate Protocol) Ressource Access Profile zwischen Gruppen ändern, möglicherweise die Profile in Konflikt stehen und fehl. Beispielsweise angenommen, dass ein Profil mit lokalen Exchange-Server, dessen Ziel Gruppe A, auf e-Mail und dann erstellen Sie ein neues e-Mail-Profil, das mit Exchange online verweist auf die Gruppe b abgestimmten Wenn Sie Benutzer aus Gruppe A b Gruppe verschieben, Geräte beibehalten das lokal Exchange-e-Mail-Profil, und versuchen, installieren Sie das Exchange online-e-Mail-Profil, das vorgesehen ist Gruppe B.

An diesem Punkt tritt eine der folgenden Aktionen aus: 
* Wenn e-Mail-Profile A und B identisch sind, lehnt das Gerät e-Mail-Profil B da e-Mail-Profil B bereits e-Mail-Profil a enthält
* Ist-e-Mail-Profil A wie im Beispiel oben erwähnten e-Mail-Profil B, abweicht, endet das Gerät mit zwei e-Mail-Profilen.

**Hinweis:** Der Hostname und das Attribut für Username verwendet werden überprüft, um eine e-Mail-Profil voneinander zu unterscheiden.

In beiden Fällen wurde das Ressource Access-Profil (e-Mail-Profil) nicht vom Gerät entfernt, um unbeabsichtigtes Entfernen eines Benutzers Zugriff auf e-Mail- oder Kunden SCEP Zertifikat zu verhindern.

**Dieses Problem zu umgehen:** Keine.

## Wenn Sie ein Gerät Windows 8.1, die einen Proxyserver authentifizieren muss registrieren, schlägt die Registrierung mit keinen sichtbaren Hinweis über die Ursache des Fehlers
**Problem:** Wenn Sie ein Gerät Windows 8.1 registrieren, und das Gerät an einen Proxyserver, während der Registrierung authentifizieren muss, schlägt in die Registrierung das Gerät nicht die Proxy-Serveranmeldeinformationen zwischengespeichert. Wenn die Anmeldeinformationen für den Proxy-Server nicht auf dem Gerät zwischengespeichert werden, muss den Benutzer zur Eingabe der Anmeldeinformationen Registrierung warten. Aufgefordert werden, die Proxy Server-Anmeldeinformationen angeben werden jedoch keine während der Registrierung angezeigt. Das Ergebnis ist, dass der Registrierungsprozess kann nicht mit dem Proxyserver authentifizieren und es keinen sichtbaren Hinweis dieses Fehlers dem Benutzer angezeigt dafür.

**Dieses Problem zu umgehen:** Für Windows 8.1-Geräten, die in einem Netzwerk, die mit einem authentifizierten Proxyserver erfordert registrieren, konfigurieren und die Anmeldeinformationen für den Proxyserver vor der Registrierung des Geräts speichern müssen. So konfigurieren, und speichern die Anmeldeinformationen auf einem Windows 8.1-Gerät:

1.  Öffnen Sie **Internet Explorer**, auf dem Windows 8.1-Gerät.

2.  Wenn Sie für die Proxy-Serveranmeldeinformationen aufgefordert werden, geben Sie die Anmeldeinformationen ein, und wählen Sie dann die Option **Anmeldedaten speichern**.

3.  Das Gerät zu registrieren.

## Windows Phone 8.1 Geräte ein Fehler auftreten, die mit Microsoft Intune registrieren, wenn in AD FS Geräteauthentifizierung aktiviert ist
**Problem:** Wenn Sie ein Windows Phone 8.1 Gerät zu registrieren schlägt Registrierung die optionale Einstellung für die Geräteauthentifizierung als Teil des globalen Authentifizierungsrichtlinie in Active Directory Partnersuche Services (AD FS) aktiviert ist.

**Problemumgehung:** Deaktivieren Sie die Geräteauthentifizierung, auf dem AD FS-Server, indem Sie unter **Geräteauthentifizierung aktivieren** , in die **Globale Authentifizierungsrichtlinie bearbeiten**. Weitere Informationen finden Sie unter [Konfigurieren von Authentifizierungsrichtlinien](http://technet.microsoft.com/library/dn486781.aspx)


## Microsoft Intune App umbrechen Tool für Android weist keine Funktion deinstallieren integriert
**Problem:** Das **Microsoft App umbrechen Tool für Android** muss nicht integrierte Funktionen für das Tool deinstallieren.

**Dieses Problem zu umgehen:** Navigieren Sie zu dem Speicherort, in dem Sie das Tool installiert haben, und löschen Sie das Verzeichnis. Ist der Standardspeicherort für die Installation: **c:\Programme Dateien (x86) \Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Weitere Informationen zum Tool Umbruch app finden Sie unter [Vorbereiten Android apps für die Verwaltung von mit App-Tool Textumbruch](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## Remoteunterstützung steht nicht zur Verfügung, auf Computern mit Windows 8 oder Windows 8.1
**Problem:** In diesem Release ist das Funktion "Remoteunterstützung" nicht verfügbar, auf Computern, die Windows 8 oder Windows 8.1 ausgeführt werden.

**Dieses Problem zu umgehen:** Keine.

## Benachrichtigung für Empfänger, die automatisch hinzugefügt wurden funktioniert nicht
**Problem:** Wenn ein Empfänger eine Benachrichtigung automatisch hinzugefügt wird, können er nicht immer eine Benachrichtigung erhalten.

**Dieses Problem zu umgehen:** Um sicherzustellen, dass Empfänger Nachricht eine Benachrichtigung erhalten, sollten Sie Empfänger-Benachrichtigung manuell hinzufügen.

## Sprache in der Vorschau Azure-Portal unterstützen
Im Portal Azure Vorschau ist auf eine neue Plattform integriert und unterstützt die folgenden Sprachen - Chinesisch (vereinfacht), Chinesisch (traditionell), Tschechisch, Niederländisch, Englisch, Deutsch, Ungarisch, Italienisch, Japanisch, Portugiesisch (Brasilien), Portugiesisch (Portugal), Russisch, Spanisch, Englisch, Französisch, Koreanisch, Polnisch, Schwedisch, Türkisch.

Der Administrator Intune-Verwaltungskonsole und den Endbenutzer gegenüberliegende mobile Erfahrung unterstützen Dänisch, Griechisch, Fertig stellen, Norwegisch und Rumänisch, sowie alle von Azure Preview-Portal unterstützten Sprachen.
