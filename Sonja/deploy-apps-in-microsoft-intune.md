---
title: 'Gewusst wie: Bereitstellen von apps | Microsoft Intune'
description: Verwenden Sie die Informationen in diesem Thema beim Bereitstellen von apps mit Microsoft Intune helfen.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: 904b89a92cef870f4672e5f40e6ac91ece10d3b7
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# In Microsoft Intune apps bereitstellen

Verwenden Sie die Informationen in diesem Thema beim Bereitstellen von apps mit Microsoft Intune helfen.


## Bereitstellen einer app
In diesem Verfahren erhalten Sie eine app für ausgewählte Gruppen von Geräten oder Benutzer bereitstellen.

### Bereitstellen eine app

1. Klicken Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com)auf **Apps** &gt; **Apps** die Liste der apps anzeigen möchten, die Sie verwalten.

2.  Wählen Sie die app, die Sie bereitstellen möchten, und klicken Sie dann auf **Bereitstellung verwalten**.

3.  In der * &lt;app-Name&gt; * im Dialogfeld auf der Seite **Gruppen auswählen** , wählen Sie die Benutzer oder Gerät Gruppen, dem Sie die app bereitstellen möchten.

4.  Konfigurieren Sie auf der Seite **Aktion Bereitstellung** Folgendes ein:

    - **Genehmigung** - auswählen, ob die Bereitstellung ist:
        - **Erforderlich** (erforderliche Installation)
        - **Verfügbar** (Benutzer installieren vom Unternehmen Portal bei Bedarf)
        - **Nicht verfügbar** (die app ist nicht installiert oder im Portal Unternehmen angezeigt)
        - **Deinstallieren von** (die app wird auf den Geräten deinstalliert)
    - **Stichtag** - für Installationen erforderlich, wählen Sie, wie schnell die app bereitstellen. Sie können aus den vordefinierten Werten auswählen oder Sie können **benutzerdefinierte** so konfigurieren Sie Ihre eigenen Stichtag auswählen.

5. Wenn die app, die Sie bereitstellen möchten von einer mobilen Anwendung zur Dokumentverwaltungsrichtlinie konfiguriert werden kann, wird der **Mobile** -App-Verwaltungsseite angezeigt. Wählen Sie auf dieser Seite die mobile Anwendung zur Dokumentverwaltungsrichtlinie, die Sie diese app zuordnen möchten.

    [Finden Sie unter welche Microsoft-apps mit mobilen Anwendung Informationsverwaltungsrichtlinien kompatibel sind.](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. Wenn die app, die Sie bereitstellen mit Intune VPN Profile kompatibel ist, wird die **Option VPN** Profilseite angezeigt. Auf dieser Seite können Sie auswählen, eine VPN-Profil iOS-apps zuordnen, die Sie bereitgestellt haben. Die VPN-Verbindung wird automatisch geöffnet werden, wenn die app gestartet wird. Um ein Profil VPN verfügbar zu machen, müssen sie die **pro-app VPN** Profil Einstellung aktiviert.
 Informationen zum Konfigurieren von VPN Profile, einschließlich Informationen zur Verwendung von apps, Profile zuordnen finden Sie unter [VPN-Verbindungen in Microsoft Intune](vpn-connections-in-microsoft-intune.md).

## Beispiel

In diesem Beispiel bereitgestellt Sie die app auf einem iOS-Gerät als **verfügbar** .
Die app zeigt auf Geräten der Benutzer im Unternehmen Portal und Benutzer können ihn von dort aus installieren.

Beispielsweise wurde in diesem Screenshot der Bing für iOS-app bereitgestellt, mithilfe der **Externen** Installation Verknüpfungsart mit einem benutzerdefinierten Symbol. Die Option **diese als bereitgestellten app anzeigen, und markieren Sie es im Portal Unternehmen** aktiviert wurde.  
![Verfügbare app für iOS](./media/available-install-on-iOS.png)

Wenn Sie die app als **erforderlich** auf einem iOS-Gerät bereitgestellt, erhalten der Benutzer eine Benachrichtigung, die eine app installiert werden kann. Beispielsweise wurde in diesem Screenshot die Arbeit Ordner für iOS-app bereitgestellt, mit der Eingabe der **verwaltete iOS-app aus dem app Store** Installation.  
![erforderlichen iOS-app](./media/iOS-Required-install.PNG)

## Nächste Schritte

Nachdem Sie eine app bereitgestellt haben, möchten Sie den Fortschritt zu überwachen. Weitere Informationen hierzu finden Sie unter [Überwachen der apps in Microsoft Intune](monitor-apps-in-microsoft-intune.md).
