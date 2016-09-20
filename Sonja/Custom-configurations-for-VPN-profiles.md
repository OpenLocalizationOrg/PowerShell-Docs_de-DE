---
title: "Benutzerdefinierte Konfigurationen für VPN Profile | Microsoft Intune"
description: Verwenden Sie benutzerdefinierte Konfigurationen VPN Profile in Intune erstellen.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 6f6a18318070aa9e7d6dfc27a820d9d8f2054069
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Benutzerdefinierte Konfigurationen für VPN Profile

## Erstellen einer benutzerdefinierten Konfigurations
Benutzerdefinierte Konfigurationen können Sie VPN Profile in Intune erstellen. So erstellen Sie eine benutzerdefinierte Konfiguration

   1. In der Intune Admin-Konsole **Richtlinie** > **Richtlinie hinzufügen** > *<Expand platform>* > **benutzerdefinierte Konfiguration** > **Richtlinie erstellen**.
   2. Geben Sie einen Namen für die Richtlinie ein.
   3. Wählen Sie für jede URI-Einstellung **Hinzufügen**aus, und geben Sie die angeforderte Informationen. Hier ist ein Beispiel:

   ![Im Dialogfeld Profil benutzerdefinierte Konfiguration VPN](./media/Intune_Add_VPN_URI.png)

   4.  Nachdem Sie alle Einstellungen URI eingegeben haben, wählen Sie die **Richtlinie speichern**aus, und klicken Sie dann bereitstellen Sie die Richtlinie.

## Bereitstellen einer Konfigurationsrichtlinie

1.  Klicken Sie im Arbeitsbereich **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und klicken Sie dann auf **Bereitstellung verwalten**.

2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :

    -   **Die Richtlinie bereitstellen** - wählen Sie eine oder mehrere Gruppen, dem Sie die Richtlinie bereitstellen möchten, und klicken Sie dann auf **Hinzufügen** &gt; **OK**.

    -   **Zum Schließen des Dialogfelds ohne es** - wählen Sie **Abbrechen**aus.

Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Richtlinien Liste anzeigen.

##Beispiel für URI-Einstellungen für eine benutzerdefinierte Konfiguration von VPN-Profil
Hier sind Beispieleinträge für die zum Erstellen einer benutzerdefinierten Konfigurations für ein VPN in fiktive Firma Contoso-URI-Werte ein. Weitere Informationen, wie den Datentyp für jeden Eintrag finden Sie unter [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx).

Systemeigene Contoso VPN (IKEv2): ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

VPN.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

EAP ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig Xmlns = "http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;geben Xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;-Anbieter-ID Xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType Xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AutorID Xmlns = "http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config Xmlns = "http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap Xmlns = "http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Typ&gt;13 &lt;/Type&gt;&lt;EapType Xmlns = "http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;falsch&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;falsch&lt;/DifferentUsername&gt;&lt;PerformServerValidation Xmlns = "http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;falsch&lt;/PerformServerValidation&gt;&lt;AcceptServerName Xmlns = "http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;falsch&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** WAHR

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** WAHR

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** % Programme % (x86) \Internet

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** % Programme % (x86) \Internet

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Fragen zu wie diese Einstellungen verwendet werden soll, oder weitere Details, welche Aufgaben sie ausführen, Kunden sollte finden Sie in der Konfiguration Service Provider (CSP) Dokumentation: https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx.

## URI-Einstellungen für Android pro-app VPN auf PulseSecure
### BENUTZERDEFINIERTEN URI FÜR PAKETLISTE
-  Datentyp = Zeichenfolge
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList
-  Wert = Trennzeichen getrennte Paketliste.
   - Trennzeichen: Semikolon (;), Doppelpunkt (:), Semikolon (;), senkrechter Strich (|)

Beispiele:
- com.Android.Chrome
- com.Android.Chrome;com.Android.Browser

### BENUTZERDEFINIERTEN URI FÜR MODUS (OPTIONAL)
- Datentyp = Zeichenfolge
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Notizen
> - Verwenden Sie den gleichen *Namen* , die das benutzerdefinierte Profil zugewiesen wurden
> - Mögliche Werte: *GLOBAL*, *WEIßEN*, *SCHWARZEN*
> - Standardeinstellungen auf *GLOBAL* , wenn keine PackageList (Abwärtskompatibilität mit System organisationsweite Profile) bereitgestellt wird
> - Standardmäßig *weißen Liste* , wenn eine PackageList bereitgestellt wird


### Siehe auch
(VPN-Verbindungen in Microsoft Intune) [Vpn-Verbindungen-in-Microsoft-intune.md]
