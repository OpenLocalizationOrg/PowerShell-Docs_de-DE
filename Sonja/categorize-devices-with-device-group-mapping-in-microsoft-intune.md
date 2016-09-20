---
title: "Kategorisieren Geräte mit Gerät Gruppe Zuordnung | Microsoft Intune"
description: "Verwenden Sie Microsoft Intune Gerät Gruppe Zuordnung zu Gruppe Geräte in denen denen von Ihnen festgelegten, damit Sie diese Geräte verwalten erleichtern, Kategorien."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: sumitp
ms.suite: ems
ms.openlocfilehash: ad63978de4b9fdcacc0046fc05202ac7d7e5edd6
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Kategorisieren Sie Geräte mit Gerät Gruppe Zuordnung in Microsoft Intune
Verwenden Sie Microsoft Intune **Gerät Gruppe Zuordnung** zu Gruppe Geräte in denen denen von Ihnen festgelegten, damit Sie diese Geräte verwalten erleichtern, Kategorien. 

Gerät Gruppe Zuordnung verwendet den folgenden Workflow:
1. Sie erstellen Intune Gerätegruppen für jede Kategorie, die Sie verwenden möchten.
2. Konfigurieren von Gerät Gruppe Zuordnungsregeln, die Kategorie, die Sie auswählen, in der Gerätegruppe zuordnen, die Sie erstellt haben.
3. Wenn Endbenutzer Geräts registrieren, müssen sie aus den Kategorien, die konfiguriert wurde, die eine Kategorie auswählen. Nachdem sie ausgewählt haben, wird Geräts automatisch die entsprechende Gerätegruppe hinzugefügt werden, die Sie erstellt haben.
4. Klicken Sie dann können diesen Gerätegruppen beim Bereitstellen von Richtlinien und apps.

Beispiele für Kategorien möglicherweise:
* Persönliche
* Punkt Verkauf-Gerät
* Demo-Gerät
* Umsatz
* Buchhaltung
* Manager

Sie können jedoch alle Kategorien konfigurieren Sie die gewünschten.

## Konfigurieren von Gerät Gruppe Zuordnung
1. Erstellen Sie für jede Gerätekategorie, die Sie verwenden möchten eine Intune Gerätegruppe. Informationen zum Erstellen von Gruppen finden Sie unter [Verwenden von Gruppen zum Verwalten von Benutzern und Geräten mit Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).
2. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com) **Administrator**aus.
3. Im Arbeitsbereich **Administration** erweitern Sie **Verwaltung mobiler Geräte**, und wählen Sie dann auf **Gerät zuordnen**.
4. Aktivieren Sie auf der Seite **Gerät Gruppe Zuordnung** Gerät Gruppe Zuordnung aus.
5. Wählen Sie **Hinzufügen** , um eine neue Zuordnungsregel zu erstellen.
6. Geben Sie im Dialogfeld **Gerät Gruppe Zuordnung-Regel hinzufügen** den Namen der Kategorie, die Sie öffnen möchten, erstellen, und wählen Sie aus der Dropdownliste die Gerät Sammlung, der Sie dieser Kategorie zuordnen möchten. Wenn Sie fertig sind, wählen Sie **Hinzufügen** .
7. Wenn Sie das Hinzufügen von Kategorien und Gruppen abgeschlossen haben, wählen Sie **Speichern**aus.

Jetzt, wenn Benutzer Geräts registrieren, werden diese mit einer Liste der Kategorien bereitstehen, die konfiguriert wurde. Nachdem sie eine Kategorie auswählen und Registrierung abzuschließen, wird Geräts Device-Gruppe hinzugefügt werden, die mit der Kategorie entspricht, die sie ausgewählt haben.

### Siehe auch
[Verwenden von Gruppen zum Verwalten von Benutzern und Geräten mit Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)