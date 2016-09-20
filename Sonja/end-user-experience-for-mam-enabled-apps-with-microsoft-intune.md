---
title: "Endbenutzer für MAM aktiviert apps | Microsoft Intune"
description: "In diesem Thema beschreibt, was Sie erwartet, wenn Ihre app von Informationsverwaltungsrichtlinien für mobile-app verwaltet wird."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.openlocfilehash: 48783b21c64c9031b0fbbd58afb8aa0eb911ed6b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Endbenutzer für MAM aktiviert-apps mit Microsoft Intune
Richtlinien mobilen anwendungsverwaltung (MAM) werden nur angewendet, wenn apps im Arbeitskontext verwendet werden.  Hier finden Sie die folgenden Szenarien zu verstehen, wie verwaltete apps arbeiten.
##  Zugreifen auf OneDrive auf einem iOS-Gerät

1.  Starten der **OneDrive** -app, um das Vorzeichen Seite zu öffnen.

    ![Screenshot des Laufwerks eine Seite protokollieren](../media/AppManagement/iOS_OneDriveLaunch.png)

    > [!NOTE]
    > Auf einem Gerät persönliche würde den Endbenutzer normalerweise das app herunterzuladen.  Wenn das Gerät von einer Lösung MDM, Ihre können verwaltet wird die app auf das Gerät bereitstellen.

2.  Geben Sie Ihren Benutzernamen für Arbeit-Konto an. Sie werden zur Seite **Office 365-Authentifizierung** , geben Sie Ihre Anmeldeinformationen Arbeit weitergeleitet.

    ![Screenshot der Office 365-Log in Seite](../media/AppManagement/iOS_O365SignInPage.png)

3.  Nachdem Sie Ihre Anmeldeinformationen ein, indem Sie Azure AD erfolgreich authentifiziert werden, die MAM Richtlinien werden angewendet, und werden Sie aufgefordert, die **OneDrive** -app neu zu starten.
  >[NOTIZ]! Der Neustart erforderlich ist, dass nur auf Geräten, die nicht in Intune registriert sind, klicken Sie im Dialogfeld angezeigt wird.

    ![Screenshot der Neustart erforderlich (Dialogfeld)](../media/AppManagement/iOS_AppRestartforMAM.png)

4.  Wenn Sie die **OneDrive** -app erneut starten, startet die app mit den MAM Richtlinien aktiviert ist. Jetzt aufgefordert werden, legen Sie eine **PIN** für die app. (Wenn Sie die Richtlinie für diese konfiguriert).

    ![Screenshot der OneDrive-app mit einer PIN](../media/AppManagement/iOS_AppPINPrompt.png)

5.  Sobald Sie die PIN festlegen, und bestätigen, können Sie auf die Dateien auf Ihrer **OneDrive for Business**zugreifen.

    ![Screenshot mit den Pfad der Datei mit der Liste der vorhandenen Dateien öffnen](../media/AppManagement/iOS_OneDriveSuccess.png)

    > [!NOTE]
    > Wenn Sie eine bereitgestellte Richtlinie ändern, werden die Änderungen beim nächsten angewendet die app zu öffnen.

##  Zugreifen auf OneDrive auf einem Android-Gerät

1.  Starten der OneDrive-app, um das Vorzeichen Seite zu öffnen.

    > [!NOTE]
    > Auf einem Gerät persönliche würde den Endbenutzer normalerweise das app herunterzuladen.  Wenn das Gerät von einer Lösung MDM verwaltet wird, können Sie die app auf das Gerät bereitstellen.

2.  Geben Sie Ihren Benutzernamen für Arbeit-Konto an. Sie werden zur Seite **Office 365-Authentifizierung** , geben Sie Ihre Anmeldeinformationen Arbeit umgeleitet.

    ![Screenshot der Office 365-Anmeldeseite auf einem Android-Gerät](../media/AppManagement/Android_O365SignInPage.png)

3.  Nachdem Sie Ihre Anmeldeinformationen von **Azure Active Directory**erfolgreich authentifiziert wurden, sollte die Meldung mit Anweisungen zum Installieren des Portals app Unternehmen, angezeigt wird, wenn es nicht bereits auf dem Gerät installiert ist.  Tippen Sie auf **erhalten Sie die app** , um den Vorgang fortzusetzen.

>[!NOTE]
>Die app Unternehmen Portal ist für alle apps zugeordnet MAM Richtlinien auf Android-Geräten erforderlich. Für Geräte, die nicht in Intune registriert die app muss auf dem Gerät installiert werden, aber erfordert keinen ebenso, oder melden Sie sich in der app.  


  ![Screenshot des Dialogfelds mit der Firma Portal app installieren Anforderung Nachricht](../media/AppManagement/Android_CompanyPortalMessage.png)

4.  Sie können nun die **Google Play** Store, wo Sie herunterladen und installieren Sie die app **-Portal Unternehmen** können.

    Die app Unternehmen Portal sorgt die Daten gesichert und geschützt.

    ![Screenshot der Portalseite Unternehmen-app](../media/AppManagement/Android_CompanyPortalInstall.png)

5.  Fahren Sie nach Abschluss der Installation, und wählen Sie **akzeptieren** , um zustimmen.

6.  Die **OneDrive** -app wird automatisch gestartet.

7.  Beim nächsten Öffnen OneDrive, sehen Sie aufgefordert werden, legen Sie eine **PIN**, bereitgestellten die Richtlinie erfordern eine PIN für den Zugriff von der **OneDrive** -app auf Einstellungen festgelegt sind.

    ![Screenshot der OneDrive-app eine Aufforderung zum ANHEFTEN von](../media/AppManagement/Android_OneDriveSetPIN.png)

8.  Nachdem die PIN festlegen und bestätigt ist, können Sie weiterhin mithilfe von **OneDrive**, die nun von app-Richtlinien verwaltet wird.


##  Verwendung von apps mit Unterstützung für mehrere Identität
Microsoft Word wird als ein Beispiel für dieses Szenario verwendet.

1.  Öffnen Sie die **Word** -app auf Ihrem Gerät. Wir werden einem iOS-Gerät verwenden, um die Schritte anzeigen.

2.  Tippen Sie auf **neu** , um ein neues Worddokument erstellen.

    ![Screenshot mit der neuen Menüoption auf einem iOS-Gerät am Fuß des Bildschirms angezeigt](../media/AppManagement/iOS_WordCreateNewDoc.png)

3.  Geben Sie einen Satz Ihrer Wahl.  Wenn Sie versuchen, dieses Dokument speichern, werden persönliche und geschäftlichen Speicherorte als Optionen aus, um das Dokument zu speichern, die, das Sie soeben erstellt haben, angezeigt.  In diesem Schritt werden die app-Richtlinien nicht noch übernommen, da diese Arbeit/persönlich Kontext noch nicht eingerichtet ist.

4.  Speichern Sie das Dokument zu Ihrer OneDrive for Business-Speicherort aus. Dies ist jetzt als Unternehmensdaten markiert, und die Einschränkungen für die Richtlinie anzuwenden.

    ![Screenshot der eingegebenen Satz in ein Word-Dokument](../media/AppManagement/iOS_WordCreateCompanyDoc.PNG)

5.  Öffnen Sie das Dokument, das Sie Ihre Arbeit Speicherort gespeichert haben.  Kopieren Sie den Text, öffnen Sie Ihre persönliche **Facebook** -Konto aus, und versuchen Sie den kopierten Text einzufügen.  Sie sollten nicht mehr Einfügen des Inhalts in den neuen Facebook Beitrag. Die Option zum Einfügen nicht abgeblendeter, geschieht nichts beim **Einfügen**drücken.

    ![Screenshot mit der Ausschneiden, kopieren und Einfügen der Auswahl](../media/AppManagement/iOS_WordCopyCompany.png)

    ![Screenshot, der keine eingefügten Daten in der Facebook-Beitrag zeigt](../media/AppManagement/iOS_FacebookPasteCompany.png)

6.  Jetzt wiederholen Sie die Schritte 2 und 3, um ein neues Dokument erstellen, geben Sie einen Satz und zu Ihrer Arbeit, speichern sie Ihre persönlichen Speicherort wie **OneDrive - persönliche**Speicherung Ihrer Wahl.

    ![Screenshot der Ausschneiden, kopieren und der Einfügeauswahl mit dem Satz zum Kopieren ausgewählt](../media/AppManagement/iOS_WordCopyPersonal.png)

7.  Öffnen Sie das persönliche gespeicherte Dokument.  Kopieren Sie den Text, öffnen Sie die **Facebook** -app, und versuchen Sie, den kopierten Text einzufügen. Sie sehen, dass Sie den Inhalt zu einem Beitrag Facebook einfügen können.

    ![Inhalt mit Einfügen in der Facebook-Beitrag](../media/AppManagement/iOS_FacebookPastePersonal.png)

##  Verwalten von Benutzerkonten

Intune unterstützt nur Bereitstellen von MAM Richtlinien zu nur ein Benutzerkonto pro Gerät. Wenn ein Gerät mehr als ein Konto bei Arbeit aufweist, wird durch die Richtlinien MAM immer nur ein Konto verwaltet.

Je nach der app, die Sie verwenden, der zweite Benutzer oder möglicherweise nicht auf dem Gerät blockiert werden. In allen Fällen ist jedoch nur der erste Benutzer, die die Richtlinien MAM wird von der Richtlinie betroffen.

Wenn Sie ein Gerät verfügt über mehrere Benutzerkonten vorhandenen, bevor die MAM Richtlinien bereitgestellt werden, wird das Konto, das in die MAM Richtlinien bereitgestellt wird zuerst vom Intune MAM Richtlinien verwaltet.

**Microsoft Word**, **Excel**und **PowerPoint** kein zweites Benutzerkonto blockieren, jedoch des zweiten Benutzerkontos wird durch die MAM Richtlinien nicht beeinflusst.  

**OneDrive und Outlook-apps**können Sie nur ein Konto bei Arbeit.  Hinzufügen von mehreren Konten für Arbeit auf diese apps blockiert werden.  Sie können jedoch einen Benutzer entfernen, und fügen Sie einen anderen Benutzer auf dem Gerät.

Lesen Sie das Beispielszenario unten, um ein besseres Verständnis der behandelt werden, wie mehrere Benutzerkonten zu gelangen.

Benutzer A funktioniert für die beiden Unternehmen - **Unternehmen X**und **Y Unternehmen**. Benutzer A hat ein Konto bei Arbeit für jedes Unternehmen, und beide Intune Bereitstellen MAM Richtlinien verwenden. **Firma X** bereitstellt MAM Richtlinien **vor dem** **Unternehmen Y**. **Firma X** zugeordnete Konto erhalten die Richtlinie MAM, aber nicht das Konto Unternehmen Y zugeordnet. Wenn das Benutzerkonto, das Unternehmen Y, indem Sie die Richtlinien MAM verwaltet werden zugeordnet werden soll, müssen Sie das Benutzerkonto zugeordnet Firma X entfernen.
### Hinzufügen einer zweiten Kontos
#### IOS
Wenn Sie einem iOS-Gerät, bei dem Versuch, Hinzufügen einer zweiten Arbeit-Kontos auf dem gleichen Gerät verwenden, werden Ihnen die blockieren Nachricht angezeigt.  Außerdem sehen Sie eine Option aus, um das vorhandene Konto entfernen und eine neue hinzufügen. Sie können dies tun, indem Sie auf **Ja**.

![Screenshot des Dialogfelds mit der blockierenden Nachricht und Ja ohne Optionen](../media/AppManagement/iOS_SwitchUser.PNG)
####  Android
Wenn Sie einem Android-Gerät verwenden, können die Meldung blockierenden mit Anweisungen, um das vorhandene Konto entfernen und eine neue hinzufügen.  Auf dem Android-Geräten, um das vorhandene Konto entfernen möchten, wechseln Sie zu **Einstellungen &gt;allgemeine &gt; Application Manager &gt;Unternehmen Portal und auswählen "löschen Daten"**.

![Screenshot der Fehlermeldung und Anweisungen, um das Konto entfernen](../media/AppManagement/Android_SwitchUser.png)

##  Anzeigen von Mediendateien mit der Verwaltung von Informationsrechten app freigeben
Unternehmen AV verwenden um anzuzeigen PDF- und Bilddateien auf Android-Geräten, die [Microsoft Rights Management (RMS) app freigeben](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Laden Sie diese app aus dem Google Play Store.  Sobald die app auf Ihrem Gerät installiert wurde, starten Sie die app, und mit Ihren Anmeldeinformationen authentifizieren. Sie sollten jetzt ungeschützte und geschützte Dateien von anderen apps Richtlinie verwaltet sein.

Die folgenden Filetypes werden unterstützt:

* **Audio:** AAC LC, HE-AACv1 (AAC +), HE-AACv2 (Erweiterte AAC +), AAC ELD (enhanced niedrig Verzögerung AAC), AMR-Hinweis:, AMR-WB, FLAC, MP3-, MIDI, Vorbis, PCM/WELLE.
* **Video:** H. 263, H. 264 AVC, MPEG-4 SP, VP8.
* **Bild:** Jpg, Pjpg, Png, Ppng, Bmp, Pbmp, Gif, Pgif, Jpeg, Pjpeg.
* PDF-DATEI, PPDF

------------
|**pFile**|**Text**|
|----|----|
|PFile ist eine generische "Wrapper"-Format für geschützte Dateien, schließt die verschlüsselte Inhalte und den RMS-Lizenzen und kann verwendet werden, um alle Dateitypen schützen.|Auch wenn sie geschützt sind, können Textdateien, einschließlich XML, CSV, usw. bei der Anzeige in der app geöffnet werden. Dateitypen: Txt, Ptxt, Csv, Pcsv, Log, Plog, Xml, Pxml.|
---------------
**Android-Geräten, die nicht in Intune registriert sind**

Bevor Sie den Freigabe app RMS zum Anzeigen von Dateien aus anderen apps von Intune verwaltet verwenden können, starten Sie die app RMS und mit Ihrem Konto Arbeit authentifizieren.  Wenn Sie sich anmelden, sehen Sie mit der folgenden Nachricht **nur, wenn Sie eine Lizenz für RMS besitzen**:

**Authentifizierung erfolgreich – Sie können nun Dateien im Unternehmen anzeigen, aber Ihre Organisation eingerichtet nicht zur Verfügung, in dem Sie die Dateien schützen können. Weitere Informationen hierzu wenden Sie sich an Ihre IT-Administrator.**

Dies verhindert nicht mithilfe des app Freigabe RMS Unternehmen Dateien anzuzeigen. Können Sie immer noch öffnen und Anzeigen von Unternehmens-Dateien aus anderen apps von Intune verwaltet werden, und die Richtlinien MAM wendet weiterhin.  Was ist diese Nachricht zu sagen ist, dass Sie nicht die zusätzlichen Schutzfunktionen hinzufügen, die der Freigabe app RMS bietet.  Sie müssen eine Lizenz RMS Schutz auf Ihre Dateien hinzufügen können. Weitere Informationen zu RMS Datei Schutzfunktionen finden Sie unter [Schützen einer Datei, die Sie per e-Mail freigeben](https://docs.microsoft.com/en-us/rights-management/rms-client/sharing-app-protect-by-email)und [Schützen einer Datei auf einem Gerät](https://docs.microsoft.com/en-us/rights-management/rms-client/sharing-app-protect-in-place) .


### Siehe auch
[Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien mit Microsoft Intune mobile-app](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
