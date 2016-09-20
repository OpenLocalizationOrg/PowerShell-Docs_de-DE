---
title: WLAN-Verbindungen | Microsoft Intune
description: "Verwenden Sie Wi-Fi-Profile in Verbindung mit Ihrem WLAN Benutzern dabei helfen können."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 5bad6dce377bcec66154ecbb4febe5316894402f
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Konfigurieren der Verbindung zu Ihrem corporate WLAN Geräte

Verwenden Sie Microsoft Intune Wi-Fi-Profile, um die Einstellungen für drahtlose Netzwerke für Benutzer und Geräte in Ihrer Organisation bereitstellen. Wenn Sie mit einem Wi-Fi-Profil bereitstellen, haben Ihre Benutzer Zugriff auf Ihre corporate Wi-Fi ohne selbst konfigurieren.

Angenommen, Sie installieren ein neues Wi-Fi-Netzwerk mit dem Namen **"Contoso" Wi-Fi** und alle iOS-Geräte einrichten, die Verbindung zu diesem Netzwerk herstellen möchten. Hier ist der Vorgang ein:

![Wi-Fi-Prozess Zusammenfassung](..\media\wi-fi-process-diagram.png) 

1.   Erstellen Sie ein WLAN-Profil, enthält die Einstellungen für die Verbindung zu den **Contoso Wi-Fi** -Netzwerk ein.

2. Bereitstellen des Profils für die Gruppe von Benutzern mit iOS-Geräte.

3.   Benutzer finden in der Liste der drahtlosen Netzwerke das neue **"Contoso" Wi-Fi** -Netzwerk und können einfach die Verbindung zu diesem Netzwerk.


## So erstellen Sie ein WLAN-Profil

Sie können die folgenden Plattformen Wi-Fi-Profile bereitstellen:

-   Android 4.0 und höher

-   iOS 8.0 und höher

-   Mac OS X 10.9 und höher

Für Geräte, die Windows 8.1 oder Windows 10 desktop oder mobilen ausgeführt werden, können Sie ein Profil der Wi-Fi-Konfiguration importieren, die zuvor in eine Datei exportiert wurde. Details finden Sie unter [Exportieren oder importieren Sie eine WLAN - Konfigurationsprofil für Windows-Geräte](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com)auf die **Richtlinie** &gt; **Richtlinie hinzufügen**.

2.  Wählen Sie eine der folgenden Tabstopptypen Richtlinie, und klicken Sie dann auf **Richtlinie zu erstellen**:

    -   Wi-Fi-Profil (Android 4 und höher)

    -   Wi-Fi-Profil (iOS 8.0 und höher)

    -   Wi-Fi-Profil (Mac OS X 10.9 und höher)

    Es gibt keine empfohlenen Einstellungen für diese Richtlinie ein. Sie müssen eine benutzerdefinierte Richtlinie erstellen.

3.  Geben Sie die Namen und eine Beschreibung für das Profil ein.

4. Geben Sie die Werte **Netzwerk Verbindungen** an.
 - **SSID (Service Set Identifier)**: Benutzer finden Sie unter den Netzwerknamen, nicht die SSID.
 - **Verbinden, wenn das Netzwerk seinen Namen (SSID) nicht übertragen wird**: Wählen Sie diese Option, um Geräte können mit dem Netzwerk herzustellen, wenn es nicht in der Liste der Netzwerke sichtbar ist (weil es ausgeblendet ist und übertragen nicht auf deren Namen).
 
5. Konfigurieren der **Sicherheitseinstellungen** für die ausgewählte Plattform an. Verfügbaren Einstellungen abhängig von der Sicherheitstypen, die Sie auswählen und [Sicherheitseinstellungen](#security-settings)beschrieben werden.

6. (iOS und MAC OS X nur) Konfigurieren von **Proxyeinstellungen**

    |Name der Einstellung|Weitere Informationen|Verwenden Sie bei:|
    |----------------|-------------------|-------------|
    |**Proxyeinstellungen für diese WLAN-Verbindung**|Wählen Sie aus, dass die Proxyeinstellungen geben:<br /><br />-   **Keine** (Standard)<br />-   **Manueller** – manuell Geben Sie die URL und port-Nummer des Proxy-Servers.<br />-   **Automatische** – Verwenden einer Konfigurationsdatei zum Konfigurieren des Proxyservers.|Immer|
    |**Server-Proxyadresse** und **Port-Nummer**|Geben Sie die URL und port-Nummer des Proxy-Servers.|**Proxyeinstellungen für diese WLAN-Verbindung** ist auf **manuell** gesetzt.|
    |**Proxy-Server-URL**|Geben Sie die URL der Datei mit Proxyeinstellungen ein.|**Proxyeinstellungen für diese WLAN-Verbindung** wird auf **Automatische** festgelegt.|

7.  Speichern Sie das Wi-Fi-Profil

Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt. Informationen zum Bereitstellen des Profils finden Sie unter **Nächste Schritte** .

## Exportieren oder Importieren eines Wi-Fi-Konfigurationsprofils für Windows-Geräte
 
Für Geräte, die Windows 8.1 oder Windows 10 desktop oder mobilen ausgeführt werden, können Sie ein Profil der Wi-Fi-Konfiguration importieren, die zuvor in eine Datei exportiert wurden. 

### Exportieren eines Wi-Fi-Profils
Unter Windows können Sie das **Netsh Wlan** -Programm so exportieren Sie ein vorhandenes Wi-Fi-Profil in eine XML-Datendatei lesbare von Intune verwenden. Führen Sie auf einem Windows-Computer, der bereits installierte das erforderliche WiFi-Profil dieses folgenden Verfahren aus.

1.  Erstellen Sie einen lokalen Ordner für die exportierte W-Fi-Profile, z. B. c:\WiFi

2.  Öffnen Sie ein Eingabeaufforderungsfenster als Administrator.

3.  Führen Sie den Befehl `netsh wlan show profiles`, und notieren Sie den Namen des Profils, das Sie exportieren möchten.  In diesem Beispiel wird der Name des Profils *WiFiName*.

4.  Führen Sie diesen Befehl: `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Dadurch wird eine WLAN-Profil-Datei mit dem Namen "Wi-Fi-WiFiName.xml ist die im Ordner" Ziel "" erstellt.

### Importieren eines Wi-Fi-Profils
Verwenden Sie die **Windows Wi-Fi importieren Richtlinie** , um eine Reihe von WLAN-Einstellungen zu importieren, die Sie dann die erforderlichen Gruppen für Benutzer oder Gerät bereitstellen können.


1.  Klicken Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com)auf die **Richtlinie** &gt; **Richtlinie hinzufügen**.

2.  Konfigurieren eine Richtlinie vom Typ **Windows** &gt; **Wi-Fi importieren (Windows 8.1 und höher)**.

    Dieser Richtlinie kann angewendet werden, um Windows 8.1 und Windows 10 Desktop- und Mobile Geräte.

    Sie können nur erstellen und Bereitstellen einer *benutzerdefinierten* Richtlinie für Windows Wi-Fi-importieren. Empfohlene Einstellungen sind nicht verfügbar.

3.  Geben Sie die folgenden allgemeinen Werte für die Richtlinie Windows Wi-Fi importieren:

    |Name der Einstellung|Weitere Informationen|
    |----------------|--------------------|
    |**Namen**|Geben Sie einen eindeutigen Namen für das WLAN-Profil, um ihn in die Intune-Verwaltungskonsole zu identifizieren.|
    |**Beschreibung**|Geben Sie eine Beschreibung, die das Wi-Fi-Profil und weitere relevante Informationen, die Sie danach zu suchen dabei unterstützt, w.|

4.  Geben Sie die folgenden Werte unter der Überschrift **Benutzerdefinierte Wi-Fi-Profil** an:

    |Name der Einstellung|Weitere Informationen|
    |----------------|--------------------|
    |**Konfigurationsdatei-Profil**|Klicken Sie auf **Importieren** , um Wählen Sie die XML-Datei, enthält die Wi-Fi-einräumen, die Sie in Intune importieren möchten.|
    |**Benutzerdefinierte Konfiguration Profilname (für Benutzer angezeigt)**|Zeigt den Namen des Profils Wi-Fi-Konfiguration für Benutzer Geräts angezeigt wird.|
    |**Konfiguration von Profildetails**|Zeigt den XML-Code für das Konfigurationsprofil, das Sie ausgewählt haben.|

5.  Wenn Sie fertig sind, klicken Sie auf **Richtlinie speichern**.

6.  Die neue Richtlinie zeigt in den Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** .

## Bereitstellen des Profils

Ein Profil ist eine Art Richtlinie, verwenden Sie also den Richtlinie Arbeitsbereich bereitzustellen.

1.  Klicken Sie im Arbeitsbereich **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und klicken Sie auf **Bereitstellung verwalten**.

2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :

    -   **Die Richtlinie bereitstellen** - wählen Sie eine oder mehrere Gruppen aus, dem Sie die Richtlinie bereitstellen möchten, und klicken Sie auf **Hinzufügen** &gt; **OK**.

    -   **Zum Schließen des Dialogfelds ohne es** - klicken Sie auf **Abbrechen**.


Eine Zusammenfassung Status und Benachrichtigungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie** identifizieren Sie Probleme mit der Richtlinie, die Ihre Aufmerksamkeit erfordern. Darüber hinaus wird ein Zusammenfassung Status im Dashboard-Arbeitsbereich ein.

## Sicherheitseinstellungen
In diesen Tabellen müssen die Details für die Einstellungen, die für Android, iOS und Mac OS X Wi-Fi-Profile verfügbar sind. 

### Sicherheitseinstellungen für Android-Geräten

  |Name der Einstellung|Weitere Informationen|Verwenden Sie bei:|
|----------------|--------------------|-------------|
|**Sicherheitstyp**|Wählen Sie das Protokoll für das WLAN ein:<br /><br />-   **WPA-Enterprise/WPA2-Unternehmen**<br />-   **Keine Authentifizierung (offen)** , wenn das Netzwerk unsicher ist.|Immer|
|**EAP-Typ**|Wählen Sie den Extensible Authentication-Protokoll (EAP) abgesichert Kommunikationsmedien Authentifizierung verwendet:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Sie aktiviert den Sicherheitstyp **WPA-Enterprise/WPA2-Unternehmen** .|
|**Wählen Sie Stammzertifikate für Server-Überprüfung**|Klicken Sie auf **auswählen**, und wählen Sie dann das vertrauenswürdiges Zertifikatsprofil verwendet, um die Verbindung zu authentifizieren. **Wichtige:** So erstellen Sie das Profil vertrauenswürdiges Zertifikat finden Sie unter [sicheren Ressourcenzugriff mit Zertifikatsprofile](secure-resource-access-with-certificate-profiles.md).|Alle **EAP-Typ** ausgewählt ist.|
|**Authentifizierungsmethode**|Wählen Sie die Authentifizierungsmethode für die Verbindung aus:<br /><br />-   **Zertifikate** , um anzugeben, das Client-Zertifikat<br />-   **Benutzername und Kennwort** an eine andere Methode für die Authentifizierung|Der **EAP-Typ** ist **PEAP-** oder **EAP-TTLS**.|
|**Wählen Sie eine Methode nicht EAP für die Authentifizierung (inneren Identität)**|Wählen Sie, wie Sie die Verbindung zu authentifizieren werden:<br /><br />-   **Keine**<br />-   **Unverschlüsselter Kennwort (PAP)**<br />-   **Herausforderung Handshake Authentication-Protokoll (CHAP)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP Version 2 (MS-CHAP 2)**<br /><br />Die verfügbaren Optionen hängen vom gewählten EAP-Typ ab.|Der **Authentifizierungsmethode** ist **Benutzernamen und Ihr Kennwort ein**.|
|**Aktivieren Sie Identitätsdatenschutz (externe Identität)**|Geben Sie den Text, der als Antwort auf eine EAP Identität Request gesendet. Dieser Text kann jeder Wert sein. Während der Authentifizierung diese anonyme Identität ursprünglich gesendet, und klicken Sie dann gefolgt von der real Kennung in einen sicheren Tunnel gesendet.|Der **EAP-Typ** ist **PEAP-** oder **EAP-TTLS**.|
|**Wählen Sie ein Clientzertifikat für Client-Authentifizierung (Identität Zertifikat)**|Klicken Sie auf **auswählen**, und wählen Sie dann das SCEP Zertifikatsprofil verwendet, um die Verbindung zu authentifizieren. **Wichtige:** Zum Erstellen einer SCEP Zertifikat Profils finden Sie unter [sichere Ressourcenzugriff mit Zertifikatsprofilen](secure-resource-access-with-certificate-profiles.md).|Der Sicherheitstyp ist **WPA-Enterprise/WPA2-Unternehmen**und alle **EAP-Typ** ausgewählt ist.|

### Sicherheitseinstellungen für iOS und Mac OS X-Geräte

  |Name der Einstellung|Weitere Informationen|Verwenden Sie bei:|
|----------------|--------------------|-------------|
|**Sicherheitstyp**|Wählen Sie das Protokoll drahtlosen Netzwerk aus:<br /><br />-   **WPA-Persönlich/WPA2-Persönlich**<br />-   **WPA-Enterprise/WPA2-Unternehmen**<br />-   **WEP**<br />-   **Keine Authentifizierung (offen)** , wenn das Netzwerk unsicher ist.|Immer|
|**EAP-Typ**|Wählen Sie den Extensible Authentication-Protokoll (EAP) abgesichert Kommunikationsmedien Authentifizierung verwendet:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **SPRUNG**<br />-   **EAP-SIM**|Ausgewählten einen Sicherheitstyp des **WPA-Enterprise/WPA2-Unternehmen**.|
|**Vertrauenswürdige Zertifikat Servernamen**|Wählen Sie das vertrauenswürdiges Zertifikatsprofil verwendet, um die Verbindung zu authentifizieren. **Wichtige:** So erstellen Sie das Profil vertrauenswürdiges Zertifikat finden Sie unter [sicheren Ressourcenzugriff mit Zertifikatsprofile](secure-resource-access-with-certificate-profiles.md).|Ausgewählten EAP-Typ **EAP-TLS**, **PEAP**, **EAP-TTLS** oder **EAP-FAST**.|
|**Verwenden Sie geschützte Zugriffsberechtigung (PAC)**|Wählen Sie die um Anmeldeinformationen für geschützten Zugriff zu verwenden, um einen authentifizierten Tunnel zwischen dem Client und Authentifizierungsserver einrichten. Eine vorhandene PAC-Datei wird verwendet, falls vorhanden.|Der **EAP-Typ** ist **EAP-FAST**.|
|**Bereitstellen von PAC**|Vorschriften die PAC-Datei auf Geräte.<br /><br />Wenn verwendet haben, können Sie auch auswählen **Bereitstellen PAC anonym** um sicherzustellen, dass die PAC-Datei ohne Authentifizieren des Servers bereitgestellt wird.|**Verwenden Sie geschützte Zugriffsberechtigung (PAC)** aktiviert ist.|
|**Authentifizierungsmethode**|Wählen Sie die für die Verbindung verwendete Authentifizierungsmethode aus:<br /><br /><ul><li>**Zertifikate** das Client-Zertifikat angeben.</li><li>**Benutzername und Kennwort** auf eine der folgenden Methoden für die Authentifizierung (auch bekannt als inneren Identität) nicht EAP angeben:<br /><br /><ul><li>**Keiner**</li><li>**Unverschlüsselter Kennwort (PAP)**</li><li>**Herausforderung Handshake Authentication-Protokoll (CHAP)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP Version 2 (MS-CHAP 2)**</li><li>**EAP-TLS**</li></ul></li></ul>|Der **EAP-Typ** ist **PEAP-**oder **EAP-TTLS**.|
|**Wählen Sie ein Clientzertifikat für Client-Authentifizierung (Identität Zertifikat)**|Wählen Sie das SCEP Zertifikatsprofil verwendet, um die Verbindung zu authentifizieren. **Wichtige:** Zum Erstellen eines SCEP Zertifikat Profils finden Sie unter [sichere Ressourcenzugriff mit Zertifikatsprofilen](secure-resource-access-with-certificate-profiles.md).|Der Sicherheitstyp **WPA-Enterprise/WPA2-Unternehmen** und den **EAP-Typ** wird **EAP-TLS**, **PEAP** oder **EAP-TTLS**.|
|**Aktivieren der Identitätsdatenschutz (externe Identität)**|Geben Sie Text ein, der als Antwort auf eine EAP Identität Request gesendet. Dieser Text kann jeder Wert sein.<br /><br />Während der Authentifizierung wird diese anonyme Identität ursprünglich gesendet gefolgt von der real Kennung in einen sicheren Tunnel gesendet.|Wenn der **EAP-Typ** **PEAP**, **EAP-TTLS** oder **EAP-FAST**festgelegt ist.|


### Siehe auch
Informationen Sie zum Erstellen eines Profils WLAN-Verbindung mit einer vorinstallierten Schlüssel [vorinstallierten Key Wi-Fi](pre-shared-key-wi-fi-profile.md) -Profil
