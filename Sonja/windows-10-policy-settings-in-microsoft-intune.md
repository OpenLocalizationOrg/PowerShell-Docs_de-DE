---
title: Windows-10-Richtlinieneinstellungen | Microsoft Intune
description: "Verwenden Sie die in diesem Artikel aufgeführten Richtlinieneinstellungen helfen Ihnen die Konfiguration der integrierter und benutzerdefinierter Einstellungen für registrierten Windows 10 Desktop- und 10 unter Windows Mobile Geräte."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 712883874f022ceb3f38473839fe0d6e4c373164
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Richtlinieneinstellungen für Windows-10-Geräte in Microsoft Intune Intune

Dieses Thema enthält Informationen, die zuerst die Einstellungen für die Informationsverwaltungsrichtlinie Intune verstehen, dass Sie zum Verwalten von Windows-10-Geräten verwenden können. Lesen Sie dieses Thema entlang der Verfahren in [Einstellungen verwalten und Features auf Ihrer Geräte mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) zum Konfigurieren der integrierter und benutzerdefinierter Einstellungen für registrierten 10 Windows-Desktop, und 10 unter Windows Mobile Geräte. Sie können nicht diesen Richtlinien mit PCs verwenden, die die [Intune PC-Clientsoftware](/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)ausgeführt werden.

Sie können zwei Arten von Richtlinie auswählen:

- **Benutzerdefinierte Richtlinie** - verwenden Sie die Microsoft Intune **benutzerdefinierte Richtlinie** für Windows 10 und 10 unter Windows Mobile OMA-URI (Open Mobile Alliance Uniform Resource Identifier) Einstellungen bereitgestellt, die zum Steuern der Features auf Geräten verwendet werden können. Windows-10 bereitgestellt, viele Einstellungen über die [Richtlinie Konfiguration Service Provider (CSP Richtlinie)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Von allgemeinen Konfigurationsrichtlinie** - Verwendung dieser Richtlinie zu geben, wenn Sie Einstellungen aus der integrierten Liste Lieferumfang von Microsoft Intune auswählen möchten.

## Benutzerdefinierte Richtlinieneinstellungen

Geben Sie die folgenden Einstellungen in einer benutzerdefinierten Richtlinie:

## &nbsp;&nbsp;&nbsp;Allgemeine

Geben Sie einen Namen und optional eine Beschreibung für diese Richtlinie in der Verwaltungskonsole Intune erkennbar.

## &nbsp;&nbsp;&nbsp;OMA-URI-Einstellungen

Geben Sie für jede OMA-URI-Einstellung, die Sie hinzufügen möchten die folgenden Informationen ein. Verwenden Sie die [Windows-10-URI-Einstellungen-Verweis](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) in diesem Artikel lernen Sie die Einstellungen kennen, die Sie verwenden können: 

- **Festlegen von Namen** - Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung, damit es in der Liste der Einstellungen zu identifizieren.
- Geben Sie die **Beschreibung festlegen** – optional eine Beschreibung für die Einstellung ein.
- **Datentyp** - wählen Sie aus:
    - **Zeichenfolge**
    - **Zeichenfolge (XML)**
    - **Datum und Uhrzeit**
    - **Ganze Zahl**
    - **Gleitkommazahl**
    - **Boolesch**
- **OMA-URI (Groß-/Kleinschreibung wird beachtet)** – Geben Sie den OMA-URI eine Einstellung für bereitstellen möchten.
- **Wert** – Geben Sie den Wert, mit dem OMA-URI zugeordnet werden soll Sie eingegeben haben.

### Beispiel
**Conectivity/AllowVPNOverCellular** wurde im Screenshot unten, die Einstellung aktiviert. Auf diese Weise können ein Windows-10-Gerät auf einem Mobilfunknetz eine VPN-Verbindung zu öffnen.

> ![Beispiel für benutzerdefinierte Richtlinien mit VPN-Einstellungen](./media/custom-policy-example.png)

## Windows-10-URI-Einstellungen
Verwenden Sie diesen Abschnitt lernen die OMA-URI-Einstellungen, die Sie mit einer **Windows 10 benutzerdefinierte Richtlinie**konfigurieren können.

## &nbsp;&nbsp;&nbsp;Richtlinie

|Name der Richtlinie und URI|Details|
|---------------|------------|-----------|
|**Automatische Aktualisierung zulassen**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Nur Desktop<br>**Datentyp:** Ganze Zahl<br />**Werte:** **0**  -  **5** (Standard: **1**)|
|**Zeitplan installieren Tag**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Nur Mobile<br>**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - täglich (Standard)<br>**1** : Sonntag<br>**2** - Montag<br>**3** - Dienstag<br>**4** - Mittwoch<br>**5** : Donnerstag<br>**6** - Freitag<br>**7** - Samstag|
|**Zeitpunkt der Terminplan-Installation**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** bis **23** Stunden (**0** ist Mitternacht) (Standardeinstellung: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - nicht Benutzer den Kennwort Nachfrist Zeitgeber festlegen; Wert wird als "Jeder" festgelegt.<br>**1** - Benutzer kann den Kennwort Nachfrist Timer (Standardeinstellung) festlegen.|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – **Verwenden von WLAN - Verbindung**nicht zulassen.<br>**1** –**Zulassen verwenden WLAN - Verbindung** (Standard)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Desktop- und mobile<br>**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulassen Internet Sharing, **1** – zulassen Internet Sharing (Standard)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – keine WLAN-Verbindung außerhalb MDM nach der Bereitstellung zulässig ist.<br>**1** – Hinzufügen von neuen Netzwerk SSIDs jenseits der bereits MDM nach der Bereitstellung Schriftarten ist zulässig (Standard).|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Desktop- und mobile<br>**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – nicht zulässig (Enterprise nur festlegen).<br>**1** – eingeschränkt.<br>**2** – vollständigen (Standard)<br>**3** - Informationen zu vollständigen und Diagnose|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – nicht zulässig.<br>**1**- Einstellungen nur (Standard)<br>**2**- Einstellungen und experimentieren|
|**Sicherheit/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - Anti-Diebstahl-Modus nicht zulassen<br>Einstellung des Benutzers **1** (Standard)|
|**Konnektivität/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Konnektivität/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Konnektivität/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - ist VPN nicht über Mobiltelefon zulässig.<br>**1** – VPN eine Verbindung einschließlich Mobiltelefon (Standard) verwenden|
|**Konnektivität/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Konnektivität/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Konnektivität/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – nicht ermöglicht dem Benutzer Bluetooth aktivieren.<br>**1** – reserviert. Der Benutzer kann aktivieren und Konfigurieren von Bluetooth (nicht in Windows Phone 8.1 für MDM, EAS, 10 Windows-Desktop oder 10 unter Windows Mobile unterstützt)<br>**2** : zulässig. Der Benutzer kann aktivieren und Konfigurieren von Bluetooth (Standard)|
|**Erfahrung/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Erfahrung/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Erfahrung/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Erfahrung/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulassen roaming, **1** – zulassen roaming (Standard)|
|**Erfahrung/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Konten/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Konten/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Sicherheit/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Sicherheit/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Suchen/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** (Standard), **1**|
|**Suchen/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0**, **1** (Standard)|
|**Suchen/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** (Standard), **1**|
|**Suchen/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** (Standard), **1**|
|**Suchen/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** (Standard), **1**|
|**Suchen/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0**, **1** (Standard)|
|**Suchen/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** (Standard), **1**|
|**Sicherheit/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Sicherheit/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** (Standard), **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – nicht zulassen<br>Offenes erweitertes Wörterbuch ist deaktiviert.<br>Ein Benutzer ist nicht möglich:<br>-Ein neues offenes erweitertes Wörterbuch hinzufügen<br />– Hinzufügen einer neuen Integration suchkonfigurationsdatei<br>-Verwenden Sie die Cloud Candidate-Funktion<br>-Senden Sie Benutzer registriert Word.<br>**1** : zulassen<br>Offenes erweitertes Wörterbuch kann hinzugefügt und standardmäßig verwendet werden. Darüber hinaus kann die Integration mit der Suchfunktion standardmäßig verwendet werden.<br>Kann ein Benutzer:<br>Verwenden Sie das Cloud Candidate Feature.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - Misconversion abmelden.<br>**1** - Misconversion-Befehl (Standard)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig **1** – zulässig (Standard).|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - sind keine Zeichen gefilterte (Standard)<br>**1** : alle außer Shift-JIS-Zeichen gefiltert werden|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br />**0** - sind keine Zeichen gefilterte (Standard)<br>**1** : Alles außer JIS0208 Zeichen gefiltert werden|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - sind keine Zeichen gefilterte (Standard)<br>**1** : Alles außer JIS0208 oder EUDC Zeichen gefiltert werden|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Einstellungen/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Erfahrung/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Suchen/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – Strict, höchsten gegen jugendgefährdenden Inhalt filtern<br>**1** – moderieren, moderieren Filtern anhand jugendgefährdenden Inhalt (gültige Suche Ergebnisse nicht gefiltert werden - Standard)|
|**Erfahrung/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**Erzwingen, dass Start Größe**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - Benutzer Größe ändern (Standard) zulassen<br>**1** - nicht Vollbild force<br>**2** - Force Vollbild|
|**Aktualisieren/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0**: zurückstellen nicht Upgrade (greifen im aktuellen Zweig, CB - Standard)<br>**1**: aktualisiert wird, aktivieren und Upgrades werden zurückgestellt (Gerät folgt aktuellen Zweig für Business, CBB, Regeln)<br />Weitere Informationen finden Sie unter:<br>[Einführung in die Windows-10 Wartung](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planen der Verwendung von Windows-10-Bereitstellung](https://technet.microsoft.com/library/mt574241.aspx)|
|**Aktualisieren/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Desktop- und mobile<br>**Beschreibung:** Richtlinien zum Zurückstellen Softwareupdates bis zu vier Wochen<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br> **0**: Anwenden von Updates sofort (Standard)<br>**1**-**4**: Zahl zum Zurückstellen Softwareupdates Wochen.<br />Weitere Informationen finden Sie unter:<br>[Einführung in Windows 10 Wartung](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planen der Verwendung von Windows-10-Bereitstellung](https://technet.microsoft.com/library/mt574241.aspx)|
|**Aktualisieren/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Desktop- und mobile<br>**Beschreibung:** Richtlinien zum Zurückstellen Feature Upgrades für bis zu 8 Monaten<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0**: Anwenden von Updates sofort (Standard)<br>**1**-**8**: Anzahl der Monate zum Feature Upgrades zurückstellen.<br />Weitere Informationen finden Sie unter:<br>[Einführung in die Windows-10 Wartung](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planen der Verwendung von Windows-10-Bereitstellung](https://technet.microsoft.com/library/mt574241.aspx)|
|**Aktualisieren/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Desktop- und mobile<br>**Beschreibung:** Kann ein Gerät der Empfang von Updates und Upgrades 5 Wochen beenden.<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0**: Anwenden von Updates sofort (Standard)<br>**1**: Pause Updates und Upgrades (läuft ab nach 5 Wochen)|

## &nbsp;&nbsp;&nbsp;Windows Defender

|Name der Richtlinie und URI|Details|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – überwachen Sie alle Dateien (Standard)<br>**1** – Monitor eingehende Dateien<br>**2** – Monitor ausgehende Dateien|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - **90** – darstellt, welche welcher Schadsoftware beibehalten werden<br>**Standard:** behält in einem Ordner für immer **0** – und nicht automatisch entfernen|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**1** – quick Scan (Standard)<br>**2** - vollständigen scan|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - täglich (Standard)<br>**1** : Montag<br>**2** - Dienstag<br>**3** - Mittwoch<br>**4** : Donnerstag<br>**5** : Freitag<br>**6** - Samstag<br>**7** : Sonntag<br>**8** – keine geplanter scan|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - 12:00 Uhr<br>**60** – 1:00 Uhr<br>**120** – 2:00 Uhr (Standard)<br>**180** – 3:00 zurück<br>**240** – 4:00 Uhr<br>**300** – 5:00 Uhr<br>**360** – 6:00 Uhr<br>**420** – 7:00 Uhr<br>**480** – 8:00 Uhr<br>**540** – 9:00 Uhr<br>**600** – 10:00 Uhr<br>**660** – 11:00 ein<br>**720** – 12:00 Uhr<br>**780** – 1:00 Uhr<br>**840** – 2:00 Uhr<br>**900** – 3:00 Uhr<br>**960** – 4:00 Uhr<br>**1020** – 5:00 Uhr<br>**1080** – 6:00 Uhr<br>**1140** – 7:00 Uhr<br>**1200** – 8:00 Uhr<br>**1260** – 9:00 Uhr<br>**1320** – 10:00 Uhr<br>**1381** – Wartungsfenster|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Nur Desktop<br>**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** - 12:00 Uhr<br>**60** – 1:00 Uhr<br>**120** – 2:00 Uhr (Standard)<br>**180** – 3:00 zurück<br>**240** – 4:00 Uhr<br>**300** – 5:00 Uhr<br>**360** – 6:00 Uhr<br>**420** – 7:00 Uhr<br>**480** – 8:00 Uhr<br>**540** – 9:00 Uhr<br>**600** – 10:00 Uhr<br>**660** – 11:00 ein<br>**720** – 12:00 Uhr<br>**780** – 1:00 Uhr<br>**840** – 2:00 Uhr<br>**900** – 3:00 Uhr<br>**960** – 4:00 Uhr<br>**1020** – 5:00 Uhr<br>**1080** – 6:00 Uhr<br>**1140** – 7:00 Uhr<br>**1200** – 8:00 Uhr<br>**1260** – 9:00 Uhr<br>**1320** – 10:00 Uhr<br>**1380** – 11:00 Uhr|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0**  -  **100** (Standard: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Nur Desktop<br />**Datentyp:** Ganze Zahl<br>**Werte:** **0** – nicht zulässig (Standard), **1** – zulässig.|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig (Standard), **1** – zulässig.|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – (Standard) – zugelassen wird auch ausgeführt, wenn RTP auf If zulässige festgelegt wurde|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – nicht auf einem Intervall für Signaturen aktivieren<br>**1** : Überprüfen der Signaturen stündlich<br>**2** – Kontrollkästchen Alle 2 Stunden, usw..<br>**24** – Kontrollkästchen jeden Tag<br>**Standardwert:** 8 – Überprüfen Sie alle 8 Stunden|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulässig, **1** – zulässig (Standard).|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – immer anfordern (Standard)<br>**1** – senden SFI nimmt automatisch<br>**2** – nie senden<br>**3** – alle nimmt automatisch senden|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Nur Desktop<br />**Datentyp:** Zeichenfolge<br />**Werte:**<br>* &lt;Liste der Erweiterungen durch Semikolons getrennt&gt; * Z. B. **Obj; Bibliothek**<br>**Standard:** Ohne Erweiterung ausgeschlossen|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Nur Desktop<br />**Datentyp:** Zeichenfolge<br />**Werte:**<br />*&lt;Liste der Pfade durch Semikolons getrennt&gt;*<br />Beispiel: **c:\test;c:\test1.exe**<br />**Standardwert:** Es werden keine Pfade ausgeschlossen.|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Nur Desktop<br />**Datentyp:** Zeichenfolge<br />**Werte:**<br>*&lt;Liste der Pfade durch Semikolons getrennt&gt;*<br>Beispiel: **c:\test.exe;c:\test1.exe**<br>**Standardwert:** Es werden keine Prozesse ausgeschlossen.|

## &nbsp;&nbsp;&nbsp;Rand-browser

|Name der Richtlinie und URI|Details|
|---------------|------------|-----------|
|**Browser zulassen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Nur Mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0**: Durchsuchen aus, **1**: Browsen auf (Standard)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0**: nicht anzeigen Vorschläge, **1**: Anzeigen der Vorschläge (Standard)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0**: deaktiviert (open Intranetwebsites Kante Browser - Standard))<br>**1** - aktiviert (Öffnen Intranetwebsites in Internet Explorer).|
|**Führen Sie zulassen nicht nachverfolgen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Desktop- und mobile)<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – deaktiviert (DNT nicht gesendet - Standard), **1** – aktiviert (senden DNT)|
|**Konfigurieren von SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – nicht zulassen, **1** – zulassen (Standard)|
|**Popups zulassen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – Popups (Standard), **1** – Popups zulassen|
|**Zulassen von Cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – zulassen Cookies von allen Websites (Standard)<br>**1** – nur Drittanbieter-Cookies blockieren<br>**2** – alle Cookies blockieren|
|**Kennwort speichern zulassen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Desktop- und mobile<br />**Datentyp:** Ganze Zahl<br />**Werte:**<br>**0** – Kennwort-Manager ist deaktiviert. <br>**1** – Kennwort-Manager ist aktiviert (Standard)|
|**Zulassen von AutoAusfüllen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Nur Desktop<br />**Datentyp:** Ganze Zahl<br />**Werte:** **0** – deaktiviert (Standard), **1** – aktiviert|
|**Enterprise-Websiteliste konfigurieren**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Nur Desktop<br />**Datentyp:** Zeichenfolge<br />**Werte:<br>**0** – nicht konfiguriert<br>**1** – Verwenden Sie Internet Explorer Enterprise-Modus Websiteliste Wenn (Standard) konfiguriert<br>**2 ** – geben an, der Liste der Enterprise-Website|

## Allgemeine Konfiguration Richtlinieneinstellungen

Verwenden Sie Microsoft Intune **Richtlinie allgemeine Konfiguration** für Windows 10 so konfigurieren Sie die integrierte Einstellungen für registrierten Windows 10 Desktop- und 10 unter Windows Mobile Geräte ein. 

## &nbsp;&nbsp;&nbsp;Kennwort

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|
|**Anfordern eines Kennworts zum Entsperren von Geräten**|-|
|**Kennwort geben erforderlich**|Gibt an, ob das Kennwort numerisch sein muss nur oder alphanumerische|
|**Kennwort geben erforderlich** - **legt minimale Anzahl von Zeichen**|Es gibt vier Zeichensätzen, Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole. Diese Einstellung gibt an, wie viele dieser Datensätze im Kennwort enthalten sein müssen.|
|**Mindestlänge des Kennworts**|Gilt nur für Windows-10-Mobile|
|**Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird**|Für Windows-10-Geräte: Wenn das Gerät BitLocker aktiviert hat, es wird angeordnet werden in BitLocker Wiederherstellungsmodus nach der Anmeldung an, wie oft schlägt Sie angeben. Wenn das Gerät nicht BitLocker aktiviert ist, wird diese Einstellung nicht angewendet.<br>Für 10 unter Windows Mobile-Geräte: nach der Anmeldung an, wie oft fehlschlägt Sie angeben, wird das Gerät bereinigt.|
|**Minuten nach der letzten, bevor der Bildschirm ausgeschaltet**|Gibt die Länge der Zeit, die ein Gerät im Leerlauf sein muss, bevor der Bildschirm gesperrt ist.|
|**Kennwortablauf (Tage)**|Gibt die Länge der Zeit nach dem Kennwort für das Gerät geändert werden muss.|
|**Denken Sie daran Kennwortverlauf**|Gibt an, ob Sie verhindern, dass der Endbenutzer zuvor verwendete Kennwörter erstellen möchten.|
|**Denken Sie daran Kennwortverlauf** - **zu verhindern, dass Wiederverwendung von vorherigen Kennwörtern**|Gibt die Anzahl der zuvor verwendete vom Gerät gespeicherte Kennwörter an.|
|**Anfordern eines Kennworts, wenn Sie das Gerät aus Leerlauf zurückgibt**|Wenn Sie aktiviert ist, muss der Benutzer ein Kennwort zum Entsperren des Geräts eingeben. (Nur Windows 10 Mobile)|

## &nbsp;&nbsp;&nbsp;Verschlüsselung

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|
|**Vorschreiben von Verschlüsselung auf mobilen Geräten**|Aktivieren der Verschlüsselung auf den Geräten.<br>(Nur Windows 10 Mobile)|

## &nbsp;&nbsp;&nbsp;System

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|
|**Einen Bildschirmausschnitt zulassen**|Lassen Sie uns der Benutzer den Gerätebildschirm als Bild erfassen. (Nur Windows 10 Mobile)|
|**Manuelle Unenrollment zulassen**|Ermöglicht dem Benutzer, der das Konto Arbeitsplatz manuell vom Gerät löschen.|
|**Manuelle Root Zertifikatinstallation erlauben**|Gilt für Windows 10 Mobile|
|**Zulassen von Diagnose- und die Verwendung von Daten an Microsoft gesendet werden**|Mögliche Werte sind:<br><br>**Keine** : keine Daten an Microsoft gesendet wird.<br>**Grundlegende** - eingeschränkte Informationen wird folgendem Microsoft gesendet.<br>**Enhanced** - Enhanced diagnostic Daten werden an Microsoft gesendet.<br>**Vollständige (empfohlen)** -sendet dieselben Daten als **Enhanced**sowie weitere Daten zum Gerätestatus|


## &nbsp;&nbsp;&nbsp;Konto und Synchronisierung

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|---------------------|
|**Zulassen von Microsoft-Konto**|Kann der Benutzer ein Microsoft-Konto mit dem Gerät zugeordnet werden soll.|
|**Zulassen Sie Manuelles Hinzufügen von nicht-Microsoft-Konten**|Ermöglicht dem Benutzer, e-Mail-Konten hinzufügen, um das Gerät, das nicht mit einem Microsoft-Konto verknüpft sind.|
|**Zulassen der Synchronisierung von Einstellungen für Microsoft-Konten**|Lassen Sie Gerät und app-Einstellungen, die mit einem Microsoft-Konto für die Synchronisierung zwischen Geräten verbunden sind zu.|

## &nbsp;&nbsp;&nbsp;Microsoft-Rand

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|
|**Webbrowser zulassen**|Die Verwendung des Webbrowsers Kante auf dem Gerät zulassen.<br>(Nur Windows 10 Mobile)|
|**Adressleiste Suchvorschläge zulassen**|Können Ihre Websites vorschlagen, während der Eingabe Suchausdrücke Suchmaschine an.|
|**Zulassen Sie senden von Datenverkehr im Intranet in Internet Explorer**|Ermöglicht Benutzern das Intranet-Websites in Internet Explorer zu öffnen.<br>(Nur für Windows-10-Desktop)|
|**Zulassen kann nicht nachverfolgen**|Konfiguriert den Rand Browser senden nicht Nachverfolgen von Kopfzeilen zu Websites, die Benutzer besuchen.|
|**Aktivieren Sie SmartScreen**|-|
|**Active scripting zulassen**|Ermöglicht es Skripts, wie Javascript im Browser Kante auszuführenden aus.|
|**Popups zulassen**|Gilt nur für Windows-10-desktop|
|**Zulassen von cookies**|-|
|**Zulassen von AutoAusfüllen**|Benutzern Sie die AutoVervollständigen-Einstellungen im Browser zu ändern.<br>(Nur für Windows-10-Desktop)|
|**Kennwort-Manager zulassen**|Aktivieren Sie oder deaktivieren Sie die Funktion Kante Kennwort-Manager.|
|**Enterprise-Modus Website Listenspeicherort**|Gibt an, wo finden Sie die Liste der Websites, die in der Enterprise-Modus geöffnet wird. Benutzer können nicht auf diese Liste bearbeiten.<br>(Nur für Windows-10-Desktop)|

## &nbsp;&nbsp;&nbsp;Apps

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|---------------------|
|**Anwendungsspeicher zulassen**|Gilt nur für Windows-10-Mobile|



## &nbsp;&nbsp;&nbsp;Mobiltelefon

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|---------------------|
|**Daten roaming zulassen**|Zulassen von roaming zwischen Netzwerken beim Zugriff auf Daten.|
|**Zulassen von VPN über Mobiltelefon**|Steuert, ob das Gerät VPN-Verbindungen bei einer Mobile bestehender zugreifen kann.|
|**Zulassen Sie VPN über Mobiltelefon roaming**|Steuert, ob das Gerät VPN-Verbindungen zugreifen kann, klicken Sie auf einem Mobilfunknetz Roaming.|

## &nbsp;&nbsp;&nbsp;Hardware

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|
|**Kamera zulassen**|-|
|**Wechselmedien zulassen**|Gibt an, ob externen Speichergerät, z. B. einer SD-Karte mit dem Gerät verwendet werden können.|
|**Wi-Fi zulassen**|Gilt nur für Windows-10-Mobile|
|**Internetfreigabe zulassen**|Lassen Sie die Verwendung von ICS auf dem Gerät zu.|
|**Manuelle Konfiguration von WLAN-Verbindung zulassen**|Steuert, ob der Benutzer eigene WLAN-Verbindungen konfigurieren kann oder ob sie nur Verbindungen mit einem Wi-Fi-Profil konfiguriert verwendet werden können.<br>(Nur Windows 10 Mobile)|
|**Zulassen Sie automatische Verbindung mit Wi-Fi-Hotspots frei**|Ermöglicht das Gerät automatisch mit kostenlosen Wi-Fi-Hotspots verbinden und automatisch Geschäftsbedingungen für die Verbindung zu akzeptieren.|
|**Geografischen Standort zulassen**|Gibt an, ob das Gerät Standortinformationen für Dienste verwenden kann.|
|**NFK zulassen**|Ermöglicht das Gerät in der Nähe Feld Kommunikation Funktionen verwenden.|
|**Bluetooth zulassen**|-|
|**Zulassen von auffindbar zu Bluetooth-Modus**|Lassen Sie uns werden dieses Gerät von anderen Bluetooth-Geräten erkannt.|
|**Bluetooth-Werbung zulassen**|Ermöglicht Geräten ankündigen über Bluetooth empfangen.|
|**Telefon zurücksetzen zulassen**|Steuert, ob die Benutzer können Factory Geräts zurücksetzen.|
|**USB-Verbindung zulassen**|Steuert, ob Geräte externe Geräte über eine USB-Verbindung zugreifen können.|
|**AntiTheft Modus zulassen**|Konfigurieren Sie, ob Windows Antitheft Modus aktiviert ist.|

## &nbsp;&nbsp;&nbsp;Features

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|----------------------|---------------------|
|**Zulassen von kopieren und einfügen**|Gilt nur für Windows-10-Mobile|
|**Aufzeichnen von gesprochenem Text zulassen**|Gilt nur für Windows-10-Mobile|
|**Cortana zulassen**|Aktivieren Sie oder deaktivieren Sie des Cortana VoIP-Assistenten.|
|**Zulassen der Aktion Center Benachrichtigungen**|Aktivieren Sie oder deaktivieren Sie der Aktion Center Benachrichtigungen im Sperrbildschirm Gerät.<br>(Nur Windows 10 Mobile)|

## &nbsp;&nbsp;&nbsp;Windows Defender

Alle Einstellungen sind für Windows 10 Desktop nur auf.

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|-|-|
|**Spalten können in Echtzeit überwacht werden**|Ermöglicht die Echtzeit-Scan für Malware, Spyware und anderer unerwünschter Software.|
|**Verhalten Überwachung zulassen**|Können prüfen, ob bestimmte bekannte Muster verdächtiger Aktivitäten auf Geräten Defender.|
|**Aktivieren Sie Network Prüfung System**|Das Netzwerk Prüfung System (NIS) können mithilfe von Signaturen bekannter Sicherheitsprobleme aus dem Microsoft Endpoint Protection Center besser erkennen und blockieren bösartigen Datenverkehr Geräte vor Netzwerk-basierten Angriffen schützen.|
|**Scannen Sie alle downloads**|Steuert, ob Defender alle aus dem Internet heruntergeladene Dateien durchsucht.|
|**Skript-Scanner zulassen**|Ermöglicht Defender Skripts scannen, die Sie in Internet Explorer verwendet werden.|
|**Überwachen der Aktivitäten in Datei- und Programm**|Aktivieren Sie diese Einstellung, damit Defender zum Überwachen der Aktivitäten in Datei- und Programm auf Geräten ermöglichen.|
|**Tage bis gelöst Schadsoftware nachverfolgen**|Ermöglicht Defender weiterhin für die Anzahl der Tage gelöst Schadsoftware verfolgen Sie angeben, damit Sie manuell können, dass das Kontrollkästchen zuvor Geräte betroffen. Wenn Sie die Anzahl der Tage auf **0**festgelegt, Schadsoftware bleibt in einem Ordner, und wird nicht automatisch entfernt. |
|**Client-Benutzeroberfläche Zugriff zulassen**|Steuert, ob die Benutzeroberfläche von Windows Defender Endbenutzer ausgeblendet ist.<br>Wenn diese Einstellung geändert wird, wird es das nächste Mal wirksam, die, das den Endbenutzer-Computer neu gestartet wurde.|
|**Planen eines täglichen schnellen-Scans**|Können Sie einen schnellen Scan planen, der täglich gleichzeitig angezeigt wird, die Sie auswählen.|
|**Planen Sie einen System-scan**|Können Sie einen vollständige oder schnelle Systemscan planen, der regelmäßig tritt auf Datum und Uhrzeit, die Sie auswählen.|
|**CPU-Auslastung während einer Überprüfung zu beschränken.**|Können Sie den Umfang der CPU zu beschränken, die scannt (zwischen **1** und **100**) verwendet werden darf|
|**Scannen Archivieren von Dateien**|Diese Berechtigung ermöglicht Defender archivierte Dateien wie Zip oder Cab überprüft.|
|**Scannen von e-Mail-Nachrichten**|Diese Berechtigung ermöglicht Defender e-Mail-Nachrichten überprüft Ankunft auf dem Gerät.|
|**Austauschbare Laufwerke scannen**|Ermöglicht Defender austauschbare Datenträger wie USB-Sticks scannen.|
|**Scannen lösende**|Scannen von Dateien auf zugeordneten Netzlaufwerk Defender, können.<br>Wenn Sie die Dateien auf das Laufwerk schreibgeschützt sind, werden Defender kann nicht gefunden in diese Malware entfernt.|
|**Scannen von Dateien in freigegebenen Ordnern im Netzwerk geöffnet**|Ermöglicht Defender Scannen von Dateien auf freigegebenen Netzlaufwerk Laufwerke (z. B., die einen FERNEN Pfad zugegriffen.<br>Wenn Sie die Dateien auf das Laufwerk schreibgeschützt sind, werden Defender kann nicht gefunden in diese Malware entfernt.|
|**Signatur Aktualisierungsintervall**|Geben Sie das Intervall, in dem Defender prüft, für neue Signaturdateien an.|
|**Cloud-Schutz zulassen**|Zulassen Sie oder Sperren Sie der Dienst Microsoft Active Schutz von empfangen Informationen zu Schadsoftware Aktivität von Geräten, die Sie verwalten. Diese Informationen werden verwendet, um den Dienst in der Zukunft zu verbessern.|
|**Benutzer auffordern, zum Senden von Beispielen**|Steuert, ob Dateien, die weiteren möglicherweise Analyse von Microsoft erfordern, um festzustellen, ob sie bösartiger sind automatisch an Microsoft gesendet werden.|
|**Potenziell unerwünschte Anwendung Erkennung**|Mit dieser Einstellung kann registrierten Windows-desktop Geräte gegen das Ausführen von Windows Defender klassifiziert, wie potenziell unerwünschte Software geschützt verwendet werden. Sie können Schutz vor dieser Anwendung, die ausgeführt, oder verwenden Audit Modus Bericht aus, wenn eine potenziell unerwünschte Anwendung installiert ist.|
|**Dateien und Ordner, wann ausschließen, einen Scan ausgeführt, oder verwenden Schutz in Echtzeit**|Fügen Sie eine oder mehrere Dateien und Ordner wie **C:\Path** oder **%ProgramFiles%\Path\filename.exe** in der Liste der Ausschlüsse hinzu. Diese Dateien und Ordner werden nicht in einer beliebigen scannt in Echtzeit oder geplanten berücksichtigt.|
|**Dateierweiterungen wann ausschließen einen Scan ausgeführt, oder verwenden Schutz in Echtzeit**|Ein oder mehrere Dateierweiterungen wie **Jpg** oder **Txt** der Ausschlüsse Liste hinzufügen. Alle Dateien mit folgenden Erweiterungen werden nicht in einer beliebigen scannt in Echtzeit oder geplante berücksichtigt.|
|**Prozesse wann ausschließen einen Scan ausgeführt, oder verwenden Schutz in Echtzeit**|Fügen Sie einen oder mehrere Prozesse der Typ **.exe**, **.com**oder **.scr** zur Liste Ausschlüsse aus. Diese Prozesse werden nicht in einer beliebigen scannt in Echtzeit oder geplanten berücksichtigt.| 


## &nbsp;&nbsp;&nbsp;Updates

|Name der Einstellung|Weitere Informationen (sofern erforderlich)|
|----------------|---------------|
|**Zulassen von automatischen updates**|Aktivieren Sie diese Einstellung, um automatische Updates zu ermöglichen. Konfigurieren Sie dann eine der folgenden Einstellungen Aktualisierungsverhalten steuern:<br />**Benachrichtigen herunterladen**<br />**Automatische Wartung gleichzeitig installieren**<br />**Automatische installieren und Wartung Zeitpunkt neu starten**<br />**Automatische installieren und zum geplanten Zeitpunkt neu starten** **Hinweis:** Wenn diese Option ausgewählt ist, können Sie auch die folgenden Einstellungen konfigurieren: **unterdrücken Benachrichtigung des Endbenutzers** und **definieren Tag für geplante Updates zu installieren**.<br>(Nur für Windows-10-Desktop)|
|**Vorabversion Features ermöglichen**|Ermöglicht Microsoft Windows 10 Geräte Vorabversion Einstellungen und Features bereitstellen. Sie können auswählen, nur Einstellungen oder alle Einstellungen Vorabversion und Features installiert werden.|

### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


