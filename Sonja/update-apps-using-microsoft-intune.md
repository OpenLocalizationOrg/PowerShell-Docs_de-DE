---
title: Aktualisieren von apps | Microsoft Intune
description: Verwenden Sie die Informationen in diesem Thema um zu verstehen, wie Sie apps zu aktualisieren, wenn eine neue Version erforderlich ist.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: cefe90cdb0cda5ada259576af7cf477642860446
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Aktualisieren von apps, die mit Microsoft Intune
Microsoft Intune helfen Ihnen die app-Updates zu verwalten. Verwenden Sie die Informationen in diesem Thema um zu verstehen, wie Sie apps zu aktualisieren, wenn eine neue Version erforderlich ist.

## So aktualisieren Sie apps
Wenn eine neue Version von einer app, die Sie bereitgestellt haben freigegeben ist, kann Intune aktualisieren und Bereitstellen von der neueren Version der app aus. Sie können nur eine Bereitstellung durch eine neuere Version der gleichen app ersetzen (mit dem gleichen Bezeichner). Sie können app Updates verwenden, um eine Bereitstellung zu einer anderen app-Paket zu aktualisieren.

### App-IDs
Der app-Bezeichner ist eine Eigenschaft, die eine app identifiziert. Sie können nicht mehrere Kopien einer app mit demselben Bezeichner installieren. Es folgen einige Beispiele für app Bezeichner:

- **iOS** - Paket-ID (Beispiel: com.microsoft.excel)
- **Android** - Paket-ID (Beispiel: com.microsoft.excel)
- **Windows Phone** – (XAP-Installer) verwenden Produkt-ID (GUID)
- **Windows** - (Appx/Appxbundle), verwenden Sie den vollständigen Namen des Pakets



> [!IMPORTANT]
> Wenn Sie eine app mit einer Bereitstellungsaktion der **erforderlichen installieren** und höher ändern bereitstellen die Bereitstellungsaktion **Installieren verfügbare**Updates für die app werden nicht automatisch installiert auf Geräten, die vor der Bereitstellung Änderung der Installation der app. Um dieses Problem zu beheben, können Sie die folgenden Aktionen ausführen:
>
> -   Lassen Sie die Benutzer des Geräts Unternehmen Portal auswählen die installierte app wechseln, und wählen Sie dann auf **Installieren**.
> -   Ändern Sie die Bereitstellungsaktion zu **Deinstallieren**und nach der Deinstallation von der app erneut bereitstellen Sie die app mit einer Bereitstellungsaktion von **Installieren verfügbar**.

### Aktualisieren eine app

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), **Apps** &gt; **Apps**.

2.  Der **Apps** -Liste Wählen Sie die app, die Sie aktualisieren möchten, und wählen Sie dann auf **Bearbeiten**.

3.  Geben Sie im Assistenten **Software bearbeiten** alle neuen Details für das app-Paket aus.

4.  Wenn Sie fertig sind, wählen Sie **Aktualisieren**.

Wenn verfügbaren apps Geräte weiter zu überprüfen, wird automatisch die app auf die neueste Version aktualisiert werden.
Für apps von ein app-Paket (Zeile des Geschäfts-apps) installiert haben wird die app automatisch für erforderlichen und verfügbaren Bereitstellungen aktualisiert werden, solange die Anwendung den gleichen Bezeichner ist.

Für apps, die als eine Verknüpfung zu einem Speicher bereitgestellt werden wird das Update vom Speicher verwaltet aus der die app stammt.
