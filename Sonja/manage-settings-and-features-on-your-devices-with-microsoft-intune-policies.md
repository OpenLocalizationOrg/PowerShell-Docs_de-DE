---
title: "Verwalten des Audiogeräts mit Richtlinien | Microsoft Intune"
description: "Verwenden Intune erstellen und Bereitstellen von Richtlinien, die auf Einstellungen und Features steuern registriert Geräten, die Sie verwalten."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 0dc10ea029d078840a584424f7900f340189b960
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien
Microsoft Intune- *Richtlinien* sind Gruppen von Einstellungen, die Features auf mobilen Geräten und Computern steuern. Sie Richtlinien mithilfe von Vorlagen, die enthalten empfohlene oder benutzerdefinierte Einstellungen erstellen und bereitstellen, klicken Sie dann auf Gerät oder Benutzergruppen.

## Typen von Richtlinien

Intune-Richtlinien fallen in die folgenden Kategorien. Die Kategorie, die Sie verwenden wirkt sich auf das Erstellen und die Richtlinie bereitstellen.


- **Konfiguration von Richtlinien**: Diese werden häufig verwendet, um die Sicherheitseinstellungen und Features auf Ihren Geräten verwalten. Verwenden Sie die Informationen in diesem Thema, um weitere Informationen über das Erstellen und Bereitstellen dieser Richtlinien sowie verfügbaren Einstellungen durchsuchen.
- **Compliance-Richtlinien Gerät**: Diese definieren die Regeln und Einstellungen, die einem Gerät mit erfüllen müssen, um von bedingten Access kompatiblen Richtlinien berücksichtigt werden. Sie können auch Compliance-Richtlinien zu überwachen und Behebung die Compliance von Geräten unabhängig von bedingten Zugriff zu verwenden.
Weitere Informationen finden Sie unter [Gerät Compliance-Richtlinien in Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Bedingte Richtlinien**: Diese Richtlinien helfen Ihnen bei sicheren e-Mail und andere Dienste, je nach den Bedingungen, die Sie angeben.
Weitere Informationen finden Sie unter [Einschränken des Zugriffs auf e-Mail und Office 365-Diensten mit Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Corporate Gerät Registrierungs-Richtlinien**: Informationen zu den Registrierungs-Richtlinien Ihres Unternehmens Gerät finden Sie unter [iOS und Mac-Verwaltung mit Microsoft Intune einrichten](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Ressourcen-Richtlinien**: Diese Richtlinien zusammenarbeiten können die Benutzern Zugriff auf Dateien und Ressourcen, die sie tun müssen, seine Arbeit erfolgreich, wo sie sind.
Weitere Informationen finden Sie unter [Aktivieren des Zugriffs auf Firma Ressourcen mit Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


Eine vollständige Liste der Intune-Richtlinien finden Sie unter [Microsoft Intune Richtlinie Bezug](microsoft-intune-policy-reference.md).




## Erstellen einer Konfigurationsrichtlinie

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/), die **Richtlinie** &gt; **Konfigurationsrichtlinien** &gt; **Hinzufügen**.

2.  Wählen Sie die Richtlinie, die Sie wünschen, wählen Sie die empfohlenen Einstellungen für die Richtlinie (sofern verfügbar; Sie diese Einstellungen später ändern zu können) verwenden, oder wählen Sie zum Erstellen einer benutzerdefinierten Richtlinie mit Ihrer eigenen Einstellungen aus.

    > [!TIP]
    > Hilfe bei der Auswahl der richtigen Richtlinie finden Sie im [Microsoft Intune Richtlinie Bezug](microsoft-intune-policy-reference.md).

3.  Wenn Sie bereit sind, wählen Sie die **Richtlinie erstellen**.

4.  Klicken Sie auf der Seite **Richtlinie erstellen** einen Namen und optional eine Beschreibung für die Richtlinie zu konfigurieren.

5.  Konfigurieren Sie die erforderlichen Richtlinieneinstellungen, und wählen Sie dann die **Richtlinie zu speichern**.

    Wenn Sie die Einstellungen für die Informationsverwaltungsrichtlinie Hilfe benötigen, wählen Sie den Richtlinientyp Ihrer aus der folgenden Liste:

    - [Einstellungen für iOS-Geräte](ios-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Android-Geräten](android-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Windows 8 und Windows 8.1-Geräte](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Windows Phone 8.1-Geräte](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Windows 10 Desktop- und mobile Geräte](windows-10-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Geräte mit Windows-Team](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für die Aktualisierung von Windows-edition](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Mac OS X-Geräte](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für die allgemeinen Geschäftsbedingungen Richtlinie](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Allgemeine Einstellungen für mobile Geräte (ältere Versionen)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  Bestätigungsdialogfeld wählen Sie **Ja** jetzt die Richtlinie bereitstellen, oder wählen Sie **Nein** , um die Richtlinie zu erstellen, ohne es aus.

Sie können anzeigen und bearbeiten die neue Richtlinie durch Blättern in den Abschnitten für jeden Richtlinie im Arbeitsbereich **Richtlinie** .

Beim Erstellen einer Richtlinie, die die empfohlenen Einstellungen verwendet, ist der Name der neuen Richtlinie eine Kombination der Vorlagenname, Datum und Uhrzeit aus. Wenn Sie die Richtlinie zu bearbeiten, wird der Name mit Datum und Uhrzeit der Bearbeitung aktualisiert.

Nachdem Sie eine Richtlinie erstellen, sollten Sie normalerweise diese für eine oder mehrere Gruppen oder Benutzer bereitstellen.

> [!TIP]
> Sie bereitstellen nicht alle Richtlinientypen. Beispielsweise wird die Richtlinie mobilen Anwendung Management (MAM) nicht bereitgestellt. Dieser Richtlinie ist stattdessen eine app, die Sie dann bereitstellen zugeordnet.

## Bereitstellen einer Konfigurationsrichtlinie

1.  Klicken Sie im Arbeitsbereich **Richtlinie** wählen Sie die Richtlinie, die Sie bereitstellen möchten, und wählen Sie dann die **Bereitstellung verwalten**.

2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :

    -   Die Richtlinie bereitstellen, wählen Sie eine oder mehrere Gruppen aus, dem Sie die Richtlinie bereitstellen möchten, und wählen Sie dann auf **Hinzufügen** &gt; **OK**.

    -   Wählen Sie **Abbrechen**aus, um das Dialogfeld zu schließen, ohne die Richtlinie bereitstellen.

Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Liste Richtlinien anzeigen.

## Verwalten von Richtlinien

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/)die **Richtlinie**, und navigieren Sie zu, und wählen Sie die Richtlinie, die Sie verwalten möchten.

2.  Wählen Sie eine der folgenden Aktionen aus:

- **Bearbeiten**: Öffnen Sie die Eigenschaften für die ausgewählte Richtlinie, sodass Sie Änderungen vornehmen können.
- **Löschen**: Löscht die ausgewählte Richtlinie.<br>Wenn Sie eine Richtlinie löschen, wird es aus allen Gruppen entfernt, dem sie bereitgestellt wurde.
- **Verwalten der Bereitstellung**: Wählen Sie die Gruppe, die Sie die Richtlinie bereitstellen möchten, und wählen Sie dann auf **Hinzufügen**.


## Häufig gestellte Fragen zu Intune-Richtlinien

### Wie lange dauert es für mobile Geräte, um eine Richtlinie oder apps erhalten, nachdem sie bereitgestellt wurden?
Wenn eine Richtlinie oder eine app bereitgestellt wird, beginnt Intune sofort versucht, das Gerät zu benachrichtigen, das mit dem Intune-Dienst überprüft werden soll. Dadurch gelangen normalerweise weniger als fünf Minuten.

Wenn Sie ein Gerät checken Sie nicht in die Richtlinie erhalten, nachdem die erste Benachrichtigung gesendet wird, macht Intune drei weitere Versuche aus.  Wenn das Gerät offline ist (beispielsweise, es ist deaktiviert oder nicht mit einem Netzwerk verbunden), es möglicherweise nicht die Benachrichtigungen erhalten. In diesem Fall wird das Gerät die Richtlinie bei der nächsten geplanten Einchecken mit dem Intune-Dienst wie folgt angezeigt:

- iOS und Mac OS x alle 6 Stunden.
- Android: Alle 8 Stunden.
- Windows Phone: Alle 8 Stunden.
- Windows RT-Geräten registriert: alle 24 Stunden.
- Windows 8.1 und Windows 10 PCs registriert als Geräte: alle 8 Stunden.

Wenn das Gerät direkt registriert ist, wird die Häufigkeit Einchecken wie folgt häufigere, werden:

- iOS und Mac OS x alle 15 Minuten, damit 6 Stunden, und klicken Sie dann auf alle 6 Stunden.
- Android: Alle 3 Minuten für 15 Minuten, und klicken Sie dann auf alle 15 Minuten für 2 Stunden, und klicken Sie dann auf alle 8 Stunden.
- Windows Phone: 5 Minuten für 15 Minuten, und klicken Sie dann auf alle 15 Minuten für 2 Stunden, und klicken Sie dann auf alle 8 Stunden.
- Windows-PCs als Geräte registriert: alle 3 Minuten für 30 Minuten, und klicken Sie dann auf alle 8 Stunden.

Benutzer können auch öffnen Sie die app Unternehmen Portal und synchronisieren das Gerät sofort für die Richtlinie jederzeit überprüfen.

### Welche Aktionen führen Intune sofort eine Benachrichtigung an ein Gerät senden?
Videogeräte prüfen mit Intune entweder so, wenn sie eine Benachrichtigung, die sie erhalten prüfen oder nur während ihrer regelmäßigen Einchecken erfahren.  Wenn Sie ein Gerät oder ein Benutzer, insbesondere mit einer Aktion wie eine zurücksetzen, sperren, Kenncode zurücksetzen, app, Profil Bereitstellung (Wi-Fi, VPN, e-Mail- usw.) oder Richtlinie Bereitstellung, Intune Zielgruppen werden sofort versuchen, dem Gerät zu informieren, dass es mit den Intune-Dienst erhalten Sie diese Updates überprüfen soll.

Andere Änderungen, wie etwa die Kontaktinformationen im Portal Unternehmen überarbeiten verursachen keine sofortige Benachrichtigung Geräte.

### Wenn Sie mehrere Richtlinien auf dem Benutzer oder der Gerät bereitgestellt werden, wie kann ich feststellen, welche Einstellungen angewendet werden?
Wenn zwei oder mehr Richtlinien für den gleichen Benutzer oder Gerät bereitgestellt werden, wird die Auswertung für die Einstellung angewendet wird Ebene der einzelnen Einstellung umgesetzt:

-   Compliance-Richtlinieneinstellungen haben immer Vorrang vor Konfiguration Richtlinieneinstellungen.

-   Einstellung der am meisten eingeschränkte Compliance wird angewendet, wenn sie diese Einstellung in einer anderen Compliance-Richtlinie ausgewertet wird.

-   Wenn eine Konfigurationsrichtlinie Konflikte mit einer Einstellung in einer anderen Konfigurationsrichtlinie festlegen, wird dieser Konflikt in der Intune Verwaltungskonsole angezeigt. Sie müssen manuell solche Konflikte lösen.

### Was geschieht beim mobilen Anwendung Informationsverwaltungsrichtlinien miteinander in Konflikt stehen? Der wird bei der app angewendet werden?
Konflikt Werte sind die höchsten Einschränkung Einstellungen in einer Richtlinie MAM zur Verfügung, außer für die Anzahl Eintrag Felder (wie PIN vor dem Zurücksetzen versucht).  Die Zahl Eingabefelder werden die gleiche als Werte festgelegt werden, als wäre Sie die Einstellungsoption empfohlene verwenden eine Richtlinie MAM in der Verwaltungskonsole erstellt.

Konflikte auftreten, wenn zwei Richtlinieneinstellungen gleich sind.  Beispielsweise so konfiguriert, dass Sie zwei MAM Richtlinien, die eine Ausnahme bilden jedoch die Einstellung Kopieren/Einfügen identisch sind.  In diesem Szenario wird die Einstellung kopieren und Einfügen der am meisten einschränkenden Wert festgelegt werden, aber der Rest der Einstellungen werden angewendet werden, wie konfiguriert.

Wenn Sie eine Richtlinie wird bei der app bereitgestellt und wirksam und anschließend eine zweite bereitgestellt wird, dauert der ersten Phase Rangfolge und greifen angewendet, während das zweite in Konflikt zeigt. Wenn sie beide zur gleichen Zeit angewendet werden, d. h., es keine vorherige Richtlinie ist, werden sie beide in Konflikt stehen. Die höchsten Einschränkung Werte werden alle in Konflikt stehenden Einstellungen festgelegt werden.

### Was geschieht beim iOS benutzerdefinierte Richtlinien in Konflikt stehen?
Intune wertet den Nutzdaten der Konfiguration Apple-Dateien oder eine benutzerdefinierte Open Mobile Alliance Uniform Resource Identifier (URI-OMA) Richtlinie nicht. Es ist lediglich die Übermittlung Verfahren.

Wenn Sie eine benutzerdefinierte Richtlinie bereitstellen, stellen Sie sicher, dass die konfigurierten Einstellungen nicht in Konflikt mit Compliance, Konfiguration oder anderen benutzerdefinierten Richtlinien sind. Wenn eine benutzerdefinierte Richtlinie mit Einstellungen Konflikte ist die Reihenfolge, in der Einstellungen angewendet werden, zufällig.

### Was passiert bei eine Richtlinie gelöschte oder nicht mehr verfügbar ist?
Wenn Sie eine Richtlinie löschen oder entfernen Sie ein Gerät aus einer Gruppe, die eine Richtlinie bereitgestellt wurde, werden die Richtlinie und Einstellungen vom Gerät entsprechend den folgenden Listen entfernt.

#### Registrierten Geräte

- Wi-Fi, VPN, Zertifikat und e-Mail-Profilen: Diese Profile werden von allen unterstützten registrierten Geräten entfernt.
- Alle anderen Richtlinientypen:
    - **Windows und Android-Geräten**: Einstellungen nicht vom Gerät entfernt werden.
    - **Windows Phone 8.1 Geräte**: die folgenden Einstellungen entfernt werden:
        - Anfordern eines Kennworts zum Entsperren von mobiler Geräten
        - Einfache Kennwörter zulassen
        - Mindestlänge des Kennworts
        - Kennwort geben erforderlich
        - Kennwortablauf (Tage)
        - Denken Sie daran Kennwortverlauf
        - Anzahl der wiederholter Anmeldung Fehler an, bevor das Gerät bereinigt wird
        - Minuten nach der letzten vor dem Kennwort erforderlich ist.
        - Geben Sie erforderliche Kennwort – minimale Anzahl von Zeichensätzen
        - Kamera zulassen
        - Vorschreiben von Verschlüsselung auf mobilen Geräten
        - Wechselmedien zulassen
        - Webbrowser zulassen
        - Anwendungsspeicher zulassen
        - Einen Bildschirmausschnitt zulassen
        - Geografischen Standort zulassen
        - Zulassen von Microsoft-Konto
        - Zulassen von kopieren und einfügen
        - Wi-Fi tethering zulassen
        - Zulassen Sie automatische Verbindung mit Wi-Fi-Hotspots frei
        - Wi-Fi-Hotspot reporting zulassen
        - Zulassen von Factory zurücksetzen
        - Bluetooth zulassen
        - NFK zulassen
        - Wi-Fi zulassen

    - **iOS**: alle Einstellungen werden entfernt, außer:
        - VoIP roaming zulassen
        - Daten roaming zulassen
        - Automatische Synchronisierung beim roaming zulassen

#### Computer mit Windows Intune-Clientsoftware ausgeführt

- **Endpunkt Schutz Einstellungen**: Einstellungen auf ihre empfohlene Werte wiederhergestellt werden. Die einzige Ausnahme ist die **Teilnahme an Microsoft aktiven Protection Service** Einstellung, für die der Standardwert **Nein**ist. Details finden Sie unter [secure Windows PCs mit Endpunkt Schutz für Microsoft Intune helfen](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Software Updates Einstellungen**: Einstellungen sind für das Betriebssystem, das im Standardzustand zurücksetzen. Weitere Informationen finden Sie unter [Beibehalten Windows PCs auf dem neuesten Stand mit Softwareupdates von Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Microsoft Intune Center Einstellungen**: alle supportkontaktinformationen, die von der Richtlinie konfiguriert wurde, wird von allen Computern gelöscht.
- **Windows-Firewall-Einstellungen**: Einstellungen auf die Standardeinstellung für das Betriebssystem zurückgesetzt werden. Details finden Sie unter [secure Windows PCs mit Endpunkt Schutz für Microsoft Intune helfen](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).


### Wie kann ich die Richtlinien auf einem Gerät aus, um sicherzustellen, dass sie aktuell sind aktualisieren (gilt für Windows-PCs, die nur die Intune-Clientsoftware ausgeführt)?

1.  In einem beliebigen Gerätegruppe wählen Sie die Geräte auf dem Sie die Richtlinien aktualisieren möchten, und wählen Sie dann **Remoteaufgaben** &gt; **Richtlinien aktualisieren**.
2.  Wählen Sie in der unteren rechten Ecke der Verwaltungskonsole Überprüfen des Vorgangsstatus Intune **Remoteaufgaben** aus.

### Wo finde ich Hilfe zur Problembehandlung für Richtlinien?

Finden Sie unter [Behandeln von Richtlinien in Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune).
