---
title: "Verwenden Sie remote sperren und Kenncodes zurücksetzen | Microsoft Intune"
description: "Intune bietet sowohl remote sperren und Kenncodes Funktionen zurücksetzen."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
ms.openlocfilehash: 3a7c87d915abd6ef4090c1773af3e58b81366998
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Schützen Sie Ihrer Geräte mit entfernten sperren und Kenncodes zurücksetzen
Microsoft Intune bietet, dass sowohl remote sperren und Kenncodes Funktionen zurücksetzen.

## Ein Gerät Remote Sperren
Wenn ein Benutzer Geräts verliert können Sie das Gerät Remote sperren. Die folgende Tabelle enthält wie remote Sperren funktioniert auf anderen mobilen Plattformen. Remote Sperren wird nicht unterstützt.

|Plattform|Remote Sperren|
|------------|---------------|
|iOS|Unterstützt|
|Android|Unterstützt|
|Windows 10 und Windows 10 Mobile|Unterstützt|
|Windows Phone 8 und Windows Phone 8.1|Unterstützt|
|Windows RT 8.1 und Windows RT|Unterstützt, wenn der aktuelle Benutzer des Geräts denselben Benutzer ist, die für das Gerät registriert.|
|Windows 8.1|Unterstützt, wenn der aktuelle Benutzer des Geräts denselben Benutzer ist, die für das Gerät registriert.|

Remote Sperren wird für Windows-PCs, die mit dem Intune Software Client registriert nicht unterstützt.

### Sperren ein mobiles Geräts Remote über die Intune-Verwaltungskonsole

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Geräte** &gt; **Alle Mobile Geräte**.

2.  Wählen Sie **Alle direkten verwalteten Geräten** für Geräte registriert Intune oder **Alle Exchange ActiveSync verwalteten Geräten**aus.

    > [!TIP]
    > Sie können auch auf ein Gerät vom Benutzer navigieren. Wählen Sie **alle Benutzer**aus. Klicken Sie auf der Eigenschaftenseite des Benutzers wählen Sie **Geräte**aus, und wählen Sie dann auf den Namen des mobilen Geräts, die Sie zurücksetzen möchten.

3.  Wählen Sie in der Liste des Geräts oder Geräte, die Sie sperren möchten. Klicken Sie auf der Taskleiste wählen Sie **Remote Vorgänge**aus, und wählen Sie **Remote Sperren**.

## Den Kenncode auf einem Gerät zurücksetzen
Ein Benutzer ihre Kenncode vergessen hat, können Sie durch die Kennung ein Gerät entfernen oder indem Sie einen neuen temporären Kenncode für ein Gerät erzwingen helfen. Die folgende Tabelle enthält wie Kenncode Works auf anderen mobilen Plattformen zurücksetzen.

|Plattform|Kenncode zurücksetzen|
|------------|------------------|
|iOS|Zum Löschen des Kenncodes auf einem Gerät unterstützt. Erstellt einen neuen temporären Kenncode nicht.|
|Android|Unterstützt und ein temporärer Kenncode wird erstellt.|
|Mobile für Windows 10|Unterstützt|
|Windows Phone 8 und Windows Phone 8.1|Unterstützt|
|Windows RT 8.1 und Windows RT|Nicht unterstützt|
|Windows 8.1|Nicht unterstützt|

Zurücksetzen der Kenncode wird für Windows-PCs, die mit dem Intune Software Client registriert nicht unterstützt.

### Um einen Kenncode zurückzusetzen.

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/), **Gruppen** &gt; **Alle Geräte** &gt; **Alle Mobile Geräte**.

2.  Wählen Sie **Alle direkten verwalteten Geräten** für Geräte registriert Intune oder **Alle Exchange ActiveSync verwalteten Geräten**aus.

    > [!TIP]
    > Sie können auch auf ein Gerät vom Benutzer navigieren. Klicken Sie auf **alle Benutzer**. Klicken Sie auf der Eigenschaftenseite des Benutzers klicken Sie auf **Geräte**, und klicken Sie dann auf den Namen des mobilen Geräts, die Sie zurücksetzen möchten.

3.  Wählen Sie in der Liste des Geräts oder Geräte, die Sie sperren möchten. Klicken Sie auf der Taskleiste wählen Sie **Remote Vorgänge**aus, und wählen Sie **Kenncode zurücksetzen**.


### Siehe auch
[Zurückziehen Geräte](retire-devices-from-microsoft-intune-management.md)
[Windows selektiven Wischen Sie für die Verwaltung Gerät](http://technet.microsoft.com/library/dn486874.aspx)
