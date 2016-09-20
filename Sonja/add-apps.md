---
title: "Hinzufügen von apps | Microsoft Intune"
description: Bevor Sie mit Intune apps bereitstellen beginnen, machen Sie etwas Zeit, um sich mit den in diesem Thema vorgestellten Konzepten vertraut zu machen.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: 93c05ecd0154bb637f421dcc5d7ee56ff8d3ab2d
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Hinzufügen von apps mit Microsoft Intune
Bevor Sie mit Microsoft Intune apps bereitstellen beginnen, nehmen Sie einige Zeit mit den in diesem Thema vorgestellten Konzepten vertraut. Diese Konzepte hilft Ihnen, welche apps zu verstehen, auf welcher Plattform bereitgestellt werden kann. Diese auch Ihnen helfen zu verstehen, die erforderlichen Komponenten, die direkte sein muss, bevor Sie die apps bereitstellen.

## App-Typen, die Sie bereitstellen können

### Software installer

|App-Datentyp|Details|
|----------------|-------|
|**Windows Installer (& #42;. EXE & #42;. MSI)**|Diese Art von app muss Hintergrundinstallation mit ohne Benutzereingabe unterstützen. Der app-Dokumentation sollte die relevanten Befehlszeilenoptionen zum Installieren der im Hintergrund der app (beispielsweise **/q/q**) enthalten. Sie können eine Liste der gebräuchlichsten Befehlszeilenoptionen in [Von Befehlszeilenoptionen für das Tool Microsoft Windows Installer](https://support.microsoft.com/en-us/kb/227091)suchen.<br><br>Gegebenenfalls weitere Dateien und Ordner, die Installationsprogramm des app erfordert müssen aus dem Speicherort verfügbar, die Sie für die app-Setup-Dateien angeben.<br><br>In den meisten Fällen erfordern Windows Installer (MSI-Datei) und Windows Installer-Datei (.msp) Dateien keine Intune Befehlszeilenargumente installieren. Überprüfen Sie Ihre app Dokumentation.<br><br>Wenn Befehlszeilenargumente erforderlich sind, müssen sie als Name eingegeben werden = Wert-Paare (z. B. TRANSFORMS=custom_transform.mst).|
|**App-Pakets für Android (& #42;. Apk)**|Um Android apps bereitstellen zu können, müssen Sie eine gültige .apk Paket verfügen.|
|**App-Pakets für iOS (& #42;. IPA)**|Um iOS-apps bereitstellen zu können, müssen Sie eine gültige .ipa Paket verfügen.<br><br>Das Paket .ipa von Apple signiert werden muss, und das Ablaufdatum im provisioning Profil muss gültig sein. Intune kann Enterprise Zertifikat iOS Applikationen verteilen.<br><br>Nicht alle Apple Developer Zertifikat apps werden unterstützt.<br><br>Ihr Unternehmen muss für den iOS Developer Enterprise-Programm registriert sein.<br><br>Stellen Sie sicher, dass der Firewall Ihrer Organisation Zugriff auf die iOS bereitgestellt und Zertifizierung Websites ermöglicht.<br><br>Sie benötigen keine Manifestdatei (.plist), mit der app bereitstellen.|
|**Windows Phone-app-Pakets (& #42;. XAP-, .appx, .appxbundle)**|Um apps bereitstellen zu können, benötigen Sie ein Zertifikat Enterprise mobilen Code signieren. Weitere Informationen finden Sie unter [Einrichten der Verwaltung von Windows Phone mit Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md).|
|**Windows-app-Pakets (.appx, .appxbundle)**|Um apps bereitstellen zu können, benötigen Sie ein Zertifikat Enterprise mobilen Code signieren. Weitere Informationen finden Sie unter [Einrichten der Verwaltung von Windows-Gerät mit Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).|
|**Windows Installer bis MDM (& #42;. MSI)**|Verwenden Sie diese app zu erstellen und Bereitstellen von Windows Installer-basierten apps für registrierten PCs, die Windows-10 ausgeführt werden. Diese PCs werden durch Verwaltung mobiler Geräte (MDM) verwaltet.<br /><br />Sie können nur eine einzelne Datei mit der Erweiterung MSI-Datei hochladen.<br><br>Für die app Erkennung werden Produktcode und Produktversion der Datei verwendet.<br><br>Das Standardverhalten des Neustart der app wird verwendet werden. Intune wird dadurch nicht gesteuert.<br><br>MSI-Paketen pro Benutzer werden für einen einzelnen Benutzer installiert sein.<br><br>Pro Computer MSI-Paketen werden für alle Benutzer auf dem Gerät installiert werden.<br><br>MSI-Pakete sind derzeit nur für alle Benutzer auf dem Gerät installiert werden.<br><br>App-Updates werden unterstützt, wenn der MSI-Produktcode jeder Version identisch ist.<br>
Alle Software Installer app Typen werden in der Cloud Speicherplatz hochgeladen.

### **Externer Link**
Verwenden Sie eine externe Verknüpfung bei a:
- Die URL, die Benutzer eine app aus einer app Store herunterladen kann.
- Link zu einer webbasierten app, die im Webbrowser ausgeführt wird.

Apps basierend auf externe Links werden nicht in die Speicherplatz verschwendet Intune Cloud gespeichert.
### **IOS-app aus dem app Store verwaltet**
Sie können verwaltete iOS-apps zum Verwalten und Bereitstellen von iOS-apps, die aus dem app Store kostenlos sind verwenden. Sie können auch verwaltete iOS-apps verwenden, um [Informationsverwaltungsrichtlinien mobilen Anwendung](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) [kompatibel apps](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) zuzuordnen, und überprüfen deren Status in der Verwaltungskonsole.<br /><br />Verwaltete iOS, apps nicht in die Speicherplatz verschwendet Intune Cloud gespeichert sind.

> [!TIP]
> Optionen für mobile Geräte sind nicht verfügbar, bis Sie [den MDM Zertifizierungsstelle festlegen](get-ready-to-enroll-devices-in-microsoft-intune.md) , dass Intune.

## Intune Softwarepublisher
Die Microsoft Intune Software Publisher startet beim Hinzufügen oder Ändern von apps aus der Intune-Verwaltungskonsole auf. Herausgeber Sie wählen und konfigurieren einen Software Installer Typ, die entweder wird:

- Hochladen von apps (Programme für Computer oder apps für mobile Geräte) um in Intune Cloud-Speicher gespeichert werden.
- Link zu einer Onlinespeicher oder Webanwendung.

Bevor Sie beginnen, die den Herausgeber der Software verwenden, müssen Sie die Vollversion von [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851)installieren. Nach der Installation müssen Sie Ihren Computer neu starten, bevor der Herausgeber der Software ordnungsgemäß geöffnet wird.

## Cloud-Speicherplatz
Alle apps, die Sie erstellen, indem Sie mit der Software Installer Installationstyp (beispielsweise einer Line-of-Business-app) sind eine separate und Intune Microsoft Cloud-Speicher geladen. Ein Testabonnement von Intune enthält 2 Gigabyte (GB) cloudbasierte Datenspeicher, der zum Speichern von verwalteten apps und Updates verwendet wird. Ihr vollständige Abonnement umfasst 20 GB an Speicherplatz.

Sie können sehen, wie viel Speicherplatz Sie in den Knoten **Speicher verwenden** des Arbeitsbereichs **Administrator** verwenden.

Anforderungen für Cloud Speicherplatz werden wie folgt aus:

-   Alle Dateien der app-Installation muss sich in demselben Ordner.
-   2 GB ist die maximale Dateigröße für eine Datei, die Sie hochladen.


## Unterstützung von Universal Windows-Plattform (UWP) apps
Windows 10 PCs erfordern eine Sideloading-Taste, um die Branchen apps zu installieren. Jedoch müssen der Registrierungsschlüssel **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** Wert **1** Sideloading aktivieren.

Wenn Sie diesen Registrierungsschlüssel konfiguriert ist, wird automatisch auf Intune diesen Wert auf **1** das erste Mal festgelegt Sie eine app für das Gerät bereitstellen. Wenn Sie diesen Wert auf **0**festgelegt, Intune den Wert nicht automatisch ändern, und die Bereitstellung von Branchen apps schlägt fehl.

Universal Windows-Plattform Branchen apps müssen mit einem Zertifikat signieren von Code angemeldet sein, die auf jedem Gerät vertrauenswürdig ist, der die app bereitgestellt wird. Sie können ein Zertifikat aus einer für Öffentliche Key Infrastruktur oder ein Zertifikat aus ein Zertifikat einer Drittanbieter-öffentliche Stammzertifizierungsstelle auf dem Gerät installiert.

Auf 10 unter Windows Mobile Geräte können Sie nicht Symantec Code-Signaturzertifikat universeller **.appx** apps anmelden. **XAP** -apps, und auch **.appx** -Paketen speziell für Windows Phone 8.1, die Sie auf 10 unter Windows Mobile Geräte installieren möchten, müssen Sie einen Code Symantec-Signaturzertifikat verwenden.

## Nächste Schritte

Sie müssen in der Intune Verwaltungskonsole apps hinzufügen, bevor Sie bereitgestellt werden können. Das Hinzufügen von apps für [Geräte registriert](add-apps-for-mobile-devices-in-microsoft-intune.md) oder [Windows-PCs, die Sie mit der Intune-Clientsoftware verwalten](add-apps-for-windows-pcs-in-microsoft-intune.md)können.
