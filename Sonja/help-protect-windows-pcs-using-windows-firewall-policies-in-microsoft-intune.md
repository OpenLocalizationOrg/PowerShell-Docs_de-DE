---
title: "Richtlinien für Windows-PCs Firewall | Microsoft Intune"
description: "Intune helfen Ihnen zu schützen Sie, mit dem Client Intune in eine Reihe von Methoden verwalten, einschließlich hilft Ihnen, so konfigurieren Sie die Windows-Firewall-Einstellungen."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 3fde6fb88bd929956d18e4dda502071901e4c4b4
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Schützen von Windows-PCs mit Windows-Firewall-Richtlinien in Microsoft Intune
Microsoft Intune hilft Ihnen Windows-PCs zu sichern, die Sie mit dem Intune-Client auf vielfältige Weise zu verwalten. Eine Möglichkeit besteht darin, in denen dies bedeutet, stellen Richtlinien bereit, mit die Sie die Windows-Firewall-Einstellungen auf PCs konfigurieren können.

Wenn Sie den Computer mit Windows Intune-Client noch nicht auf Ihrem Computer installiert haben, finden Sie unter [installieren den Windows-PC-Client, mit dem Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Verwenden Sie die Informationen in den folgenden Abschnitten, mit deren Hilfe Sie konfigurieren, bereitstellen und Überwachen von Windows-Firewall-Richtlinien auf Windows-PCs.

## Verwenden von Intune-Richtlinien zum Verwalten von Windows-Firewall
Die Windows-Firewall-Richtlinie können Sie erstellen und Bereitstellen von Einstellungen, die Windows-Firewall auf verwalteten PCs steuern. Sie können keine benutzerdefinierte Ausnahmen für Windows-Firewall verwalten, und diese Einstellungen wirken sich nicht auf Firewalls von Drittanbietern.

> [!NOTE]
> Wenn Microsoft Intune Richtlinie und Gruppenrichtlinien konfiguriert sind, um diese Einstellung auf dem Computer verwalten, wird der Gruppenrichtlinien-Einstellung die Richtlinie Microsoft Intune überschrieben. Informationen dazu, wie Konflikte zwischen Intune Richtlinie und Gruppenrichtlinien vermieden werden sollten finden Sie unter [Gruppenrichtlinienobjekt beheben und Microsoft Intune Richtlinie Konflikte](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Wenn Bereitstellung von Windows-Firewall-Einstellungen auf Computern, die unter Windows Vista ausgeführt werden soll, müssen Sie zuerst auf diesen Computern [Update KB971800](http://support2.microsoft.com/kb/971800) installieren.

> [!IMPORTANT]
> Zum Verwalten von Windows-Firewall mit Intune stellen Sie sicher, dass die beiden folgenden Dienste auf den Computern, die Sie verwalten, aktiviert sind:
>
> -   Windows-Firewall
> -   IP-Sicherheitsrichtlinie Agent

## Konfigurieren einer Richtlinie für Windows-Firewall

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), die **Richtlinie** &gt; **Richtlinie hinzufügen**.

2.  Konfigurieren und Bereitstellen einer Richtlinie für die **Windows-Firewall-Einstellungen** . Sie können die empfohlenen Einstellungen verwenden oder Anpassen der Einstellungen. Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien, finden Sie unter [Allgemeine Windows-PC-Verwaltungsaufgaben mit dem Microsoft Intune Computer Client](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    Im folgende Abschnitt listet die Werte, die Sie konfigurieren können, in der Richtlinie und auch die Standardwerte, die verwendet werden, wenn Sie nicht die Richtlinie anpassen.

Nachdem Sie eine Windows-Firewall-Richtlinie bereitstellen, können Sie deren Status auf der Seite **Alle Richtlinien** des Arbeitsbereichs **Richtlinie** anzeigen.

## Festlegen der Richtlinieneinstellungen für Windows-Firewall

### Aktivieren Sie die Windows-Firewall

Diese Richtlinieneinstellungen aktivieren Windows-Firewall auf verwalteten Computern, die sind:
- Bei einer Verbindung zu einer Domäne (z. B. am Arbeitsplatz)
- Verbindung mit einem privaten (vertrauten) Netzwerk (beispielsweise einem Heimnetzwerk)
- Bei einer Verbindung zu einem nicht vertrauenswürdigen öffentlichen Netzwerk (beispielsweise einem Café)

Der Standardwert für jede diese Einstellungen ist **Ja**, welche ist die sicherste Wert.



### Blockieren Sie alle eingehende Verbindungen, einschließlich der Empfänger in der Liste der zugelassenen Programme

Diese Richtlinieneinstellungen konfigurieren Windows-Firewall eingehenden Netzwerkverkehr auf verwalteten Computern blockiert werden:
- Bei einer Verbindung zu einer Domäne (z. B. am Arbeitsplatz)
- Verbindung mit einem privaten (vertrauten) Netzwerk (beispielsweise einem Heimnetzwerk)
- Bei einer Verbindung zu einem nicht vertrauenswürdigen öffentlichen Netzwerk (beispielsweise einem Café)

Der Standardwert für jede diese Einstellungen ist **Ja**, welche ist die sicherste Wert.

> [!IMPORTANT]
> Wenn Ihre Umgebung verwaltete Computern, die ohne Service Packs installiert unter Windows Vista ausgeführt werden enthält, müssen Sie installieren Sie das Update, das in der Microsoft Knowledge Base- [Artikel 971800](http://go.microsoft.com/fwlink/?LinkId=188405) zugeordnet ist oder deaktivieren die **Blockieren aller eingehender Verbindungen** Richtlinieneinstellungen Richtlinien, die auf den Computern bereitgestellt werden.

### Den Benutzer benachrichtigt, wenn die Windows-Firewall ein neues Programm blockiert

Mit diesen Richtlinien bestimmen, ob die Windows-Firewall einen PC-Benutzer benachrichtigt, wenn es eingehenden Netzwerkverkehr blockiert, wenn der verwaltete Computer ist:
- Bei einer Verbindung zu einer Domäne (z. B. am Arbeitsplatz)
- Verbindung mit einem privaten (vertrauten) Netzwerk (beispielsweise einem Heimnetzwerk)
- Bei einer Verbindung zu einem nicht vertrauenswürdigen öffentlichen Netzwerk (beispielsweise einem Café)

Der Standardwert für jede diese Einstellungen ist **Ja**aus.


### Vordefinierte Ausnahmen konfigurieren

Sie können Ausnahmen konfigurieren, die bestimmte Arten von Netzwerkverkehr durch die Firewall unabhängig von den Werten zu ermöglichen, die Sie zuvor konfiguriert. Keiner der diese Einstellungen werden automatisch konfiguriert.

|Name der Einstellung|Details|
|------------------|--------------------|
|**BranchCache - Abruf von Inhalten**<br>(Windows 7 oder höher)|Ermöglicht BranchCache Clients HTTP zum Abrufen von Inhalten aus anderen BranchCache-Clients während im verteilten Modus und aus dem gehosteten Cache im gehosteten Cachemodus verwenden. Diese Einstellung verwendet HTTP.|
|**BranchCache - gehostete Cacheclient**<br>(Windows 7 oder höher)|Ermöglicht BranchCache-Clients einen gehosteten Cache zu nutzen. Diese Einstellung wird HTTPS verwendet.|
|**BranchCache - Server gehostete Caches**|Ermöglicht BranchCache Clients einen gehosteten Cache zur Kommunikation mit anderen Clients verwenden. Diese Einstellung wird HTTPS verwendet.|
|**BranchCache - Peer-Suche**<br>(Windows 7 oder höher)|Ermöglicht das Web Services dynamische Discovery (WS-Discovery)-Protokoll verwenden, um die Verfügbarkeit der Inhalte im lokalen Subnetz Nachschlagen BranchCache-Clients an.|
|**BITS-Peercaching**|Ermöglicht Clients intelligente Service (BITS) verwenden, suchen und Freigeben von Dateien, die im Cache BITS auf Clients im selben Subnetz gespeichert werden. Diese Einstellung verwendet Webdienste Geräte (WSDAPI) und (Remote Procedure Call, RPC).|
|**Verbinden Sie mit einem Netzwerkprojektor**|Ermöglicht Benutzern das Verbinden mit Projektoren über kabelgebundene oder drahtlosen Netzwerke, um Präsentationen. Diese Einstellung verwendet WSDAPI.|
|**Core Netzwerke**|Ermöglicht Clients IPv4 und IPv6 zu verwenden, um die Verbindung zum Netzwerk.|
|**Verteilte Transaktionskoordinator**|Ermöglicht verwaltet Computern zum Koordinieren von Transaktionen, die Transaktion geschützte Ressourcen wie Datenbanken, Nachrichten und Dateisysteme aktualisieren.|
|**Datei- und Druckerfreigabe**|Ermöglicht Benutzern, die lokale Dateien und Drucker für andere Benutzer im Netzwerk freigeben. Diese Einstellung verwendet NetBIOS, Link lokale Multicast Namen Auflösung (LLMNR), RPC und Protokoll (SMB = Server Message Block).|
|**Heimnetzgruppe**<br>(Windows 7 oder höher)|Ermöglicht verwalteten Computern zur Teilnahme an einer Heimnetzgruppe Netzwerk.|
|**iSCSI-Dienst**|Ermöglicht verwalteten Computern iSCSI-Servern und Geräten herstellen.|
|**Schlüsselverwaltungsdienst**|Ermöglicht Computern, die für die Einhaltung der Lizenzen in Enterprise-Umgebungen gezählt werden sollen.|
|**Media Center Extender**|Ermöglicht Media Center Extendern die Kommunikation mit Computern, die Windows Media Center ausgeführt werden. Diese Einstellung verwendet Simple Service Discovery Protocol (SSDP) und qWave.|
|**Anmeldedienst**|Konfiguriert einen Sicherheitskanal zwischen Domänenclients und einem Domänencontroller für die Benutzerauthentifizierung und Dienste an. Diese Einstellung verwendet RPC.|
|**Netzwerk-Suche**|Ermöglicht Computern ermitteln andere Geräte und von anderen Geräten im Netzwerk ermittelt werden. Diese Einstellung verwendet die Funktion Discovery Host und Publikation Services und SSDP, NetBIOS, LLMNR und UPnP Netzwerkprotokolle.|
|**Leistungsprotokolle und Warnungen**|Aktiviert den Dienst Leistungsprotokolle und Warnungen remote verwaltet werden. Diese Einstellung verwendet RPC.|
|**Remote-Administration**|Ermöglicht remote-Verwaltung des Computers.|
|**Remoteunterstützung**|Ermöglicht Benutzern von verwalteten Computern Anfordern von Remoteunterstützung andere Benutzer im Netzwerk. Diese Einstellung verwendet SSDP, Peer Name Auflösung-Protokoll (PNRP), Teredo und UPnP Netzwerkprotokolle.|
|**Remotedesktop**|Ermöglicht, dass den Computer Remotedesktop zum Zugreifen auf anderen Computern verwenden.|
|**Ereignisprotokoll Remote-Verwaltung**|Ermöglicht Client-Ereignisprotokollen angezeigt und Remote verwaltet werden. Diese Einstellung verwendet Named Pipes und RPC.|
|**Remote geplanter Aufgaben**|Ermöglicht remote-Verwaltung des Vorgangs Planung Services an. Diese Einstellung verwendet RPC.|
|**Remote Servicemanagement**|Ermöglicht remote-Verwaltung von Lokale Dienste auf Clients. Diese Einstellung verwendet Named Pipes und RPC.|
|**Remote Volume Management**|Ermöglicht die remote-Software und Hardware Datenträger Volume-Verwaltung. Diese Einstellung verwendet RPC.|
|**Routing und RAS**|Ermöglicht eingehenden VPN und RAS Verbindungen mit Computern.|
|**Secure Sockets Tunnel Protokoll**|Ermöglicht Eingehende VPN-Verbindungen für verwaltete Computer mit Secure Sockets Tunnel Protokoll (SSTP). Diese Einstellung wird HTTPS verwendet.|
|**SNMPTraps**|Verwaltete Computer (einfaches Netzwerkverwaltungsprotokoll) Ablaufverfolgungsdienst-Verkehr empfangen können.|
|**UPnP-Framework**|Konfiguriert den UPnP-Framework Service auf Computern, damit sie ermitteln und UPnP-zertifizierte Geräte verwenden können.|
|**Windows für die Zusammenarbeit Computer Name Registration Service**|Suchen und kommunizieren mit anderen Computern mithilfe von SSDP und PNRP Computer genutzt werden können.|
|**Windows MediaPlayer**|Ermöglicht Benutzern das streaming Media über User Datagram Protocol (UDP) erhalten.|
|**Windows Media Player Netzwerk Freigabe Service**|Ermöglicht Benutzern das Freigeben von Medien in einem Netzwerk. Diese Einstellung wird die SSDP und qWave UPnP Netzwerkprotokolle verwendet.|
|**Windows Media Player Netzwerk Freigabe Service (Internet)**<br>(Windows 7 oder höher)|Ermöglicht Benutzern das home Medien über das Internet freigeben.|
|**Windows-Teamarbeit**|Ermöglicht Benutzern, die über ein Netzwerk zum Freigeben von Dokumenten, Programme und ihre Desktops zusammenarbeiten. Diese Einstellung werden verteilt Datei System Replikation (DFSR) und P2P verwendet.|
|**Windows-Peer-zu-Peer-Zusammenarbeit Foundation**|Konfiguriert verschiedene Peer-to-Peer-Programme und Technologien, um die Verbindung zu aktivieren. Diese Einstellung verwendet SSDP und PNRP.|
|**Windows Remote Management (Kompatibilität)**|Ermöglicht remote-Verwaltung von verwalteten Computern mit WS-Verwaltung, ein Protokoll mit Web Services für remote-Verwaltung von Betriebssystemen und Geräten.|
|**Windows Remote Management**<br>(Windows 8 oder höher)|Ermöglicht remote-Verwaltung von verwalteten Computern mit WS-Verwaltung, ein Protokoll mit Web Services für remote-Verwaltung von Betriebssystemen und Geräten.|
|**Virtuelle Windows-PC**<br>(Windows 7 oder höher)|Ermöglicht virtuellen Computern mit anderen Computern kommunizieren.|
|**Drahtlosen tragbare Geräte**|Ermöglicht die Übertragung von Medien auf einem Gerät Netzwerk aktiviert, Kamera oder Medien für verwaltete Computer mit Media Transfer Protocol (MTP). Diese Einstellung verwendet SSDP und UPnP Netzwerkprotokolle.|

### Siehe auch
[Richtlinien zum Schutz von Windows-PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md)
