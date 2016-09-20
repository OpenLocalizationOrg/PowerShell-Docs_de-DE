---
title: "Steuern Windows Hallo für Business-Einstellungen auf Geräten | Microsoft Intune"
description: "Erfahren Sie, wie Intune in Windows Hallo für Unternehmen eine alternative Anmeldung Methode integriert, die Active Directory oder Azure-Active Directory-Konto wird verwendet, um ein Kennwort, Smartcard oder virtuelle Smartcard ersetzt werden."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: c2c2774dd85d8ce9c056248f801220e06f17063b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Steuerelement Windows Hallo für Business-Einstellungen auf Geräten mit Microsoft Intune
Microsoft Intune arbeitet mit Windows Hallo for Business (vormals Microsoft Passport für Arbeit), eine alternative Anmeldung Methode, die Active Directory oder Azure-Active Directory-Konto wird verwendet, um ein Kennwort, Smartcard oder eine virtuelle Smartcard ersetzt werden.

Hallo für Unternehmen können Sie eine *Benutzeraktion* zu verwenden, anstelle eines Kennworts anmelden. Eine Benutzeraktion möglicherweise eine einfache PIN, wie Windows Hallo biometrische Authentifizierung oder einem externen Gerät, beispielsweise einen Fingerabdruck-Reader.

Intune integriert Hallo for Business auf zwei Arten:

-   Eine Richtlinie Intune Steuerelement können die Gesten Benutzer können und können nicht zum Anmelden verwendet.

-   Sie können die Authentifizierungszertifikate in der Windows Hallo für Business Schlüsselspeicheranbieter (KSP) speichern. Weitere Informationen hierzu finden Sie unter [sichere Ressourcenzugriff mit Zertifikatsprofilen in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).

## Erstellen von einem Windows Hallo für Business Richtlinie

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **Windows** &gt; **Windows Hallo for Business** auf den Windows Hallo für Business-Seite zu öffnen.

    ![Windows Hallo für Business-Seite](../media/passport.png)

2.  Wählen Sie eine der folgenden Optionen:
    - **Deaktivieren von Windows Hallo for Business auf registrierten Geräten**. Wenn Sie nicht Windows Hallo für Unternehmen verwenden möchten, wählen Sie diese Einstellung. Alle anderen Einstellungen auf dem Bildschirm sind nicht verfügbar.
    - **Aktivieren von Windows Hallo for Business auf registrierten Geräten**. Wählen Sie diese Einstellung, wenn Sie Windows Hallo für Unternehmen Einstellungen konfigurieren möchten.
    - **Nicht konfiguriert**. Wählen Sie diese Einstellung, wenn Sie nicht Intune zum Steuern des Windows Hallo für Unternehmen Einstellungen verwenden möchten. Alle vorhandenen Windows Hallo für Business-Einstellungen auf Windows-10-Geräten werden nicht geändert werden. Alle anderen Einstellungen auf dem Bildschirm sind nicht verfügbar.
3.  Wenn Sie **Aktivieren Windows Hallo for Business auf registrierten Geräte**ausgewählt haben, konfigurieren Sie die erforderlichen Einstellungen, die an alle registrierten Windows 10 und 10 unter Windows Mobile Geräte angewendet wird.
4.  Wenn Sie fertig sind, wählen Sie **Speichern**aus.


## Einstellungen für das Windows Hallo für Business-Richtlinie

- **Verwenden einer Trusted Platform Module (TPM)**. Ein TPM Chip bietet eine zusätzliche Sicherheitsebene Daten.<br>Wählen Sie eine der folgenden Werte:
    - **Erforderlich** (Standard). Nur Geräte mit einem barrierefreien TPM können Windows Hallo für Unternehmen bereitstellen.
    - **Bevorzugte**. Geräte versuchen Sie zuerst ein TPM verwenden. Wenn dies nicht verfügbar ist, können sie Software-Verschlüsselung verwenden.
- **Benötigen Mindestlänge der PIN**/**maximale Länge der PIN anfordern**. Konfiguriert Geräte, um die Länge der PIN Mindest- und Höchstwerten verwenden, die Sie angeben, dass sichere Anmeldung sicherzustellen. Die Länge der Standard-PIN ist 6 Zeichen, aber Sie können eine Mindestlänge 4 Zeichen erzwingen. Die maximale Länge der PIN ist 127 Zeichen.
- **Kleinbuchstaben in PIN erforderlich**/**Großbuchstaben in PIN erforderlich**/**Sonderzeichen in PIN anfordern**. Sie können eine sicherere PIN erzwingen, durch die Verwendung von Großbuchstaben, Kleinbuchstaben und Sonderzeichen in die PIN anfordern. Wählen Sie aus:
    - **Zulässig**. Benutzer können Sie den Zeichentyp in ihre PIN, aber nicht obligatorisch ist.
    - **Erforderlich**. Benutzer müssen Sie mindestens eines der Zeichentypen in seine PIN einschließen. Beispielsweise ist es üblich, die mindestens einen Großbuchstaben und ein Sonderzeichen erfordern.
    - **Nicht zulässig.** (Standard). Benutzer dürfen nicht diese Zeichentypen in ihre PIN verwenden. (Dies ist auch das Verhalten, wenn die Einstellung nicht konfiguriert ist.)<br>Sonderzeichen enthalten: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [\] ^ _ & #96; {& #124;} ~**.
- **Ablauf PIN (Tage)**. Es empfiehlt sich einen Ablaufzeitraum für eine PIN, angeben, nach denen Benutzer geändert werden müssen. Die Standardeinstellung ist 41 Tage.
- **Denken Sie daran PIN Verlauf**. Schränkt die Wiederverwendung von zuvor verwendete PINs. Standardmäßig können die letzten 5 Stifte wiederverwendet werden.
- **Biometrische Authentifizierung zulassen**. Ermöglicht biometrischen Authentifizierung, z. B. Gesichtsausdruck Spracherkennung oder Fingerabdruck, als Alternative zum eine PIN für Windows Hallo für Unternehmen. Müssen die Benutzer weiterhin eine geschäftlichen PIN konfigurieren Fall biometrischer Authentifizierung schlägt fehl. Wählen Sie aus:
    - **Ja**. Windows Hallo für Business ermöglicht biometrischen Authentifizierung.
    - **No**. Windows Hallo for Business verhindert (für alle Kontotypen) biometrischen Authentifizierung.
- **Verwenden von erweiterten Anti-spoofing, sobald Sie verfügbar sind**. Konfiguriert, ob die Anti-spoofing Features von Windows Hallo auf Geräten verwendet werden, die es (beispielsweise ein Foto einer Fläche anstelle einer realen Smiley erkennen) unterstützen.<br>Wenn diese auf **Ja**gesetzt ist, erfordert Windows alle Benutzer Anti-spoofing für Gesichtszüge verwendet, wenn die unterstützt wird.
- **Verwenden Sie Telefon anmelden**. Wenn diese Option auf **Ja**festgelegt haben, können Benutzer einen remote Sie dienen als Companion tragbaren Gerät zum Desktopcomputer Authentifizierung aus. Der Desktopcomputer müssen Azure Active Directory verbunden, und das Gerät Companion mit einem Windows Hallo für Business PIN konfiguriert sein.

## Weitere Informationen
Weitere Informationen zu Microsoft Passport finden Sie [den Leitfaden](https://technet.microsoft.com/library/mt589441.aspx) in der Windows-10-Dokumentation.
