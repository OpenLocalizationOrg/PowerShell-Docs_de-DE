---
title: Verwalten von Web Access mit verwalteten Browser | Microsoft Intune
description: "Bereitstellen der Anwendung verwalteten Browser zum Einschränken des WebBrowser-Steuerelements und die Datenübertragung Web an andere apps."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
ms.openlocfilehash: a8cf580a7df1d9c5240fc702107563bc965ce6ad
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwalten von Microsoft Intune verwalteten Browserrichtlinien mit Zugriff auf das Internet
Verwaltete Browser wird eine Surfen im Internet-Anwendung, die Sie in Ihrer Organisation mithilfe von Microsoft Intune bereitstellen können. Eine Richtlinie verwalteten Browser konfiguriert eine Liste oder einer Sperrliste aufgeführt, die die Websites beschränkt, die Benutzer des Browsers verwalteten besuchen können.

Da diese app einer verwalteten app ist, können Sie auch die app Informationsverwaltungsrichtlinien mobilen Anwendung zuweisen. Diese Richtlinien steuern der Verwendung von Ausschneiden, kopieren, enthalten möglicherweise und um sicherzustellen, dass Links zu Inhalte, die Benutzer in anderen öffnen wählen Sie aus verwalteten apps einfügen, verhindern Bildschirm erfasst werden. Details finden Sie unter [Konfigurieren und Bereitstellen von Informationsverwaltungsrichtlinien in der Microsoft-Intune Verwaltungskonsole mobilen Anwendung](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Wenn Benutzer verwalteten Browser aus dem app Store installieren und Intune nicht verwalten, gilt folgende Verhalten:<br /><br />
Die verwaltete Browser-app für iOS – kann als eine einfache Webbrowser verwendet werden, aber einige Features nicht zur Verfügung, und es ist nicht möglich Zugriff auf Daten aus anderen apps Intune verwaltet.<br />
Android – die verwaltete Browser-app kann nicht verwendet werden.<br /><br />
Wenn der Benutzer im Browser verwalteten selbst auf einem iOS-Gerät mit einer älteren Version als iOS 9 installiert haben, werden keine Richtlinien, die Sie erstellen im Browser verwalten. Um sicherzustellen, dass Intune im Browser verwaltet werden, müssen Benutzer die app deinstallieren, bevor Sie auf diese als verwaltete app bereitstellen können. Unter iOS 9 und höher Wenn die Benutzer den verwalteten Browser selbst, installieren werden sie aufgefordert, damit Sie von der Richtlinie, verwaltet werden kann.

Sie können verwaltete Browserrichtlinien für die folgenden Arten von Gerät erstellen:

-   Geräte, die Android 4 und höher ausgeführt werden

-   Geräte, die iOS 8.0 und höher ausgeführt werden

Intune verwaltete Browser unterstützt Webinhalte durch [Anwendungspartner Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)öffnen.

## Erstellen einer Richtlinie verwalteten browser

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** &gt; **Richtlinie hinzufügen**.

2.  Konfigurieren Sie die folgenden Arten von **Software** Richtlinie aus:

    -   **Verwaltete Browser (Android 4 und höher)**

    -   **Verwaltete Browser (iOS 8.0 und höher)**

    Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien finden Sie unter dem Thema [Einstellungen verwalten und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) .

3.  Verwenden Sie die folgenden helfen Ihnen die Konfiguration der verwalteten Richtlinie Browsereinstellungen:

    - **Namen**. Geben Sie einen eindeutigen Namen für die Richtlinie verwalteten Browser in der Intune Verwaltungskonsole erkennbar.
    - **Beschreibung**. Stellen Sie eine Beschreibung, die bietet einen Überblick über die Richtlinie verwalteten Browser und weitere relevante Informationen, die hilft Ihnen, danach zu suchen.
    - **Aktivieren eines Zulassungsliste oder Blockierliste, um die URLs beschränken verwaltete Browser geöffnet werden kann**. Wählen Sie eine der folgenden Optionen aus:
        - **Zulassen der verwalteten Browser, damit nur die unten aufgeführten URLs öffnen**. Geben Sie eine Liste der URLs, die verwaltete Browser geöffnet werden kann.
        - **Blockieren der verwalteten Browser Öffnens die unten aufgeführten URLs**. Geben Sie eine Liste der URLs, der verwaltete Browser öffnen blockiert werden.
**Hinweis:** Sie können nicht in der gleichen verwalteten Browser Richtlinie zugelassenen und blockierten URLs einschließen.
Weitere Informationen zu den URL-Formaten, die Sie angeben können, finden Sie unter **URL-Format für zulässig und blockierte URLs** in diesem Thema.

4.  Wenn Sie fertig sind, wählen Sie die **Richtlinie zu speichern**.

Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt.

## Erstellen einer bereitstellungs für die verwaltete Browser-app
Nachdem Sie die Richtlinie verwalteten Browser erstellt haben, können Sie dann eine Bereitstellung von Software für die verwaltete Browser-app erstellen und die von Ihnen erstellte verwaltete Browser Richtlinie zuordnen.

> [!IMPORTANT]
> Verwaltete Browser, die auf die gleiche Weise wie andere Intune Richtlinien nicht Richtlinien bereitgestellt werden. Diese Art von der Richtlinie muss die verwaltete Browser-Software-Paket zugeordnet werden.

Bereitstellen der app, um sicherzustellen, dass Sie wählen Sie die Richtlinie verwalteten Browser auf der Seite **Verwaltung der Mobile-App** , die Richtlinie mit der app zugeordnet werden soll.

Weitere Informationen dazu, wie Sie apps bereitgestellt werden können finden Sie unter [Bereitstellen von apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## Sicherheit und Datenschutz für verwaltete browser

-   Websites, die Benutzer zu besuchen, die ein Zertifikat abgelaufen oder nicht vertrauenswürdigen aufweisen kann nicht geöffnet werden, auf iOS-Geräte.

-   Einstellungen verwendet, die Benutzern für integrierte Browser auf ihren Geräten vereinfacht der verwaltete Browser nicht. Dies ist, da der verwaltete Browser keinen Zugriff auf diese Einstellungen.

-   Wenn Sie die Option **einfache PIN für den Zugriff erforderlich** oder **erfordern corporate Anmeldeinformationen für den Zugriff** in einer mobilen Anwendung zur Dokumentverwaltungsrichtlinie verwalteten Browser zugeordnet konfigurieren und der Benutzer den Hilfelink auf der Authentifizierungsseite wählt, können sie dann suchen alle Internetsites unabhängig davon, ob sie eine Sperrliste in die Richtlinie verwalteten Browser hinzugefügt wurden.

-   Verwaltete Browser kann Sperren des Zugriffs auf Websites nur, wenn sie direkt zugegriffen werden. Es kann keine Zugriff blockieren, wenn zwischen-XT für Services (wie etwa einen Übersetzungsdienst) verwendet werden, um die Website zugreifen.

-   Sicherstellen, dass die Dokumentation Intune werden kann und -Authentifizierung zulässig zugegriffen**& #42;. Microsoft.com** ist nicht in der listeneinstellungen blockieren oder zulassen. Es ist immer zulässig.

### Deaktivieren der von Verwendungsdaten
Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung von verwalteten Browser zu Microsoft-Produkten und Dienstleistungen zu verbessern. Benutzer können Datensammlung deaktivieren, mithilfe der Einstellung **Verwendungsdaten** auf ihren Geräten. Sie haben keine Kontrolle über die Sammlung von Daten aus.

## Referenzinformationen

### URL-Format für zulässig und blockierte URLs
Verwenden Sie die folgende Informationen, um Informationen zu den zulässigen Formate und Platzhalter, die Sie zum Angeben der URLs in den Listen zugelassenen und blockierten verwenden können:

-   Sie können Platzhalterzeichen-Symbol (**& #42;**) nach den Regeln in der folgenden Liste für zugelassene Mustern verwenden.

-   Stellen Sie sicher, dass Sie alle URLs mit **http** oder **Https** voranstellen, wenn sie in die Liste eingeben.

-   Sie können die Adresse Portnummern angeben. Wenn Sie eine Port-Nummer nicht angeben, werden die Werte verwendet werden:

    -   Port 80 für http

    -   Port 443 für https

    Verwenden von Platzhaltern für die Port-Nummer wird nicht unterstützt. Beispielsweise * *http&colon;//www&period;Contoso&period;com:*;* *und* *http&colon;//www&period;Contoso&period;com: /*; ** werden nicht unterstützt.

-   Verwenden Sie in der folgenden Tabelle, um die zulässigen Muster wissen möchten, die Sie verwenden können, wenn Sie URLs angeben:

|URL|Details|Suchergebnisse|Stimmen nicht überein|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Entspricht eine einzelne Seite|www.contoso.com|Host.contoso.com<br /><br />www.contoso.com/Images<br /><br />Contoso.com/|
    |http://contoso.com|Entspricht eine einzelne Seite|Contoso.com/|Host.contoso.com<br /><br />www.contoso.com/Images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Entspricht allen URLs, die mit www.contoso.com beginnen|www.contoso.com<br /><br />www.contoso.com/Images<br /><br />www.contoso.com/Videos/tvshows|Host.contoso.com<br /><br />Host.contoso.com/Images|
    |http://&#42;.contoso.com/&#42;|Klicken Sie unter "contoso.com" alle Unterdomänen entspricht|Developer.contoso.com/resources<br /><br />News.contoso.com/Images<br /><br />News.contoso.com/Videos|Contoso.Host.com|
    |http://www.contoso.com/Images|Dieses Zeichen entspricht einen einzelnen Ordner|www.contoso.com/Images|www.contoso.com/images/Dogs|
    |http://www.contoso.com:80|Entspricht eine einzelne Seite mit einer Reihe von port|http://www.contoso.com:80||
    |https://www.contoso.com|Entspricht eine einzelne, sichere Seite|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|Dieses Zeichen entspricht einem einzelnen Ordner und alle Unterordner|www.contoso.com/images/Dogs<br /><br />www.contoso.com/images/Cats|www.contoso.com/Videos|

-   Im folgenden finden Beispiele für einige der Eingaben, die Sie angeben können:

    -   & #42;. com

    -   & #42;. Contoso / & #42;

    -   www.contoso.com/&#42;Images

    -   www.contoso.com/&#42;Images&#42;pigs

    -   www.contoso.com/Page&#42;

    -   IP-Adressen

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com: & #42;

    -   http://www.contoso.com: / & #42;

### Wie Konflikte zwischen der Liste zulassen und blockieren aufgelöst werden.
Wenn mehrere verwaltete Browserrichtlinien ein Gerät und der in Konflikt stehen, sowohl den Modus bereitgestellt werden (zulassen oder blockieren) und die URL-Listen für Konflikte ausgewertet werden. Bei einem Konflikt gilt das folgende Verhalten:

-   Wenn die Modi in jeder Richtlinie gleich sind, aber die URL-Listen unterscheiden, werden die URLs auf dem Gerät nicht erzwungen.

-   Wenn die Modi in jeder Richtlinie unterscheiden, aber die URL-Listen gleich sind, werden die URLs auf dem Gerät nicht erzwungen.

-   Wenn ein Gerät verwalteten Browserrichtlinien für das erste Mal und zwei Richtlinien Konflikt eingeht, werden die URLs auf dem Gerät nicht erzwungen. Verwenden Sie den **Richtlinie Konflikte** Knoten des Arbeitsbereichs **Richtlinie** , um die Konflikte anzuzeigen.

-   Wenn ein Gerät hat eine Richtlinie verwalteten Browser bereits erhalten, und eine zweite Richtlinie mit in Konflikt stehenden Einstellungen bereitgestellt wird, bleiben die ursprünglichen Einstellungen auf dem Gerät. Verwenden Sie den **Richtlinienkonflikten** Knoten des Arbeitsbereichs **Richtlinie** , in die Konflikte anzeigen.
