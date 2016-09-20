---
title: Einrichten von 10 unter Windows Mobile und Windows Phone Management | Microsoft Intune
description: "Aktivieren Sie Verwaltung mobiler Geräte (MDM) für 10 unter Windows Mobile oder Windows Phone-Geräten mit Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 2c3d0b63520b1b49acb29b27d98fd08778e13e62
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einrichten von Windows Phone und 10 unter Windows Mobile Management mit Microsoft Intune

Als Administrator Intune können Sie die Registrierung und Verwaltung für 10 unter Windows Mobile und Windows Phone Geräte auf zwei Arten von aktivieren:

- **[Automatische Registrierung mit Azure AD](#azure-active-directory-enrollment)** - Windows 10 und Fenster 10 Mobile Benutzer registrieren aktivierten Geräte, indem Sie das Gerät ein Konto geschäftlichen oder schulnotizbücher hinzufügen
- **[Unternehmen Portal Registrierungs](#company-portal-app-enrollment)** - Windows Phone 8.1 oder höher verfügen, die durch Herunterladen und Installieren der app-Portal Unternehmen und dann seine Arbeit eingeben registriert sind oder Schule Anmeldeinformationen für das Konto in der app.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Unternehmen Portal app Registrierung
Sie können die Benutzer ihren Geräten installieren und registrieren aktivierten Geräte mit der app Intune Unternehmen Portal registrieren lassen. Erstellen einen CNAME-DNS kann Benutzer eine Verbindung herstellen und in Intune registrieren, ohne den Servernamen eingeben. Wenn Sie Windows Phone 8.0 Geräte verwalten oder das Unternehmen Portal für Windows Phone Geräte bereitstellen müssen, müssen Sie auch herunterladen und melden Sie sich die app-Portal Unternehmen. [Einrichten von Windows Phone 8.0 Management](set-up-windows-phone-8.0-management-with-microsoft-intune.md)finden Sie unter.

1.  **Intune einrichten**<br>Wenn Sie noch nicht geschehen ist, für die Verwaltung von mobilen Geräten durch [Festlegen der mobilen Gerät Management Zertifizierungsstelle](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) als **Microsoft Intune** und Einrichtung MDM vorbereiten

2.  **Erstellen von CNAMEs** (optional)<br>Erstellen von **CNAME** DNS-Ressourceneinträgen für die Domäne Ihres Unternehmens. Beispielsweise ist Ihres Unternehmens Website contoso.com, möchten Sie einen CNAME in DNS erstellen, die EnterpriseEnrollment.contoso.com mit manage.microsoft.com umgeleitet. Wenn mehrere überprüfte Domäne vorhanden ist, erstellen Sie einen CNAME-Eintrag für jede Domäne aus. Die Ressource CNAME-Einträge müssen die folgende Informationen enthalten:

  |TYP|Hostname|Für verweist auf|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Stunde|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Stunde|
  DNS-datensatzänderungen können auf Objektebene überschrieben werden bis zu 72 Stunden dauern. Die DNS-Änderung in Intune überprüfen nicht, bis Sie der DNS-Eintrag wird weitergegeben.

  `EnterpriseEnrollment-s.manage.microsoft.com` – Unterstützt eine Umleitung zum Dienst Intune mit der Spracherkennung Domäne aus der e-Mail-Domänennamen

  `EnterpriseRegistration.windows.net` – Unterstützung für Windows 8.1 und 10 unter Windows Mobile Geräte, die mit Azure Active Directory mit ihrer geschäftlichen oder schulnotizbücher-Konto registriert wird

  Wenn Ihr Unternehmen mehrere Domänen für Anmeldeinformationen des Benutzers verwendet, CNAME-Einträge für jede Domäne zu erstellen.

  Beispielsweise ist Ihres Unternehmens Website contoso.com, möchten Sie einen CNAME in DNS erstellen, die EnterpriseEnrollment.contoso.com mit EnterpriseEnrollment-s.manage.microsoft.com umgeleitet. DNS-datensatzänderungen können auf Objektebene überschrieben werden bis zu 72 Stunden dauern. Sie können keine überprüfen Sie die DNS-Änderung Intune bis gibt Sie der DNS-Eintrag weiter.

3.  **Vergewissern Sie sich CNAME**<br>Klicken Sie in der [Intune-Verwaltungskonsole](http://manage.microsoft.com)auf **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **Windows Phone**. Geben Sie die URL der Domäne überprüft der Firmen-Website in das Feld **Geben Sie einen Domänennamen überprüft** , und klicken Sie dann auf **Automatische Erkennung von testen**.

    ![Einrichten von mobilen Geräten Verwaltung für Windows-Dialogfeld](../media/windows-phone-enrollment.png)

4.  **Optionale Schritte**<br>Der **Tasten hinzufügen Sideloading** Schritt ist nicht für Windows 10 erforderlich. Der **Code hochladen Signaturzertifikat** Schritt ist nur erforderlich, wenn Sie Line-of-Business (LOB) apps auf Geräte nicht verfügbar aus dem Windows Store freigeben möchten. [Weitere Informationen](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

5.  **Informieren der Benutzer**<br>Die Benutzer müssen wissen, wie aktivierten Geräte registrieren und was Sie erwartet, nachdem sie in Verwaltung eingebunden sind.
    - [Was Ihre Endbenutzer Informationen zum Verwenden von Microsoft Intune mitteilen](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Endbenutzer-Leitfaden für Windows-Geräte](../enduser/using-your-windows-device-with-intune.md)

Ohne zusätzlicher Aufwand ist erforderlich, es sei denn, Sie die im Unternehmen-Portal auf Geräte bereitstellen.  Die Schritte 2 und 3 in der Administratorkonsole können ignoriert werden.
