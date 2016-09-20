---
title: Konfigurieren von Zertifikatsprofilen | Microsoft Intune
description: Informationen Sie zum Erstellen eines Profils der Intune Zertifikat.
keywords: 
author: nbigman
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
ms.openlocfilehash: e383b39493a7113d4e7c50b16df01d291b45036e
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren von Intune Zertifikatsprofilen
Nachdem Sie Ihre Infrastruktur und Zertifikate in [Konfigurieren Zertifikatinfrastruktur für SCEP](configure-certificate-infrastructure-for-scep.md) oder [Konfigurieren Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md)beschriebenen konfiguriert haben, können Sie die Zertifikatsprofile erstellen. Hier ist der Vorgang ein:

- **Aufgabe 1**: exportieren Sie das Zertifikat vertrauenswürdige Stammzertifizierungsstelle
- **Aufgabe 2**: Erstellen vertrauenswürdige Zertifikatsprofile
- **Aufgabe 3**: Erstellen Sie eine von zwei Arten von Zertifikaten Profil:
  - SCEP Zertifikatsprofile
  - . PFX Zertifikatsprofile

## **Aufgabe 1**: exportieren Sie das Zertifikat vertrauenswürdige Stammzertifizierungsstelle
Das Zertifikat Trusted Root Zertifizierungsstellen (CA) als **CER** -Datei von einer Zertifizierungsstelle, die exportiert oder von einem beliebigen Gerät aus, die Ihre Zertifizierungsstelle vertrauen. Exportieren Sie den privaten Schlüssel nicht.

Beim Einrichten eines vertrauenswürdigen Zertifikat Profils werden Sie das Zertifikat zu importieren.

## **Aufgabe 2**: Erstellen vertrauenswürdige Zertifikatsprofile
Sie müssen ein vertrauenswürdigen Zertifikat-Profil erstellen, vor dem Erstellen einer einfachen Registrierung SCEP (Certificate Protocol) oder eine PKCS #12 (. PFX) Zertifikatsprofil. Benötigen Sie eines vertrauenswürdigen Zertifikat Profils und einer SCEP oder. PFX-Profil für jedes Mobilgerät Plattform.

### Zum Erstellen eines vertrauenswürdigen Zertifikat Profils

1.  Wählen Sie in der [Verwaltungskonsole Intune](https://manage.microsoft.com)- **Richtlinie** &gt; **Richtlinie hinzufügen**.
2.  Fügen Sie eine der folgenden Arten Richtlinie hinzu:
    - **Android &gt; vertrauenswürdige Certificate Profile (Android 4 und höher)**
    - **iOS &gt; vertrauenswürdige Certificate Profile (iOS 8.0 und höher)**
    - **Mac OS X &gt; vertrauenswürdige Certificate Profile (Mac OS X 10.9 und höher)**
    - **Windows &gt; vertrauenswürdige Certificate Profile (Windows 8.1 und höher)**
    - **Windows &gt; vertrauenswürdige Certificate Profile (Windows Phone, 8.1 und höher)**

    Weitere Informationen: [Einstellungen verwalten und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Geben Sie die angeforderte Informationen zum Konfigurieren der vertrauenswürdigen Zertifikat einräumen für Android, iOS, Mac OS X, Windows 8.1 oder 8.1 für Windows Phone. 
4.  Importieren Sie die Einstellung **Zertifikatsdatei** das Zertifikat vertrauenswürdige Stammzertifizierungsstelle (CER-Datei), das Sie aus Ihrer Zertifizierungsstelle exportiert. Die Einstellung **Ziel speichern** gilt nur für Geräte Ausführen von Windows 8.1 und höher, und nur, wenn das Gerät verfügt über mehr als einen Zertifikat.
    
4.  Wählen Sie die **Richtlinie speichern**aus.

Die neue Richtlinie ist im Arbeitsbereich **Richtlinie** angezeigt. Jetzt können Sie es bereitstellen.

## **Aufgabe 3**: SCEP erstellen oder. PFX Zertifikatsprofile
Erstellen Sie nach dem Erstellen einer vertrauenswürdigen Zertifizierungsstelle Zertifikatsprofil SCEP oder. PFX Zertifikatsprofile für jede Plattform, die Sie verwenden möchten. Wenn Sie ein Zertifikat-Profil SCEP erstellen, müssen Sie ein vertrauenswürdigen Zertifikat Profils für die gleiche Plattform angeben. Dadurch werden die zwei Zertifikatsprofile verknüpft, aber weiterhin müssen bereitgestellt werden jedes Profil getrennt.

### Zum Erstellen einer SCEP Zertifikat Profils

1.  Wählen Sie in der [Verwaltungskonsole Intune](https://manage.microsoft.com)- **Richtlinie** &gt; **Richtlinie hinzufügen**.
2.  Fügen Sie eine der folgenden Arten Richtlinie hinzu:
    - **Android &gt; SCEP Certificate Profile (Android 4 und höher)**
    - **iOS &gt; SCEP Certificate Profile (iOS 8.0 und höher)**
    - **Mac OS X &gt; SCEP Certificate Profile (Mac OS X 10.9 und höher)**
    - **Windows &gt; SCEP Certificate Profile (Windows 8.1 und höher)**
    - **Windows &gt; SCEP Certificate Profile (Windows Phone, 8.1 und höher)**

    Weitere Informationen: [Einstellungen verwalten und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Folgen Sie den Anweisungen auf der Profilseite Konfiguration konfigurieren die SCEP Zertifikat einräumen.
    > [!NOTE]
    >
    > Klicken Sie unter **Namensformat Betreff**wählen Sie **benutzerdefinierte** Format für einen benutzerdefinierten Betreff Name (in iOS Profile nur) eingeben.
    >
    > Sind die beiden Variablen, die zurzeit für das benutzerdefinierte Format unterstützt `Common Name (CN)` und `Email (E)`. Durch eine Kombination der folgenden Variablen und statische Zeichenfolgen, können Sie eine benutzerdefinierte Betreffzeile Namensformat, wie diese erstellen:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > In diesem Beispiel der Administrator erstellt einen Betreff Namensformat Sie zusätzlich zu den `CN` und `E` Variablen verwendet Zeichenfolgen für Organisationseinheit, Organisation, Ort, Bundesland und Land Werte. [Funktion CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) Listen unterstützt Zeichenfolgen.

4.  Wählen Sie die **Richtlinie speichern**aus.

Die neue Richtlinie ist im Arbeitsbereich **Richtlinie** angezeigt. Jetzt können Sie es bereitstellen.

### Zum Erstellen einer. PFX Zertifikatsprofil

1.  Wählen Sie in der [Verwaltungskonsole Intune](https://manage.microsoft.com)- **Richtlinie** &gt; **Richtlinie hinzufügen**.
2.  Fügen Sie eine der folgenden Arten Richtlinie hinzu:
  - **Android &gt; . PFX Certificate Profile (Android 4 und höher)**
  - **Windows &gt; PKCS #12 (. PFX) Certificate Profile (Windows 10 und höher)**
  - **Windows &gt; PKCS #12 (. PFX) Certificate Profile (Windows Phone 10 und höher)**
  - **iOS > PKCS #12 (. PFX) Certificate Profile (iOS 8.0 und höher)**    
    Weitere Informationen: [Einstellungen verwalten und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Geben Sie im Formular Richtlinie angeforderte Informationen ein.
4.  Wählen Sie die **Richtlinie speichern**aus.

Die neue Richtlinie ist im Arbeitsbereich **Richtlinie** angezeigt. Jetzt können Sie es bereitstellen.

## Bereitstellen von Zertifikatsprofile
Beim Bereitstellen von Zertifikatsprofilen ist die Zertifikatsdatei aus dem vertrauenswürdige CA Zertifikatsprofil auf dem Gerät installiert. Das Gerät verwendet die SCEP oder. PFX-Zertifikatsprofil, um eine Anforderung vom Gerät zu erstellen.

Zertifikatsprofile werden nur auf die Plattform, die Sie verwenden, wenn Sie das Profil erstellen-Geräten installieren.

-   Sie können das Zertifikatsprofile Benutzer Websitesammlungen oder Gerät Websitesammlungen bereitstellen.

    > [!TIP]
    > Um ein Zertifikat auf einem Gerät schnell nach veröffentlichen das Gerät registriert wird, Bereitstellen Sie das Zertifikatsprofil einer Benutzergruppe und nicht zu einer Gerätegruppe. Wenn Sie eine Gruppe Gerät bereitstellen, wird eine vollständige Gerät Registrierung erforderlich, bevor das Gerät Richtlinien erhält.

-   Obwohl Sie jedes Profil separat bereitstellen, müssen Sie auch die vertrauenswürdige Stammzertifizierungsstelle und die SCEP bereitstellen oder. PFX-Profil. Andernfalls die SCEP oder. PFX Zertifikatrichtlinie schlägt fehl.

Bringen Sie Zertifikatsprofile die gleiche Weise, wie Sie andere Richtlinien für Intune bereitstellen:

1.  Klicken Sie im Arbeitsbereich **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und wählen Sie dann die **Bereitstellung verwalten**.
2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :
    -   **Die Richtlinie bereitstellen**, wählen Sie eine oder mehrere Gruppen, um die Richtlinie bereitstellen, und wählen Sie dann auf **Hinzufügen** &gt; **OK**.
    -   **Um das Dialogfeld, ohne es zu schließen**, wählen Sie **Abbrechen**aus.

Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung von Richtlinien im unteren Teil der Liste anzeigen.

### Nächste Schritte

Als Nächstes erfahren Sie, wie Verwendung von Zertifikaten für sicheren e-Mail, Wi-Fi und VPN Profile helfen.

-  [Konfigurieren des Zugriffs auf Ihres Unternehmens-e-Mail-e-Mail-Profile verwenden](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [WLAN-Verbindungen in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [VPN-Verbindungen in Microsoft Intune](vpn-connections-in-microsoft-intune.md)
