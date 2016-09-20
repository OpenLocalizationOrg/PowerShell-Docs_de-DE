---
title: "Pro-app VPN für Android verwenden Pulse Secure | Microsoft Intune"
description: "Sie können pro-app VPN-Profil für Android-Geräten von Intune verwaltet erstellen."
keywords: 
author: nbigman
manager: angrobe
ms.date: 08/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
ms.openlocfilehash: a2af91827f3a5ebc549e7f474943f1b0cc6208dd
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Verwenden einer benutzerdefinierten Richtlinie zum Erstellen eines pro-app VPN Profils für Android-Geräten

Erstellen von Profil VPN-app für Android 5.0 oder höher, die vom Intune verwaltet werden. Erstellen Sie zuerst ein VPN-Profil, das den Secure Pulse Verbindungstyp verwendet. Klicken Sie dann Erstellen einer benutzerdefinierten Konfigurationsrichtlinie, die das Profil VPN mit bestimmten apps zuordnet. 

Nachdem Sie die Richtlinie auf Ihrem Android-Gerät oder die Benutzergruppen bereitgestellt, sollten Benutzer mit dem PulseSecure VPN beginnen. PulseSecure lässt Datenverkehr nur von der angegebenen apps öffnen VPN-Verbindung mit der zu.

> [!NOTE]
>
> Dieses Profil wird nur der Secure Pulse Verbindungstyp unterstützt.


### Schritt 1: Erstellen eines Profils VPN

1. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** > **Richtlinie hinzufügen**.
2. Zum Auswählen einer Vorlage für die neue Richtlinie erweitern Sie **Android**zu, und wählen Sie dann die **Option VPN Profil (Android 4 und höher)**.
3. In der Vorlage für **Verbindungstyp**wählen Sie **Pulse Secure aus**.
4. Beenden Sie und speichern Sie das Profil VPN. Weitere Informationen zu Benutzerprofilen VPN finden Sie unter [VPN-Verbindungen](../deploy-use/vpn-connections-in-microsoft-intune.md).

> [!NOTE]
>
> Notieren Sie sich die Option VPN Profilname im nächsten Schritt verwenden. Beispielsweise MyAppVpnProfile.

### Schritt 2: Erstellen einer benutzerdefinierten Konfigurationsrichtlinie

   1. Wählen Sie in der Verwaltungskonsole Intune **Richtlinie** > **Richtlinie hinzufügen** > **Android** > **benutzerdefinierte Konfiguration** > **Richtlinie erstellen**.
   2. Geben Sie einen Namen für die Richtlinie aus.
   3. Wählen Sie unter **Einstellungen OMA-URI** **Hinzufügen**.
   4. Geben Sie einen Einstellungsnamen.
   5. Geben Sie für den **Datentyp** **Zeichenfolge**ein.
   6. Geben Sie diese Zeichenfolge für **OMA-URI**: * *./Vendor/MSFT/VPN/Profile/*Namen*/PackageList**, wobei *Name* ist die Option VPN Profilname Sie in Schritt 1 notiert haben. In diesem Beispiel wäre die Zeichenfolge **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   **Wert**erstellen Sie eine durch Semikolons getrennte Liste der Pakete, mit dem Profil zugeordnet werden soll. Wenn Sie Excel und Google Chrome-Browsers die VPN-Verbindung verwenden möchten, geben Sie beispielsweise **com.microsoft.office.excel;com.android.chrome**.

![Beispiel für Android pro-app VPN benutzerdefinierte Richtlinie](./media/android_per_app_vpn_oma_uri.png)

#### Legen Sie Ihre app-Liste auf schwarzen oder weißen Liste (optional)
  Sie können einer Liste der apps *können nicht* verwenden die VPN-Verbindung angeben, mit dem Wert **SCHWARZEN** . Alle anderen apps werden über die Option VPN verbinden.
Alternativ können Sie den Wert **weißen Liste** einer Liste der apps verwenden *können* die VPN-Verbindung angeben. Apps, die nicht in der Liste sind werden nicht über die Option VPN verbinden.
  1.    Wählen Sie unter Einstellungen **OMA-URI** **Hinzufügen**.
  2.    Geben Sie einen Einstellungsnamen.
  3.    Geben Sie für den **Datentyp** **Zeichenfolge**ein.
  4.    Verwenden Sie diese Zeichenfolge für **OMA-URI**: * *./Vendor/MSFT/VPN/Profile/**Name/Mode**, wobei *Name* ist die Option VPN Profilname Sie in Schritt 1 notiert haben. In diesem Beispiel wäre die Zeichenfolge **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    Geben Sie **Wert** **SCHWARZEN** oder **weißen Liste**aus.



### Schritt 3: Bereitstellen von beiden Richtlinien

Sie müssen den *gleichen* Intune Gruppen *sowohl* Richtlinien bereitstellen.

1.  Klicken Sie im Arbeitsbereich **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und wählen Sie dann die **Bereitstellung verwalten**.
2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :
    -   **Die Richtlinie bereitstellen**, wählen eine oder mehrere Gruppen für die Bereitstellung der Richtlinie, und wählen Sie dann **Hinzufügen** > **OK**.
    -   **Zum Schließen des Dialogfelds, ohne die Richtlinie bereitstellen**, wählen Sie **Abbrechen**aus.

Eine Zusammenfassung Status und Benachrichtigungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie** identifizieren Sie Probleme mit der Richtlinie, die Ihre Aufmerksamkeit erfordern. Ein Zusammenfassung Status wird auch im **Dashboard** -Arbeitsbereich angezeigt.
