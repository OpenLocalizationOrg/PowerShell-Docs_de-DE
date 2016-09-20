---
title: "Das Zertifikat Profile für den Zugriff auf Ressourcen | Microsoft Intune"
description: "Secure VPN, Wi-Fi und e-Mail-Access mit einem Zertifikat, das auf jedem Benutzergerät installiert."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
ms.openlocfilehash: b807ecdbd132692dc022bfa5f7a9418d3a614dfb
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Sicherer Ressourcenzugriff für die mit Zertifikatsprofile in Microsoft Intune
Wenn Sie Benutzern Zugriff auf Ressourcen des Unternehmens über ein VPN, WLAN oder e-Mail-Profile gewähren, können Sie den Zugriff sichern, mit einem Zertifikat, das auf jedem Benutzergerät installiert ist. Und so funktioniert es:

1. Stellen Sie sicher, dass Sie die richtigen Zertifikatinfrastruktur eingerichtet haben in [Konfigurieren Zertifikatinfrastruktur für SCEP](configure-certificate-infrastructure-for-scep.md) und [Konfigurieren Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md)beschriebenen.

2. Installieren Sie ein Zertifikat einer Stammzertifizierungsstelle oder eine mittlere Zertifizierungsstelle (CA) Zertifikat auf jedem Gerät, damit das Gerät die Echtheit der Zertifizierungsstelle erkennt. Hierzu erstellen Sie und Bereitstellen Sie eines **Vertrauenswürdigen Zertifikatsprofil**. Wenn Sie dieses Profil bereitstellen, die Geräte, die mit Intune verwaltet anfordern und das Zertifikat der Stamm erhalten. Sie müssen ein eigenes Profil für jede Plattform zu erstellen. Das **Vertrauenswürdige Zertifikatsprofil** ist für diese Plattformen verfügbar:
 -  iOS 8.0 und höher
 -  Mac OS X 10.9 und höher
 -  Android 4.0 und höher
 -  Windows 8.1 und höher
 -  Windows Phone 8.1 und höher

3. Erstellen Sie Zertifikatsprofile, sodass Geräte ein Zertifikat für die Authentifizierung von VPN, Wi-Fi und e-Mail-Zugriff anzufordern, in [Konfigurieren Intune Zertifikatsprofile](configure-intune-certificate-profiles.md)beschriebenen. Sie können das Erstellen und Bereitstellen einer **PKCS #12 (. PFX) Certificate Profile** *oder* ein **SCEP Certificate Profile** für diese Plattformen-Geräte:

  -  iOS 8.0 und höher
  -  Android 4.0 und höher
  -  Windows-10 (Desktop und Mobile) und höher

  Verwenden eines **SCEP Certificate Profile** für diese Plattformen-Geräte:
    -   Mac OS X 10.9 und höher
    -   Windows Phone 8.1 und höher

Sie müssen ein eigenes Profil für jede Plattform erstellen. Wenn Sie das Profil erstellt haben, ordnen Sie es mit dem **Trusted Root Certificate Profile** , die Sie bereits erstellt haben.

> [!NOTE]           
> - Wenn Sie eine Enterprise-Zertifizierungsstelle besitzen, müssen Sie einen erstellen.
>- Wenn Sie sich entscheiden, müssen basierend auf Ihrem Geräteplattformen, das Profil vereinfachtes Registrierung SCEP (Certificate Protocol) verwenden Sie auch so konfigurieren Sie einen Server Netzwerk Gerät Registrierung Service (NDES).
>-  Gibt an, ob Sie SCEP verwenden möchten oder. PFX-Profile, müssen Sie herunterladen und Konfigurieren der Microsoft Intune Zertifikat Verbinder.
>-  Erfahren Sie, wie Sie alle erforderlichen Dienste in [Konfigurieren Zertifikatinfrastruktur für SCEP](configure-certificate-infrastructure-for-scep.md) oder [Konfigurieren Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md)konfigurieren.

### Nächste Schritte
- [Zertifikatinfrastruktur für SCEP konfigurieren](configure-certificate-infrastructure-for-scep.md)
- [Konfigurieren von Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md)
- [Konfigurieren von Intune Zertifikatsprofilen](configure-intune-certificate-profiles.md)
