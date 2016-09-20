---
title: "Einrichten der Verwaltung von Windows-Gerät mit Microsoft Intune | Microsoft Intune"
description: "Aktivieren Sie Verwaltung mobiler Geräte (MDM) für Windows-PCs, einschließlich der Windows-10-Geräte mit Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 6b6249c2429af6c9dd85d5044dd8e0cc1f4d9a67
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einrichten der Verwaltung von Windows-Geräte

Sie können als Administrator Intune Registrierung und Verwaltung für Windows-PCs auf zwei Arten von aktivieren:

- **[Automatische Registrierung mit Azure AD](#azure-active-directory-enrollment)** - Windows 10 und Fenster 10 Mobile Benutzer registrieren aktivierten Geräte, indem Sie das Gerät ein Konto geschäftlichen oder schulnotizbücher hinzufügen
- **[Unternehmen Portal Registrierungs](#company-portal-app-enrollment)** - Windows 8.1 oder höher verfügen, die durch Herunterladen und Installieren der app-Portal Unternehmen und dann seine Arbeit eingeben registriert sind oder Schule Anmeldeinformationen für das Konto in der app.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Konfigurieren von Unternehmens-Portal app Registrierung
Sie können die Benutzer ihre Geräte zu installieren und ihre Geräte mit der app Intune Unternehmen Portal registrieren registrieren lassen. Erstellen einen CNAME-DNS kann Benutzer eine Verbindung herstellen und in Intune registrieren, ohne den Servernamen eingeben.

1. **Einrichten von Intune**<br>
Wenn Sie noch nicht geschehen ist, für die Verwaltung von mobilen Geräten durch [Festlegen der mobilen Gerät Management Zertifizierungsstelle](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) als **Microsoft Intune** und Einrichten von MDM vorbereiten

2. **Erstellen von CNAMEs** (optional)<br>Erstellen Sie **CNAME** DNS-Ressource Datensätze für Ihres Unternehmens Domäne für die Registrierung vereinfachen. Erstellen von DNS CNAME-Einträge ist optional erleichtert Erstellen des CNAME-Einträge Registrierung für Benutzer. Wenn keine Registrierungs-CNAME-Eintrag gefunden wird, werden Benutzer aufgefordert, den Servernamen MDM manuell eingeben `https://manage.microsoft.com`.  Die Ressource CNAME-Einträge müssen die folgende Informationen enthalten:

  |TYP|Hostname|Verweist auf|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Stunde|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Stunde|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Unterstützt eine Umleitung zum Dienst Intune mit der Spracherkennung Domäne aus der e-Mail-Domänennamen

  `EnterpriseRegistration.windows.net` – Unterstützt Windows 8.1 und 10 unter Windows Mobile Geräte, die mit Azure Active Directory mit ihrer geschäftlichen oder schulnotizbücher-Konto registriert wird

  Wenn Ihr Unternehmen über mehrere Domänen für Anmeldeinformationen des Benutzers verwendet, erstellen Sie CNAME-Einträge für jede Domäne aus.

  Beispielsweise ist Ihres Unternehmens Website contoso.com, möchten Sie einen CNAME in DNS erstellen, die EnterpriseEnrollment.contoso.com mit EnterpriseEnrollment-s.manage.microsoft.com umgeleitet. DNS-datensatzänderungen können auf Objektebene überschrieben werden bis zu 72 Stunden dauern. Die Änderung der DNS-Intune überprüfen nicht, bis Sie der DNS-Eintrag wird weitergegeben.

3.  **Vergewissern Sie sich CNAME**<br>Klicken Sie in der [Intune-Verwaltungskonsole](http://manage.microsoft.com)auf **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **Windows**. Geben Sie die URL der Domäne überprüft der Firmen-Website **überprüft Domänenname angeben** im ein, und klicken Sie dann auf **Testen automatische Erkennung**.

  ![Windows-Gerät Management-Dialogfeld](../media/enroll-intune-winenr.png)

4.  **Optionale Schritte**<br>Der **Tasten hinzufügen Sideloading** Schritt ist nicht für Windows 10 erforderlich. Der **Code hochladen Signaturzertifikat** Schritt ist nur erforderlich, wenn Sie Line-of-Business (LOB) apps auf Geräte nicht verfügbar aus dem Windows Store freigeben möchten. [Weitere Informationen](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

6.  **Informieren der Benutzer**<br>Sie müssen die Benutzer informieren, so aktivierten Geräte registrieren, und was Sie erwartet, nachdem sie in Management eingebunden sind:
      - [Was Ihre Endbenutzer zur Verwendung von Microsoft Intune mitteilen](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Endbenutzer-Leitfaden für Windows-Geräte](../enduser/using-your-windows-device-with-intune.md)

### Siehe auch
[Fertigstellen Sie Geräte in Microsoft Intune registrieren.](get-ready-to-enroll-devices-in-microsoft-intune.md)
