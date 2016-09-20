---
title: Einrichten von iOS und Mac-Verwaltung | Microsoft Intune
description: "Aktivieren Sie für iOS-Geräte einschließlich iPads und iPhones sowie Mac OS X-Geräten mit Microsoft Intune Mobilgerät Management (MDM)."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 566a1bbf353921257b4ab7c7c0b73aac987c2085
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einrichten von iOS und Mac-Gerät-Verwaltung
Wenn Sie Ihre iOS oder Mac-Gerät eingerichtet haben, finden Sie Hilfe [hier](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md).

Verwaltung von Intune mobiler Geräte iPads, iPhones, und Mac OS X-Geräte und Unternehmens-e-Mail und apps Zugriff gewähren. Eine Apple Pushbenachrichtigungen Benachrichtigung (APNs) Zertifikat ist erforderlich, damit Intune iOS und Mac-Geräte verwalten. Nachdem das Zertifikat Intune hinzugefügt wird, Benutzer die app Unternehmen Portal zum Registrieren aktivierten Geräte installieren können oder der Administrator kann [im Unternehmen im Besitz iOS-Gerätemanagement](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)einrichten.

1.  **Einrichten von Intune**<br>
    Wenn Sie noch nicht geschehen ist, für die Verwaltung von mobilen Geräten durch [Festlegen der mobilen Gerät Management Zertifizierungsstelle](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) als **Microsoft Intune** und Einrichten von MDM vorbereiten

2.  **Fordern Sie ein Zertifikat signieren Anforderung**<br>
    Als Benutzer mit Administratorrechten, öffnen Sie die [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com), wechseln Sie zu **Administration** &gt; **Verwaltung mobiler Geräte** &gt; **iOS und Mac OS X** &gt; **ein Zertifikat APNs hochladen**, und klicken Sie auf **die Anforderung APNs herunterladen**. Speichern Sie das Zertifikat signieren Anforderungsdatei lokal (.csr). So fordern Sie ein Zertifikat für die Beziehung Vertrauensstellung vom Apple Pushbenachrichtigungen Zertifikate-Portal an, wird die Datei .csr verwendet.

    ![APNs Sie im Dialogfeld Zertifikat hochladen](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Besorgen Sie sich einen Apple Pushbenachrichtigungen Benachrichtigung Dienstzertifikat**<br>
    Wechseln Sie zum [Apple Pushbenachrichtigungen Zertifikate Portal](http://go.microsoft.com/fwlink/?LinkId=269844) , und melden Sie sich mit Ihrem Unternehmen Apple-ID unter Verwendung der Datei .csr APNs Zertifikat erstellt. Nach dem Klicken auf Apple für Pushbenachrichtigungen Zertifikat Porta **Hochladen** , erhalten Sie eine Datei .json die für APNs verwendet werden kann. Den Download abzuschließen und Apple Pushbenachrichtigungen Zertifikate-Portal zurück, für **die Feiertage für Drittanbieter-Servers** ein, und klicken Sie auf **herunterladen**.

    Laden Sie das Zertifikat APNs (.pem), und speichern Sie die Datei lokal. Diese Apple-ID muss in Zukunft So erneuern Sie Ihr APNs Zertifikat verwendet werden.

4.  **Fügen Sie das Zertifikat APNs Intune hinzu**<br>
    Wechseln Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com)zu **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **iOS und Mac OS X** &gt; **ein Zertifikat APNs hochladen**, und klicken Sie auf **das Zertifikat APNs hochladen**. **Navigieren** Sie zu das Zertifikat (.pem) Datei, und klicken Sie auf **Öffnen** , und geben Sie dann Ihre **Apple ID**. Mit dem Zertifikat APNs kann Intune registrieren und Verwalten von iOS-Geräte Drücken Sie die Richtlinie nach registrierten mobile Geräte.

5.  **Informieren der Benutzer so erhalten Sie Zugriff auf Unternehmensressourcen mit dem Portal für Unternehmen**<br>
    Die Benutzer müssen wissen, wie ihre Geräte registrieren und was Sie erwartet, nachdem sie in Management eingebunden sind.
    - [Was Ihre Endbenutzer zur Verwendung von Microsoft Intune mitteilen](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Endbenutzer-Leitfaden für iOS und Mac-Geräte](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Wenn Ihre Firma oder Organisation iOS-Geräte für Benutzer Einkäufe, können diese Geräte auch für die Verwaltung als [im Besitz eines Unternehmens iOS-Geräte](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)registriert sein.

### Siehe auch
[Fertigstellen Sie Geräte in Microsoft Intune registrieren.](get-ready-to-enroll-devices-in-microsoft-intune.md)
