---
title: Installieren der PC-Clientsoftware | Microsoft Intune
description: "Verwenden Sie dieses Handbuch Sie Ihre Windows-PCs von der Microsoft-Intune-Clientsoftware verwaltete optimal nutzen können."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: d59a0a08b6d72d2b2cb9462d99fc8e435fe0fba8
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Installieren des Software Intune-Clients auf Windows-PCs
Windows-PCs können nach der Installation von Intune-Clientsoftware registriert sein. Die Intune-Clientsoftware kann auf folgende Weise installiert werden:

- Manuell installiert
- Installieren Sie die Verwendung von Gruppenrichtlinien
- Schließen Sie in ein Datenträgerabbild ein
- Von den Benutzern installiert

## Herunterladen von Intune-Clientsoftware

Alle Methoden, es sei denn, in dem Benutzer die Intune-Clientsoftware selbst, installieren erfordern, dass Sie die Software herunterladen, damit es bereitgestellt werden kann.

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/)auf **Administrator** &gt; **Clientsoftware herunterladen**

  ![Herunterladen des Intune PC-Clients](../media/pc-sa-client-download.png)

2.  Klicken Sie auf der Seite **Clientsoftware herunterladen** klicken Sie auf **Clientsoftware herunterladen** , und speichert das **Microsoft_Intune_Setup.zip** -Paket mit der Software an einem sicheren Ort in Ihrem Netzwerk.

    > [!NOTE]
    > Installationspaket des Intune-Client-Software enthält Informationen zu Ihrem Konto an. Wenn nicht autorisierte Benutzer auf das Installationspaket zugreifen, können diese Computer mit dem Konto registrieren, die durch die eingebetteten Zertifikat dargestellt wird.

3.  Extrahieren Sie den Inhalt des Installationspakets zu die sicheren Ort in Ihrem Netzwerk ein.

    > [!IMPORTANT]
    > Nicht umbenennen oder Entfernen der **ACCOUNTCERT** -Datei, die extrahiert wurden oder die Client-Software-Installation schlägt fehl.

## Manuelles bereitstellen.

1.  Navigieren Sie zu dem Ordner, in dem die Client-Software-Installation-Dateien befinden, und führen Sie dann auf **Microsoft_Intune_Setup.exe** zum Installieren der Clientsoftware, auf einem Computer.

    > [!NOTE]
    > Wenn Sie auf das Symbol in der Taskleiste auf dem Clientcomputer zeigen, wird der Status der Installation angezeigt.

## Mit der Verwendung von Gruppenrichtlinien bereitstellen

1.  Führen Sie in den Ordner mit den Dateien **Microsoft_Intune_Setup.exe** und **MicrosoftIntune.accountcert**den folgenden Befehl aus, um die von Windows Installer-basierten Installationsprogramme für 32-Bit- und 64-Bit-Computer zu extrahieren:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Kopieren der **Microsoft_Intune_x86.msi** -Datei, die Datei **Microsoft_Intune_x64.msi** und die Datei **MicrosoftIntune.accountcert** an einem Netzwerkspeicherort, der von allen Computern zugegriffen werden kann, die die Clientsoftware ist, installiert sein.

    > [!IMPORTANT]
    > Nicht trennen oder Umbenennen von Dateien oder den Client Softwareinstallation schlägt fehl.

3.  Verwenden von Gruppenrichtlinien zum Bereitstellen der Software auf Computern in Ihrem Netzwerk an.

    Weitere Informationen zur Verwendung von Gruppenrichtlinien zur Bereitstellung von Software finden Sie unter der Windows Server-Dokumentation.

## Installieren Sie als Teil eines Bilds
Sie können mithilfe der im folgenden Beispielverfahren als Grundlage Intune-Clientsoftware auf Computern als Teil eines Bilds Betriebssystem bereitstellen:

1.  Kopieren der Client-Installationsdateien, **Microsoft_Intune_Setup.exe** und **MicrosoftIntune.accountcert** in den Ordner **%Systemdrive%\Temp\Microsoft_Intune_Setup** auf dem Computer verweisen.

2.  Das Skript **SetupComplete.cmd** mit dem folgenden Befehl hinzu, um den Registrierungseintrag **WindowsIntuneEnrollPending** zu erstellen:

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  Fügen Sie den folgenden Befehl zu **setupcomplete.cmd** auszuführenden Registrierungs-Paket mit Argument /PrepareEnroll Befehlszeile aus:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > Das Skript **SetupComplete.cmd** ermöglicht Windows Setup Änderungen an das System, bevor ein Benutzer Protokolle vornehmen. Argument **/PrepareEnroll** Befehlszeile kann einen den Computer nach Abschluss der Installation von Windows automatisch in Intune registriert werden.

4.  Setzen Sie in den Ordner **%Windir%\Setup\Scripts** **SetupComplete.cmd** auf dem Computer verweisen.

5.  Zeichnen Sie ein Abbild des Computers ein Bezug und Bereitstellen Sie diese dann auf Zielcomputern.

Bei dem Neustart des Computers zielgerichteten nach Abschluss des Windows-Setup wird der Registrierungsschlüssel **WindowsIntuneEnrollPending** erstellt. Das Registrierungs-Paket überprüft, ob auf der Computer registriert ist. Wenn der Computer registriert ist, wird keine weitere Aktion ausgeführt. Wenn der Computer nicht registriert ist, erstellt das Registrierungs-Paket eine Microsoft Intune automatische Registrierung Aufgabe

Wenn die Aufgabe automatische Registrierung zum nächsten geplanten Zeitpunkt ausgeführt wird, es prüft das Vorhandensein den Registrierungseintrag **WindowsIntuneEnrollPending** und versucht wird, den gezielten PC in Intune registrieren. Wenn die Registrierung aus irgendeinem Grund fehlschlägt, wird die Registrierung das nächste Mal wiederholt, wenn, das der Vorgang ausgeführt wird. Die Wiederholungsversuche weiterhin für einen Zeitraum von einem Monat.

Die Intune automatische Registrierung Aufgabe, den Registrierungseintrag **WindowsIntuneEnrollPending** und das Kontozertifikat werden aus dem betreffenden Computer, wenn die Registrierung erfolgreich war, oder einen Monat gelöscht.

## Weisen Sie Benutzer an sich selbst registrieren.

Benutzer können die Intune-Clientsoftware installieren, indem Sie suchen auf [http://portal.manage.microsoft.com](http://portal..manage.microsoft.com). Wenn das Web-Portal erkennen, dass das Gerät auf einem PC unter Windows ist, er aufgefordert, PC durch Herunterladen des Intune Software Clients registrieren. Nachdem heruntergeladen haben, können Benutzer die Software, um ihre PCs in Management übertragen installieren.

![Aufforderung zum Herunterladen des Software-Clients Intune Intune-Portal](../media/software-client-download.png)

## Überwachen Sie und überprüfen Sie die erfolgreiche Client-Bereitstellung
Verwenden Sie eine der folgenden Verfahren, mit deren Hilfe Sie überwachen und überprüfen Sie die erfolgreiche Client-Bereitstellung.

### So überprüfen die Installation der Clientsoftware von der Microsoft-Intune-Verwaltungskonsole

1.  Klicken Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com/)auf **Gruppen** &gt; **Alle Geräte** &gt; **Alle Computer**.

2.  Einen Bildlauf nach unten die Liste der Computer zu verwaltete Computern zu suchen, das mit Intune kommuniziert werden, oder wenn Sie nach einer bestimmten suchen verwaltete Computer durch Eingeben von Namen des Computers oder einen beliebigen Teil der Namen in das Feld **Suchen Geräte** .

3.  Überprüfen des Status des Computers im unteren Bereich der Verwaltungskonsole, und Beheben von Fehlern.

### Zum Erstellen eines Berichts Computer Inventory, zum Anzeigen aller registriert Computern

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/)auf **Berichte** &gt; **Computer Inventory Berichte**.

2.  Lassen Sie alle Felder auf der Seite **Neue Berichte erstellen** wie die Standardwerte (es sei denn, Sie Filter anwenden möchten), und klicken Sie auf **Bericht anzeigen**.

3.  Die **Computer Inventory** Berichtseite wird geöffnet, in einem neuen Fenster, in dem alle Computer, die erfolgreich registriert sind in Intune angezeigt.

    > [!TIP]
    > Klicken Sie auf eine beliebige Spaltenüberschrift im Bericht, um die Liste nach dem Inhalt dieser Spalte zu sortieren.


### Siehe auch
[Verwalten von Windows-PCs mit Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
[Behandeln von Clients](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune)
