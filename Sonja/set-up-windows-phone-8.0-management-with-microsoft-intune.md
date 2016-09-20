---
title: Einrichten von Windows Phone 8.0 Management | Microsoft Intune
description: "Aktivieren Sie Verwaltung mobiler Geräte (MDM) für Windows Phone 8.0 Geräte mit Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 61e9b6c3-8795-49b0-8ab2-a9a05ee3ea1f
ms.reviewer: priyar
ms.suite: ems
ms.openlocfilehash: c6aff6de22c01db680b5a7bb2c6f68e8185b4350
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einrichten von Device Management für Windows Phone 8.0

Windows Phone 8.0 erfordert ein Zertifikat Symantec zum Installieren der app Intune Unternehmen Portal und Gerät-Verwaltung zulassen. Ein Zertifikat ist ebenfalls Branchen apps Anmeldung erforderlich. Im folgende Thema ist nur für Windows Phone 8.0. Zum Verwalten von Windows Phone 8.1 oder höher, einschließlich 10 Mobile für Windows finden Sie unter [Einrichten von Windows Phone-Registrierung](set-up-windows-phone-management-with-microsoft-intune.md).

> [!IMPORTANT]
> Starten der 2016 September, werden die Unternehmen Portal-app für Windows 8.0 und Windows Phone 8.0 nicht mehr zum Download zur Verfügung.

-   **Windows Phone 8** - Zertifikat erforderlich
-   **Windows Phone 8.1 und 10 unter Windows Mobile** erfordern eine Zertifikat nur, wenn:

    -   Die Unternehmen Portal-app mit Intune bereitstellen möchten.

    -   Sie erhalten-Branchen (Alias "Seite-geladen") apps bereitstellen


![Zertifikat Anforderungen Diagramm](../media/wpcertreqs.png)

  > [!IMPORTANT]
  > Das Zertifikat, den Sie Symantec zum Verwalten von bestimmter Windows und Windows Phone mobile Geräte [regelmäßig erneuert werden muss](renew-a-symantec-code-signing-certificate.md).

Setup-Anforderungen für die Verwaltung von Windows Phone mobiler Geräte hängen davon ab, wie Geräte verwaltet werden.  Festlegen von zwei CNAMEs in die DNS-Registrierung Ihres Unternehmens erleichtert Registrierung verwendet. Wenn Ihre Benutzer die app Unternehmen Portal aus dem Speicher herunterladen, nachdem Sie die DNS-Einstellungen konfiguriert haben müssen Sie nur zum Einrichten von Unternehmens-Portal und informieren der Benutzer zum Registrieren.  Für Windows Phone 8.0 oder Windows Phone 8.1, in der das Unternehmen Portal bereitgestellt werden, benötigen Sie ein Zertifikat Symantec Code-Signieren der app.

## Konfigurieren von Setup Anforderungen für Windows Phone-Verwaltung aktivieren
1.  **Einrichten von Intune** Wenn Sie noch nicht geschehen ist, für die Verwaltung von mobilen Geräten durch [Festlegen der mobilen Gerät Management Zertifizierungsstelle](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) als **Microsoft Intune** und Einrichten von MDM vorbereiten

2.  **Festlegen einen DNS-Alias für die Adresse des Registrierungs-Servers** (optional)

    Ein DNS-Server Alias (CNAME Datensatztyp) macht es einfacher Benutzer aktivierten Geräte durch Auffüllen automatisch den Servernamen während der Registrierung registrieren.

    1.  Klicken Sie in der [Intune-Verwaltungskonsole](http://manage.microsoft.com)auf **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **Windows Phone**.

    2.  Geben Sie die URL der Domäne überprüft der Firmen-Website **überprüft Domänenname angeben** im ein, und klicken Sie dann auf **Testen automatische Erkennung**.

    3.  Erstellen von **CNAME** DNS-Ressourceneinträgen für Domäne Ihres Unternehmens. Die Ressource CNAME-Einträge müssen die folgende Informationen enthalten:

        |Hostname|Verweist auf|TTL|
        |-------------|-------------|-------|
        |enterpriseenrollment.company_domain.com|Enterpriseenrollment-s.manage.microsoft.com |1 Stunde|
        |enterpriseregistration.company_domain.com|enterpriseregistration.Windows.NET|1 Stunde|
        Beispielsweise ist Ihres Unternehmens Website contoso.com, möchten Sie einen CNAME in DNS erstellen, die EnterpriseEnrollment.contoso.com mit manage.microsoft.com umgeleitet. Wenn mehrere überprüfte Domäne vorhanden ist, erstellen Sie einen CNAME-Eintrag für jede Domäne aus.

        -   `enterpriseenrollment-s.manage.microsoft.com` – Unterstützt eine Umleitung zum Dienst Intune mit der Spracherkennung Domäne aus der e-Mail-Domänennamen

        -   `enterpriseregistration.windows.net` – Unterstützt Arbeitsplatz Verknüpfung für mobile Geräte. Darüber hinaus unterstützt bedingten Zugriff für Windows 8.1

    ![Klicken Sie im Dialogfeld Windows Phone Mobile Management des Audiogeräts](../media/windows-phone-enrollment.png)

3.  **Zertifikatverwaltung zur Unterstützung bei der Anmeldung app** [Für Windows Phone 8.0 und Windows Phone 8.1, die Zugriff auf dem Windows Phone-Store und/oder benötigen Branchen apps wird nicht erforderlich ist.]

    Zur Unterstützung der Unternehmen Portal-app für Windows Phone 8.0 und Unternehmen apps für Windows Phone 8.1 bereitstellen, müssen Sie ein **Symantec Enterprise Mobile Code Signaturzertifikat**abrufen. Können kein Zertifikat, das von Ihrer eigenen Zertifizierungsstelle ausgestellt wurde, da Windows Phone Geräte nur das Symantec Zertifikat vertrauenswürdig ist. Dieses Zertifikat ist erforderlich, um:

    -   Melden Sie sich die app Unternehmen Portal für die Bereitstellung auf [!INCLUDE[winphone8_client_1](../includes/winphone8_client_1_md.md)] für die Verwaltung von Registrierung und Telefon

    -   Melden Sie sich company Branchen apps, also [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] können sie Windows Phones bereitstellen

    Die folgenden Schritte aus hilft Ihnen die erforderlichen Zertifikate abrufen und melden Sie sich im Portal app Unternehmen. Benötigen Sie ein Konto für Windows Phone Developer Center und müssen Sie ein Zertifikat Symantec erwerben.

    1.  **Teilnehmen an der Windows Phone Developer Center** Teilnehmen an der [Windows Phone Developer Center](http://go.microsoft.com/fwlink/?LinkId=268442) unter Verwendung Ihres Unternehmens Kontoinformationen bei der Anmeldung bei Ihrem Unternehmenskonto erwerben. Diese Anforderung wird durch ein Mitglied der Geschäftsleitung autorisiert sein, bevor Sie ein Zertifikat zum Signieren von Code erhalten müssen.

    2.  **Besorgen Sie sich einem Unternehmen Symantec Zertifikat** Kaufen Sie ein Zertifikat von der [Symantec-Website](http://go.microsoft.com/fwlink/?LinkId=268441) mit Ihrer Symantec ID. Nachdem Sie das Zertifikat erworben haben, erhalten der corporate Genehmiger wem Sie in Ihrem Windows Phone Developer Center-Konto als verwendet eine e-Mail-Nachricht mit Bitte um Genehmigung der Zertifikatsanfrage. Weitere Informationen zu den Symantec Zertifikat Anforderung, finden Sie unter der [Warum Windows Phone erfordert ein Zertifikat Symantec?](https://technet.microsoft.com/en-us/library/dn764959.aspx#BKMK_Symantec) Häufig gestellte Fragen zu Windows-Gerät Registrierung.

    3.  **Importieren von Zertifikaten** Nachdem die Anforderung genehmigt wurde, erhalten Sie eine e-Mail mit Anweisungen zum Importieren von Zertifikaten. Folgen Sie den Anweisungen in der e-Mail, um die Zertifikate zu importieren.

    4.  **Überprüfen von Zertifikaten importiert** Um zu überprüfen, dass die Zertifikate ordnungsgemäß importiert wurden, wechseln Sie zum **Zertifikat** -Snap-in, mit der rechten Maustaste **Zertifikate**, und wählen Sie **Zertifikate suchen**. Klicken Sie im Feld **enthält** Geben Sie "Symantec", und klicken Sie auf **Jetzt suchen**. Die von Ihnen importierte Zertifikate sollte die Ergebnisse angezeigt werden.

        ![Suchen Sie das Zertifikat Symantec](../media/wit.gif)

    5.  **Exportieren ein signierenden Zertifikats** Nachdem bestätigt wurde, dass die Zertifikate vorhanden sind, können Sie die PFX-Datei zum Anmelden im Portal Unternehmen exportieren. Wählen Sie das Zertifikat Symantec mit **Verwendungszweck** "Code-Signierung." Mit der rechten Maustaste in des Code-signiertes Zertifikats und dann auf **Exportieren**.

        ![Exportieren des Signaturzertifikats](../media/wit-walk-cert2.gif)

        Das **Zertifikat Export-Assistenten**wählen Sie **Ja, privaten Schlüssel exportieren** aus, und klicken Sie dann auf **Weiter**. Select personenbezogene **Exchange – PKCS #12 (. PFX)** , und aktivieren Sie **Alle Zertifikate im Zertifizierungspfad falls möglich einbeziehen**. Schließen Sie den Assistenten. Weitere Informationen finden Sie unter [So exportieren Sie ein Zertifikat mit dem privaten Schlüssel](http://go.microsoft.com/fwlink/?LinkID=203031).

    6.  **Herunterladen, und melden Sie sich die app Unternehmen-Portal**

        Unterstützung für Windows Phone-Registrierung erfordert die app für Windows Phone 8.0 Unternehmen Portal angemeldet und Intune geladen werden.

        1.  **Herunterladen des Unternehmens-Portals** Das [Unternehmen Intune Portal für Windows Phone](http://go.microsoft.com/fwlink/?LinkId=268440) aus dem Download Center herunterladen Ist der Standardspeicherort für die Installation `C:\Program Files (x86)\Microsoft Corporation\Windows Intune Company Portal for Windows Phone`.

        2.  **Herunterladen der Windows Phone SDK 8.0** Laden Sie die [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=615570).

        3.  **Code-Signieren der Portalseite Unternehmen-app** Verwenden der app XAPSignTool heruntergeladen mit dem SDK sich im Portal Unternehmen mit der PFX-Datei, die Sie aus dem Symantec Zertifikat erstellt haben. Weitere Informationen finden Sie unter [So melden Sie eine app Unternehmen mithilfe von XapSignTool](http://go.microsoft.com/fwlink/?LinkID=280195).

    7.  **Die app Unternehmen Portal Intune hochladen** Hochladen der signierten Unternehmen Portal app-Datei und Ihre Code-signiertes Zertifikat die app Ihre Endbenutzer zur Verfügung stellen.

        1.  Klicken Sie in der [Intune-Verwaltungskonsole](http://manage.microsoft.com) auf **Verwaltung** &gt; **Windows Phone**.

        2.  Klicken Sie auf die **Angemeldet App-Datei hochladen** , und melden Sie sich mit Ihrem Administrator Intune-ID an.

        3.  Klicken Sie auf die **Software** Einrichtungsseite für **Angeben des Orts für die Software Setup-Dateien**wechseln Sie zum Code signiert Unternehmen Portal app Speicherort (XAP-Datei für Windows Phone 8.0) oder .appx für Windows Phone 8.1.

            Wenn Sie Intune Auswertung und Hochladen einer Datei Code signiert app in ein Testkonto Intune, deaktivieren Sie das Kontrollkästchen **Unternehmen Portal App von der Stichprobe Symantec Code signiertes Zertifikat Signatur verwenden** .

        4.  Fügen Sie die Zertifikatsdatei (PFX-Datei), die Sie in der **Code-signiertes Zertifikat** exportiert und erstellen Sie ein Kennwort für das Zertifikat.

        5.  Führen Sie auf der Seite **Beschreibung der Software** die Felder Bedenken Sie, dass Benutzer diese Informationen auf ihren Geräten angezeigt, die beim Anzeigen von Details zu der app im Portal Unternehmen ein.

        6.  Schließen Sie den Assistenten. Benutzer, die ein Windows Phone 8.0 Gerät registrieren erhalten jetzt die Unternehmen Portal-app auf ihren Geräten während der Registrierung. Windows Phone 8.1-Benutzer können die app Unternehmen Portal aus der Store Version des Portals Unternehmen installieren.  Wenn Windows Phone 8.1 Geräte aus dem Windows Phone-Speicher blockiert werden, oder Sie die Unternehmen Portal-app mit Intune bereitstellen möchten, müssen Sie herunterladen, und melden Sie sich die app für Windows Phone 8.1 Unternehmen-Portal (SSP.appx).

4.  **Informieren der Benutzer so erhalten Sie Zugriff auf Unternehmensressourcen mit dem Portal für Unternehmen** Die Benutzer müssen wissen, wie ihre Geräte registrieren und was Sie erwartet, nachdem sie in Management eingebunden sind. [Was Ihre Endbenutzer zur Verwendung von Microsoft Intune mitteilen](what-to-tell-your-end-users-about-using-microsoft-intune.md)

## Bereitstellen der Windows Phone 8.1 Unternehmen Portal-app
Sie können die app Unternehmen Portal auf 8.1 für Windows Phone-Geräten mit Intune bereitstellen, statt nur aus dem Windows Phone-Speicher. Sie müssen Windows Phone-Gerät Registrierung mit den Schritten unter Verwendung des Zertifikats Symantec weiterhin aktivieren. Klicken Sie dann müssen Sie die app für Windows Phone 8.1 Unternehmen Portal herunterladen und Signieren es mit dem Symantec Zertifikat.  Dies ist nur erforderlich, wenn die Benutzer den Unternehmen Speicher verwendet nicht und im Unternehmen Portal für Windows Phone 8.1 Geräte bereitstellen möchten.


1.  **Herunterladen des Unternehmens-Portals**

    Herunterladen Sie die [Microsoft Intune Unternehmen Portal App für Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) aus dem Download Center, und führen Sie die selbst extrahierende (.exe) Datei. Diese Datei enthält zwei Dateien:

    -   CompanyPortal.appx– im Unternehmen Portal Installation app für Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1 – ein PowerShell-Skript, die Sie verwenden können, die app-Datei Unternehmen Portal anmelden, damit es in Windows Phone 8.1 Geräte bereitgestellt werden können

2.  **Herunterladen der Windows Phone SDK** [Windows Phone SDK 8.0](http://go.microsoft.com/fwlink/?LinkId=615570) (http://go.microsoft.com/fwlink/?LinkId=268439) herunterladen Sie und installieren Sie das SDK auf Ihren Computer. Dieses SDK ist erforderlich, eine Anwendung Registrierungs-Token zu generieren.

3.  **Generieren einer AETX-Datei** Generieren einer Anwendung Registrierung Token (.aetx) Datei aus der Symantec PFX-Datei AETGenerator.exe, Teil des Windows Phone SDK 8.0 verwenden. Informationen dazu, wie Sie eine Datei AETX erstellen finden Sie unter [wie generiert eine Anwendung Registrierung Token für Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)

4.  **Herunterladen von Windows SDK für Windows 8.1** Herunterladen Sie und installieren Sie der [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Beachten Sie, dass das PowerShell-Skript enthalten, mit der app Unternehmen Portal den standardmäßigen verwendet installieren Speicherort `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Wenn Sie an anderer Stelle installiert haben, müssen Sie die Position in einem Cmdlet-Parameter einschließen.

5.  **Code-Signieren der app mithilfe der PowerShell** Als Administrator öffnen **Windows PowerShell** auf dem Host installiert, mit dem Windows SDK, die Symantec Enterprise Mobile Code Signaturzertifikat, navigieren Sie zu der Datei Sign-WinPhoneCompanyPortal.ps1 und führen Sie das Skript.

    **Beispiel 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    In diesem Beispiel wird der CompanyPortal.appx am C:\temp\ anmeldet und der CompanyPortalEnterpriseSigned.appx erzeugt. Es PFX-Kennwort 1234 verwenden, und lesen die Publisher-ID aus der PFX-Datei. Er liest die Enterprise-ID aus der cert.aetx-Datei ein.

    **Beispiel 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    In diesem Beispiel wird die CompanyPortal.appx am C:\temp\ meldet und der CompanyPortalEnterpriseSigned.appx erzeugt. Es PFX-Kennwort 1234 verwenden, und die angegebene Publisher-ID verwenden.

    **Parameter:**

    -   `-InputAppx` – Die lokale Pfad zu der Datei CompanyPortal.appx in einfache Anführungszeichen. Beispielsweise 'C:\temp\CompanyPortal.appx'

    -   `-OutputAppx` – Die lokale Pfad und den Dateinamen Namen für die signierte Unternehmen Portal-app in einfache Anführungszeichen. Beispielsweise 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` – Die lokale Pfad und Dateiname für die exportierte PFX-Datei des Zertifikats Symantec. Beispielsweise 'C:\signing\cert.pfx'

    -   `-PfxPassword` – Das Kennwort verwendet, um die PFX-Datei in einfache Anführungszeichen signieren. Beispiel für '1234'

    -   `-AetxPath` – Die lokale Pfad der Datei .aetx verwendet wird, für die Enterprise-ID lesen, wenn das Argument "Unternehmens-ID" definiert ist. Entweder dieses Argument oder das Unternehmens-ID bereitgestellt werden. Beispielsweise 'C:\signing\cert.aetx'

    -   `-PublisherId` -Die Publisher-ID des Unternehmens. Wenn Sie nicht vorhanden ist, das Feld 'Betreff' des Symantec Enterprise Mobile Code signieren Zertifikats verwendet wird. Beispielsweise "OID.0.9.2342.19200300.100.1.1=1000000001", "CN ="Test, Inc."Organisationseinheit = Test 1'

    -   `-SdkPath` – Der Pfad zu den Stammordner des Windows SDK für Windows 8.1. Dieses Argument ist optional und hat den Standardwert ${env:ProgramFiles(x86)} \Windows Kits\8.1.

    -   `-EnterpriseId` -Der Enterprise-ID an. Entweder dieses Argument oder das 'AetxPath' bereitgestellt werden. Wenn dieses Argument nicht bereitgestellt wird, wird die Enterprise-ID aus der Datei AETX gelesen. Beispielsweise 1000000001

6.  Bereitstellen von Windows Phone 8.1 Unternehmens app Portal (SSP.appx).

    > [!IMPORTANT]
    > Die ssp.xap und das Unternehmen Portal aus dem Speicher können beide gleichzeitig, installiert die mitunter für Benutzer schwer. Damit alle Benutzer mit der ssp.xap, Erstellen einer gesperrten app Store Version des Portals Unternehmen. Damit alle 8.1 für Windows Phone-Geräten nur die Store Version des Portals Unternehmen verwenden, haben Sie drei Optionen aus:
    >
    > -   Wenn Sie wird nicht Sideload apps und nicht zur Unterstützung von Windows Phone 8.0 müssen, Hochladen Sie nicht der signierte ssp.xap.
    > -   Ändern Sie Wenn Sideloaded apps erforderlich sind, und es sind keine Windows Phone 8-Geräte registrieren, die automatisch erstellte ssp.xap Bereitstellung von "verfügbar" auf "Deinstallieren".
    > -   Wenn Sideloaded apps installiert werden müssen, und Windows Phone 8.0 Geräte registrieren und die ssp.xap erhalten, erstellen eine neue Software-Bereitstellung von der ssp.xap und stellen es mit der Aktion **Deinstallieren** müssen. Windows Phone 8.0 Geräte nicht unterstützen erzwungenen installieren oder Deinstallieren von apps, damit sie die Bereitstellung ignoriert werden kann. Windows Phone 8.1 Geräte unterstützen die Aktion deinstallieren und die ssp.xap werden entfernt.
