---
title: "Erstellen eine Richtlinie für Geräte Konformität | Microsoft Intune"
description: "Erstellen einer Richtlinie Compliance um Hilfe sichere mobile Geräten und PCs Zugriff auf Ihr Unternehmensdaten verwendet."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 2ff0b24d0a6991c22b23da5da5c63a9bb26ccdd2
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Erstellen einer Richtlinie für Geräte Compliance in Microsoft Intune
In diesem Thema werden die Schritte, die Sie verwenden können, eine Compliance-Richtlinie zu erstellen, die ein Gerät beachten müssen, um kompatibel sein.

##  Schritt 1: Hinzufügen einer neuen Richtlinie
  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** &gt; **Compliance-Richtlinien** &gt; **Hinzufügen**.

  ![Screenshot der Seite Richtlinie Compliance, in der die Intune-Verwaltungskonsole mit die Option hinzufügen klicken Sie im Menü am oberen Rand der Seite](./media/intune-sa-3a-add-compliance-policy.png)

##  Schritt 2: Konfigurieren von Einstellungen
Aktivieren Sie die Einstellungen, die Sie benötigen, klicken Sie auf der Seite **Richtlinie erstellen** :
  -   Die Sicherheit Systemeinstellungen wie Ihr Kennwort ein, und die Verschlüsselung
  -   Integrität des Audiogeräts wie unabhängig davon, ob ein Gerät Jailbroken ist, oder vom Windows-Gerät Gesundheit Befähigungsnachweis Dienst fehlerfrei gemeldet wird.
  -   Einstellungen für Audiogeräte Eigenschaft wie die maximal zulässige Betriebssystemversion OS Mindestversion erforderlich.
![Registerkarte Allgemein der Seite Richtlinie erstellen ](./media/intune-sa-3b-create-policy.png)


##  Schritt 3: Speichern Sie die Richtlinie
Wenn Sie fertig sind, wählen Sie die **Richtlinie speichern**.

Sie haben die Möglichkeit, die Richtlinie bereitstellen, rechts, nachdem Sie die Richtlinie gespeichert, oder Sie können auch diese später bereitstellen. Die neue Richtlinie zeigt in den Knoten **Compliance-Richtlinien** des Arbeitsbereichs **Richtlinie** .

##  Schritt 4: Legen Sie die Gültigkeitsdauer des Compliance-status
Um den Zeitraum anzugeben, die das Gerät verfügt über dem Einchecken vor einem Gerät nicht kompatibel ist, wechseln Sie zu Richtlinieneinstellungen Compliance und aktualisieren Sie die Uhrzeit zu.  Die Standardeinstellung ist 30 Tage festgelegt.

![Compliance-Richtlinie Einstellungsoption in der Menüleiste Richtlinie](../media/mdm-compliance-policy-settings.png)

![Konformität (Dialogfeld)](../media/mdm-ca-compliance-status-validity-period.png)

## Unterstützte Richtlinieneinstellungen
Der folgenden Tabelle sind die Compliance-Richtlinieneinstellungen und den Plattformen, an denen sie unterstützt werden.

-------------
|Einstellung|iOS|Android|Windows|
|-----|----|-----|-----|
|Anfordern eines Kennworts zum Entsperren von mobiler Geräten|iOS 6 und höher|Android 4.0 und höher <br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8 und höher|
|Einfache Kennwörter zulassen|iOS 6 und höher|Nicht unterstützt|Windows Phone 8 und höher|
|Mindestlänge des Kennworts|iOS 6 und höher| Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher| Windows Phone 8 und höher<br>Windows 8.1|
|Kennwort geben erforderlich|iOS 6 und höher|Nicht verfügbar|Windows Phone 8 und höher <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Mindestanzahl von Zeichensätzen|iOS 6 und höher|Nicht verfügbar|Windows Phone 8 und höher <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Kennwort Qualität|Nicht verfügbar|Android 4.0 und höher <br>Samsung KNOX Standard 4.0 und höher|Nicht verfügbar|
|Minuten nach der letzten vor dem Kennwort erforderlich ist.|iOS 6 und höher|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Kennwortablauf (Tage)|iOS 6 und höher|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Denken Sie daran Kennwortverlauf|iOS 6 und höher|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Verhindern, dass Wiederverwendung von vorherigen Kennwörtern|iOS 6 und höher|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8 und höher<br>Windows RT und Windows RT 8.1<br>Windows 8.1|
|Anfordern eines Kennworts, wenn Sie das Gerät aus Leerlauf zurückgibt| Nicht verfügbar| Nicht verfügbar|Mobile für Windows 10|
|Vorschreiben von Verschlüsselung auf mobilen Geräten|Nicht verfügbar|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8 und höher<br> Windows 8.1|
|Geräte als fehlerfrei zu meldende erforderlich| Nicht verfügbar| Nicht verfügbar|Windows <br>Mobile für Windows 10|
|Gerät muss nicht Jailbroken oder einen Stamm|iOS 6 und höher|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher|Nicht verfügbar|
|E-Mail-Konto muss von Intune verwaltet werden|iOS 6 und höher|Nicht verfügbar| Nicht verfügbar|
|Wählen Sie das e-Mail-Profil, das vom Intune verwaltet werden müssen|iOS 6 und höher|Nicht verfügbar| Nicht verfügbar|
|Minimum OS erforderlich|iOS 6 und höher|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher| Windows Phone 8 und höher<br>Windows 8.1|
|Die maximal zulässige Betriebssystemversion|iOS 6 und höher|Android 4.0 und höher<br>Samsung KNOX Standard 4.0 und höher|Windows Phone 8 und höher<br>Windows 8.1|

Wählen Sie eine der folgenden erfahren Sie mehr über das Complianceeinstellungen auf jeder Plattform unterstützt:
> [!div class="op_single_selector"]
- [Compliance-Richtlinien für iOS-Geräte](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Compliance-Richtlinien für Android-Geräten](android-compliance-policy-settings-in-microsoft-intune.md)
- [Compliance-Richtlinien für Windows und Windows Phones ](windows-compliance-policy-settings-in-microsoft-intune.md)


## Nächste Schritte
[Bereitstellen Sie und überwachen Sie Ihrer Richtlinie](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Siehe auch
[Einführung in die Compliance-Geräterichtlinien](introduction-to-device-compliance-policies-in-microsoft-intune.md)
