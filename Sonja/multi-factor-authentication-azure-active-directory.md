---
title: Mehrstufige Authentifizierung Azure AD-| Microsoft Intune
description: "So kombinierte Authentifizierung in Azure AD für Gerät Registrierung erforderlich."
keywords: 
author: nbigman
manager: angerobe
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: 90f05f63e5df7776d6c6fde4de60731ccf1cddf0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Mehrstufige Authentifizierung für Microsoft Intune

Intune integriert Azure AD-kombinierte Authentifizierung (MFA) für die Registrierung von Gerät zu Ihnen dabei helfen Ihres Unternehmens Ressourcen zu schützen. MFA erfordert Authentifizierungsfaktoren wie Text-Authentifizierung über Benutzernamen und Kennwörter an. Dies ist für iOS, Android, Windows 8.1 oder höher, oder Windows Phone 8.1 oder höher unterstützt.

> [!NOTE]
>
> In älteren Versionen von Konfigurations-Manager (früher als 1610 freizugeben) sehen Sie immer noch die Einstellung MFA in der Konfigurations-Manager-Verwaltungskonsole. Führen Sie im Konfigurations-Manager-Verwaltungskonsole MFA konfigurieren wie nicht funktionieren. Konfigurieren Sie MFA aus, wie in diesem Artikel beschrieben.

### Konfigurieren von Intune mehrstufige Authentifizierung am Gerät Registrierung erforderlich sein
Um MFA am Gerät Registrierung erforderlich ist, gehen Sie folgendermaßen vor:

1. Melden Sie sich bei Ihrem [Microsoft Azure-Portal](https://manage.windowsazure.com) mit Administrator-Anmeldeberechtigungen.
2. Wählen Sie aus Ihrem Mandanten.
2. Wählen Sie die Registerkarte **Applications** aus. Sie sehen eine Liste der Dienste für die Azure AD-Sicherheitsfeatures konfiguriert werden können.
3. Wählen Sie **Microsoft Intune Registrierung**aus.
4. Wählen Sie **Konfigurieren**. 
5. Klicken Sie unter **kombinierte Authentifizierung und Access standortbasierte Regeln** können Sie folgende Aktionen ausführen:
    -  Aktivieren Sie die Access-Regeln
    -  Wählen Sie aus, ob die Regeln für alle Benutzer und bestimmte Azure gelten AD-Sicherheitsgruppen.
    -  Verlangen der kombinierte Authentifizierung für die Registrierung aller Geräte.
    -  Mehrstufige Authentifizierung für die Registrierung erforderlich, wenn das Gerät nicht im Büro ist.
    -  Wählen Sie **Blockieren des Zugriffs auf Ressourcen des Unternehmens** , um die Registrierung von einem Gerät zu verhindern, wenn es nicht mit dem Firmennetzwerk verbunden ist. 
4. Sie können auch den Link, um **Ihre Arbeit Netzwerkspeicherort definieren oder bearbeiten**, klicken, um Network Connectivity Anforderungen für die Registrierung Gerät zu konfigurieren.
> [!IMPORTANT]
> 
> Konfigurieren Sie **Gerät basierenden Access Regeln** nicht für die Microsoft Intune Registrierung.
