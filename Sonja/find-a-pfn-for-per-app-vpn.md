---
title: "Suchen eines Pakets Familienname (PFN) für pro-app VPN | Microsoft Intune"
description: "Finden Sie eine PFN, damit Sie ein pro-app VPN konfigurieren können."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ms.reviewer: tycast
ms.suite: ems
ms.openlocfilehash: 194e6e2b20c90cce5adcc684a4674e972d0cdc1b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Suchen Sie ein Paket Familienname (PFN) für pro-app VPN-Konfiguration

Es gibt zwei Möglichkeiten, um eine PFN suchen, sodass Sie ein VPN-app einrichten können.

## Suchen nach einer PFN für eine app, die auf einem Windows-10-Computer installiert ist

Wenn die app, der Sie beim Arbeiten mit bereits auf einem Windows-10-Computer installiert ist, können Sie das PowerShell-Cmdlet [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) verwenden, können Sie um die PFN zu gelangen.

Die Syntax für Get-AppxPackage lautet:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
Möglicherweise müssen Sie PowerShell als Administrator zum Abrufen der PFN ausführen.

Um Informationen zu allen universeller apps auf dem Computer installiert zu gelangen, beispielsweise für Folgendes verwenden `Get-AppxPackage`.

Um Informationen zu einer app zu gelangen, wenn Sie den Namen oder einen Teil des Namens kennen, verwenden Sie `Get-AppxPackage *<app_name>`. Beachten Sie die Verwendung der das Platzhalterzeichen verwenden, also besonders hilfreich, wenn Sie nicht sicher des vollständigen Namens der app befinden. Angenommen, die Informationen für OneNote verwenden, um `Get-AppxPackage *OneNote`.


Hier sind die Informationen, die für OneNote abgerufen:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## Suchen nach einer PFN, wenn die app nicht auf einem Computer installiert ist

1.  Wechseln Sie zu https://www.microsoft.com/en-us/store/apps.
2.  Geben Sie den Namen der app in der Suchleiste ein. Suchen Sie in diesem Beispiel nach OneNote.
3.  Wählen Sie den Link zur app. Beachten Sie, dass die URL am Ende einer Reihe von Buchstaben enthält. In diesem Beispiel die URL sieht wie folgt aus: `https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`.
4.  Fügen Sie in einer anderen Registerkarte, die folgende URL, `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`. Ersetzen Sie `<app id>` mit der app-Id, die Sie von https://www.microsoft.com/en-us/store/apps - dieser Reihe von Buchstaben am Ende der URL in Schritt 3 erhalten haben. In diesem Beispiel von OneNote, fügen Sie: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

Microsoft Edge zeigt die gewünschten Informationen. Wählen Sie in Internet Explorer **Öffnen** , damit die Informationen sehen. Der Wert PFN wird in der ersten Zeile angegeben. Hier sind die Ergebnisse für unsere Beispiel:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
