---
title: "Exchange-Connector für Exchange Online | Microsoft Intune"
description: "Verbinden mit Office 365 Exchange-Dienst zur Unterstützung der Verwaltung von Exchange ActiveSync mobiler Geräte (MDM) Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: 1aabf820170483eacc83bec5e2b275e84dc07ffd
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren von Connector Dienst Intune für Exchange Online

Verwenden Sie diese Informationen, um Microsoft Intune und Exchange Online oder neue Exchange Online dedizierte Service verbinden. Um festzustellen, ob es sich bei Ihrer Umgebung Exchange Online ausschließlich in der **neuen** oder **älteren**wird, wenden Sie sich an Ihren Account Manager. Intune unterstützt nur ein Exchange-Connector-Verbindung eines beliebigen Typs pro Abonnement.

## Anforderungen für den Connector Dienst
Der **Verbinder um den Dienst** unterstützt nur Exchange Online oder neuer Exchange Online dedizierter und keine Anforderungen für lokale Infrastruktur.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Exchange Online konfiguriert und ausgeführt|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Mobiles Gerät Management Zertifizierungsstelle| [Legen Sie den mobilen Gerät Management-Zertifizierungsstelle auf Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Microsoft Exchange-version|Exchange Online oder neue Exchange Online dedizierte service|
|Active Directory-Synchronisierung|Bevor Sie den Verbinder Intune verwenden können, müssen Sie [Einrichten von Active Directory-Synchronisierung](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) , damit der lokale Benutzer und Sicherheitsgruppen mit Ihrer Instanz von Azure Active Directory synchronisiert werden.|

### Exchange-Cmdlet Anforderungen

Sie müssen auch ein Benutzerkonto für Exchange Online erstellen, die vom Exchange Connector Intune verwendet wird. Das Konto muss die Berechtigung zum Verwenden der Administrator Intune-Verwaltungskonsole und zum Ausführen dieser erforderlichen Exchange von Windows PowerShell-Cmdlets verfügen:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, neue-MobileDeviceMailboxPolicy-MobileDeviceMailboxPolicy entfernen
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, neue-ActiveSyncDeviceAccessRule-ActiveSyncDeviceAccessRule entfernen
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## Einrichten des Connectors Dienst

1. Öffnen Sie die [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) mit einem Benutzerkonto mit Exchange-Administratorrechte und Berechtigungen für die Cmdlets [über](#exchange-cmdlet-requirements)ein. Microsoft Intune verwendet die e-Mail-Adresse des aktuell angemeldeten Benutzers, um die Verbindung einzurichten.

2.  Im Verknüpfungsbereich Arbeitsbereich, wählen Sie **Administrator**aus, und gehen Sie dann **Verwaltung mobiler Geräte** > **Microsoft Exchange** > **Exchange-Verbindung**.
![Um den Dienst Connector-Seite einrichten](../media/intunesa5cservicetoserviceconnector.png)

3.  Wählen Sie auf der Seite **Exchange-Verbindung** **Festlegen von Dienst zu Dienst Verbinder**aus.


Der Verbinder Dienst werden automatisch konfiguriert und Synchronisieren mit Ihrem Exchange Online oder neue Exchange Online dedizierte Umgebung.

## Überprüfen Sie Ihre Exchange-Verbindung

Nachdem Sie den Exchange-Connector erfolgreich konfiguriert haben, in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) wählen Sie den **Administrator** und **Mobile Geräte-Verwaltung**wechseln > **Microsoft Exchange** , und überprüfen Sie, ob Sie die Angaben unter **Exchange Verbindungsinformationen**angezeigt.

Sie können auch das Datum und Uhrzeit von der letzten erfolgreich Synchronisierungsversuch überprüfen.
