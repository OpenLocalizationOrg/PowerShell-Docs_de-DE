---
title: Wi-Fi mit PSK | Microsoft Intune
description: "Verwenden Sie benutzerdefinierte Konfiguration, um ein WLAN-Profil mit einem vorinstallierten Schlüssel erstellen."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e977c7c7-e204-47a6-b851-7ad7673ceaab
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 35906378f7d489cebbf7b65a5025ad2040c56895
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Erstellen eines Profils WLAN-Verbindung mit einer vorinstallierten Schlüssel
So sieht wie mithilfe Intunes **Benutzerdefinierte Konfiguration** Wi-Fi Profil mit einem vorinstallierten Schlüssel erstellen aus. In diesem Thema enthält auch ein Beispiel zum Erstellen eines Profils EAP-basierten Wi-Fi.

> [!NOTE]
-   Unter Umständen einfacher, kopieren Sie den Code über einen Computer, der mit diesem Netzwerk verbindet, wie unten beschrieben.
- Für Android müssen Sie auch die Möglichkeit, diese [Android PSK Generator](http://johnathonb.com/2015/05/intune-android-pre-shared-key-generator/) von Johnathon Biersack bereitgestellt.
-   Sie können mehrere Netzwerke und Schlüssel hinzufügen, durch Hinzufügen weiterer OMA-URI-Einstellungen.
-  Verwenden Sie für iOS Apple-Konfiguration auf einen Mac Sender einrichten das Profil ein. Alternativ verwenden Sie diese [iOS PSK Mobile Config Generator](http://johnathonb.com/2015/05/intune-ios-psk-mobile-config-generator/) von Johnathon Biersack bereitgestellt.


1.  Zum Erstellen einer WLAN-Profil mit einem vorinstallierten Schlüssel für Android oder Windows oder eine EAP-basierten Wi-Fi-Profil, beim Erstellen einer Richtlinie wählen Sie **Benutzerdefinierte Konfiguration** für diese Geräteplattform anstelle von einem Wi-Fi-Profil.

2.  Geben Sie einen Namen und eine Beschreibung ein.
3.  Fügen Sie eine neue OMA-URI-Einstellung hinzu:

   ein.   Geben Sie einen Namen für diese Einstellung der Wi-Fi-Netzwerk ein.

   b.   Geben Sie eine Beschreibung der Einstellung OMA-URI oder nichts ein.

   c.   **Datentyp**: Legen Sie auf "String(XML)"

   d.   **OMA-URI**:

    - **Für Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **Für Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
Achten Sie darauf, dass der Punkt am Anfang einschließen möchten.

    SSID ist die SSID, für die Sie die Richtlinie erstellen. Beispielsweise
    `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **Wertfeld** ist, in dem Sie Ihren XML-Code einfügen. Hier ist ein Beispiel für ein. Jeder Wert sollte an Ihre Netzwerkeinstellungen angepasst werden. Im Kommentarbereich des Codes für einige Hinweise finden Sie unter.
4. Wählen Sie **OK**, speichern, und klicken Sie dann bereitstellen Sie die Richtlinie.

    > [!NOTE]
    > Dieser Richtlinie kann nur die Benutzergruppen bereitgestellt werden.

Das nächste Mal, das jedes Gerät überprüft, wird die Richtlinie angewendet werden, und ein Wi-Fi-Profil auf dem Gerät erstellt werden. Das Gerät wird automatisch eine Verbindung mit dem Netzwerk herstellen können.
## Android oder Windows Wi-Fi-Profil

Hier ist ein Beispiel für den XML-Code für ein Android oder Windows Wi-Fi-Profil ein:

> [!IMPORTANT]
> 
> `<protected>false</protected>`muss auf **false**festgelegt werden, wie **Wahr** konnte dazu führen, Gerät dass zu erwarten ein verschlüsseltes Kennwort und versuchen Sie dann entschlüsseln, die eine fehlgeschlagene Verbindung führen können.
> 
>  `<hex>53534944</hex>` Klicken Sie auf den hexadezimalen Wert festgelegt werden `<name><SSID of wifi profile></name>`.
>  Windows-10-Geräten möglicherweise einen Fehler *0x87D1FDE8 Fehler bei der Wiederherstellung* false zurück, aber weiterhin mit dem Profil bereitgestellt werden.

    <!--
    <Name of wifi profile> = Name of profile
    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
    <nonBroadcast><true/false></nonBroadcast>
    <Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
    <Type of encryption> = Type of encryption used by the network
    <protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
    <password> = Password to connect to the network
    <hex>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
    -->
    <WLANProfile
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <hex>53534944</hex>
        <name><SSID of wifi profile></name>
        </SSID>
        <nonBroadcast>false</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication><Type of authentication></authentication>
            <encryption><Type of encryption></encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial>MyPassword</keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>

## EAP-basierten Wi-Fi-Profils
Hier ist ein Beispiel des XML-Codes für ein Profil EAP basierende WLAN ein:

    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>

## Erstellen der XML-Datei aus einer bestehenden WLAN-Verbindung
Sie können auch eine XML-Datei aus einer bestehenden WLAN-Verbindung erstellen:
1. Auf einem Computer, die mit verbunden ist oder weist zuletzt mit dem wireless-Netzwerk verbunden ist, öffnen Sie den folgenden Ordner: C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{Guid}.

    Es empfiehlt sich, einen Computer, der nicht mit vielen drahtlosen Netzwerken verbunden weist zu verwenden, weil Sie jedes Profil zum finden der richtigen durchsuchen müssen.
3.     Suchen Sie die XML-Dateien, die diejenige mit dem richtigen Namen gesucht werden soll.
4.     Nachdem Sie die richtige XML-Datei gefunden haben, kopieren Sie, und fügen Sie den XML-Code in das Datenfeld der Seite Einstellungen OMA-URI aus.

## Die Richtlinie bereitstellen

1.  Klicken Sie im Arbeitsbereich **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und wählen Sie dann die **Bereitstellung verwalten**.

2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :

    -   **Die Richtlinie bereitstellen** - wählen Sie eine oder mehrere Gruppen, dem Sie die Richtlinie bereitstellen möchten, und wählen Sie dann auf **Hinzufügen** &gt; **OK**.

    -   **Zum Schließen des Dialogfelds ohne es** - wählen Sie **Abbrechen**aus.

Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Liste Richtlinien anzeigen.

### Siehe auch
[WLAN-Verbindungen in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
