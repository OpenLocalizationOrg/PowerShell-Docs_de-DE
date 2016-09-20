---
title: "Verwalten von Windows Store für Geschäfts-apps | Microsoft Intune"
description: "Schließen Sie Microsoft Intune an Windows Store für Business, verwalten und Bereitstellen von Lautstärke gekauft apps der Intune Verwaltungskonsole werden soll"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 077029a962797a18fab27c3f1f5340eae6edfe04
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwalten von apps, die Sie aus dem Windows Store for Business mit Microsoft Intune erworben haben
Im [Windows Store für Unternehmen](https://www.microsoft.com/business-store) bietet Ihnen einen Speicherort zum Suchen und erwerben von apps für Ihre Organisation, einzeln oder in Lautstärke. Im Store an Microsoft Intune anschließen, können Sie die Intune-Verwaltungskonsole Lautstärke gekauft apps verwalten. Beispiel:
* Sie können die Liste der apps synchronisieren, die Sie aus dem Speicher mit Intune erworben haben.
* Apps, die synchronisiert werden angezeigt, in der Intune-Verwaltungskonsole, und können Sie diese wie jede andere apps bereitstellen.
* Sie können nachverfolgen, wie viele Lizenzen verfügbar sind, und wie viele in der Intune-Verwaltungskonsole genutzt werden.
* Intune blockiert Bereitstellung und Installation von apps, wenn keine ausreichende Anzahl von Lizenzen verfügbar sind.

## Bevor Sie beginnen
Überprüfen Sie die folgende Informationen, bevor Sie beginnen, Synchronisierung und Bereitstellen von apps aus dem Windows Store für Unternehmen:
* Sie müssen Intune als die Zertifizierungsstelle Mobilgerät Management für Ihre Organisation konfigurieren. Weitere Informationen finden Sie unter [Vorbereiten Geräte in Microsoft Intune registrieren](get-ready-to-enroll-devices-in-microsoft-intune.md).
* Sie müssen für ein Konto in Windows Store für Business angemeldet haben.
* Nachdem Sie eine Business-Windows Store-Konto Intune zugeordnet wurde, können nicht Sie zukünftig an ein anderes Konto ändern.
* Apps aus dem Store erworben haben können nicht manuell hinzugefügt oder aus Intune gelöscht werden soll. Sie können nur mit dem Windows Store for Business synchronisiert werden.
* Intune synchronisiert nur online lizenzierte apps, die Sie aus dem Windows Store für Unternehmen erworben haben.
* Geräte müssen verknüpfte in Active Directory-Domänendiensten oder Arbeitsplatz beigetreten, diese Funktion zu verwenden.
* Registrierten Geräte müssen die 1511 Version von Windows 10 verwenden.

## Zuordnen von Ihrem Windows Store for Business-Konto zu Intune
Bevor Sie die Synchronisierung in der Intune Verwaltungskonsole aktivieren, müssen Sie Ihr Konto Store, wenn Sie ein Verwaltungstool Intune verwenden konfigurieren:
1. Stellen Sie sicher, dass Sie melden Sie sich bei dem Unternehmen Speicher mit demselben mandantenadministratorkonto, die, das Sie verwenden, melden Sie sich bei Intune.
2. Wählen Sie im Store Business **Einstellungen**aus > **Tools zum Projektmanagement**.
3. Klicken Sie auf der Seite Management Tools wählen Sie **Hinzufügen eines Verwaltungstool aus**, und wählen Sie **Microsoft Intune**.

Jetzt können Sie fortfahren und Einrichten der Synchronisierung in der Intune-Verwaltungskonsole.

## Konfigurieren der Synchronisierung

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Administrator**aus.
2. Klicken Sie im Arbeitsbereich **Administration** erweitern Sie **Verwaltung mobiler Geräte**und wählen Sie dann **Store für Unternehmen**.
3. Klicken Sie auf der Seite **Windows Store für Business** folgendermaßen Sie vor:
 * Wenn Sie dies noch nicht getan haben, klicken Sie auf den Link zum Melden Sie sich für Windows Store für Unternehmen.
 * Sobald Sie angemeldet oben sind, wählen Sie **Synchronisieren konfigurieren**.
4. Wählen Sie im Dialogfeld **Konfigurieren Windows Store für Business-app synchronisieren** **Aktivieren Windows Store für Unternehmen synchronisieren**.
5. Wählen Sie aus der Dropdownliste **Sprache** die Sprache aus, in der apps aus dem Windows Store für Unternehmen in der Intune Verwaltungskonsole angezeigt werden. Unabhängig von der Sprache, in der sie angezeigt werden, werden sie in der Endbenutzer Sprache, wenn verfügbar installiert werden.
6. Klicken Sie auf **OK**.

## Synchronisieren von apps

1. Wählen Sie **Jetzt synchronisieren** , um die apps zu synchronisieren, die Sie im Store mit Intune erworben haben, klicken Sie auf der Seite **Windows Store für Unternehmen** .
2. Wählen Sie im Arbeitsbereich **Apps** **Verwaltete Software** > **Lizenzierte Software** zum Anzeigen der verfügbaren apps, und stellen Sie sicher, dass Ihre erworbenen apps ordnungsgemäß importiert wurden. Der apps in diesem Knoten werden angezeigt, mit der Gesamtzahl der Lizenzen, die Sie besitzen, und die Anzahl der Lizenzen Ihnen zur Verfügung stehen.

## Bereitstellen von apps

Sie bereitstellen apps aus dem Speicher in die gleiche Weise, wie, die Sie eine beliebige andere Intune app bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Wenn Sie eine Windows Store for Business-app bereitstellen, wird eine Lizenz von jedem Benutzer verwendet, die die app-Installationen. Wenn Sie alle verfügbaren Lizenzen für eine bereitgestellte app verwenden, werden Sie keine mehr Kopien bereitstellen sein. Sie müssen eine der folgenden Aktionen ausführen:
* Deinstallieren Sie die app aus einigen Geräten aus.
* Reduzieren Sie die aktuelle Bereitstellung werden sollen nur die Benutzer, die, denen Sie über die erforderlichen Lizenzen vorhanden sind.
* Kaufen von mehr Kopien der app aus dem Windows Store für Unternehmen.

> [!Important]
> Bereitgestellte apps sind nur für den Benutzer, der für das Gerät ursprünglich registriert verfügbar. Kein anderer Benutzer können die app zugreifen.


### Siehe auch
[Hinzufügen von apps für mobile Geräte in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)
