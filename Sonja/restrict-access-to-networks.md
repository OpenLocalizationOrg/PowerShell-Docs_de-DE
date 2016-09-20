---
title: "Einschränken des Zugriffs auf Netzwerke mit Cisco ISE | Microsoft Intune"
description: "Verwenden von Cisco ISE mit Intune, dass Geräte Intune registriert und Richtlinie kompatibel sind, bevor sie Zugriff auf Wi-Fi und VPN, die von Cisco ISE gesteuert werden."
keywords: 
author: nbigman
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: 972848a33764e7073fd9c1867e0a7df643dd630e
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Verwenden von Cisco ISE mit Microsoft Intune
Intune Integration mit Cisco Identität Services Engine (ISE) können Sie zum Richtlinien für Netzwerke in Ihrer Umgebung ISE mithilfe des Intune Gerät Registrierung und Compliance Zustands. Diese Richtlinien können Sie sicherstellen, dass Ihres Unternehmensnetzwerks Zugriff auf Geräte beschränkt ist, die von Intune verwalteten und mit Intune-Richtlinien kompatibel sind.

## Konfigurationsschritte

Um diese Integration zu aktivieren, brauchen Sie jedem Setup in Ihrem Mandanten Intune führen. Sie müssen Berechtigungen zu Ihrem Server Cisco ISE Ihrem Mandanten Intune Zugriff auf bereitstellen. Nach Abschluss dessen geschieht, der Rest der Einrichtung in Ihrem Cisco ISE-Server. Dieser Artikel bietet Ihnen die Anweisungen auf den ISE-Server mit Berechtigungen zum Zugreifen auf Ihrem Mandanten Intune bereitstellen.

### Schritt 1: Verwalten der Zertifikate
Exportieren Sie das Zertifikat aus der Konsole Azure Active Directory (Azure AD), und dann in der Speicher vertrauenswürdige Zertifikate der Konsole ISE importieren:

#### InternetExplorer 11


   ein. Führen Sie Internet Explorer als Administrator aus, und melden Sie sich bei der Azure AD-Verwaltungskonsole.

   b. Wählen Sie die Schlosssymbol in der Adressleiste aus, und wählen Sie **Anzeigen von Zertifikaten**.

   c. Wählen Sie auf der Registerkarte **Details** der Zertifikateigenschaften **in Datei kopieren**aus.

   d. Wählen Sie auf der Begrüßungsseite **Zertifikat export-Assistent** **Weiter**.

   e. Klicken Sie auf der Seite **Dateiformat exportieren** behalten Sie die Standardeinstellung, **DER-codierte binäre x. 509 (. CER)**, und wählen Sie **Weiter**aus.  

   f. Klicken Sie auf der Seite **zu exportierenden Datei** wählen Sie aus, **Navigieren** Sie zu wählen Sie einen Speicherort zum Speichern der Datei, und geben Sie einen Dateinamen an. Obwohl sie den Eindruck haben Sie eine Datei zum Exportieren auswählen, haben Sie tatsächlich die Datei benennen, der an das exportierte Zertifikat gespeichert werden soll. Auswählen der **nächsten** &gt; **Fertig stellen**.

   g. Importieren Sie von innerhalb der Verwaltungskonsole ISE das Zertifikat Intune (die Datei, die Sie exportiert) in den **Vertrauenswürdige Zertifikate** -Speicher ein.

#### Safari

 ein. Melden Sie sich an die Azure AD-Konsole aus.

b. Wählen Sie das Schlosssymbol &gt; **Weitere Informationen**.  

   c. KlickenSie auf **Zertifikat anzeigen** &gt; **Details**.

   d. Wählen Sie das Zertifikat aus, und wählen Sie dann auf **Exportieren**. 

   e. Importieren Sie von innerhalb der Verwaltungskonsole ISE das Zertifikat Intune (die Datei, die Sie exportiert) in den **Vertrauenswürdige Zertifikate** -Speicher ein.

> [!IMPORTANT]
>
> Überprüfen Sie das Ablaufdatum des Zertifikats, werden Sie besitzen, exportieren und importieren ein neues Zertifikat aus, wenn Sie diesen Termin läuft ab.


### Ein selbst signiertes Zertifikat aus ISE zu erhalten. 

1.  Wechseln zur **Verwaltung**der Verwaltungskonsole ISE > **Zertifikate** > **Systemzertifikate** > **Generieren selbst signierte Zertifikat**.  
2.       Exportieren Sie das selbst signierte Zertifikat.
3. In einem Text-Editor, bearbeiten Sie das exportierte Zertifikat: [Kommentar]: <> ich einen Zeitraum am Ende der folgenden beiden Aussagen lieber nicht setzen möchten, wahrscheinlich konnte verwirrend sein.
 - Löschen Sie **---beginnen Zertifikat (...)**
 - Löschen Sie **---Beenden Zertifikat (...)**
 
Sicherstellen, dass alle den Text ist eine Textzeile


### Schritt 2: Erstellen einer app für ISE in Ihrem Azure AD-Mandanten
1. Wählen Sie in der Verwaltungskonsole Azure AD- **Applications** > **Hinzufügen eine Anwendung** > **eine Anwendung, die zur Entwicklung von meinem Unternehmen hinzufügen**.
2. Geben Sie einen Namen und einen URL für die app aus. Die URL könnte Website Ihres Unternehmens.
3. Herunterladen des app-Manifests (eine JSON-Datei).
4. Bearbeiten der JSON-Manifestdatei an. Bereitstellen von der Einstellung **KeyCredentials**aufgerufen, den Text bearbeiteten Zertifikat aus Schritt 1 als Wert festlegen.
5. Speichern Sie die Datei, ohne deren Namen zu ändern.
6. Geben Sie Ihre app mit Berechtigungen zum Microsoft Graph und Intune-API von Microsoft.

 ein. Wählen Sie für Microsoft Graph die folgenden Schritte aus:
    - **Anwendungsberechtigungen**: Lesen Directory-Daten
    - **Delegierte Berechtigungen**:
        - Jederzeit Zugriff auf Daten des Benutzers
        - Melden Sie sich Benutzer in

 b. Für die Microsoft-Intune-API **Anwendungsberechtigungen**, wählen Sie **erste des Geräts und Konformität von Intune**.

7. Wählen Sie **Ansicht Endpunkte** aus, und kopieren Sie die folgenden Werte für die Verwendung in ISE Einstellungen konfigurieren:

|Wert Azure AD-Portal|Entsprechendes Feld ISE-Portal|
|-------------------|---------------------------------|
|Microsoft Azure AD Graph-API Endpunkt|Automatische Erkennung URL|
|OAuth 2.0 Token Endpunkt|Token ausstellenden URL|
|Aktualisieren Sie den Code für Ihre Kunden-ID|Client-ID|

### Schritt 4: Hochladen des selbst signierten Zertifikats aus ISE in der app ISE, dass Sie in Azure Active Directory erstellt
1.     Abrufen von die base64-codierte Zertifikat Wert und Fingerabdruck aus einer öffentlichen Zertifikatsdatei CER-X509. In diesem Beispiel wird PowerShell:
   
      
    `$cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2`
     `$cer.Import(“mycer.cer”)`
      `$bin = $cer.GetRawCertData()`
      `$base64Value = [System.Convert]::ToBase64String($bin)`
      `$bin = $cer.GetCertHash()`
      `$base64Thumbprint = [System.Convert]::ToBase64String($bin)`
      `$keyid = [System.Guid]::NewGuid().ToString()`
 
    Speichern Sie die Werte für base64Thumbprint $, base64Value $ und $keyid, um im nächsten Schritt verwendet werden.
2.       Laden Sie das Zertifikat über die Manifestdatei hoch. Melden Sie sich bei der [Azure-Verwaltungsportal](https://manage.windowsazure.com)
2.      Suchen Sie in Azure AD-Snap-in der Anwendungs, die Sie mit einem x 509-Zertifikat konfigurieren möchten.
3.      Laden Sie die Anwendungsmanifestdatei ein. 
5.      Ersetzen Sie die leeren "KeyCredentials": [], mit den folgenden JSON-Eigenschaft.  KeyCredentials komplexen Typs wird im[Entität und komplexen Typ verweisen](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType)beschrieben.

 
    `“keyCredentials“: [`
    `{`
     `“customKeyIdentifier“: “$base64Thumbprint_from_above”,`
     `“keyId“: “$keyid_from_above“,`
     `“type”: “AsymmetricX509Cert”,`
     `“usage”: “Verify”,`
     `“value”:  “$base64Value_from_above”`
     `}2. `
     `], `
 
Beispiel:
 
    `“keyCredentials“: [`
    `{`
    `“customKeyIdentifier“: “ieF43L8nkyw/PEHjWvj+PkWebXk=”,`
    `“keyId“: “2d6d849e-3e9e-46cd-b5ed-0f9e30d078cc”,`
    `“type”: “AsymmetricX509Cert”,`
    `“usage”: “Verify”,`
    `“value”: “MIICWjCCAgSgAwIBA***omitted for brevity***qoD4dmgJqZmXDfFyQ”`
    `}`
    `],`
 
6.      Speichern Sie die Änderung, um die Anwendungsmanifestdatei.
7.      Hochladen der bearbeiteten Anwendungsmanifestdatei durch die Azure Management mortal.
8.      Optional: Herunterladen des Manifests erneut, um zu überprüfen, dass Ihre x. 509-Zertifikat auf der Anwendung vorhanden ist.

>[!NOTE]
>
> KeyCredentials ist, daher können Sie mehrere x. 509-Zertifikate für Rollover Szenarien hochladen oder Zertifikate Vorlagen in Kompromisse Szenarien löschen.


### Schritt 4: Konfigurieren von ISE Einstellungen
Bieten Sie in der Verwaltungskonsole ISE Administrator diese Einstellungswerte ein:
  - **Server-Typ**: Mobile Geräte-Manager
  - **Authentifizierungstyp**: OAuth – Client-Anmeldeinformationen
  - **AutoErmittlung**: Ja
  - **URL für die automatische ermitteln**: *Geben Sie den Wert aus Schritt 1.*
  - **Client-ID**: *Geben Sie den Wert aus Schritt 1.*
  - **Token ausgeben URL**: *Geben Sie den Wert aus Schritt 1.*



## Informationen, die von Ihrem Mandanten Intune und Ihre Cisco ISE-Server gemeinsam genutzt
Diese Tabelle listet die Informationen, die zwischen Ihrem Mandanten Intune und Ihre Cisco ISE Server für Geräte, die vom Intune verwaltet werden freigegeben werden.

|Eigenschaft|  Beschreibung|
|---------------|------------------------------------------------------------|
|complianceState|Die Zeichenfolge true oder false, die angibt, ob das Gerät kompatibel oder nicht kompatibel ist.|
|isManaged|Die Zeichenfolge true oder false, die angibt, ob der Client vom Intune oder nicht verwaltet wird.|
|macAddress|Die MAC-Adresse des Geräts.|
|Seriennummer|Die fortlaufende Zahl des Geräts. Es gilt nur für iOS-Geräte.|
|IMEI|Die IMEI (15 Dezimalziffern: 14 Ziffern plus eine Ziffer Kontrollkästchen) oder IMEISV (16 Ziffern) Zahl umfassen Informationen zu den Ursprung, Modell und fortlaufende Zahl des Geräts. Die Struktur der diese Nummer wird im 3GPP Terminaldienste 23.003 angegeben. Es gilt nur für Geräte mit SIM-Karten.|
|UDID|Die eindeutige Geräte-ID, also eine Abfolge von 40 Buchstaben und Zahlen. Es gilt nur für iOS-Geräte.|
|meid|Mobile Geräte-ID, also eine global eindeutige Zahl, die einen physischen Ausrüstungsgegenstand CDMA Mobilstation identifiziert. Das Zahlenformat wird durch den Bericht 3GPP2 S. R0048 definiert. Allerdings kann praktisch es als eine IMEI, jedoch mit hexadezimale Ziffern angezeigt werden. Eine MEID ist 56-Bit lang (14 hex-Ziffern). Es besteht aus drei Feldern, einschließlich einer Landes-/ 8-Bit-Code (Eintrag), einen Herstellercode 24-Bit-und eine 24-Bit-Hersteller zugewiesen fortlaufende Zahl.|
|osVersion|Die Version des Betriebssystems für das Gerät.
|Modell|Das Gerätemodell.
|Hersteller|Gerätehersteller.
|azureDeviceId|Der Geräte-ID, nachdem sie mit Azure AD beigetreten Arbeitsplatz hat. Es ist eine leere GUID für Geräte, die nicht verknüpft sind.|
|lastContactTimeUtc|Datum und Uhrzeit, wenn das Gerät mit der Verwaltungsdienst Intune zuletzt geprüft.


## Benutzererfahrung

Wenn ein Benutzer versucht, Ressourcen mithilfe eines unenrolled Geräts zuzugreifen, wird eine Aufforderung zum Registrieren, wie den hier abgebildeten:

![Beispiel für die Registrierung auffordern](../media/cisco-ise-user-iphone.png)

Wenn ein Benutzer zu registrieren, werden sie an den Registrierungs-Prozess Intune umgeleitet. Die Registrierung Benutzerfunktionalität für Intune wird in den folgenden Themen beschrieben:

- [Registrieren Sie Ihre Intune Android-Gerät](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [Registrieren Sie Ihre Intune iOS-Gerät](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [Registrieren Sie Ihre Mac OS X-Gerät Intune](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [Registrieren Sie Ihre Windows Intune-Gerät](/intune/enduser/enroll-your-device-in-intune-windows)</br>

Es gibt auch einen [herunterladbaren Satz von Registrierungs-Anweisungen](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) , die Sie zum Erstellen von angepassten Anleitungen für Ihre Erfahrungen verwenden können.


### Siehe auch

[Cisco Identität Services-Engine Administrator-Handbuch, Version 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)
