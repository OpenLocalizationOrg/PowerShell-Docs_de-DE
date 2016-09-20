---
title: "Verwenden von Remotezurücksetzung zum Schützen von Daten | Microsoft Intune"
description: "Intune bietet selektiven löschen und vollständigen zurücksetzen-Funktionen, die entfernt werden sensibler Daten und zu viele Ihres Unternehmens Ressourcen Zugriff muss entfernt werden."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ms.reviewer: lancecra
ms.suite: ems
ms.openlocfilehash: 309f0701426d6ea22c2c9bd1c3a64393b95c4859
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Schützen von Daten mit vollständigen oder selektiven zurücksetzen mit Microsoft Intune
Gibt an, ob ein Gerät wird nicht mehr benötigt, da aufbereiten wird ist oder wurde entfernt, können Sie apps und Ihre Daten mit Intune verwaltete Geräte zurücksetzen. Dazu bietet Intune selektiven löschen und Funktionen, die vollständige zurücksetzen. Darüber hinaus können Benutzer eine remote-Gerät zurücksetzen vom Unternehmen Intune Portal auf Privat Besitzer Geräten für Intune registriert-Befehl angeben.

  > [!NOTE]
  > In diesem Thema wird nur zum Bereinigen von Geräten von Intune Mobilgerät Management verwaltet werden. Sie können Sie auch [im Portal Azure Vorschau](https://portal.azure.com) zu [Unternehmensdaten von apps zurücksetzen aus](wipe-managed-company-app-data-with-microsoft-intune.md). Sie können auch [zurückziehen Computern, die mit der Intune-Clientsoftware verwaltet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## Vollständige zurücksetzen

**Vollständige zurücksetzen** stellt ein Gerät auf die Standardeinstellungen Factory, entfernen alle Unternehmen und Benutzerdaten und Einstellungen. Das Gerät wird aus Intune entfernt. Vollständige zurücksetzen eignet sich für ein Gerät zurücksetzen, bevor sie einen neuen Benutzer oder Instanzen, in dem das Gerät verloren gegangen sind oder gestohlen wurden, zugewiesen.  **Achten Sie darauf, dass Sie zur Auswahl der vollständigen zurücksetzen. Daten auf dem Gerät nicht wiederhergestellt werden**.


> [!Warning]
> Windows 10 RTM Geräte (d. h. Geräte früher als die Windows-10-Version 1511 mit weniger als 4 GB RAM) möglicherweise nicht zugegriffen werden kann, wenn endgültig gelöscht werden. Um ein Windows-10-Gerät zugreifen, die mehr reagiert, können Sie das Gerät aus einem USB-Laufwerk oder ähnliche problemumgehung starten.

### Wischen Sie Remote ein Gerät aus der Intune-Verwaltungskonsole

1.  Wählen Sie die Geräte demnächst zurückgesetzt werden soll. Sie können sie entweder durch Benutzer oder Gerät suchen.

    -   **Von Benutzer:**

        1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Benutzer**.

        2.  Wählen Sie den Namen des Benutzers, dessen Mobilgerät, die Sie zurücksetzen möchten. Wählen Sie **Eigenschaften anzeigen**aus.

        3.  Klicken Sie auf der Seite **Eigenschaften** des Benutzers wählen Sie **Geräte**, und wählen Sie dann auf den Namen des mobilen Geräts, die Sie zurücksetzen möchten. Verwenden Sie STRG + Klicken Sie auf Mehrfachauswahl Geräte.

    -   **Vom Gerät:**

        1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Mobile Geräte**.

      ![Starten eine Außerkraftsetzungsrichtlinie oder Vorgang zurücksetzen](../media/dev-sa-wipe.png)

        2.  Wählen Sie **Geräte**aus, und wählen Sie dann auf den Namen des mobilen Geräts, die Sie zurücksetzen möchten. Verwenden Sie STRG + Klicken Sie auf Mehrfachauswahl Geräte.

2.  Wählen Sie **Zurückziehen/zurücksetzen**aus.

3.  Eine Meldung angezeigt wird, werden Sie aufgefordert, zu bestätigen, ob Sie das Gerät nicht mehr verwenden möchten.

    -   Wählen Sie **Ja**, um eine **selektive zurücksetzen aus** Ausführen der nur Unternehmen apps und Daten entfernt.

    -   Um eine **vollständige zurücksetzen** ausführen, werden alle apps und der Daten gelöscht, und gibt das Gerät zu Factory-Standardeinstellungen, wählen Sie **das Gerät vor dem Zurückziehen zurücksetzen**aus. Diese Aktion gilt für alle Plattformen außer Windows 8.1. **Entfernte, indem Sie eine vollständige zurücksetzen Daten können nicht wiederhergestellt werden**.

Angegebenen das Gerät eingeschaltet ist und nimmt verbunden, weniger als 15 Minuten für einen Befehl zurücksetzen, um für alle Arten von Gerät auf Objektebene überschrieben werden.

## Selektives zurücksetzen

**Wischen Sie selektive** entfernt Unternehmensdaten mobile-app Management (MAM) Daten einschließlich, sofern zutreffend,-Einstellungen und e-Mail-Profile auf einem Gerät. Selektives zurücksetzen belässt des Benutzers persönliche Daten auf dem Gerät. Das Gerät wird aus Intune entfernt. Die folgenden Tabellen beschreiben-Plattform welche Daten entfernt werden und die Auswirkung auf die Daten, die bleibt auf dem Gerät nach einem selektiven zurücksetzen.

**iOS**

|Datentyp|iOS|
|-------------|-------|
|Apps für Unternehmen und die zugeordneten Daten von Intune installiert.|Apps deinstalliert werden. Unternehmen app Daten werden entfernt.<br /><br />App-Daten aus Microsoft-apps, die mobile-app Management verwenden werden entfernt. Die app wird nicht entfernt.|
|Einstellungen|Konfigurationen, die von der Richtlinie Intune festgelegt wurden, werden nicht mehr umgesetzt, und Benutzer können die Einstellungen ändern.|
|Wi-Fi und VPN einräumen|Entfernt|
|Zertifikat einräumen|Zertifikate entfernt und widerrufen.|
|Management Agent|Management-Profil wird entfernt.|
|E-Mail|E-Mail-Profile, die über Intune bereitgestellt werden entfernt, und Cache-e-Mail auf dem Gerät wird gelöscht.|
|Die Mitgliedschaft beenden Azure-Active Directory (AAD)|AAD Datensatz entfernt|
|Kontakte | Kontakte aus der app direkt auf systemeigenen Adressbuch synchronisiert werden entfernt.  Kontakte aus dem Adressbuch systemeigenen auf eine andere externe Quelle synchronisiert mit können nicht gelöscht. <br /> <br />Aktuell wird nur die Outlook-app unterstützt.

**Android**

|Datentyp|Android|Android Samsung KNOX|
|-------------|-----------|------------------------|
|Weblinks|Entfernt.|Entfernt|
|Nicht verwalteten Google Play apps|Apps und Daten bleiben installiert|Apps und Daten bleiben installiert|
|Nicht verwaltete Textzeile Geschäfts-apps|Apps und Daten bleiben installiert|Apps deinstalliert werden, und lokale app Daten werden als Ergebnis entfernt. Es werden keine Daten außerhalb der app (SD-Karte usw.) entfernt.|
|Verwaltete Google Play apps|App-Daten werden entfernt. App wird nicht entfernt. Durch MAM Verschlüsselung außerhalb der app (SD-Karte usw.) geschützte Daten bleiben verschlüsselte und unbrauchbar, aber Sie werden nicht entfernt.|App-Daten werden entfernt. App wird nicht entfernt. Daten geschützt MAM außerhalb der app (SD-Karte usw.) bleiben verschlüsselt, aber nicht zur Verfügung.|
|Verwalteten Textzeile Geschäfts-apps|App-Daten werden entfernt. App wird nicht entfernt. Durch MAM Verschlüsselung außerhalb der app (SD-Karte usw.) geschützte Daten bleiben verschlüsselte und unbrauchbar, aber Sie werden nicht entfernt.|App-Daten werden entfernt. App wird nicht entfernt. Durch MAM Verschlüsselung außerhalb der app (SD-Karte usw.) geschützte Daten bleiben verschlüsselte und unbrauchbar, aber Sie werden nicht entfernt.|
|Einstellungen|Konfigurationen, die von der Richtlinie Intune festgelegt wurden, sind nicht länger erzwungen und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Richtlinie Intune festgelegt wurden, werden nicht mehr umgesetzt, und Benutzer können die Einstellungen ändern.|
|Wi-Fi und VPN einräumen|Entfernt|Entfernt|
|Zertifikat einräumen|Zertifikate widerrufen, aber nicht entfernt.|Zertifikate entfernt und widerrufen.|
|Management Agent|Gerät Administratorrechte wurde widerrufen.|Gerät Administratorrechte wurde widerrufen.|
|E-Mail|E-Mail erhalten von der Microsoft Outlook-app für Android-app wird entfernt.|E-Mail-Profile, die über Intune bereitgestellt werden entfernt, und Cache-e-Mail auf dem Gerät wird gelöscht.|
|Die Mitgliedschaft beenden Azure-Active Directory (AAD)|AAD Datensatz entfernt|AAD Datensatz entfernt|
|Kontakte | Kontakte aus der app direkt auf systemeigenen Adressbuch synchronisiert werden entfernt.  Kontakte aus dem Adressbuch systemeigenen auf eine andere externe Quelle synchronisiert mit können nicht gelöscht. <br /> <br />Aktuell wird nur die Outlook-app unterstützt.|Kontakte aus der app direkt auf systemeigenen Adressbuch synchronisiert werden entfernt.  Kontakte aus dem Adressbuch systemeigenen auf eine andere externe Quelle synchronisiert mit können nicht gelöscht. <br /> <br />Aktuell wird nur die Outlook-app unterstützt.

**Windows**

|Datentyp|Windows 8.1 (MDM) und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|Windows-10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Apps für Unternehmen und die zugeordneten Daten von Intune installiert.|Durch EFS geschützte Dateien haben ihre Schlüssel zurückgenommen und der Benutzer zum Öffnen der Dateien nicht möglich.|Unternehmen apps werden nicht entfernt.|Apps, die ursprünglich über das Unternehmen Portal installiert deinstalliert werden. Unternehmen app Daten werden entfernt.|Apps deinstalliert werden und Sideloading Tasten werden entfernt.|
|Einstellungen|Konfigurationen, die von der Richtlinie Intune festgelegt wurden, werden nicht mehr umgesetzt, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Richtlinie Intune festgelegt wurden, werden nicht mehr umgesetzt, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Richtlinie Intune festgelegt wurden, werden nicht mehr umgesetzt, und Benutzer können die Einstellungen ändern.|Konfigurationen, die von der Richtlinie Intune festgelegt wurden, werden nicht mehr umgesetzt, und Benutzer können die Einstellungen ändern.|
|Wi-Fi und VPN einräumen|Entfernt|Entfernt|Nicht unterstützt|Entfernt|
|Zertifikat einräumen|Zertifikate entfernt und widerrufen.|Zertifikate entfernt und widerrufen.|Nicht unterstützt|Zertifikate entfernt und widerrufen.|
|E-Mail|Entfernt die e-Mail, die ist, dass EFS aktiviert, der die E-Mail-app für Windows-e-Mails und Anlagen enthält.|Nicht unterstützt|E-Mail-Profile, die über Intune bereitgestellt werden entfernt, und Cache-e-Mail auf dem Gerät wird gelöscht.|Entfernt die e-Mail, die ist, dass EFS aktiviert, der die E-Mail-app für Windows-e-Mails und Anlagen enthält. Entfernt die e-Mail-Konten, die vom Intune bereitgestellt wurden.|
|Die Mitgliedschaft beenden Azure-Active Directory (AAD)|Nein|Nein|AAD Datensatz entfernt|Nicht verfügbar. Windows-10 unterstützt keine Unterstützung selektiven zurücksetzen für Azure Active Directory Geräte beigetreten|

## Wischen Sie Verschlüsselung Dateisystem (EFS)-Inhalte aktiviert
Selektiven Löschen des Inhalts EFS verschlüsselten wird von Windows 8.1 und Windows RT 8.1 unterstützt. Eine selektiven Löschen des Inhalts EFS aktiviert gilt Folgendes:

-   Nur apps und Daten, die durch EFS mithilfe derselben Internetdomäne als Intune-Konto geschützt sind sind Selektives endgültig gelöscht. Weitere Informationen hierzu finden Sie unter [Windows selektiven zurücksetzen, für die Verwaltung Gerät aus](http://technet.microsoft.com/library/dn486874.aspx).

-   Falls vorhanden, dass die zugeordnete EFS Domäne geändert wird sind, können die Änderungen bis zu 48 Stunden vor apps und Daten mithilfe der neuen Domäne können Selektives endgültig gelöscht.

-   Jede Domäne, die mit Intune registriert ist, wird gelöscht.

Die Daten und apps, die aktuell durch EFS selektiven zurücksetzen unterstützt werden:

-   Mail-app für Windows

-   Ordner arbeiten

-   Dateien und Ordner von EFS verschlüsselt. Weitere Informationen finden Sie unter [bewährte Methoden für das Dateisystem verschlüsseln](http://support.microsoft.com/kb/223316).

-   Wenn Ihre Organisation seine Identität in Active Directory verwaltet, muss der Directory-Synchronisierungstool (DirSync) zum von Synchronisierungsinformationen in AAD für EFS selektiven zurücksetzen ordnungsgemäß funktioniert verwendet werden.  Weitere Informationen zum DirSync finden Sie unter [Directory synchronisieren Szenario](http://technet.microsoft.com/library/dn441212.aspx) in Azure Active Directory-Dokumentation.

## Monitor zurückziehen, zurücksetzen und Löschen von Aktionen
So erhalten Sie einen Bericht zu Geräten, die Rente, endgültig gelöscht, oder gelöscht wurden, und wer die Aktion ausgeführt:

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Berichte** &gt; **Gerät Verlauf Berichte**.

2.  Geben Sie ein Start- und Datum für den Bericht, und wählen Sie dann **View-Berichts**.


### Siehe auch
[Deaktivieren von Geräten](retire-devices-from-microsoft-intune-management.md)

[Wischen Sie Windows selektiven für Gerät Datenverwaltung](http://technet.microsoft.com/library/dn486874.aspx)
