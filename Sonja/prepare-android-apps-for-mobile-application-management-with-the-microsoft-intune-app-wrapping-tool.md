---
title: Android-apps mit App umbrechen Tool umbrechen | Microsoft Intune
description: "Verwenden Sie die Informationen in diesem Artikel erfahren Sie, wie Ihre Android apps umbrochen ohne Ändern des Codes der App ähneln. Bereiten Sie die apps, damit Sie mobile-app Informationsverwaltungsrichtlinien anwenden können."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
ms.openlocfilehash: 51da3e13af385a3263cc9c6f282d569295b1106b
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Vorbereiten von Android apps für mobile anwendungsverwaltung mit dem Intune App umbrechen Tool
Verwenden Sie das **Microsoft Intune App umbrechen Tool für Android** so ändern Sie das Verhalten Ihrer für Android-Apps, in dem Sie die Features der app konfigurieren, ohne den Code der App ähneln ändern können.

Das Tool ist eine Befehlszeile Windows-Anwendung, die in PowerShell ausgeführt wird und einen Wrapper um die app erstellt. Sobald die app verarbeitet wird, können Sie dann ändern des app Funktionen, die mit [mobilen Anwendung Informationsverwaltungsrichtlinien](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) , die Sie konfigurieren.


Überprüfen Sie vor dem Ausführen des Tools, die [Sicherheit beim Ausführen der app Tool umbrechen](#security-considerations-for-running-the-app-wrapping-tool). Wenn Sie das Tool herunterladen möchten, finden Sie unter [Microsoft Intune App umbrechen Tool für Android](https://www.microsoft.com/download/details.aspx?id=47267).

>[!IMPORTANT]
>Die Version der app umbrechen Tool, mit dem Geräte nicht registriert Intune unterstützt, steht für public Preview-Version. Wenn Sie in der Vorschau öffentlichen teilnehmen möchten, können Sie das Tool für Android von [dieser Seite Github](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview) herunterladen.

Das Szenario wird im Thema [schützen LOB apps auf Geräten, die nicht in Intune registriert](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md) beschrieben.


## Schritt 1 erfüllen die Voraussetzung für die Verwendung der app umbrechen tool

-   Führen Sie die app umbrechen Tool auf einem Windows-Computer unter Windows 7 oder höher.

-   Ihre Eingabe app muss auf eine gültige Android Anwendungspaket mit der Erweiterung **.apk** Datei und:

    -   Kann nicht verschlüsselt werden

    -   Muss nicht bereits von der app umbrechen Tool umbrochen wurde wurden

    -   Muss für Android 4.0 oder höher geschrieben werden

-   Die app muss durch oder für Ihr Unternehmen entwickelt werden. Sie können keine dieses Tool zum Verarbeiten von apps aus dem Google Play Store heruntergeladen verwenden.

-   Um das Tool umbrechen ausführen können, müssen Sie installieren die neueste Version von [Java Runtime-Umgebung](http://java.com/download/) und anschließend sicherstellen, dass die Path-Variable Java **C:\ProgramData\Oracle\Java\javapath** in Ihren Windows-Umgebungsvariablen festgelegt wurde. Weitere Hilfe finden Sie in Ihrer [Java-Dokumentation](http://java.com/download/help/).

    > [!NOTE]
    > In einigen Fällen kann die 32-Bit-Version von Java Arbeitsspeicherprobleme führen. Es empfiehlt sich, dass Sie die 64-Bit-Version zu installieren.

## Schritt 2 installieren die app Tool umbrechen

1.  Vom Microsoft Download Center herunterladen Sie und öffnen Sie die Installationsdatei app Umbruch Tools auf einem Windows-Computer.

2.  Dem Lizenzvertrag, und klicken Sie dann die Installation abzuschließen.

Beachten Sie den Ordner, in dem Sie das Tool installiert. Ist der Standardspeicherort: **c:\Programme Dateien (x86) \Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**.

## Schritt 3 Führen Sie die app Tool umbrechen

1.  Klicken Sie auf der Windows-Computer, in dem Sie die app umbrechen Tool installiert haben, öffnen Sie ein PowerShell-Fenster im Administratormodus.

2.  Importieren Sie aus dem Ordner, in dem Sie das Tool installiert haben die app umbrechen PowerShell-Modul:

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  Führen Sie das Tool mithilfe des Befehls **Aufrufen AppWrappingTool** zusammen mit den folgenden Parametern an.

|Parameter|Weitere Informationen|Beispiele|
|-------------|--------------------|---------|
|**InputPath -**&lt;Zeichenfolge&gt;|Pfad der Quelle Android app (.apk).| |
|**OutputPath -**&lt;Zeichenfolge&gt;|Pfad mit der Android "Ausgabe". Ist dies der gleichen Directory Pfad als InputPath-, schlägt die Verpackung fehl.| |
|**-KeyStorePath**&lt;Zeichenfolge&gt;|Pfad zur Datei Keystore, die die öffentlichen und privaten Schlüssel für die Signatur enthält.| |
|**-KeyStorePassword**&lt;SecureString&gt;|Kennwort zum Entschlüsseln des Schlüsselspeichers. Android erfordert, dass alle Anwendung (.apk) verpackt, um angemeldet sein. Mit der Java-Taste-Tool können Sie die KeyStorePassword generieren, wie im Beispiel dargestellt. Weitere Informationen zum [Schlüsselspeicher](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html).|keytool.exe - Genkey - V - Schlüsselspeicher Keystorefile-Alias ks - Keyalg RSA - Keysize 2048 - Gültigkeit 50000 |
|**-KeyAlias**&lt;Zeichenfolge&gt;|Der Name des Schlüssels zum Signieren verwendet werden.| |
|**-KeyPassword**&lt;SecureString&gt;|Kennwort verwendet, um den privaten Schlüssel entschlüsseln, der zum Signieren verwendet wird.| |
|**-SigAlg**&lt;SecureString&gt;|Name des Signaturalgorithmus zum Signieren verwendet werden. Der Algorithmus muss mit dem privaten Schlüssel kompatibel sein.|Beispiele: SHA256withRSA, SHA1withRSA, MD5withRSA|


**&lt;CommonParameters&gt; ** 
 (optional – unterstützt allgemeinen PowerShell-Parameter wie ausführliche, Debuggen, usw..)

- Eine Liste der allgemeinen Parameter finden Sie im [Microsoft Script Center](https://technet.microsoft.com/library/hh847884.aspx).

- Um finden Sie unter Hilfe für das Tool, geben Sie den Befehl:

    ```
    Help Invoke-AppWrappingTool
    ```

**Beispiel:**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app.wrapped\HelloWorld_wrapped2.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\keystorefile" -keyAlias ks -SigAlg SHA1withRSA -Verbose

Sie werden dann für die **KeyStorePassword** und **KeyPassword**aufgefordert.

Die Umgebrochene app ist generiert und gespeichert, zusammen mit einer Protokolldatei, in der von Ihnen angegebene Ausgabepfad.

## Sicherheit Überlegungen zum Ausführen der app umbrechen tool
So verhindern Sie potenzielle spoofing, Informationsfreigabe und Erweiterung von Berechtigungen:

-   Sicherstellen Sie, dass die Eingabewerte Line-of-Business-Anwendung, Ausgabe Anwendung und Java KeyStore auf demselben Computer sind, wo das app-Umbruch-Tool ausgeführt wird.

-   Importieren Sie die Anwendung Ausgabe der Intune-Verwaltungskonsole auf dem gleichen Computer, auf dem das Tool ausgeführt wird. Finden Sie unter [Keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) Weitere Informationen zu den Java-Keytool.

-   Wenn die Anwendung Ausgabe und das Tool, klicken Sie auf einen Pfad Universal Naming Convention (UNC sind) und Sie nicht das Tool und von Dateien auf dem gleichen Computer ausführen, Konfigurieren der Umgebung benutzerspezifisch secure mithilfe von [Internet Protocol Security (IPsec)](http://en.wikipedia.org/wiki/IPsec) oder [Signaturen (SMB = Server Message Block)](https://support.microsoft.com/en-us/kb/887429).

-   Stellen Sie sicher, dass die Anwendung von einer vertrauenswürdigen Quelle stammt denen die Anwendung auf das Token AAD während der Laufzeit zugreifen können möglicherweise.

-   Secure Ausgabeverzeichnis, das app die Umgebrochene enthält. Erwägen Sie ein Verzeichnis auf Benutzerebene für die Ausgabe.



### Siehe auch
- [Entscheiden Sie, wie apps für mobile anwendungsverwaltung mit Microsoft Intune vorbereiten](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [Verwenden Sie das SDK apps für mobile anwendungsverwaltung aktivieren](use-the-sdk-to-enable-apps-for-mobile-application-management.md)
