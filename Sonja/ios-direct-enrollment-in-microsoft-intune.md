---
title: "Direkte Registrierung für iOS-Geräte | Microsoft Intune"
description: "Mithilfe des Tools Apple-Konfiguration direkt im Unternehmen im Besitz iOS-Geräte mit einer vordefinierten Richtlinie durch Herstellen einer Verbindung USB registrieren, um einen Mac."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 17836bc826bc89e3f041f7b369be09c1cce9ea4f
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Registrieren Sie direkt unter Verwendung Konfiguration Apple iOS-Geräte
Intune unterstützt die Registrierung von corporate im Besitz iOS-Geräte, die mithilfe des Tools für [Apple-Konfiguration](http://go.microsoft.com/fwlink/?LinkId=518017) auf einem Mac ausgeführt wird. Dieses Verfahren wird nicht Factory-Zurücksetzen des Geräts und registriert wird das Gerät mit einer vordefinierten Richtlinie. Diese Methode ist für Geräte mit **keine Benutzer Zugehörigkeit** und müssen Sie das iOS-Gerät an einen Mac-Computer zum Einrichten Ihres Unternehmens Registrierung USB-verbinden. Bei der Registrierung von iOS-Geräte direkt, können Sie ein Gerät registrieren, ohne die fortlaufende Zahl des Geräts erwerben. Sie können auch das Gerät zur Identifizierung benennen, bevor Intune den Namen des Geräts während der Registrierung erfasst werden. Die app Unternehmen Portal wird direkte registrierten Geräte nicht unterstützt. Dieser Leitfaden wird davon ausgegangen, dass Sie Apple-Konfiguration 2.0 auf einem Mac-Computer verwenden.

1.  **Erstellen eines Profils für Geräte** Ein Gerät Registrierungs-Profil definiert die Einstellungen auf Geräte angewendet. Wenn Sie noch nicht getan haben, erstellen Sie ein Gerät Registrierungs-Profil für iOS-Geräte mit Apple-Konfiguration registriert.

    1.  Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) **Richtlinie** &gt; **Corporate Gerät Registrierung**, und wählen Sie dann **hinzufügen...**.

        ![Gerät Registrierungs-Profilseite erstellen](../media/pol-sa-corp-enroll.png)

    2.  Geben Sie die Details für die Geräteprofile aus:

        -   **Name** – Name des Profils Registrierung Gerät. Für Benutzer nicht sichtbar.

        -   **Beschreibung** – Beschreibung des Profils Registrierung Gerät. Für Benutzer nicht sichtbar.

        -   **Benutzer Zugehörigkeit** – gibt an, wie Geräte registriert sind. Wählen Sie für die direkte Registrierung **keine Benutzer Zugehörigkeit**ein.

        -   **Vor dem Gerät gruppenzuordnung** – alle Geräte bereitgestellt dieses Profil wird zunächst dieser Gruppe angehören. Sie können nach der Registrierung Geräte zuweisen.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    3.  Wählen Sie **Profil speichern** , um das Profil hinzufügen aus.

5.  **Exportieren ein Profils als .mobileconfig für die Bereitstellung auf iOS-Geräte** Wählen Sie das Geräteprofil, die, das Sie erstellt haben. Wählen Sie **exportieren...** Klicken Sie in der Taskleiste. Wählen Sie die **Profil herunterladen** , und speichern Sie die heruntergeladene .mobileconfig-Datei.

6.  **Übertragen Sie die Datei** Kopieren Sie die heruntergeladene .mobileconfig-Datei mit einem Mac-Computer an.
    > [!NOTE]
    > Die URL der Registrierung Profil gilt für zwei Wochen aus, wenn diese exportiert werden. Nach zwei Wochen müssen Sie eine neue Registrierungs-Profil-URL zum Registrieren iOS-Geräte mit Setup-Assistenten exportieren.
7.  **Vorbereiten des Geräts mit Apple-Konfiguration** iOS-Geräte sind mit dem Mac-Computer verbunden und für die Verwaltung mobiler Geräte registriert.

    1.  Starten Sie auf einem Mac **Apple Konfiguration 2.0**aus.

    2.  Herstellen einer Verbindung dem Mac Computer mit einem USB-Kabel mit dem iOS-Gerät. Schließen Sie **Fotos**, **iTunes**und andere apps, die für das Gerät zu öffnen, wenn das Gerät erkannt wird.

    3.  Im Apple-Konfiguration einzelner Klick des verbundenen iOS-Geräts, und wählen Sie dann auf die Schaltfläche **Hinzufügen** . Optionen, die das Gerät hinzugefügt werden können, die in der Dropdown-Liste angezeigt werden. Wählen Sie auf **Profile** .

    4.  Verwenden Sie die Datei Datumsauswahl, um die Datei .mobileconfig auszuwählen, die von Intune exportiert, und wählen Sie dann auf **Hinzufügen**. Das Profil wird auf dem Gerät hinzugefügt.  Wenn das Gerät **Unsupervised**ist, wird die Installation Annahme auf dem Gerät erforderlich ist.

8.  **Installieren Sie das Profil** Sie können das Profil auf dem iOS-Gerät installieren. Das Gerät muss bereits abgeschlossen haben den Setup-Assistenten und verwendet werden.  Wenn Registrierung app-Bereitstellungen umfasst, sollte das Gerät verfügen, Apple ID einrichten, da die app-Bereitstellungen erfordern werden, dass Sie über einen Apple-ID für die App Store angemeldet haben.

    1.  Aufheben der Sperre iOS-Gerät.

    2.  Tippen Sie im Dialogfeld **Profil installieren** für **Management-Profil**auf **Installieren**.

    3.  Bereitstellen von **Geräte-Kenncode** oder **Apple-ID**, falls erforderlich.

    4.  Akzeptieren Sie die **Warnung**, und tippen Sie auf **Installieren**.

    5.  Akzeptieren Sie die **Remote-Warnung**, und tippen Sie auf **vertrauen**.

    6.  Wenn das Feld **Installierte Profil** , dass das Profil **installiert**wurde bestätigt, wählen Sie **Fertig**.

9. **Vergewissern Sie sich Profil** 
    auf dem iOS-Gerät, starten Sie die **Einstellungen** , und wechseln Sie **Allgemeine** &gt; **Device Management** &gt; **Management-Profil** &gt; und bestätigen der Profilinstallation aufgeführt ist, überprüfen Sie die iOS Richtlinie Einschränkungen und installierten apps. Richtlinie Einschränkungen und apps können auf dem Gerät angezeigt werden bis zu 10 Minuten dauern.

10. **Verteilen von Geräten** IOS-Gerät ist nun mit Intune registriert und verwaltet.
