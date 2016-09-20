---
title: Erneuern eines Symantec Enterprise Code-signiertes Zertifikat zur Verwendung mit Intune | Microsoft Intune
description: "Anleitungen So erneuern Sie Symantec Zertifikate zum Verwalten von bestimmter mobilen Geräten für Windows und Windows Phone"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 09b5bf6501acfa7743555737d9e69a6141dda8ac
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Erneuern eines Symantec Enterprise Code-signiertes Zertifikat für Windows-Geräte

Das Zertifikat Symantec zum Verwalten von bestimmter mobilen Geräten für Windows und Windows Phone muss regelmäßig erneuert werden. Für Windows Phone 8.0 Geräte werden einer signierten Unternehmen Portal-app und der Code-signiertes Zertifikat für die Registrierung Gerät benötigt. Höher für Windows Phone können im Portal Unternehmen app aus dem Speicher heruntergeladen. Signaturzertifikat mit Code ist auch zum Bereitstellen von Branchen apps werden.

## So erneuern das Symantec Enterprise Code-signiertes Zertifikat

1.  Suchen Sie nach einer Erneuerung e-Mail-Nachricht gesendet von Symantec ungefähr 14 Tage vor Zertifikatsablauf. Diese e-Mail enthält Anweisungen von Symantec zu erneuern Ihr Enterprise-Zertifikat.

    Weitere Informationen zu Symantec Zertifikate besuchen Sie [www.symantec.com](http://www.symantec.com) , oder rufen Sie 1-877-438-8776 oder 1-650-426-3400.

2.  Wechseln Sie zu der Website (Beispiel: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)), und melden Sie sich mit der Symantec Publisher-ID und e-Mail-berücksichtigt das Zertifikat zugeordnet. Denken Sie daran, mit dem gleichen Computer für die Erneuerung, die Sie verwenden möchten, laden Sie das Zertifikat ab.

3.  Sobald die Erneuerung ist genehmigt und bezahlt, laden Sie das Zertifikat ein.

## So installieren Sie das aktualisierte Zertifikat für Windows Phone 8.0

1.  Herunterladen, und melden Sie sich das neueste Windows Phone Unternehmen Portal befindet sich hier: [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Öffnen Sie Ihre Intune-Verwaltungskonsole ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)) und wechseln Sie zu **Admin**, **Verwaltung mobiler Geräte** &gt; **Windows Phone** , und klicken Sie auf **Hochladen angemeldet App**.

3.  Hochladen der neu signierten Unternehmen-Portal an. Sie benötigen die neu signierten SSP.xap und das neue. PFX-Datei, die Sie erhalten von Symantec oder der Anwendung Registrierungs-Token, das mit diesem neu erstellt wurde. PFX-Datei.

4.  Nach Abschluss des Uploads entfernen Sie die alte Version des Unternehmens Portal im Arbeitsbereich **Software** in der Intune-Verwaltungskonsole.

5.  Melden Sie sich alle Enterprise Branchen apps erneut verwenden das gleiche Zertifikat und hochladen und vorhandene Applikationen ersetzen.

Bereitstellen einer signierten SSP.xap Datei ist derzeit die einzige Möglichkeit um den aktualisierten Code Signaturzertifikat bereitzustellen. Signierte Branchen apps unterstützt, müssen Sie melden und eine app Unternehmen Portal hochladen, obwohl die Benutzer die app Unternehmen Portal aus dem Speicher installieren.

## So installieren Sie das aktualisierte Zertifikat für Windows Phone 8.1 oder höher

1.  Herunterladen, und melden Sie sich das neueste Windows Phone Unternehmen Portal aus dem Download Center befindet sich hier: [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Öffnen Sie Ihre [Intune-Verwaltungskonsole](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com), und wechseln Sie zu **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **Windows Phone** , und klicken Sie auf **Hochladen angemeldet App**.

3.  Hochladen der neu signierten Unternehmen-Portal an. Sie benötigen die neu signierten SSP.xap und das neue. PFX-Datei, die Sie erhalten von Symantec oder der Anwendung Registrierungs-Token, das mit diesem neu erstellt wurde. PFX-Datei.

4.  Nach Abschluss des Uploads, entfernen Sie die alte Version des Unternehmens Portal im Arbeitsbereich für die **Software** aus.

5.  Melden Sie alle neuen und beliebiger aktualisierten Enterprise Branchen apps mit dem neuen Zertifikat. Vorhandene Applikationen müssen nicht erneut signiert und erneut bereitgestellt werden.


### Siehe auch
[Einrichten von Windows Phone 8.0 Management](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[Einrichten der Verwaltung von Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)
