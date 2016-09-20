---
title: "Zulässige und gesperrte von apps für KNOX | Microsoft Intune"
description: "Benutzerdefiniertes Profil zum Erstellen einer Liste von zulässig und apps für KNOX blockiert."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
ms.openlocfilehash: 937e291f193f61329598395baa63c24d7fefa25f
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwenden Sie benutzerdefinierte Richtlinien zum Zulassen oder apps für Samsung KNOX Geräte blockieren

Verwenden Sie die Verfahren in diesem Thema eine benutzerdefinierte Microsoft Intune-Richtlinie zu erstellen, die erstellt eine der folgenden Aktionen aus:

- Eine Liste der apps, die auf dem Gerät ausführen gesperrt sind. Keine anderen apps dürfen ausgeführt werden. Apps in dieser Liste werden ausgeführt werden, blockiert, auch wenn sie bereits installiert wurden, wenn die Richtlinie angewendet wurde.
- Eine Liste der apps, die Benutzer des Geräts zulässig sind, aus dem Google Play Store zu installieren. Nur die apps Sie Liste installiert werden kann. Keine anderen apps können aus dem Store installiert sein.

Diese Einstellungen können nur von Geräten verwendet werden, die Samsung KNOX ausgeführt werden.

## Zum Erstellen einer Liste der zulässigen oder geblockten-app

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), die **Richtlinie** &gt; **Konfigurationsrichtlinien** &gt; **Hinzufügen**.
2. Im Dialogfeld **neue Richtlinie erstellen** erweitern Sie **Android**, wählen Sie **Benutzerdefinierte Konfiguration**aus, und wählen Sie die **Richtlinie erstellen**.
3. Geben Sie einen Namen und optional eine Beschreibung für die Richtlinie, und wählen Sie im Abschnitt **Einstellungen OMA-URI** **Hinzufügen**.
4. Geben Sie im Dialogfeld **Hinzufügen oder Bearbeiten von OMA-URI-Einstellung** folgende Angaben: eine Liste der apps, die auf dem Gerät ausführen gesperrt werden:
    
    - **Name der Einstellung.** Geben Sie **PreventStartPackages**ein.
    - **Wenn eine Beschreibung ein.** Geben Sie optionale eine Beschreibung wie "Liste der apps, die Ausführung blockiert werden."
    -   **Geben Sie Daten ein.** Wählen Sie aus der Dropdownliste **Zeichenfolge**aus.
    -   **OMA-URI.** Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Wert.** Geben Sie eine Liste mit den Namen der app-Paket, die Sie zulassen möchten. Sie können **;:,** oder **|** als Trennzeichen. (Beispiel: Paket1 unterscheidet sich daher; package2;)

    Eine Liste der apps, die Benutzer, die Google Play Store zu installieren, nicht jedoch alle anderen apps zulässig sind:

    - **Name der Einstellung.** Geben Sie **AllowInstallPackages**ein.
    - **Wenn eine Beschreibung ein.** Geben Sie optionale eine Beschreibung wie "Liste der apps, die Benutzer von Google Play installiert werden können."
    - **Geben Sie Daten ein.** Wählen Sie aus der Dropdownliste **Zeichenfolge**aus.
    - **OMA-URI.** Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Wert.** Geben Sie eine Liste mit den Namen der app-Paket, die Sie zulassen möchten. Sie können **;:,** oder **|** als Trennzeichen. (Beispiel: Paket1 unterscheidet sich daher; package2;)

4. Klicken Sie auf **OK**, und klicken Sie dann auf **Richtlinie zu speichern**. 

>[TIPP] Sie können die Paket-ID von einer app finden, indem Sie bei der app auf der Google Play Store durchsuchen. Die Paket-ID, die in der URL des app Seite enthalten ist. Die Paket-ID von Microsoft Word app beträgt beispielsweise **com.microsoft.office.word**.

Das nächste Mal jedes Ziel Gerät Prüfungen in die app, die Einstellungen angewendet werden soll.


## Die Richtlinie bereitstellen

1.  Des Arbeitsbereichs **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und klicken Sie auf **Bereitstellung verwalten**.

2.  Wählen Sie im Dialogfeld **Bereitstellung verwalten** , eine oder mehrere Gruppen, dem Sie die Richtlinie bereitstellen möchten, und klicken Sie auf **Hinzufügen** &gt; **OK**.

 
Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Liste Richtlinien anzeigen.

### Siehe auch
[Android und Richtlinieneinstellungen in Microsoft Intune Samsung KNOX](android-policy-settings-in-microsoft-intune.md)
