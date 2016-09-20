---
title: "Registrieren Sie mit der Registrierung Geräte-Manager | Microsoft Intune"
description: "Das Gerät Registrierungs-Manager (DEM) Konto kann große Anzahl von freigegebenen, Ihres Unternehmens im Besitz eines mobilen Geräten mit eines einzelnen Benutzerkontos verwalten."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 585ce92b0f0159060d9a8f1960b4c7b05eafdee7
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Registrieren Sie Ihres Unternehmens im Besitz Geräte mit der Registrierung Geräte-Manager in Microsoft Intune
Organisationen können Intune verwenden, um große Anzahl von mobilen Geräten für ein einzelnes Benutzerkonto verwalten zu können. Das Konto *Geräte Registrierungs-Manager* (DEM) ist eine spezielle Intune, die bis zu 1.000 Geräte registrieren kann. Es empfiehlt sich, dass Sie über dieses Konto gemeinsam genutzten Geräten, sondern als persönliche ("BYOD") Geräte registrierte Geräten verwenden. Benutzer werden kann nicht "native" e-Mail-apps, beispielsweise verwendet.

Beispielhaft könnten Sie ein Gerät Registrierungs-Manager Benutzerkonto einer Geschäftsführer oder einem Vorgesetzten, lassen sie zuweisen:

-   Geräte in Intune zu registrieren.

-   Melden Sie sich mit dem Portal Unternehmen zu Unternehmen apps zu erhalten.

-   Installieren Sie und deinstallieren Sie der Software.

-   Konfigurieren des Zugriffs auf Unternehmensdaten.


**Ein Gerät Registrierungs-Manager Szenario:** Ein Restaurant möchte POS-Tablets für Warten Personal und Reihenfolge Monitore für deren Küche Mitarbeiter. Die Mitarbeiter müssen nie Unternehmensdaten zugreifen, oder melden Sie sich als Benutzer. Der Administrator Intune ein Gerät Registrierungs-Manager-Konto erstellt und registriert die im Besitz eines Unternehmens Geräte mit diesem Konto. Alternativ konnte der Administrator den Registrierung Geräte-Manager Geben Sie Anmeldeinformationen an einen Vorgesetzten Restaurant, der den Manager informieren möchten registrieren und Verwalten der Geräte.

Der Administrator oder Manager kann funktionsspezifischen apps für das Restaurant Geräte bereitstellen. Administrator können Sie auch wählen Sie das Gerät in der Intune-Verwaltungskonsole und Verwaltung mobiler Geräte mit der Verwaltungskonsole zurückziehen.

Geräte, die mit einem Gerät Registrierungs-Manager-Konto registriert sind, stehen die folgenden Einschränkungen:
  - Es gibt keine bestimmten Gerät "Benutzer" – also keine Daten-Access-e-Mail oder einen Firmennamen. Jedoch konnte VPN, beispielsweise weiterhin Gerät-apps mit Zugriff auf Daten zur Verfügung stellen.
  - Da diese Szenarien pro Benutzer sind ist keine bedingte Zugriff.
  - Sie können keine diese Geräte vom Unternehmen Portal zurücksetzen.
  - Nur die lokale Geräte wird im Unternehmen Portal app oder Website angezeigt.
  - Apple Lautstärke Language Pack für-Programm (VPP) apps verwenden keine aufgrund von Apple-ID-Anforderungen pro Benutzer für die Verwaltung der app.
  - (iOS) Sie können keine auch mit Apple-Konfiguration oder Apple-Gerät Registrierungs-Programm (DEP) registriert, aber DEP oder Apple-Konfiguration verwalteten Geräten ohne Benutzer Zugehörigkeit registriert sein.

> [!NOTE]
> Bereitstellen von um Geräte Unternehmen apps bereitstellen, die vom Gerät Registrierungs-Manager verwaltet werden, die app Unternehmen Portal als **Erforderlich, installieren Sie** die Geräte Registrierungs-Manager-Benutzerkonto.
> Zum Verbessern der Leistung zeigt die Unternehmen Portal-app auf einem Gerät von DEM anzeigen nur das lokale Gerät. Remote-Verwaltung von anderen Geräten DEM kann nur der Administrator Intune-Verwaltungskonsole erfolgen.

## Erstellen von Gerät Registrierungs-Manager-Konten
Gerät Registrierungs-Manager-Konten sind Benutzerkonten mit der Berechtigung zum Registrieren große Anzahl von Geräten im Unternehmen gehören. Nur Benutzer in der Intune Verwaltungskonsole können Gerät Registrierungs-Manager sein.

#### Hinzufügen von einem Gerät Registrierungs-Manager zu Intune

1.  Wechseln Sie zum [Microsoft Intune Kontoportal](http://go.microsoft.com/fwlink/?LinkId=698854) , und melden Sie sich bei Ihrem Administratorkonto.

2.  Wählen Sie **Benutzer hinzufügen**.

3.  Bestätigen Sie, dass das Benutzerkonto, die für ein Gerät Registrierungs-Manager aufgeführt ist. Wenn sie nicht möchten, fügen Sie den Benutzer, indem Sie auf **neu** , und zum Abschluss der **Benutzer hinzufügen** . Eine Abonnementlizenz ist für jeden Benutzer, die den Dienst greift auf erforderlich. Der Registrierung Geräte-Manager sein nicht Intune-Administrator. Überprüfen Sie, ob Sie weitere Lizenzen hinzufügen, bevor Sie dieses Feature verwenden müssen.

4.  Melden Sie sich an die [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) mit Administrator-Anmeldeberechtigungen.

5.  Wählen Sie **Administrator**im Navigationsbereich, wechseln Sie zur **Verwaltung der Administrator**und wählen Sie **Geräte Registrierungs-Manager aus**. Das **Gerät Registrierungs-Manager** wird geöffnet.

6.  Wählen Sie " **hinzufügen...**". Im Dialogfeld **Geräte hinzufügen Registrierungs-Manager** wird geöffnet.

7.  Geben Sie die **Benutzer-ID** des Kontos Intune, und wählen Sie dann auf **OK**. Benutzer des Geräts Registrierungs-Manager sein nicht Intune-Administrator.

8.  Registrierung Geräte-Manager kann sich nun registrieren mobile Geräte mit demselben Verfahren, das ein Benutzer für ein BYOD Szenario im Portal für Unternehmen verwendet.

## Löschen eines Geräte Registrierungs-Managers aus Intune

1.  Melden Sie sich mit dem [Microsoft Intune Administratorportal](http://manage.microsoft.com) mit Administrator-Anmeldeberechtigungen.

2.  Wählen Sie **Administrator**im Navigationsbereich, wechseln Sie zur **Verwaltung der Administrator**und wählen Sie **Geräte Registrierungs-Manager aus**. Das **Gerät Registrierungs-Manager** wird geöffnet.

3.  Wählen Sie den Registrierungs-Manager **Benutzer** , den Sie löschen möchten, und wählen Sie dann auf **Löschen**. Diesen Benutzer aus Intune wird nicht gelöscht, und die Geräte, die diesem Benutzer verwaltet werden in Intune registrierten bleiben. Löschen einen Gerät Registrierungs-Manager wird verhindert, dass den Benutzer mehr Geräten in Intune registrieren.

4.  Wählen Sie **Ja** , um zu bestätigen, dass Sie den Registrierungs-Manager löschen möchten.

Löschen eines Geräte Registrierungs-Managers wirkt sich nicht auf registrierten Geräte aus. Wenn ein Gerät Registrierungs-Manager gelöscht wird:

-   Es sind keine registrierten Geräte betroffen.

-   Registrierten Geräte weiterhin vollständig verwaltet werden.

-   Die gelöschten Gerät Registrierungs-Manager Anmeldeinformationen bleiben gültig Unternehmen-Portal anmelden, um apps zuzugreifen.

-   Die gelöschten Gerät Registrierungs-Manager Anmeldeinformationen immer noch nicht zurücksetzen aus oder Geräte zurückziehen.

-   Gelöschte Gerät Registrierungs-Manager des Kontos Beziehung zu registriert Geräte bleibt, aber keine zusätzliche Geräte registriert werden können.
