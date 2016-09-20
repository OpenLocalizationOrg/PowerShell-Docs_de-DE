---
title: "Hinzufügen von apps für Windows-PCs, auf denen den Software Intune-Client ausführen | Microsoft Intune"
description: "Verwenden Sie die Informationen in diesem Artikel erfahren Sie, wie apps für Windows-PCs zum Intune hinzuzufügen, bevor Sie diese bereitstellen."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 33ef6a417c38ab04095afc8fb7573ea92253f229
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Hinzufügen von apps für Windows-PCs, die den Software Intune-Client ausgeführt werden.

Verwenden Sie die Informationen in diesem Artikel erfahren Sie, wie apps zum Intune hinzuzufügen, bevor Sie diese bereitstellen.

> [!IMPORTANT]
> Die Informationen in diesem Thema hilft Ihnen das Hinzufügen von apps für Windows-PCs, die Sie mithilfe des Intune Software Clients verwalten. Wenn Sie apps für registrierten Windows-PCs und andere mobile Geräte hinzufügen möchten, finden Sie unter [Hinzufügen von apps für mobile Geräte in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).


## Hinzufügen der app
Sie verwenden die Intune Software Publisher konfigurieren Sie die Eigenschaften der app und zum Speicherplatz verschwendet Cloud hochladen können mithilfe des folgenden Verfahrens aus:

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Apps** &gt; **Apps hinzufügen** , um die Intune Software Publisher zu starten.

    > [!TIP]
    > Möglicherweise müssen Sie Ihren Benutzernamen Intune eingeben und Kennwort ein, bevor die Publisher wird gestartet.

2.  Klicken Sie auf der Seite **Software einrichten** des Herausgebers, klicken Sie unter **Wählen Sie aus, wie diese Software Geräte zur Verfügung gestellt werden**wählen Sie **Software Installer**, und geben Sie dann:

    - **Wählen Sie die Software Installer-Dateityp aus**. Dies zeigt an, den Typ der Software, die Sie bereitstellen möchten. Wählen Sie bei einem Windows-PC **Windows Installer**ein.
    - **Angeben des Orts für die Software Setup-Dateien**. Geben Sie den Speicherort der Installationsdateien, oder wählen Sie **Durchsuchen** , um die Position aus einer Liste auszuwählen.
    - **Zusätzliche Include-Dateien und Unterordner im gleichen Ordner**. Einige Software, die mit Windows Installer erfordert Hilfsdateien. Diese sind in der Regel in denselben Ordner wie die Installationsdateien gefunden. Wählen Sie diese Option, wenn Sie auch diese Hilfsdateien bereitstellen möchten.

    Beispielsweise, wenn Sie eine app, die mit dem Namen Application.msi Sie Intune veröffentlichen möchten, die Seite würde so aussehen: ![Software Einrichtungsseite des Herausgebers](./media/publisher-for-pc.png)

   Diese Installationsart verwendet einige der Speicherplatz verschwendet Cloud.

3.  Konfigurieren Sie die folgenden Einträge, klicken Sie auf der Seite **Beschreibung der Software** .

    > [!NOTE]
    > Je nach der Installer-Datei, die Sie verwenden, einige dieser Werte möglicherweise automatisch eingegeben wurden, oder möglicherweise nicht angezeigt.

    - **Publisher**. Geben Sie den Namen des Herausgebers der app aus.
    - **Namen**. Geben Sie den Namen der app aus, wie er im Portal Unternehmen dargestellt wird.<br />Stellen Sie sicher, dass alle Namen der app, mit denen Sie eindeutig sind. Wenn Sie den Namen der gleichen Anwendung zweimal vorhanden ist, wird nur von einem der apps für Benutzer im Unternehmen Portal angezeigt.
    - **Beschreibung**. Geben Sie eine Beschreibung für die app aus. Dies wird Benutzern im Unternehmen Portal angezeigt.
    - **Informationen zu URL** (optional). Geben Sie die URL einer Website, die Informationen über diese app enthält. Die URL wird für die Benutzer im Unternehmen Portal angezeigt.
    - **Datenschutz-URL** (optional). Geben Sie die URL einer Website, die Informationen zum Datenschutz für diese app enthält. Die URL wird für die Benutzer im Unternehmen Portal angezeigt.
    - **Kategorie** (optional). Wählen Sie eine der Kategorien integrierten app aus. Dies wird erleichtern für Benutzer die app beim Durchsuchen des Portals Unternehmen zu suchen.
    - **Symbol** (optional). Hochladen Sie ein Symbol, das die app zugeordnet werden soll. Dies ist das Symbol, das mit der app angezeigt wird, wenn Benutzer im Portal Unternehmen navigieren.

4.  Wählen Sie auf der Seite **Anforderungen** die Anforderungen an die erfüllt sein müssen, bevor die app installiert werden kann. Wählen Sie aus:

    - **Architektur**. Wählen Sie aus, ob diese app auf einem 32-Bit-, 64-Bit- oder beiden Betriebssystemen installiert werden kann.
    - **Betriebssystem**. Wählen Sie das minimale Betriebssystem auf dem diese app installiert werden kann.

5.  Klicken Sie auf der Seite **Erkennung Regeln** können Sie Regeln zum Ermitteln, ob die app, die Sie konfigurieren bereits auf einem PC installiert wurde konfigurieren. Alternativ können Sie die Regeln für die Erkennung um automatisch alle zuvor installierten Versionen der app zu überschreiben. Diese Option ist für Windows Installer (nur .exe-Dateien).

    Regeln, die Sie konfigurieren können, sind:
    - **Datei vorhanden ist**. Geben Sie den Pfad zu der Datei, die Sie ermitteln möchten. Sie können unter **ProgramFiles%** suchen (die **Programmdateien**durchsucht\&Lt; Pfad&gt; und **Programmdateien (x86)**\&Lt; Pfad&gt;) auf dem PC oder dem **Systemlaufwerk %** (die suchen aus dem Stammordner Laufwerk des PCs, normalerweise Laufwerk C).
    - **MSI-Produktcode vorhanden ist**. Wählen Sie **Durchsuchen** , wählen Sie die Windows Installer (MSI)-Datei, die Sie ermitteln möchten.
    - **Registrierungsschlüssel vorhanden ist**. Angeben ein Registrierungsschlüssels deaktiviert, die mit beginnt **HKEY_LOCAL_MACHINE\**. Beide 32-Bit- und 64-Bit-Registrierungspfade sind durchsucht. Wenn der Schlüssel, den Sie angegeben in beiden Speicherorten vorhanden ist, ist die Erkennung Regel erfüllt.

    Wenn die app eine Regel, die Sie konfiguriert haben erfüllt, wird es nicht installiert werden.

6.  Typ nur (MSI- und .exe) für das **Windows Installer** -Datei: Wählen Sie aus, ob Sie optional Befehlszeilenargumente für das Installationsprogramm angeben möchten, klicken Sie auf der Seite **Befehlszeilenargumente** . Einige Installer unterstützen möglicherweise das Argument **/q/q** , im Hintergrund mit keine Eingriff zu installieren.

7.  Für das **Windows Installer** -Dateityp nur (nur .exe): auf der Seite **Codes zurückgeben** , können Sie neue Fehlercodes, die Intune interpretiert, wenn die app auf einem verwalteten Windows-PC installiert wurde hinzufügen.

    Standardmäßig verwendet Intune Industriestandard Absenderadresse Codes Ausfall oder Erfolg einer app-Paket Installation melden: **0** (Erfolg) oder **3010** (Erfolg mit Neustart). Sie können auch eigene Absenderadresse Codes zu dieser Liste hinzufügen. Wenn Sie eine Liste der Rückgabetyp Codes angeben und die app-Installation gibt einen Code, der nicht in der Liste enthalten ist, wird es als Fehler interpretiert.

8.  Überprüfen Sie die Informationen, die Sie angegeben haben, klicken Sie auf der Seite **Zusammenfassung** . Wenn Sie bereit sind, wählen Sie **Hochladen**.

9. Wählen Sie **Schließen** auf Fertig stellen.

Die app wird auf dem Knoten **Apps** des Arbeitsbereichs **Apps** angezeigt.

## Nächste Schritte

Nachdem Sie eine app erstellt haben, besteht der nächste Schritt bereitzustellen. Wenn Sie mehr erfahren möchten, finden Sie unter [Bereitstellen von apps in Microsoft Intune](deploy-apps.md).
