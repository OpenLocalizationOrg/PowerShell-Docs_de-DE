---
title: "Hinzufügen von apps für registrierten Geräte | Microsoft Intune"
description: "Bevor Sie eine app bereitstellen können, müssen Sie es Intune hinzufügen. Und klicken Sie dann in der Verwaltungskonsole Intune verfügbar ist, wo Sie bereitstellen und verwalten können."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: 0951a8c8ae635fed089e7bbf87018282a73daf74
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Hinzufügen von apps für registrierten Geräte zur Intune

Bevor Sie eine app verwalten oder bereitstellen können, müssen Sie es Microsoft Intune hinzufügen. In diesem Thema wird gezeigt, wie Sie apps für registrierten Geräte hinzufügen.


> [!IMPORTANT]
> Die Informationen in diesem Thema hilft Ihnen das Hinzufügen von apps, denen Sie bereitstellen möchten Geräte registriert und registriert die Windows-PCs. Wenn Sie apps für Windows-PCs zu addieren, die Sie mithilfe der Intune-Clientsoftware verwalten möchten, finden Sie unter [Hinzufügen von apps für Windows-PCs in Microsoft Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## Hinzufügen der app
Verwenden Sie die Intune Software Publisher zum Konfigurieren der Eigenschaften der app und gegebenenfalls auf Speicherplatz verschwendet Cloud hochladen. Gehen Sie folgendermaßen vor:

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Apps** &gt; **Apps hinzufügen** , um die Intune Software Publisher zu starten.

    > [!TIP]
    > Möglicherweise müssen Sie Ihren Benutzernamen Intune eingeben und Kennwort ein, bevor die Publisher wird gestartet.

2.  Wählen Sie eine der folgenden Optionen für **Wählen Sie aus, wie diese Software Geräte zur Verfügung gestellt werden**, auf der Seite **Software einrichten** des Herausgebers:
    - **Software Installer**, für apps mit der Erweiterung **MSI** oder **.exe**:
        - **Wählen Sie die Software Installer-Dateityp aus**. Dies zeigt an, den Typ der Software, die Sie bereitstellen möchten. Beispielsweise, wenn Sie eine app für iOS installieren möchten, wählen Sie **App-Pakets für iOS (& #42;. IPA-Datei)**.
        - **Angeben des Orts für die Software Setup-Dateien**. Geben Sie den Speicherort der Installationsdateien, oder wählen Sie **Durchsuchen** , um die Position aus einer Liste auszuwählen.
        - **Zusätzliche Include-Dateien und Unterordner im gleichen Ordner**. Diese Option ist für den **Windows Installer** -Dateityp nur.<br>Einige Software, die mit Windows Installer erfordert Hilfsdateien, die in der Regel in denselben Ordner wie die Installationsdateien befinden. Wählen Sie diese Option, wenn Sie auch diese Dateien bereitstellen möchten.<br>Diese Installationsart verwendet einige der Speicherplatz verschwendet Cloud.

  -   **Externer Link**für apps, die Sie erstellen, indem Sie einen Link zu einer app Store möchten:

        - **Geben Sie die URL**. Geben Sie die URL für eine der folgenden Aktionen aus:
            - Die app Store URL der app, die Sie bereitstellen möchten. Wenn Sie die Microsoft Remote Desktop-app für Android bereitstellen möchten, geben Sie beispielsweise **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android**.<br>Verwenden Sie die URL der app finden Sie ein Suchmodul, um der Store-Seite zu finden, die die app enthält. Die Remote Desktop-Anwendung finden möchten, können Sie zum Beispiel für **Microsoft Remote Desktop Android**suchen.
            - Eine Website. Intune wird ein Verknüpfungssymbol auf der Website auf dem Gerät (bekannt als Webclip) bereitzustellen.
            - Eine app im Web. Intune wird ein Verknüpfungssymbol für die app auf dem Gerät bereitstellen.
        - **Erfordern einen verwalteten Browser, um diesen Link (Android und iOS nur) zu öffnen**. Wenn Sie einen Link zu einer Website oder Web app für Benutzer bereitstellen, werden sie können sie nur in den verwalteten Intune-Browser zu öffnen. Diese Browser muss auf ihrem Gerät installiert sein.<br>Weitere Informationen zur verwalteten Browser finden Sie unter [Verwalten Internet Access verwenden Browserrichtlinien mit Microsoft Intune verwaltet](manage-internet-access-using-managed-browser-policies.md).<br>Diese Installationsart verwendet nicht Speicherplatz verschwendet Cloud.

  -   **Verwaltete iOS-app aus dem app Store**speichern kostenlos apps aus dem iTunes, die mit mobilen Anwendung Informationsverwaltungsrichtlinien (MAM) verwaltet werden sollen:

        - **Geben Sie die URL**. Geben Sie die app Store-URL der app, die Sie bereitstellen möchten. Wenn Sie die Microsoft Arbeit Ordner app für iOS bereitstellen möchten, geben Sie beispielsweise **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8**.<br>Diese Installationsart verwendet nicht Speicherplatz verschwendet Cloud.

        Wenn Sie die app Microsoft Word aus dem iTunes-Store Geräte bereitstellen möchten, würde die Seite beispielsweise wie folgt aussehen:

        ![Intune Software Publisher](./media/publisher-for-mobile.png)

3.  Konfigurieren Sie auf der Seite **Software Beschreibung** Folgendes ein:

    > [!TIP]
    > Je nach Typ Installer, den Sie verwenden, einige dieser Werte möglicherweise automatisch eingegeben wurden.

    - **Publisher**. Geben Sie den Namen des Herausgebers der app aus.
    - **Namen**. Geben Sie den Namen der app aus, wie er im Portal Unternehmen dargestellt wird.<br>Stellen Sie sicher, dass alle Namen der app, mit denen Sie eindeutig sind. Wenn Sie den Namen der gleichen Anwendung zweimal vorhanden ist, wird nur von einem der apps für Benutzer im Unternehmen Portal angezeigt.
    - **Beschreibung**. Geben Sie eine Beschreibung für die app aus. Dies wird Benutzern im Unternehmen Portal angezeigt.
    - **URL für Software Informationen**. Dies ist nur verfügbar, wenn Sie **Software Installer**ausgewählt haben. Geben Sie optional die URL einer Website, die Informationen über diese app enthält. Die URL wird für die Benutzer im Unternehmen Portal angezeigt.
    - **Datenschutz-URL**. Dies ist nur verfügbar, wenn Sie **Software Installer**ausgewählt haben. Geben Sie optional die URL einer Website, die Informationen zum Datenschutz für diese app enthält. Die URL wird für die Benutzer im Unternehmen Portal angezeigt.
    - **Kategorie** (optional). Wählen Sie eine der Kategorien integrierten app aus. Dies wird erleichtern für Benutzer die app beim Durchsuchen des Portals Unternehmen zu suchen.
    - **Dies als bereitgestellten app anzeigen, und markieren Sie es im Portal für Unternehmen**. Anzeigen der app markante auf der Hauptseite des Portals Unternehmen beim Durchsuchen von Benutzern für apps
    - **Symbol** (optional). Hochladen Sie ein Symbol, das die app zugeordnet werden soll. Dies ist das Symbol, das mit der app angezeigt wird, wenn Benutzer im Portal Unternehmen navigieren.

        In diesem Beispiel so konfiguriert, dass Sie eine Beschreibung für die Microsoft Word-app für iOS:

        ![Beispiel für eine Beschreibung der Software](./media/ios-software-description.png)

4.  Wählen Sie auf der Seite **Anforderungen** die Anforderungen an die erfüllt sein müssen, bevor die app auf einem Gerät installiert werden kann. Für eine app-Pakets für iOS, können Sie beispielsweise die Mindestversion von iOS erforderlich auswählen. Darüber hinaus können Sie den Typ des Geräts auswählen, die sie, wie einem iPhone oder iPad sein müssen.

    > [!TIP]
    > Die **Anforderungen** Seite ist nicht für alle Arten von apps angezeigt.

5.  Weiteren werden Seiten des Assistenten angezeigt, wenn Sie den **Windows Installer** -Dateityp auswählen. Dieser Dateityp wird verwendet, wenn Sie die Software auf Windows-10-PCs bereitstellen oder höher, die mit Intune registriert sind.

6.  Überprüfen Sie die Informationen, die Sie angegeben haben, klicken Sie auf der Seite **Zusammenfassung** . Wenn Sie bereit sind, wählen Sie **Hochladen**.

7.  Wählen Sie **Schließen** auf Fertig stellen.

Die app wird auf dem Knoten **Apps** des Arbeitsbereichs **Apps** angezeigt.

## Beispiel – Bereitstellen von MSI-Anwendungen in Windows-10-Geräte
In diesem Video vier-Minuten erfahren Sie Informationen zum Windows Installer (MSI-Datei) von Applications zu registrierten Geräte bereitstellen, die Windows-10 ausgeführt werden.<br><br>

<iframe src="https://channel9.msdn.com/Series/How-to-Control-the-Uncontrolled/6--How-to-Deploy-MSI-Applications-to-Windows-10-Using-Intune-and-Mobile-Device-Management-MDM/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>

## Nächste Schritte

Nachdem Sie eine app erstellt haben, besteht der nächste Schritt bereitzustellen. Wenn Sie mehr erfahren möchten, finden Sie unter [Bereitstellen von apps in Microsoft Intune](deploy-apps.md).
