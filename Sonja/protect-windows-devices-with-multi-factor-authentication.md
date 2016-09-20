---
title: "Mehrstufige Authentifizierung für Windows | Microsoft Intune"
description: "Intune integriert kombinierte Authentifizierung (MFA), die Sie schützen Ihrer Ihres Unternehmens Ressourcen unterstützen."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
ms.openlocfilehash: e9eef5c0589fa2d75a5ba2e677ca2d3c29e305af
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Schützen von Windows-Geräten mit kombinierte Authentifizierung
Microsoft Intune integriert kombinierte Authentifizierung (MFA) zu Ihnen dabei helfen Ihres Unternehmens Ressourcen zu schützen. MFA erfordert Authentifizierungsfaktoren wie Text-Authentifizierung über Benutzernamen und Kennwörter an. Intune unterstützt die Verwendung von MFA während der Registrierung von Windows 8.1 oder höher, Windows Phone 8.1 und Windows-10-Desktop und Mobile Geräte.

## Lokale Infrastruktur Anforderungen für ADFS MFA
Um die kombinierte Authentifizierung eingerichtet haben, müssen Sie folgende Aktionen ausführen:

-   Automatische Registrierung, wie in der [Verwaltung von Windows-Geräte einrichten](set-up-windows-device-management-with-microsoft-intune.md)beschrieben.
-   **Active Directory-Domäne, mit der ADFS-Server verbunden ist.**

-   **Active Directory Federation Services (ADFS) Server für MFA konfiguriert.** Ein Server, der Windows Server 2012 R2 ausgeführt wird und als ein ADFS-Server eingerichtet ist. Weitere Informationen finden Sie unter: [Secure Cloud und lokale Ressourcen mit Azure mehrstufige Authentifizierungsserver mit Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

Die Server müssen die Systemanforderungen in [Systemvoraussetzungen und Installation Informationen für Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx)erfüllen.

 


#### MFA mit Intune
Wenn Ihre Organisation eine lokale hat IT-Infrastruktur, die eine Active Directory-Domäne mit Active Directory Federation Services (ADFS) enthält, können Sie einrichten MFA auf dem Server Föderation und dann aktivieren MFA für die Registrierung Intune. Indem Sie MFA auf Intune konfigurieren, können Benutzer Authentifizierung haben, während der Registrierung, und verwenden Sie Ihres Unternehmens Ressourcen ohne Wiederholung des Prozesses MFA jedes Mal.

>[!NOTE]
>MFA kann auf Basis pro Benutzer oder Gruppen auf dem ADFS-Server dazu aufgefordert werden.  

#### MFA ohne Intune
Wenn Sie auf dem Server Föderation MFA eingerichtet, aber Sie nicht zur Teilnahme an Intune MFA aktivieren, müssen Benutzer MFA jedes Mal verwendet werden, dass sie Ihres Unternehmens Ressourcen (nicht nur bei der Registrierung von Gerät) zugreifen.

MFA Azure Active Directory (Azure AD) können Sie auch MFA auf einzelne Benutzer jedes Mal erfordern, dass Benutzer Ihres Unternehmens Ressourcen zugreifen. Azure AD MFA ist eine Cloud-Dienst, der eine keine erfordert lokalen IT-Infrastruktur. Informationen zum Einrichten von Azure AD MFA finden Sie unter [Erste Schritte mit Azure kombinierte Authentifizierung in der Cloud.](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## Während der Registrierung von Windows-Geräten mit Anforderung der ADFS MFA
Informationen zum Aktivieren der MFA in ADFS, finden Sie unter [Verwalten von Risiken mit zusätzlichen kombinierte Authentifizierung for Applications vertrauliche](http://technet.microsoft.com/library/dn280949.aspx).

## Einrichten von Gerät Registrierung MFA in Intune
>[!Important]  
>Aktivieren Sie MFA in Ihrer Azure AD-Mandanten oder lokalen Umgebung, bevor Sie MFA für Intune Registrierung von Windows-Geräten erfordern. Wenn Sie Benutzer keinen, die versuchen, die Windows-Geräten registrieren oder in Azure AD-Verknüpfung werden aktivierten Geräte eine Fehlermeldung angezeigt, wenn die automatische Registrierung während des Azure AD-Verknüpfung eingerichtet haben.

1.  Wählen Sie in der Verwaltungskonsole Intune **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **mehrstufige Authentifizierung**.

2.  Wählen Sie **Kombinierte Authentifizierung konfigurieren**, und wählen Sie dann auf **Aktivieren kombinierte Authentifizierung**.
