---
title: "IOS-Geräte mit Setup-Assistenten registrieren | Microsoft Intune"
description: "Registrieren Sie Ihres Unternehmens im Besitz iOS Geräte unter Verwendung der Apple-Konfiguration tool zum Factory-Gerät zurücksetzen und vorbereitet den Setup-Assistenten ausführen."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 1260001be3e5479ff0758178dc161260d31dcc3e
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Registrieren Sie iOS-Geräte mit Apple-Konfiguration mit Setup-Assistenten
Intune unterstützt die Registrierung von corporate im Besitz iOS-Geräte, die mithilfe des Tools für [Apple-Konfiguration](http://go.microsoft.com/fwlink/?LinkId=518017) auf einem Mac ausgeführt wird. Dieses Verfahren Factory-setzt das Gerät und vorbereitet durch die neuen Benutzer des Geräts mit den Unternehmensrichtlinien vorinstalliert Setup-Assistenten ausführen.


## Setup-Assistenten Registrierung für iOS-Geräte mit Microsoft Intune
Unter Verwendung Apple-Konfiguration können Sie Factory iOS-Geräte zurücksetzen und die Vorbereitung für die Ausführung von Setup durch die neuen Benutzer des Geräts.  Diese Methode müssen Sie das iOS-Gerät an einen Mac-Computer zum Einrichten Ihres Unternehmens Registrierung USB-verbinden und wird davon ausgegangen, dass Sie Apple-Konfiguration 2.0 verwenden. In den meisten Fällen erfordern, dass die Richtlinie angewendet iOS-Gerät **Benutzer Zugehörigkeit** zum Aktivieren der app Intune Unternehmen Portal enthalten.

**Erforderliche Komponenten**
* [iOS-Registrierung aktiviert](set-up-ios-and-mac-management-with-microsoft-intune.md) durch Installieren eines Zertifikats APNs
* Zugang zu den iOS-Geräte - Geräte muss nicht konfiguriert (Factory zurücksetzen) ohne Kennwortschutz
* Gerät fortlaufenden Zahlen – [So erhalten Sie eine Seriennummer für iOS](https://support.apple.com/en-us/HT204308)
* USB-Verbindungskabel
* Mac-Computer mit [Apple Konfiguration 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


1.  **Erstellen von Gruppen mobilen Gerät** (Optional) Wenn Ihr Unternehmen Mobilgerät Gruppen zur Verwaltung von Geräten erforderlich ist, werden erstellen Sie diese Gruppen. [Verwenden Sie Gruppen auf Benutzer und Geräte mit Microsoft Intune verwalten](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

2.  **Erstellen eines Profils für Geräte** Ein Gerät Registrierungs-Profil definiert die Einstellungen für eine Gruppe von Geräten angewendet. Wenn Sie noch nicht getan haben, erstellen Sie ein Gerät Registrierungs-Profil für iOS-Geräte mit Apple-Konfiguration registriert.

    1.  Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) **Richtlinie** &gt; **Corporate Gerät Registrierung**, und wählen Sie dann **hinzufügen...**.
    ![Erstellen von Gerät Registrierungs-Profils](../media/pol-sa-corp-enroll.png)

    2.  Geben Sie die Details für die Geräteprofile aus:

        -   **Name** – Name des Profils Registrierung Gerät. (Für Benutzer nicht sichtbar)

        -   **Beschreibung** – Beschreibung des Profils Registrierung Gerät. (Für Benutzer nicht sichtbar)

        -   **Registrierungs-Details** – gibt an, wie Geräte registriert sind.

            -   **Für die Zugehörigkeit Benutzer auffordern** – das Gerät während der ersten Einrichtung mit einem Benutzer zugeordnet werden muss und dann Zugriff auf Unternehmensdaten und e-Mails als diesen Benutzer zugelassen werden konnte. **Zugehörigkeit Benutzer** sollten für DEP verwalteten Geräten konfiguriert werden, die für Benutzer angehören, und das Unternehmen-Portal (d. h., um apps zu installieren) verwenden müssen.

            -   **Keine Zugehörigkeit Benutzer** – das Gerät ist nicht mit einem Benutzer zugeordnet. Verwenden Sie diese Zuordnung für Geräte, die Aufgaben ausführen, ohne den Zugriff auf lokale Benutzerdaten aus. Mit Anforderung der Benutzer Zugehörigkeit, einschließlich der Unternehmen Portal-app verwendet werden, für die Installation von Branchen apps, Apps funktioniert nicht.

        -   **Vor dem Gerät gruppenzuordnung** – alle Geräte bereitgestellt dieses Profil wird zunächst dieser Gruppe angehören. Sie können nach der Registrierung Geräte zuweisen.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

          -  **Gerät Registrierungs-Programm** - Setup-Assistenten Registrierung im Apple Gerät Registrierung Programm (DEP) verwendet werden. Stellen Sie sicher, dass der Schalter **off**festgelegt ist.

    3.  Wählen Sie **Profil speichern** , um das Profil hinzufügen aus.

3.  **Hinzufügen von iOS-Geräte bei Setup-Assistenten registrieren** Wechseln Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com) **Gruppen** &gt; **Alle Geräte** &gt; **Geräte alle Corporate im Besitz eines** &gt; **Alle Geräte**, und wählen Sie dann auf **... Geräte hinzufügen**. Sie können Geräte auf zwei Arten hinzufügen:

    ![Fügen Sie im Dialogfeld Geräte](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **Hochladen einer CSV-Datei mit fortlaufenden Zahlen** – Erstellen einer durch Trennzeichen getrennte Wert (CSV) Liste von zwei Spalten ohne eine Kopfzeile 5000 Geräte oder 5 MB pro CSV-Datei zugänglich.

        |||
        |-|-|
        |&lt;Serielle #1&gt;|&lt;#1-Gerätedetails&gt;|
        |&lt;Serielle #2&gt;|&lt;Device #2-Details&gt;|
        Diese CSV-Datei, die bei der Anzeige in einem Text-Editor wird als angezeigt:

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Manuelles Gerätedetails hinzufügen** - Geben Sie die fortlaufende Zahl und bis zu fünf Geräte Gerätedetails

    > [!NOTE]
    > Wenn Sie später corporate im Besitz Geräte aus der Intune Verwaltung entfernen müssen, müssen Sie in der Gruppe **von iOS Seriennummer** Gerät unter **Corporate Einschreibung Geräte** Gerät Registrierung deaktivieren Intune Seriennummer des Geräts aufheben.  Wenn Intune eine Notfallwiederherstellungsverfahren führt auf oder neben der Uhrzeit, die fortlaufenden Zahlen entfernt wurden, müssen Sie sicherstellen, dass nur aktive Geräte fortlaufenden Zahlen in dieser Gruppe vorhanden sind.

    Wählen Sie auf **Weiter**.

4.  **Wählen Sie Geräte registrieren aus.** Bestätigen Sie die Geräte zu registrieren. Fortlaufende Zahlen bereits registriert oder anderweitig registriert können nicht importiert werden. Wählen Sie **Weiter** aus.

5.  **Profil zuweisen** Geben Sie das Profil, um hinzugefügten Geräte aus der Liste der verfügbaren Profile zuweisen, prüfen Sie den **Registrierungs-Profildetails**, und wählen Sie dann auf **Fertig stellen**. Manuell hinzugefügten Geräte, können alle Registrierungs-Profil zugeordnet werden.

6.  **Exportieren ein Profils für die Bereitstellung auf iOS-Geräte** Wechseln Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com) **Richtlinie** &gt; **Corporate Gerät Registrierung**, und aktivieren Sie das Geräteprofil für mobile Geräte bereitstellen. Wählen Sie **exportieren...** Klicken Sie in der Taskleiste. Kopieren Sie und speichern Sie die **URL des eigenen Profils**. Es werden in Apple-Konfiguration später zu definieren das Intune Profil verwendeten iOS-Geräte hochgeladen werden.
    An den Support Apple-Konfiguration 2 muss die 2.0 Profil URL bearbeitet werden. Ersetzen Sie
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    mit

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   Dieses Profil-URL, der unter Verwendung von Apple-Konfiguration im folgenden Verfahren die Intune Profile untersuchten iOS-Geräte definieren DEP Apple-Dienst hochgeladen werden.



7.  **Vorbereiten des Geräts mit Apple-Konfiguration** iOS-Geräte sind mit dem Mac-Computer verbunden und für die Verwaltung mobiler Geräte registriert.

    1.  Öffnen Sie auf einem Mac **Apple Konfiguration 2**aus. Klicken Sie in der Menüleiste wählen Sie **Apple Konfiguration 2**, und wählen Sie dann auf **Einstellungen**.

         > [!WARNING]
         > Die Geräte werden während der Registrierung Factory Konfigurationen zurückgesetzt. Als bewährte Methode zurücksetzen Sie Gerät und schalten Sie es. Geräte sollte als bewährte Methode beginnen Sie im Bildschirm **Hallo** sein, wenn Sie das Gerät verbinden.

    2. Klicken Sie im Bereich "Einstellungen" Wählen Sie **Server aus** aus, und wählen Sie das "+"-Symbol unten im linken Bereich auf den MDM Server-Assistenten zu starten. Wählen Sie auf **Weiter**.

    3. Geben Sie den **Namen** und den **Registrierungs-URL** für den MDM Server aus Schritt 6 über. Geben Sie für den Registrierungs-URL aus Intune exportierte Registrierungs-Profil-URL ein. Wählen Sie auf **Weiter**.  

       Wenn eine Warnung wird angezeigt, die besagt "Server-URL ist nicht überprüft", "können Sie problemlos die Warnung ignorieren. Um den Vorgang fortzusetzen, wählen Sie **Weiter** , bis der Assistent abgeschlossen ist.

    4.  Herstellen einer Verbindung mit einem USB-Netzwerkadapter im Apple-Computer mit mobile iOS-Geräte.

        > [!WARNING]
        > Die Geräte werden während der Registrierung Factory Konfigurationen zurückgesetzt. Als bewährte Methode zurücksetzen Sie das Gerät und schalten Sie es. Als bewährte Methode sollten Geräte auf dem Bildschirm **Hallo** beim Setup-Assistenten starten.

    5.  Wählen Sie **Vorbereiten**. Im Bereich **Vorbereiten iOS-Gerät** die Option **manuell** aus, und wählen Sie dann auf **Weiter**.

    6. Wählen Sie im Bereich **registrieren in MDM Server** den Servernamen, den Sie erstellt haben, und wählen Sie dann auf **Weiter**.

    7. Klicken Sie im Bereich **Geräte Aufsicht** wählen Sie die Ebene der Aufsicht aus, und wählen Sie dann auf **Weiter**.

    8. **Erstellen einer Organisation** im Bereich Wählen Sie die **Organisation** aus oder erstellen Sie eine neue Organisation, und wählen Sie dann auf **Weiter**.

    9. Klicken Sie im Bereich **Konfigurieren iOS-Setup-Assistenten** wählen Sie die Schritte für den Benutzer aus, und wählen Sie dann **Vorbereiten**. Wenn Sie dazu aufgefordert werden, authentifizieren Sie um Trust Einstellungen aktualisieren.  

    10. Abschluss das iOS-Gerät vorbereiten, können Sie das USB-Kabel trennen.  

8.  **Verteilen von Geräten** Die Geräte können nun für die Registrierung Ihres Unternehmens. Schalten Sie die Geräte, und an Benutzer verteilen. Wenn das Gerät aktiviert ist, wird im Setup-Assistenten starten.



### Siehe auch
[Fertigstellen Sie Geräte registrieren.](get-ready-to-enroll-devices-in-microsoft-intune.md)
