---
title: Verwalten von PCs mit Clientsoftware | Microsoft Intune
description: Verwalten PCs Windows Intune-Clientsoftware installieren.
keywords: 
author: nathbarn
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 1df2507df6bd3fc7748c10c1f398fbfdb8958a18
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwalten von Windows-PCs mit Clientsoftware Intune-PC
Anstelle von [Windows-PCs als mobile Geräte registrieren](set-up-windows-device-management-with-microsoft-intune.md)können Sie registrieren und Verwalten von Windows-PCs durch die Intune-Clientsoftware installieren.

Intune verwaltet Windows PCs mithilfe von Richtlinien kann zu ähnlich wie Windows Server Active Directory-Domänendiensten (AD DS) Group Policy Objects (GPOs). Wenn Sie Active Directory-Domäne Computer mit Intune verwalten, sollten Sie [Achten Sie darauf, dass Intune-Richtlinien nicht mit einem beliebigen Gruppenrichtlinienobjekten in Konflikt stehen](resolve-gpo-and-microsoft-intune-policy-conflicts.md) , die für Ihre Organisation eingerichtet sind.

Während der Intune Software Client [Verwaltungsfunktionen, die Schutz für PCs,](policies-to-protect-windows-pcs-in-microsoft-intune.md) unterstützt, durch die Verwaltung von Softwareupdates, Windows-Firewall und Endpunkt Schutz, PCs, die mit der Software Client mit anderen Intune-Richtlinien, einschließlich der diese Einstellungen für **Windows** Richtlinie speziell für die Verwaltung mobiler Geräte als Ziel kann Intune verwaltet werden.

> [!NOTE]
> Geräten unter Windows 8.1 oder höher können mit dem Intune-Client oder als mobilen Geräten verwaltet werden. Dieses Thema bezieht sich auf den Intune Software-Client-Computern. Installieren des Intune-Clients und registrieren bei Verwaltung mobilen Gerät wird nicht unterstützt.

## Anforderungen für Intune PC-Client-Verwaltung

**Hardware**: im folgenden werden die Hardware-Mindestanforderungen zum Installieren des Intune-Clients:

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Netzwerk|Der Client erfordert den PC zu dem Internet verbunden sind.|
|Prozessor und Arbeitsspeicher|Schlagen Sie in den Prozessor und RAM Anforderungen für die PC Betriebssystem.|
|Festplattenspeicher|200 MB verfügbarer Speicherplatz, bevor die Clientsoftware installiert ist.|

**Software**: im folgenden werden die softwareanforderungen für die Installation von dem Client:

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Betriebssystem | Windows-Gerät unter Windows Vista oder höher. Home Edition Versionen werden nicht unterstützt.|
|Administratorberechtigungen|Das Konto, das die Clientsoftware Installationen müssen lokalen Administratorberechtigungen auf dem Gerät.|
|Windows Installer 3.1|Dem Computer muss mindestens Windows Installer 3.1 haben.<br /><br />So zeigen Sie die Version von Windows Installer auf einem PC an:<br /><br />– Mit der rechten Maustaste **%windir%\System32\msiexec.exe**auf dem Computer und klicken Sie dann auf **Eigenschaften**.<br /><br />Sie können die neueste Version von Windows Installer von [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) auf der Microsoft Developer Network-Website herunterladen.|
|Entfernen Sie inkompatiblen Clientsoftware|Bevor Sie die Intune-Clientsoftware installiert haben, müssen Sie die alle Konfigurations-Manager "oder" System Management Server-Clientsoftware von diesem Computer deinstallieren.|

## Verwaltung von Computer mit dem Intune Computer client
Nach der Installation von Intune-Clientsoftware Verwaltungsfunktionen einschließen: [anwendungsverwaltung](deploy-apps-in-microsoft-intune.md), [in Echtzeit Überwachung und den Endpunkt Schutz](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md), [Verwaltung der Windows-Firewall-Einstellungen](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), Hard- und Software Inventory, Fernbedienung (über Remoteunterstützung Anfragen), [Software aktualisieren](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)und reporting Complianceeinstellungen.

Bestimmte Verwaltungsoptionen verwaltet, wie mobile Geräte nicht verfügbar, an der Software Client verwaltete PCs sind, einschließlich PCs zur Verfügung:

-   Vollständige zurücksetzen (selektiven zurücksetzen steht)
-   Bedingte access
-   Windows-Richtlinien als **Computer** Informationsverwaltungsrichtlinien

![Richtlinien Vorlage für Windows-PCs](../media/pc_policy_template.png)

Zusätzlich zu den Intune-Client-Agent Aktionen, die lokal für einzelne Computer auch können die Intune-Verwaltungskonsole Sie um andere [Allgemeine Aufgaben zur Verwaltung von Computer](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) auf Windows-PCs mit dem Client installiert zu ausführen:

-   Hard- und Software Inventory Informationen zu verwalteten Computern anzeigen

-   Einen Computer Remote neu starten

-   Zurückziehen Sie einen Computer, um die Clientsoftware deinstallieren und Management mit Intune daraus

-   Verknüpfen von Benutzern mit bestimmten verwalteten Computern

-   Antworten Sie auf Besprechungsanfragen Remoteunterstützung

Der Intune-Client-Agent in der Regel erstellen wird im Hintergrund ausgeführt ohne die Notwendigkeit viele Benutzer Interaktion oder zur Behandlung von Problemen. Jedoch sollten Sie benötigen Sie Hilfe bei der Behebung Management Computerprobleme, es gibt mehrere [Ressourcen, die sie lösen](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).
