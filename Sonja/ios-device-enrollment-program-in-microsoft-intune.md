---
title: "Apple DEP Management für iOS-Geräte | Microsoft Intune"
description: "Bereitstellen eines Registrierungs-Profil, das durch den iOS-Gerät Registrierungs-Programm (DEP) &quot;über die Luft&quot; gekauft iOS-Geräte registriert wird zum Verwalten von Apple-Geräten."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: fa02292c2cd6a8b627428752d97cf8a04dcc19b0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Registrieren Sie Ihres Unternehmens im Besitz eines Registrierungs-Programm Gerät iOS-Geräte
Microsoft Intune können ein Registrierungs-Profil bereitstellen, die iOS-Geräte gekauft bis Gerät Registrierungs-Programm (DEP) "über die Luft." registriert wird. Das Registrierungs-Paket kann Setup-Assistenten Optionen für das Gerät einbeziehen. Durch die Datenausführungsverhinderung registriert Geräte sein nicht dauerhaften registrierten von Benutzern.

## Apple DEP Management für iOS-Geräte mit Microsoft Intune
Zum Verwalten von corporate im Besitz iOS-Geräte mit Apple Gerät Registrierung Programm (DEP) müssen Sie Ihrer Organisation teilnehmen an Apple DEP und Geräte über das Programm zu erhalten. Details zu den Prozess finden Sie unter: [https://deploy.apple.com](https://deploy.apple.com). Das Programm Vorteile Headset Festlegen von Geräte ohne USB-Verbindung jedem Gerät bei einem Computer an.

Bevor Sie corporate im Besitz iOS-Geräte mit DEP registrieren können, benötigen Sie eine DEP Token von Apple. Dieses Token ermöglicht Intune zu Synchronisierungsinformationen zu DEP teilnehmenden Geräte Besitz Ihres Unternehmens. Außerdem ermöglicht es Intune Registrierungs-Profil Uploads zu Apple ausführen und diese Profile Geräte zuweisen.

1.  **Verwalten von iOS-Geräte mit Microsoft Intune starten** Bevor Sie iOS-Gerät Registrierungs-Programm (DEP) Geräte registrieren können, müssen Sie aktivieren iOS Verwaltungsoption Intune ausführen.

2.  **Abrufen ein Verschlüsselungsschlüssels** Öffnen Sie als Benutzer mit Administratorrechten, die [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com), wechseln Sie zu **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **iOS** &gt; **Gerät Registrierungs-Programm**, und klicken Sie auf **Herunterladen eines Verschlüsselungsschlüssels**. Speichern Sie die Verschlüsselung Schlüssel (.pem) Datei lokal. Die Datei .pem wird verwendet, um die Vertrauensstellung von Apple-Gerät Registrierungs-Programm-Portal anfordern.

      ![Aktualisieren Sie ein Gerät Registrierungs-Programm token](../media/dev-sa-ios-dep.png)

3.  **Ein Gerät Registrierungs-Programm token abrufen** Wechseln Sie zu dem [Gerät Registrierungs-Programm-Portal](https://deploy.apple.com) (https://deploy.apple.com), und melden Sie sich mit Ihrem Unternehmen Apple-ID an. Diese Apple-ID muss in Zukunft So erneuern Sie Ihr DEP Token verwendet werden.

    1.  Wechseln Sie im Portal [Gerät Registrierungs-Programmportal](https://deploy.apple.com) **Gerät Registrierungs-Programm** &gt; **Server verwalten**, und klicken Sie dann auf **Hinzufügen MDM Server**.

    2.  Geben Sie den **MDM Servernamen ein** , und klicken Sie dann auf **Weiter**. Der Servername ist für den Verweis auf den Server MDM zu identifizieren. Es ist nicht Namen oder die URL des Microsoft Intune-Servers.

    3.  Die **Hinzufügen &lt;ServerName&gt; ** Dialogfeld wird geöffnet. Klicken Sie auf **Datei... auswählen** zum Hochladen der Datei .pem, und klicken Sie dann auf **Weiter**.

    4.  Die **Hinzufügen &lt;ServerName&gt; ** **Your Server Token** Link Dialogfeld wird angezeigt. Herunterladen Sie der Datei auf dem Server Token (.p7m) auf Ihren Computer, und klicken Sie dann auf **Fertig**.

    Diese Zertifikatsdatei (.p7m) wird verwendet, um eine Vertrauensstellung zwischen Servern für Intune und Apple Gerät Registrierungs-Programm einrichten.

4.  **Hinzufügen der Datenausführungsverhinderung Token zu Intune** Wechseln Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com)zu **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **iOS** &gt; **Gerät Registrierungs-Programm**, und klicken Sie auf **die Datenausführungsverhinderung Token hochladen**. **Navigieren** Sie zu der Zertifikatsdatei (.p7m), geben Sie Ihre **Apple-ID**, und klicken Sie auf **Hochladen**.

5.  **Hinzufügen von der Richtlinie Ihres Unternehmens Gerät Registrierung** Wechseln Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com)auf **Richtlinie** &gt; **Corporate Gerät Registrierung** , und klicken Sie dann auf **Hinzufügen**.

    Geben Sie **Allgemeine** Details, einschließlich **Name** und **Beschreibung**, geben an, ob das Profil zugewiesen Geräte Zugehörigkeit Benutzer haben oder zu einer Gruppe gehören.
      - **Benutzer Zugehörigkeit verwendendes**: das Gerät müssen mit einem Benutzer zugeordnet werden, während der anfänglichen Installation und dann Zugriff auf Unternehmensdaten und e-Mails als diesem Benutzer zugelassen werden konnte.  **Zugehörigkeit Benutzer** sollten für DEP verwalteten Geräten konfiguriert werden, die für Benutzer angehören, und das Unternehmen-Portal (d. h., um apps zu installieren) verwenden müssen. **Hinweis:** DEP Geräte mit Benutzer Zugehörigkeit unterstützt keine kombinierte Authentifizierung.
      - **Keine Zugehörigkeit Benutzer**: das Gerät ist nicht mit einem Benutzer zugeordnet. Verwenden Sie diese Zuordnung für Geräte, die Aufgaben ausführen, ohne den Zugriff auf lokale Benutzerdaten aus. Mit Anforderung der Benutzer Zugehörigkeit, einschließlich der Unternehmen Portal-app verwendet werden, für die Installation von Branchen apps, Apps funktioniert nicht.

    Sie können auch **Geräte in der folgenden Gruppe zuweisen**. Klicken Sie auf **Select...** , um eine Gruppe auszuwählen.

    [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    Aktivieren Sie als Nächstes **Gerät Registrierungs-Programm Konfigurieren von Einstellungen für diese Richtlinie** zur Unterstützung Datenausführungsverhinderung.

      ![Bereich für Setup-Assistenten](../media/pol-sa-corp-enroll.png)

     Die folgenden Einstellungen sind für DEP verwalteten Geräten verfügbar:

     - **Abteilung** - wird angezeigt, wenn Benutzer Tippen Sie auf "Zur Konfiguration" bei der Aktivierung
     - **Supportrufnummer** – angezeigt, wenn der Benutzer auf die Schaltfläche **Benötigen Sie Hilfe** bei der Aktivierung klickt
     - **Vorbereitung Modus** – dieser Status wird bei der Aktivierung festgelegt und kann nicht geändert werden, ohne das Gerät zurückzusetzen Factory:
        - **Unsupervised** - eingeschränkte Verwaltungsfunktionen
        - **Supervised** - ermöglicht mehr Verwaltungsoptionen und Aktivierung Sperren standardmäßig deaktiviert
     - **Sperren Registrierungs-Profil, um Gerät** – dieser Status bei der Aktivierung festgelegt ist und nicht geändert werden, ohne eine Fabrik zurücksetzen
        - **Deaktivieren** - ermöglicht das Management-Profil über das Menü **Einstellungen** entfernt werden
        - **Aktivieren** - (erfordert **Vorbereitung Modus** = **Supervised**) deaktiviert iOS-Einstellungen, die zum Entfernen des Profils Management ermöglichen können
     - **Optionen des Setup-Assistenten** – diese Einstellungen sind optional, und klicken Sie im Menü **Einstellungen** iOS später konfiguriert werden können
        - **Kennung** - verwendendes Kenncode bei der Aktivierung. Einen Kenncode stets erforderlich, es sei denn, das Gerät wird gesichert werden oder haben Zugriff auf andere Weise (d. h. Kioskmodus, die das Gerät auf eine app beschränkt) gesteuert.
        - **Speicherort Services** – Wenn aktiviert, fordert Setup-Assistenten für den Dienst bei der Aktivierung
        - **Wiederherstellen** - aktiviert, für die Sicherungskopie der iCloud bei der Aktivierung Setup-Assistenten auffordert
        - **Apple-ID** – ein Apple-ID ist erforderlich, um iOS-App Store-apps, einschließlich installiert, indem Sie Intune herunterzuladen. Wenn aktiviert, fordert iOS Benutzer für eine Apple ID Wenn Intune versucht, eine app, ohne eine ID zu installieren.
        - **Allgemeinen Geschäftsbedingungen** -aktiviert, fordert Setup-Assistenten für Benutzer bei der Aktivierung von Apple allgemeinen Geschäftsbedingungen akzeptieren
        - **Tippen Sie auf ID** – Wenn aktiviert, fordert Setup-Assistenten für diesen Dienst bei der Aktivierung
        - **Apple bezahlen** – Wenn Setup-Assistenten fordert für diesen Dienst bei der Aktivierung aktiviert,
        - **Zoom** - ist aktiviert für diesen Dienst bei der Aktivierung Setup-Assistenten auffordert
        - **Siri** – Wenn aktiviert, fordert Setup-Assistenten für diesen Dienst bei der Aktivierung
        - **Diagnose Daten senden an Apple** - aktiviert, für diesen Dienst bei der Aktivierung Setup-Assistenten auffordert
     -  **Aktivieren zusätzlichen Apple-Konfiguration Management** - legen Sie **nicht zulassen** , um zu verhindern, dass bei der Synchronisierung Dateien mit iTunes oder Management über Apple-Konfiguration. Microsoft empfiehlt, Sie legen Sie **nicht zulassen**, exportieren die weitere Konfiguration von Apple-Konfiguration, und klicken Sie dann als benutzerdefinierte iOS Konfigurationsprofil über Intune bereitstellen, anstatt mit dieser Einstellung können manuelle Bereitstellung mit oder ohne ein Zertifikat zulassen.
        - **Nicht zulassen** - wird verhindert, dass das Gerät Kommunikation über USB (deaktiviert paarweise Zuordnung)
        - Ermöglicht **Zulassen** - Gerät Kommunikation über eine USB-Verbindung PC oder Mac
        - Das **Zertifikat erfordern** - ermöglicht Verbindung zu einem Mac mit einem Zertifikat, das in der Registrierung Profil importiert

6.  **Zuweisen von DEP Geräte für die Verwaltung** Wechseln Sie zu dem [Gerät Registrierungs-Programm-Portal](https://deploy.apple.com) (https://deploy.apple.com), und melden Sie sich mit Ihrem Unternehmen Apple-ID an. Wechseln der **Bereitstellung Programm** &gt; **Gerät Registrierungs-Programm** &gt; **Geräte verwalten**. Geben Sie an, wie Sie die **Geräte auswählen**werden, Bereitstellen Sie Geräteinformationen und geben Sie Details an, indem Sie Gerät **Seriennummer**, **Auftragsnummer**oder **CSV-Datei hochladen**. Klicken Sie dann **auf Server zuweisen** und wählen Sie aus der &lt;ServerName&gt; für Microsoft Intune angegeben, und klicken Sie dann auf **OK**.

7.  **Synchronisieren von DEP verwalteten Geräten** Als Administratorbenutzer, öffnen Sie die [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com), wechseln Sie zu **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **iOS** &gt; **Gerät Registrierungs-Programm**, und klicken Sie auf **Jetzt synchronisieren**. Eine Anforderung synchronisieren wird an Apple gesendet. Wechseln Sie zum nach der Synchronisierung DEP verwalteten Geräten angezeigt wird, in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) **Gruppen** &gt; **Alle Geräte** &gt; **Corporate Einschreibung Geräte** &gt; **von iOS fortlaufende Zahl**. Klicken Sie im Arbeitsbereich **durch iOS fortlaufende Zahl** liest der **Status** für verwaltete Geräte "Nicht kontaktiert", bis das Gerät eingeschaltet ist und ausgeführt im Setup-Assistenten wird um das Gerät zu registrieren.

    Um die Einhaltung von Apple für Ausdrücke für die zulässigen DEP Datenverkehr auferlegt Intune die folgenden Einschränkungen:
     -  Eine vollständige DEP Synchronisierung kann nicht mehr als einmal alle 7 Tage ausgeführt werden. Während einer vollständigen Synchronisierung aktualisiert Intune jeder Seriennummer, Apple Intune zugeordnet wurde, ob die fortlaufende zuvor oder nicht synchronisiert wurden. Wenn eine vollständige Synchronisierung 7 Tage nach der vorherigen vollständigen synchronisieren versucht wird, aktualisiert Intune nur fortlaufenden Zahlen nicht bereits im Intune aufgeführt.
     -  Alle synchronisieren Anforderung erhält 10 Minuten. Während dieser Zeit oder bis die Anforderung erfolgreich ist, ist die Schaltfläche "Synchronisieren" deaktiviert.

8.  **Verteilen von Geräten für Benutzer** Ihre Geräte Ihres Unternehmens im Besitz können jetzt an Benutzer verteilt werden. Wenn auf einem iOS-Gerät aktiviert ist aktivieren wird er für die Verwaltung registriert werden, indem Sie Intune.

## Änderungen an zugewiesenen Intune-Gruppe

Im November beginnen, werden Verwaltung von Gruppen zur Azure Active Directory verschoben. Nach der Übergang Azure-Active Directory-Gruppen wird die gruppenzuordnung nicht in den Optionen **Ihres Unternehmens Registrierungs-Profil** angezeigt. Da diese Änderung über eine Reihe von Monaten einsatzbereit wird, wird möglicherweise die Änderung nicht sofort angezeigt. Nachdem Sie auf das neue Portal verschoben, können dynamische Gerät Gruppe Zuordnungen basierend auf den Namen Ihres Unternehmens Registrierungs-Profil definiert werden. Dieses Verfahren ist sichergestellt, dass automatisch zu einer Gerätegruppe zugeordneten Geräte automatisch in der Gruppe mit apps bereitgestellt registrieren, werden. [Weitere Informationen zu Azure-Active Directory-Gruppen](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)

### Siehe auch
[Fertigstellen Sie Geräte registrieren.](get-ready-to-enroll-devices-in-microsoft-intune.md)
