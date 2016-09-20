---
title: "Erforderliche Komponenten für die Registrierung Mobilgerät | Microsoft Intune"
description: "Einrichten von mobilen Geräten Management (MDM) erforderliche Komponenten und Fertigstellen verschiedenen Betriebssysteme registrieren."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: aca401a5bc7274d6d20980bc27d2d8fe23d8e548
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Erforderliche Komponenten für die Verwaltung von mobilen Geräten in Intune
Mobile Geräte (einschließlich [Android](set-up-android-management-with-microsoft-intune.md), [iOS und Mac](set-up-ios-and-mac-management-with-microsoft-intune.md), [Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)und [Windows-PCs](set-up-windows-device-management-with-microsoft-intune.md)) mit Intune registrieren Mitarbeiter lassen oder Geräte im Besitz eines Unternehmens verwalten, müssen Sie Gerät Registrierung aktivieren. Um Registrierung zulassen möchten, müssen Sie festlegen eine mobilen Geräts Management (MDM) Zertifizierungsstelle, konfigurieren die Intune Unternehmen Portal, Zuweisen von Lizenzen und Aktivieren der Registrierung für die Geräteplattform.

## Festlegen von mobilen Geräten Management Zertifizierungsstelle
Die Zertifizierungsstelle MDM definiert den Verwaltungsdienst, der Berechtigung zum Verwalten von einer Reihe von Geräten hat. Die Optionen für die Zertifizierungsstelle MDM umfassen Intune durch selbst und mit Intune-Konfigurations-Manager. Wenn Sie als die Zertifizierungsstelle Management-Konfigurations-Manager festlegen, kann keine anderen Dienst für die Verwaltung von mobilen Geräten verwendet werden.

>[!IMPORTANT]
> Erwägen Sie sorgfältig, ob Sie Verwalten von mobilen Geräten nur Intune (Onlinedienst) oder System Center-Konfigurations-Manager mit Intune (lokalen Software-Lösung in Verbindung mit dem online-Dienst) verwenden möchten. Nachdem Sie das Mobilgerät Management Zertifizierungsstelle festgelegt haben, kann dies geändert werden.



1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com) **Administrator** &gt; **Verwaltung mobiler Geräte**.

2.  Klicken Sie in der Liste **Aufgaben** auf **Festlegen Mobile Geräte Management Zertifizierungsstelle**. Klicken Sie im Dialogfeld **MDM Zertifizierungsstelle festlegen** wird geöffnet.

    ![Festlegen MDM Zertifizierungsstelle (Dialogfeld)](../media/intune-mdm-authority.png)

3.  Intune fordert zur Bestätigung, dass Intune als Ihre MDM Zertifizierungsstelle verwendet werden soll. Wählen Sie das Kontrollkästchen, und wählen Sie dann auf **Ja** Microsoft Intune zum Verwalten von mobiler Geräten verwenden.

## Konfigurieren des Portals Intune Unternehmen

Das Intune Unternehmen-Portal ist, in dem Benutzer Unternehmensdaten zugreifen, und führen Sie allgemeine Aufgaben wie Geräte registrieren, Installieren von apps, und Suchen von Informationen für Ihre IT-Abteilung wenden können.

> [!TIP]
> Wenn Sie das Unternehmen Portal anpassen, die Konfigurationen der Website Unternehmen Portal sowohl anwenden Unternehmen Portal apps.

Anpassen des Portals Unternehmen hindert einen vertrauten und hilfreichen Umgang mit für Ihre Endbenutzer bereitstellen. Hierzu einfach melden Sie sich an die [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) als Administrator Mandanten oder einen bestimmten Dienst, und wählen Sie **Administrator** &gt; **Unternehmen Portal**, und konfigurieren Sie die Einstellungen des Unternehmens-Portal.

![Admin-Console-Admin-Workspace-Comp-Portal-Settings](../media/cp_sa_cpsetup.PNG)

### Unternehmen Kontakt Informationen und Ihre Privatsphäre-Anweisung

Der Firmenname wird als den Titel des Unternehmens Portal angezeigt. Die Kontaktinformationen und Details werden für Benutzer im Bildschirm wenden Sie sich an IT des Unternehmens Portals angezeigt. Die Datenschutzbestimmungen wird angezeigt, wenn ein Benutzer den privaten Link klickt.

|Feldname|Die Maximallänge|Weitere Informationen|
    |----------|------------------------|----------------|
    |Name des Unternehmens|40|Dieser Name wird als Titel des Portals Unternehmen angezeigt. **Hinweis**: alphanumerische Zeichen nur. Dieses Feld unterstützt keine Sonderzeichen.|
    |Kontaktname für IT-Abteilung|40|Dieser Name wird auf der Seite **Kontakt IT** angezeigt.|
    |Telefonnummer für IT-Abteilung|20|Klicken Sie auf der Seite **Wenden Sie sich an IT** wird diese Nummer des Kontakts angezeigt.|
    |IT-Abteilung e-Mail-Adresse|40|Diese Kontaktadresse wird auf der Seite **Wenden Sie sich an IT** angezeigt. Geben Sie eine gültige e-Mail-Adresse in das Format **alias@domainname.com**.|
    |Weitere Informationen|120|Diese Informationen werden auf der Seite **Kontakt IT** angezeigt.|
    |URL für Unternehmen Private-Anweisung|79|Sie können eigene Datenschutzbestimmungen Unternehmen angeben, die angezeigt wird, wenn Benutzer klicken Sie auf die privaten Links vom Unternehmen-Portal. Sie müssen eine gültige URL in das Format https://www.contoso.com eingeben.|

### Unterstützung für Kontakte
Die Support-Website ist für Benutzer im Unternehmen Portal aktivieren sie Onlinesupport Zugriff auf angezeigt.

|Feldname|Die Maximallänge|Weitere Informationen|
    |----------|------------------------|----------------|
    |Support-Website-URL|150|Wenn Sie eine Supportwebsite, die Sie den Benutzern haben verwenden möchten, geben Sie die URL hier. Die URL muss in das Format https://www.contoso.com. Wenn Sie eine URL nicht angeben, wird für den Support-Website auf der Seite **Kontakt IT** im Unternehmen Portal nichts angezeigt.|
    |Name der Website|40|Dieser Name ist der angezeigte Name, der für die URL der Support-Website angezeigt wird. Wenn Sie eine Website-URL Support und keine Anzeigenamen angeben, wird dann **Wechseln Sie zu IT-Website** auf der Seite **Kontakt IT** im Unternehmen Portal angezeigt.|


### Unternehmen branding Anpassung

Sie können Ihr Unternehmen Portal mit Ihr Firmenlogo, Firmenname, Designfarbe und Hintergrund anpassen.

|Feldname|Weitere Informationen|
    |----------|----------------|
    |Designfarbe|Wählen Sie eine Designfarbe im Portal Unternehmen zuweisen.|
    |Firmenlogo enthalten|Wenn Sie diese Option aktivieren, können Sie Ihr Firmenlogo zum Anzeigen in Ihrem Unternehmen Portal hochladen. Sie können zwei Logos hochladen: ein Logo, die angezeigt wird, wenn Sie der Hintergrund des Unternehmens Portal weiß ist und ein Logo, die angezeigt wird, wenn im Unternehmen Portal Hintergrund eine Farbe für die ausgewählte Design verwendet. Jede Logo muss eine PNG- oder JPG-Datei sein, bieten eine maximale Auflösung von 400 x 100 Pixel und 750 KB oder weniger werden.|
    |Wählen Sie einen Hintergrund für [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] Unternehmen Portal-app|Diese Einstellung wirkt sich auf den Hintergrund für die [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] nur Unternehmen Portal app.|


Nachdem Sie die Änderungen zu speichern, können Sie die Links, die zur Verfügung gestellt werden am unteren Rand der Seite **Unternehmen Portal** der Verwaltungskonsole verwenden, die Unternehmen Portal-Website angezeigt. Diese Links kann nicht geändert werden. Wenn sich der Benutzer anmeldet, Anzeigen diese Links Ihrer Abonnements im Unternehmen-Portal an.

## Zuweisen einer Benutzerlizenz Intune

Verwenden Sie im **Verwaltungsportal von Office 365** manuell cloudbasierten Benutzer hinzufügen und Zuweisen von Lizenzen aus Ihrem lokalen Active Directory Azure Active Directory (Azure AD) sowohl cloudbasierten Benutzerkonten und Konten, die synchronisiert werden.

1.  Melden Sie sich mit dem [Verwaltungsportal von Office 365](https://portal.office.com/Admin/Default.aspx) mit Ihren Mandanten Administrator-Anmeldeinformationen.

2.  Wählen Sie das Benutzerkonto, dem Sie eine Intune Benutzerlizenz zuweisen möchten, und wählen Sie dann das Kontrollkästchen **Microsoft Intune** , klicken Sie auf die Eigenschaften von Benutzerkonten.

3.  Das Benutzerkonto wird nun in der Gruppe Microsoft Intune Benutzer hinzugefügt werden, die Zugriffsberechtigungen für den Dienst verwenden und deren Geräte in Management registrieren gewährt.

## Einrichten von Gerät-Verwaltung
Nach dem Einrichten der Zertifizierungsstelle MDM, müssen Sie Device Management für den Betriebssystemen einrichten, die Ihre Organisation möchte unterstützen. Die Schritte, die erforderlich sind, zum Einrichten der Verwaltung von Gerät variieren je nach Betriebssystem. Angenommen, müssen die Android OS Sie keinen nichts Unternehmen, in der Intune-Verwaltungskonsole. Andererseits, erfordern Windows und iOS eine Vertrauensstellung zwischen Geräten und Intune Management dürfen.

Einrichten von Management für die folgenden Plattformen:
- [Android](set-up-android-management-with-microsoft-intune.md)
- [iOS und Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Windows-PCs und laptops](set-up-windows-device-management-with-microsoft-intune.md)
- [Mobile für Windows 10 und Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

Sie können auch:
 - Verwenden Sie das [Gerät Registrierungs-Manager-Konto](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) , um viele Geräte registrieren.
 - [Angeben im Besitz eines Unternehmens Geräte mithilfe IMEI Zahlen](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) besser registrieren Geräte und Richtlinie adressieren.
