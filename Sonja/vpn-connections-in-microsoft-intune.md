---
title: VPN-Verbindungen | Microsoft Intune
description: "Verwenden Sie VPN Profile VPN-Einstellungen auf Benutzer und Geräte in Ihrer Organisation bereitstellen."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 738b7fbda92f24eaeae23638ea49c1c174901e7a
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# VPN-Verbindungen in Microsoft Intune
 Virtuelle private Netzwerke (VPN) können Sie Ihre Benutzer sicheren Remotezugriff auf Netzwerk Ihres Unternehmens gewähren. Remotebenutzer können arbeiten, als wäre aktivierten Geräte physisch mit dem Netzwerk verbunden sind. Ein Profil VPN Formular Geräte mit Einleiten einer Verbindung mit dem VPN-Server. Formular mit *VPN Profile* in Microsoft Intune VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation bereitstellen. Durch die Bereitstellung von diese Einstellungen minimieren Sie den Verbindung zu Ressourcen im Unternehmensnetzwerk Aufwand Endbenutzer.

Angenommen Sie, dass Sie alle iOS-Geräte mit den Einstellungen für die Verbindung zu einer Dateifreigabe im Netzwerk Ihres Unternehmens erforderlich bereitstellen möchten. Erstellen Sie ein VPN-Profil, die Einstellungen für die Verbindung mit des Firmennetzwerk enthält, und Sie dieses Profil für alle Benutzer mit iOS-Geräte bereitstellen. Die Benutzer sehen die VPN-Verbindung in der Liste der verfügbaren Netzwerke und können eine Verbindung herstellen mit minimalen Aufwand.

Sie können die folgenden Arten von Gerät mithilfe von VPN Profile konfigurieren:

* Geräte, die Android 4 und höher ausgeführt werden
* Geräte, die iOS 8.0 und höher ausgeführt werden
* Geräte, die Mac OS X 10.9 und höher ausgeführt werden
* Registrierten Geräte, die Windows 8.1 und höher ausgeführt werden
* Geräte, die für Windows Phone 8.1 und höher ausgeführt werden
* Geräte, die Windows-10-Desktop und Mobile ausgeführt werden

Die Option VPN Profil Konfigurationsoptionen variieren je nach Typ des Geräts, den Sie auswählen.

## Typen von VPN-Verbindung

Intune unterstützt erstellen VPN Profile, die die folgenden Verbindungsarten zu verwenden:




Verbindungstyp |iOS und Mac OS X  |Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows-10-Desktop und mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Ja |Ja   |Nein    |     Nein    |Nein  |Nein    | Ja (OMA-URI, nur Mobil)|     
Cisco (IPsec)|Ja |Nein   |Nein  |  Nein|Nein  |Nein | Nein|
Citrix|Ja |Nein   |Nein  |  Nein|Nein  |Nein | Nein|
Secure Pulse|Ja  |Ja |Ja   |Nein  |Ja  |Ja| Ja|        
F5 Kante Client|Ja |Ja |Ja |Nein  |Ja  |   Ja |  Ja|   
Dell SonicWALL Mobile verbinden|Ja |Ja |Ja |Nein  |Ja |Ja |Ja|         
Wissensstand mobilen VPN|Ja |Ja |Ja |Ja |Ja|Ja|Ja|
Microsoft SSL (SSTP)|Nein |Nein |Nein |Nein |Nein|Nein|VPNv1 OMA-URI *|
Microsoft Automatische|Nein |Nein |Nein |Nein |Nein|Ja (OMA-URI)|Ja|
IKEv2|iOS benutzerdefiniertes Profil|Nein |Nein |Nein |Nein|Ja (OMA-URI)|Ja|
PPTP|iOS benutzerdefiniertes Profil|Nein |Nein |Nein |Nein|Nein|Ja|
L2TP|iOS benutzerdefiniertes Profil|Nein |Nein |Nein |Nein|Ja (OMA-URI)|Ja|

\* Ohne zusätzliche Einstellungen, die andernfalls für Windows 10 verfügbar sind.

> [!IMPORTANT]
> Bevor Sie VPN Profile befinden, die auf einem Gerät verwenden können, müssen Sie die anwendbare VPN-app für das Profil installieren. Die Informationen können unter dem Thema [Bereitstellen von apps in Intune Microsoft](deploy-apps-in-microsoft-intune.md) Sie die app anwendbare mittels Intune bereitstellen.  

 Informationen Sie zum Erstellen von benutzerdefinierter VPN Profiles mithilfe von URI-Einstellungen in [benutzerdefinierte Konfigurationen für VPN Profile](custom-configurations-for-vpn-profiles.md).     

## Methoden zum Sichern VPN Profile

VPN Profile können eine Reihe von anderen Verbindungstypen und Protokolle von anderen Herstellern. Diese Verbindungen sind in der Regel durch eine von zwei Methoden gesichert.

### Zertifikate

Wenn Sie das Profil VPN erstellen, wählen Sie ein Profil SCEP oder PFX Zertifikat, das Sie zuvor in Intune erstellt.

Dies ist als das Zertifikat zur Identifizierung bezeichnet. Es wird verwendet, um ein vertrauenswürdiges Zertifikatsprofil (oder ein Zertifikat einer Stammzertifizierungsstelle) authentifizieren, die Sie erstellt haben, um nachzuweisen, dass das Gerät des Benutzers eine Verbindung herstellen. Das vertrauenswürdige Zertifikat wird auf dem Computer bereitgestellt, die die VPN-Verbindung, in der Regel, die VPN-Server authentifiziert.

Weitere Informationen zum Erstellen und Verwenden von Zertifikatsprofile in Intune finden Sie unter [sicheren Ressourcenzugriff mit Zertifikatsprofile](secure-resource-access-with-certificate-profiles.md).

### Benutzername und Kennwort

Der Benutzer authentifiziert auf dem Server VPN können, indem Sie einen Benutzernamen und Ihr Kennwort ein.

## Erstellen eines Profils VPN

1. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** > **Richtlinie hinzufügen**.
2. Wählen Sie eine Vorlage für die neue Richtlinie durch den Gerätetyp der entsprechenden zu erweitern, und wählen Sie dann das VPN-Profil für das Gerät:
    * **VPN Profil (Android 4 und höher)**
    * **VPN-Profil (iOS 8.0 und höher)**
    * **VPN Profil (Mac OS X 10.9 und höher)**
    * **VPN-Profil (Windows 8.1 und höher)**
    * **VPN-Profil (Windows Phone, 8.1 und höher)**
    * **VPN-Profil (Windows-10-Desktop und Mobile und höher)**

 Erstellen und nur eine benutzerdefinierte VPN-Profil Richtlinie bereitstellen können. Empfohlene Einstellungen sind nicht verfügbar.

3. Verwenden Sie in der folgenden Tabelle helfen Ihnen die Konfiguration der Option VPN einräumen:

Name der Einstellung  |Weitere Informationen  
---------|---------
**Namen**     |Geben Sie einen eindeutigen Namen für das Profil VPN, um es in der Intune Verwaltungskonsole identifizieren.         
**Beschreibung**     |Geben Sie eine Beschreibung, die bietet einen Überblick über die Option VPN Profil und weitere relevante Informationen, die Sie danach zu suchen kann.         
**Name der VPN-Verbindung (für Benutzer angezeigt)**     |Geben Sie einen Namen für das Profil VPN. Dies ist der Name, der Benutzern in der Liste der verfügbaren VPN-Verbindungen auf ihren Geräten angezeigt wird.         
**Verbindungstyp**     |  Wählen Sie eine der folgenden Tabstopptypen Verbindung im Profil VPN verwendet: **Cisco AnyConnect** (nicht verfügbar für Windows 8.1 oder Windows Phone 8.1), **Pulse Secure**, **F5 Kante Client**, **Dell SonicWALL Mobile verbinden**, **Wissensstand Mobile VPN**.
**Beschreibung der VPN-server**     | Geben Sie eine Beschreibung für den VPN-Server, dem Geräte mit verbinden. Beispiel: **"Contoso" VPN-Server**. Wenn der Verbindungstyp **F5 Kante Client**ist, verwenden Sie das Feld **Server-Liste** , um eine Liste der Server Beschreibungen und IP-Adressen anzugeben.
**IP-Adresse oder den vollqualifizierten Domänennamen**    |Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers, den Geräte mit verbinden. Beispiele: **192.168.1.1**, **vpn.contoso.com**.  Wenn der Verbindungstyp **F5 Kante Client**ist, verwenden Sie das Feld **Server-Liste** , um eine Liste der Server Beschreibungen und IP-Adressen anzugeben.         |         
**Serverliste**     |Wählen Sie **Hinzufügen** zum Hinzufügen eines neuen VPN-Servers für die VPN-Verbindung verwendet werden soll. Sie können auch angeben, welche Server für die Verbindung der Standardserver werden soll. Diese Option wird nur angezeigt, wenn der Verbindungstyp **F5 Kante Client**ist.         
**Senden von sämtlichen Netzwerkverkehr über die VPN-Verbindung**     |Wenn Sie diese Option auswählen, wird durch die VPN-Verbindung alle Netzwerkverkehr gesendet. Wenn Sie nicht diese Option auswählen, wird der Client dynamisch die Arbeitspläne für geteilte Tunnel beim Herstellen einer Verbindung mit dem Drittanbieter-VPN-Server handeln. Nur Verbindungen mit dem Firmennetzwerk, die über ein VPN-Tunnel gesendet werden. VPN-Tunnel wird beim Herstellen einer Verbindung mit Ressourcen im Internet nicht verwendet.
**Authentifizierungsmethode**| Wählen Sie die Authentifizierungsmethode, die die VPN-Verbindung verwendet: **Zertifikate** oder **Benutzernamen und Ihr Kennwort ein**. (**Benutzername und Kennwort** ist nicht verfügbar, wenn der Verbindungstyp Cisco AnyConnect ist.) Die Option **Authentifizierungsmethode** ist nicht verfügbar für Windows 8.1.
**Beachten Sie die Anmeldeinformationen bei jeder Anmeldung des Benutzers**|Wählen Sie diese Option, um sicherzustellen, dass die Anmeldeinformationen des Benutzers gedacht sind, damit der Benutzer nicht jedes Mal Anwendungsinformationen eingeben, wenn eine Verbindung hergestellt wird.
**Wählen Sie ein Clientzertifikat für die Clientauthentifizierung (Identität Zertifikat)**|Wählen Sie das Client SCEP Zertifikat, das Sie zuvor erstellt haben und, die zur Authentifizierung der VPN-Verbindung verwendet werden. Weitere Informationen zur Verwendung von Zertifikatsprofilen in Intune finden Sie unter [sichere Ressourcenzugriff mit Zertifikatsprofilen](secure-resource-access-with-certificate-profiles.md). Diese Option wird nur angezeigt, wenn die Authentifizierungsmethode **Zertifikate**ist.
**Rolle**| Geben Sie den Namen der Benutzerrolle, die auf diese Verbindung zugreifen können. Eine Benutzerrolle definiert persönlichen Einstellungen und Optionen, und es aktiviert oder deaktiviert von bestimmter Features zugreifen. Diese Option wird nur angezeigt, wenn der Verbindungstyp **Pulse Secure**ist.
**Bereich**|Geben Sie den Namen Bereichsnamen, Authentifizierung, die Sie verwenden möchten. Eine Authentifizierungsbereich ist eine Gruppierung von Authentifizierung Ressourcen, die der Verbindungstyp Pulse Secure verwendet. Diese Option ist nur angezeigt, wenn der Verbindungstyp **Pulse Secure**ist.
**Anmeldegruppe oder eine Domäne**|Geben Sie den Namen der Anmeldegruppe oder Domäne, die Sie in eine Verbindung herstellen möchten. Diese Option wird nur angezeigt, wenn der Verbindungstyp **SonicWALL Mobile DellConnect**ist.
**Fingerabdruck**|Geben Sie eine Zeichenfolge (beispielsweise "Contoso Fingerabdrucks Code"), die verwendet wird, um sicherzustellen, dass der VPN-Server vertrauenswürdig sein kann. Ein Fingerabdruck kann an den Kunden gesendet werden, damit er weiß, dass alle Server vertrauen, der die gleichen Fingerabdrucks beim Herstellen einer Verbindung bietet. Wenn das Gerät des Fingerabdrucks noch nicht, fordert sie den Benutzer, den VPN-Server zu vertrauen, den sie eine Verbindung herstellen möchten, um während er sich mit dem Fingerabdruck. (Manuell des Fingerabdrucks überprüft und wählt **Trust** Verbindung.) Diese Option wird nur angezeigt, wenn der Verbindungstyp **Wissensstand Mobile VPN**ist.
**Pro-App VPN**|Wählen Sie diese Option, wenn Sie diese Verbindung VPN eine iOS oder Mac OS X-app zuordnen möchten, dass die Verbindung geöffnet wird, wenn die app ausgeführt wird. Sie können das Profil VPN mit einer app zuordnen, wenn Sie die Software bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
**Bei Bedarf VPN**|Sie können bei Bedarf VPN für 8.0 und höher iOS-Geräte einrichten. Eine Anleitung zum Einrichten dieser werden in [bei Bedarf VPN für iOS-Geräte](#on-demand-vpn-for-ios-devices)bereitgestellt.
**Automatisches Erkennen von Proxyeinstellungen** (iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1 nur)|Wenn Ihr VPN-Server einen Proxyserver für die Verbindung erforderlich ist, geben Sie an, ob die gewünschte Geräten Verbindungseinstellungen automatisch erkennen. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
**Skript für automatische Konfiguration verwenden** (iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1 nur)|Wenn Ihr VPN-Server einen Proxyserver für die Verbindung erforderlich ist, geben Sie an, ob eine automatische Konfigurationsskript definieren die Einstellungen, und geben Sie dann auf einer URLs zu der Datei, die Einstellungen enthält, verwenden möchten. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
**Proxyserver verwenden** (iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1 nur)|Wenn Ihr VPN-Server einen Proxyserver für die Verbindung erforderlich ist, wählen Sie diese Option aus, und geben Sie dann die Anzahl der Adress- und Port des Proxyservers. Weitere Informationen finden Sie unter der Windows Server-Dokumentation.
**Proxyeinstellungen für lokale Adressen umgehen** (iOS, Mac OS X, Windows 8.1 und Windows Phone 8.1 nur)|Wenn Ihr VPN-Server einen Proxyserver für die Verbindung erfordert, aktivieren Sie diese Option, wenn Sie nicht den Proxyserver für lokale Adressen zu verwenden, die Sie angeben möchten. Weitere Informationen finden Sie unter der Windows Server-Dokumentation.
**Benutzerdefinierte XML** (Windows 8.1 und höher und Windows Phone 8.1 und höher)|Geben Sie benutzerdefinierte XML-Befehle, die die VPN-Verbindung zu konfigurieren. Beispiel für **Pulse Secure**: &lt;Pulse-Schema&gt;&lt;IsSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Beispiel für **Die Mobile VPN Prüfpunkt**: &lt;CheckPointVPN Port = "443" Name = "CheckPointSelfhost" Sso = "true" Debuggen = "3" /&gt;. Beispiel für die **SonicWALL Mobile DellConnect**: &lt;MobileConnect&gt;&lt;Komprimierung&gt;falsch&lt;/Compression&gt;&lt;DebugLogging&gt;True&lt;/debugLogging&gt;&lt;PacketCapture&gt;falsch&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Beispiel für **F5 Kante Client**: &lt;f5-Vpn-ü&gt;&lt;Single Sign auf Anmeldeinformationen /&gt;&lt;/f5-vpn-conf&gt;. Lesen Sie des Herstellers VPN-Dokumentation weitere Informationen dazu, wie Sie benutzerdefinierte XML-Befehlen zu schreiben.
**DNS-Suffix Suchliste** (Nur Windows Phone 8.1)|Geben Sie einen DNS-Suffix in jeder Zeile aus. Jede von Ihnen angegebenen DNS-Suffix wird beim Herstellen einer Verbindung mit einer Website über einen kurzen Namen durchsucht. Geben Sie beispielsweise die DNS-Suffixe **domain1.contoso.com** und **domain2.contoso.com**, besuchen Sie die URL **http://mywebsite**und die URLs **http://mywebsite.domain1.contoso.com** und **http://mywebsite.domain2.contoso.com** durchsucht.
**Umgehen VPN, wenn Unternehmen Wi-Fi-Netzwerk verbunden** (Nur Windows Phone 8.1)|Wählen Sie diese Option, um anzugeben, dass die VPN-Verbindung nicht verwendet wird, wenn das Gerät mit dem Unternehmen Wi-Fi-Netzwerk verbunden ist.
**Umgehen VPN beim Start Wi-Fi-Netzwerk verbunden.** (Nur Windows Phone 8.1)|Wählen Sie diese Option, um anzugeben, dass die VPN-Verbindung nicht verwendet wird, wenn das Gerät mit einem Wi-Fi-Heimnetzwerk verbunden ist.

Die folgenden zusätzlichen Einstellungen stehen für Windows 10 Desktop- und mobile Geräte.

Name der Einstellung  |Weitere Informationen  
---------|---------
**Netzwerk Datenverkehr Regeln**|Wählen Sie aus, welche Protokolle, und welche lokale und remote-Port und Adressbereiche, für die VPN-Verbindung aktiviert werden. Wenn Sie eine Regel für den Datenverkehr Netzwerk nicht erstellen, werden alle Protokolle, Ports und Adressbereiche aktiviert. Nachdem Sie eine Regel erstellt haben, wird die VPN-Verbindung verwendet, nur die Protokolle, Ports und Adressbereiche, die Sie in der entsprechenden Regel angeben.
**Leitet**|Wählen Sie aus, welche leitet die VPN-Verbindung verwendet werden.
**DNS-Server**| Wählen Sie die DNS-Server die VPN-Verbindung verwendet wird, nachdem die Verbindung hergestellt wird.         
**Zugeordneten apps**|Stellen Sie eine Liste von apps, die automatisch die VPN-Verbindung verwendet wird. Der Typ der app wird die app-ID ermitteln. Geben Sie den Namen des Paket-Familie, für eine app universal. Geben Sie den Dateipfad der app zu einer desktop-app.          


> [!IMPORTANT]
> Es empfiehlt sich, dass Sie alle Listen mit apps sichern, die Sie zur Verwendung in die Konfiguration von VPN-app kompilieren. Wenn nicht autorisierter Benutzer die Liste ändert, und Sie in der Liste pro-app VPN app importieren, werden Sie potenziell VPN-Zugriff auf apps autorisieren, die keinen Zugriff. Eine Möglichkeit besteht darin, Sie können Listen app secure wird mithilfe einer Access-Steuerelement Zugriffssteuerungsliste.

Hier ein Beispiel für das Einstellungen für corporate Begrenzung können möglicherweise. Wenn Sie VPN nur für Remotedesktop aktivieren möchten, erstellen Sie eine Netzwerk Datenverkehr zulässt, dass Datenverkehr für das Protokoll 27 externen Port 3996. Keine anderen Datenverkehr wird das Option VPN verwendet.

Leitet in corporate Grenzen definieren ist nützlich, wenn es sich bei Ihrem VPN Verbindungstyp nicht zulässt, dass Sie um festzulegen, wie Datenverkehr in Teilen Tunnel verarbeitet wird. Verwenden Sie in diesem Fall **leitet** , um die Arbeitspläne aufgeführt sein, die das Option VPN verwendet wird.

Durch Erstellen einer benutzerdefinierten OMA-URI-Einstellung können Sie bestimmte apps VPN Verwendung für Windows 10 Geräte einschränken.

Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt.

### Bei Bedarf VPN für iOS-Geräte
Sie können bei Bedarf VPN für iOS 8.0 und höher konfigurieren.

> [!NOTE]
>  
> Pro-app VPN und bei Bedarf VPN kann nicht in der gleichen Richtlinie verwendet werden.
 
1. Klicken Sie auf der Seite Richtlinie Konfiguration finden Sie **bei Bedarf Regeln für diese VPN-Verbindung**. **Vergleich**der Bedingung, die die Regeln überprüfen und **Aktion**, die Aktion, die die Richtlinie ausgelöst werden soll, wenn die Bedingung zugeordnet wird, sind die Spalten bezeichnet. 
2. Wählen Sie **Hinzufügen** zum Erstellen einer Regel. Es gibt zwei Arten von entspricht, die Sie in der Regel einrichten können. Sie können nur eine der folgenden Arten pro Regel konfigurieren.
  - **SSIDs**, die sich auf drahtlose Netzwerke beziehen. 
  - **DNS-Suche Domänen**, die sind...  Sie können vollständig qualifizierte Domänennamen wie *Team. corp.contoso.com*oder verwendet wie etwa *"contoso.com"*, also die Entsprechung der Verwendung von Domänen * *. contoso.com*.
3. Optional: Geben Sie einen URL-Zeichenfolge Prüfpunkt, also eine URL, die die Regel als Test verwendet wird. Wenn das Gerät, auf dem dieses Profil installiert ist, diese URL ohne Umleitung zugreifen kann, wird das VPN hergestellt werden, und das Gerät wird die Ziel-URL verbinden. Der Benutzer wird die URL-Zeichenfolge Prüfpunkt-Website nicht angezeigt werden. Ein Beispiel für einen URL-Zeichenfolge Prüfpunkt ist der Adresse einer ü Webserver, mit dem Gerät Compliance vor dem Verbinden des VPNs überprüft. Eine weitere Möglichkeit ist, dass die URL, die Möglichkeit des VPN Verbindung zu einer Website, bevor Sie das Gerät zu verbinden, um die Ziel-URL, bis die Option VPN überprüft.
4. Wählen Sie eine der folgenden Aktionen aus:
  - **Verbinden**
  - **Auswerten Verbindung**, deren drei Einstellungen sind ein. **Domäne Aktion** – wählen Sie **Verbinden bei Bedarf** oder **nie verbinden** 
     b. **Durch Trennzeichen getrennte Liste der Domänen** – Sie können die Konfiguration nur dann, wenn Sie eine **Domäne Aktion** **Verbinden Bedarf** auswählen 
     c. **URL erforderlich Zeichenfolge Prüfpunkt** - ein HTTP- oder HTTPS (empfohlen) URL, beispielsweise *https://vpntestprobe.contoso.com*. Die Regel wird angezeigt, wenn es eine Antwort von dieser Adresse gibt überprüfen. Wenn dies nicht der Fall ist, und die **Domäne Aktion** **Verbinden, falls erforderlich**ist, wird das Option VPN ausgelöst werden.
     > [!TIP]
     >
     >Wenn Sie diese Aktion verwenden, wird möglicherweise ein Beispiel ist, wenn einige Websites auf das Unternehmensnetzwerk eine direkte oder VPN-Unternehmensnetzwerk Verbindung erfordern, aber andere nicht. Wenn Sie in einer **durch Trennzeichen getrennte Liste mit DNS-suchen Domänen** *corp.contoso.com*auflisten, können Sie **Verbinden bei Bedarf** auswählen und dann Liste innerhalb dieses Netzwerks, die Option VPN, z. B. *sharepoint.corp.contoso.com*erfordern möglicherweise bestimmte Websites. Die Regel dann prüfen, ob die *vpntestprobe.contoso.com* erreicht werden können. Wenn es nicht möglich ist, wird das Option VPN für die Sharepoint-Website ausgelöst werden.
  - **Ignorieren** – Dies bewirkt, dass keine Änderung in der VPN-Konnektivität. Wenn das Option VPN angeschlossen ist, verlassen, die es angeschlossen ist keine Verbindung besteht, nicht verbinden Sie es. Beispielsweise können Sie haben eine Regel, die das Option VPN für alle Ihre internen Websites Ihres Unternehmens eine Verbindung herstellt, aber soll eine dieser internen Websites barrierefreien nur, wenn das Gerät tatsächlich mit dem Firmennetzwerk verbunden ist. In diesem Fall möchten Sie eine Regel ignorieren, die einer Website erstellen.
  - **Trennen** - Geräte mit dem VPN trennen, wenn die Bedingungen übereinstimmen. Beispielsweise könnten Sie Liste Ihres Unternehmen WLAN im Feld **SSIDs** und Erstellen einer Regel, die Verbindung Geräte mit dem VPN, wenn sie mit einem dieser Netzwerke herstellen.

Spezifische Regeln werden bevor alle Domain-Regeln ausgewertet. 


## Die Richtlinie bereitstellen

1.  Klicken Sie im Arbeitsbereich **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und wählen Sie dann die **Bereitstellung verwalten**.

2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :

    -   Um die Richtlinie bereitstellen, wählen Sie eine oder mehrere Gruppen aus, dem Sie die Richtlinie bereitstellen möchten, und wählen Sie dann auf **Hinzufügen** &gt; **OK**.

    -   Wählen Sie **Abbrechen**aus, um das Dialogfeld zu schließen, ohne es.


Nach der erfolgreichen Bereitstellung sehen Benutzer den Namen der VPN-Verbindung, den Sie in der Liste der VPN-Verbindungen auf ihren Geräten angegeben haben.

Eine Zusammenfassung Status und Benachrichtigungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie** identifizieren Sie Probleme mit der Richtlinie, die Ihre Aufmerksamkeit erfordern. Darüber hinaus wird ein Zusammenfassung Status im Dashboard-Arbeitsbereich ein.

### Siehe auch
[Benutzerdefinierte Konfigurationen für VPN Profile](Custom-configurations-for-VPN-profiles.md)

[Pro-app VPN für Android Pulse sicheren](per-app-vpn-for-android-pulse-secure.md)
