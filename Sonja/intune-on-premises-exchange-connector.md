---
title: "Exchange Connector für lokale EAS | Microsoft Intune"
description: "Verwenden Sie der Verbinder, um Kommunikation zwischen der Verwaltungskonsole Intune aktivieren und lokalen Exchange-Server für Exchange ActiveSync MDM"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41ff4212-a6f5-4374-8731-631f7560cff1
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: 18614cc272323b8031c94b8e582f80aa5c06d9d3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Installieren des Intune lokalen Exchange-Connectors


Um die Einrichtung einer Verbindung, die Microsoft Intune zur Kommunikation mit dem Exchange-Server ermöglicht, hostet den mobilen Geräten Postfächer, müssen Sie herunterladen und auf lokale Verbinder aus der Intune-Verwaltungskonsole konfigurieren. Intune unterstützt nur ein Exchange-Connector-Verbindung eines beliebigen Typs pro Abonnement.

## Anforderungen für die lokale Verbinder
Die folgende Tabelle enthält die Anforderungen für den Computer, auf dem lokalen Exchange Connector installiert.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Betriebssysteme|Intune unterstützt den lokalen Exchange-Connector auf einem Computer, der eine beliebige Edition von Windows Server 2008 SP2, 64 Bit, Windows Server 2008 R2, Windows Server 2012 oder Windows Server 2012 R2 ausgeführt wird.<br /><br />Der Verbinder wird bei jeder Server Core-Installation nicht unterstützt.|
|Microsoft Exchange-version|Eines lokalen Connector erfordert Microsoft Exchange 2010 SP1 oder höher oder legacy Exchange Online dedizierter. Um festzustellen, ob Ihre Umgebung Exchange Online ausschließlich in der **neuen** oder **älteren** Konfiguration ist, wenden Sie sich an Ihren Account Manager.|
|Mobiles Gerät Management Zertifizierungsstelle| [Festlegen der mobilen Gerät Management Zertifizierungsstelle zu Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority).|
|Hardware|Des Computers, wo Sie den Verbinder installieren, erfordert eine 1,6 GHz CPU mit 2 GB Ram und 10 GB freier Speicherplatz minimale Hardware.|
|Active Directory-Synchronisierung|Bevor Sie entweder Verbinder in Verbindung mit dem Exchange-Server Intune verwenden können, müssen Sie [Einrichten von Active Directory-Synchronisierung](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) , damit der lokale Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden.|
|Zusätzliche software|Eine vollständige Installation von Microsoft .NET Framework 4 und Windows PowerShell 2.0 muss auf dem Computer installiert sein, die Host den Verbinder ist.|
|Netzwerk|Der Stelle, an der Sie den Verbinder installieren Computer muss in einer Domäne, die eine Vertrauensstellung mit der Domäne verfügt, die dem Exchange-Server hostet.<br /><br />Der Computer erfordert Konfigurationen damit Intune-Dienst über Firewalls und Proxyserver über Ports 80 und 443 zugreifen können. Domänen Intune untersuchten einbeziehen manage.microsoft.com & #42;manage.microsoft.com, und & #42;. Manage.Microsoft.com.|
|Gehostete Exchange konfiguriert und ausgeführt|Weitere Informationen finden Sie unter [Exchange Server 2016](https://technet.microsoft.com/library/mt170645.aspx) . |

### Exchange-Cmdlet Anforderungen

Sie müssen ein Active Directory-Benutzerkonto erstellen, die vom Exchange Connector Intune verwendet wird. Das Konto muss über die Berechtigung zum Ausführen von den folgenden erforderlichen Exchange von Windows PowerShell-Cmdlets verfügen:


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, neue-ActiveSyncMailboxPolicy-ActiveSyncMailboxPolicy entfernen
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, neue-ActiveSyncDeviceAccessRule-ActiveSyncDeviceAccessRule entfernen
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-Exchange
 -   Get-ActiveSyncDeviceClass
 -   Get-Empfänger
 -   Löschen-ActiveSyncDevice, entfernen-ActiveSyncDevice
 -   Set-ADServerSettings
 -   GET-Befehl

## Herunterladen des lokalen Exchange-Connector-Software Installationspakets

1. Öffnen Sie auf einem unterstützten Windows Server-Betriebssystem für den lokalen Exchange-Connector, [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) (http://manage.microsoft.com) mit einem Benutzerkonto an, die ein Administrator in der Exchange-Mandanten mit einer Lizenz Exchange Server verwendet wird.
![Öffnen Einrichten von Exchange-Verbindung](../media/ExchangeConnector.gif)

2.  Im Verknüpfungsbereich Arbeitsbereich, wählen Sie **Administrator**aus, und wählen Sie die **Verwaltung mobiler Geräte** > **Microsoft Exchange**, und wählen Sie dann auf **Exchange-Verbindung einrichten**.

3.  Wählen Sie auf der Seite **Exchange-Verbindung einrichten** **Herunterladen lokaler Verbinder**aus.

4.  Der lokalen Exchange-Connector ist in einem komprimierten ZIP-Ordner enthalten, das geöffnet oder gespeichert werden kann. Wählen Sie im Dialogfeld **Dateidownload** zum Speichern des komprimierten Ordners an einem sicheren Ort **zu speichern** .

> [!IMPORTANT]
> Umbenennen Sie oder verschieben Sie die Dateien in den lokalen Exchange-Connector-Ordner nicht. Verschieben oder Umbenennen der Inhalt des Ordners wird die Installation unterbrochen.

## Installieren und Konfigurieren der Intune lokalen Exchange-Connector
Führen Sie die folgenden Schritte aus, um den Intune lokalen Exchange-Connector installieren. Der lokalen Exchange-Connector kann nur einmal pro Intune-Abonnement und nur auf einem Computer installiert werden. Wenn Sie versuchen, einen zusätzlichen lokalen Exchange-Connector konfigurieren, ersetzt die neue Verbindung der ursprünglichen.

1.  Klicken Sie auf ein unterstütztes Betriebssystem für den Verbinder auf lokale extrahieren Sie Dateien in **Exchange_Connector_Setup.zip** an einem sicheren Ort.

2.  Nachdem die Dateien extrahiert wurden, öffnen Sie den extrahierten Ordner, und doppelklicken Sie auf **Exchange_Connector_Setup.exe** um den lokalen Exchange-Connector installieren.

    > [!IMPORTANT]
    > Wenn der Zielordner keinem sicheren Ort ist, sollten Sie nach der Installation der Verbinder auf lokale Zertifikatsdatei **WindowsIntune.accountcert** löschen.

3.  Im Feld **Exchange Server** wählen Sie Exchange Server-Umgebung, die dem Typ Ihrer entweder **Lokalen Microsoft Exchange Server** oder **Microsoft Exchange-Server gehostet**.

  ![Wählen Sie aus Ihrem Exchange Server-Datentyp](../media/IntuneSA1dconfigureExchConnector.png)

  Geben Sie für einen lokalen Exchange-Server den Servernamen oder den vollqualifizierten Domänennamen des Exchange-Servers, der die Rolle **Client Access-Server** hostet.

  Bieten Sie für eine gehostete Exchange-Server die Exchange Server-Adresse ein. So suchen Sie die gehostete Exchange Server-URL

      1.  Öffnen Sie das Outlook-Web-App für Office 365 an.

      2.  Wählen Sie aus der "?" oben auf das Symbol nach links, und wählen Sie **Info**.

      3.  Suchen Sie den Wert für die **Externen POP-Server** aus.

      4.  Wählen Sie servereinstellungen für Ihren gehostete Exchange Server **Proxyserver** Proxy angeben.
        1.  Wählen Sie **einen Proxyserver beim Synchronisieren von mobilen Geräten verwenden**.

        2.  Geben Sie den **Namen des Proxyservers** und die **Port-Nummer** , die Zugriff auf den Server verwendet werden.

        3.  Wenn es für die Benutzer Zugriff auf den Proxyserver Anmeldeinformationen erforderlich ist, wählen Sie Anmeldeinformationen verwenden, um eine Verbindung mit dem Proxyserver und geben Sie die **Domäne\Benutzer** und das **Kennwort**ein.

        4.  Wählen Sie **OK**aus.

5.  Geben Sie die Anmeldeinformationen, die **Benutzer (Domäne\Benutzer)** und **ein Kennwort** erforderlich sind, um die Verbindung zu Ihrem Exchange-Server.

6.  Geben Sie zum Senden von Benachrichtigungen zum Exchange-Postfach des Benutzers erforderlichen administrative Anmeldeinformationen. Diese Benachrichtigungen können über bedingte Richtlinien mit dem Intune konfiguriert werden.

    Stellen Sie sicher, dass der AutoErmittlungsdienst und Exchange-Webdienste auf dem Exchange-Client Access-Server konfiguriert sind. Weitere Informationen zum, finden Sie unter [Client Access-Server](https://technet.microsoft.com/library/dd298114.aspx).

7.  Bieten Sie im Feld **Kennwort** das Kennwort für dieses Konto Intune Zugriff auf den Exchange-Server zu aktivieren.

8. Wählen Sie **eine Verbindung herstellen**.

    Es kann einige Minuten dauern, während die Verbindung eingerichtet ist.

Während der Konfiguration speichert die Exchange-Connector Ihre Proxyeinstellungen zum Aktivieren des Zugriffs auf das Internet an. Wenn Ihre Proxyeinstellungen ändern zu können, müssen Sie den Exchange-Connector neu zu konfigurieren, um die aktualisierten Proxyeinstellungen des Verbinders Exchange anwenden.

Nachdem die Verbindung der Exchange-Connector legt fest, mobile Geräten zugeordnete Benutzer, die in Exchange Connector verwaltet werden automatisch synchronisiert und an den Exchange-Connector hinzugefügt. Diese Synchronisierung dauert einige Zeit in Anspruch.

> [!NOTE]
> Wenn Sie den lokalen Exchange-Connector installiert haben und zu einem bestimmten Zeitpunkt Sie die Exchange-Verbindung löschen, müssen Sie den lokalen Exchange-Connector vom Computer deinstallieren, auf denen es installiert wurde.

## Überprüfen Sie die Exchange-Verbindung

Nachdem Sie den Exchange-Connector erfolgreich konfiguriert haben, können Sie den Status der Verbindung und der letzte erfolgreiche Synchronisierungsversuch anzeigen. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com) **Administrator** des Arbeitsbereichs aus und wählen Sie unter **Verwaltung mobiler Geräte**aus **Microsoft Exchange**, und überprüfen Sie, ob die eingegebenen Details unter **Exchange Verbindungsinformationen**angezeigt.


Sie können auch das Datum und Uhrzeit der letzten erfolgreiche Synchronisierungsversuch überprüfen.
