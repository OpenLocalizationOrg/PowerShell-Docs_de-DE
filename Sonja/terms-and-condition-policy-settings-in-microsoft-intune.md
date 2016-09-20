---
title: "Ausdrücke und Richtlinieneinstellungen Bedingung | Microsoft Intune"
description: "Sie können die Benutzergruppen erläutern Intune allgemeinen Geschäftsbedingungen bereitstellen Auswirkungen der Registrierung, Zugriff auf Ressourcen der Art Arbeit und Verwenden der app Unternehmen Portal Geräte und Benutzer."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6edf0ac1-4f46-4543-a9e5-f484ac37e9a5
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 701f6c79b32a3968fd76b441b8f7fd4d9d810df6
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Von Ausdrücken und Richtlinieneinstellungen in Microsoft Intune Bedingung
Sie können die Benutzergruppen erläutern Intune allgemeinen Geschäftsbedingungen bereitstellen Auswirkungen der Registrierung, Zugriff auf Ressourcen der Art Arbeit und Verwenden der app Unternehmen Portal Geräte und Benutzer. Benutzer müssen die allgemeinen Geschäftsbedingungen akzeptieren, bevor diese im Portal Unternehmen verwenden können, registrieren und seine Arbeit zugreifen.

Sie können erstellen und Bereitstellen von mehreren Richtlinien mit anderen allgemeinen Geschäftsbedingungen. Können Sie auch Naturprodukte Versionen der gleichen allgemeinen Geschäftsbedingungen in verschiedenen Sprachen und dann diese zu ihren entsprechenden Gruppen bereitzustellen.

## Erstellen einer Richtlinie allgemeinen Geschäftsbedingungen

1.  Klicken Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com) auf die **Richtlinie** &gt; **allgemeinen Geschäftsbedingungen**.

    ![Screenshot von allgemeinen Geschäftsbedingungen Richtlinie](./media/pol-sa-terms-conditions.png)

2.  Klicken Sie auf **Hinzufügen** , um eine neue Geschäftsbedingungen Richtlinie zu erstellen.

    Sie können auch **Bearbeiten** oder **Löschen** einer vorhandenen Richtlinie.

3.  Geben Sie auf der Seite **Erstellen allgemeinen Geschäftsbedingungen** die folgenden Informationen ein:

    -   **Name** - einen eindeutigen Richtliniennamen angezeigt, in der Intune-Verwaltungskonsole

    -   **Beschreibung** - Details, die Ihnen helfen, identifizieren die Richtlinie in der Intune-Verwaltungskonsole

    -   **Titel** - der Titel, der Benutzern im Unternehmen Portal angezeigt

    -   **Text erläutern, was dies bedeutet, wenn der Benutzer akzeptiert** -Bezeichnung für Benutzer angezeigt wird, zu der Annahme. **Beispiel**: "Ich stimme zu allgemeinen Geschäftsbedingungen".

4.  Wenn Sie fertig sind, klicken Sie auf **Speichern**. Die neue Richtlinie ist im **allgemeinen Geschäftsbedingungen** Knoten des Arbeitsbereichs **Richtlinie** angezeigt.

## Bereitstellen einer allgemeinen Geschäftsbedingungen Richtlinie

1.  Klicken Sie in der [Microsoft-Intune-Verwaltungskonsole](http://manage.microsoft.com) auf die **Richtlinie** &gt; **allgemeinen Geschäftsbedingungen**.

2.  Wählen Sie in der Liste **von Ausdrücken und Bedingungen Richtlinien** die Richtlinie, die Sie bereitstellen möchten, und klicken Sie dann auf **Bereitstellung verwalten**.

3.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** wählen Sie die Benutzergruppen, denen Sie die Richtlinie bereitstellen möchten, und klicken Sie dann auf **OK**.

    Wenn Sie den Benutzern das Unternehmen-Portal zugreifen, zeigt Intune die allgemeinen Geschäftsbedingungen, die Sie bereitgestellt. Benutzer müssen zustimmen, diese Ausdrücke, bevor sie Unternehmensressourcen zugreifen können.

## Überwachen von einer Richtlinie allgemeinen Geschäftsbedingungen

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) auf die **Richtlinie** &gt; **allgemeinen Geschäftsbedingungen**.

2.  Klicken Sie auf **Bericht anzeigen**, klicken Sie im **Neuen Bericht erstellen** . Der Bericht wird geöffnet, mit detaillierten Informationen zu, welche Benutzer die allgemeinen Geschäftsbedingungen bereitgestellten akzeptiert haben.

### Updates und Versionskontrolle für die allgemeinen Geschäftsbedingungen
Wenn Sie eine vorhandene Geschäftsbedingungen Richtlinie zu bearbeiten, können Sie das Verhalten auswählen, wenn Sie die Richtlinie bereitstellen. Verwenden Sie das folgende Verfahren helfen Ihnen vorhandene Ausdrücke und Bedingungen Richtlinien zu aktualisieren.

## Zum Arbeiten mit mehreren Versionen von allgemeinen Geschäftsbedingungen

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](http://manage.microsoft.com) auf die **Richtlinie** &gt; **allgemeinen Geschäftsbedingungen**.

2.  Wählen Sie die allgemeinen Geschäftsbedingungen Richtlinie, die Sie bearbeiten möchten, und klicken Sie dann auf **Bearbeiten**.

3.  Klicken Sie auf der Seite **Bearbeiten allgemeinen Geschäftsbedingungen** nehmen Sie alle erforderlichen Änderungen vor, und geben Sie dann an, ob diese neue Version alle Benutzer die allgemeinen Geschäftsbedingungen annehmen muss oder nur für neue Benutzer wird die neue Version angezeigt.

    Wir empfehlen Ihnen die Versionsnummer erhöhen erfordern, dass die Annahme jedes Mal, wenn Sie signifikante Stellen zur allgemeinen Geschäftsbedingungen Richtlinie ändert. Lassen Sie die aktuelle Versionsnummer, wenn Sie beheben von Tippfehlern oder Ändern der Formatierung, beispielsweise.

### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
