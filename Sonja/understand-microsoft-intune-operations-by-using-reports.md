---
title: "Grundlegendes zu Vorgänge mithilfe von Berichten | Microsoft Intune"
description: "Erstellen und Verwalten von Berichten zu Software, Hardware und Lizenzen für Software in Ihrer Organisation."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ms.reviewer: pbala
ms.suite: ems
ms.openlocfilehash: c9df7eddbae77e64cc3b0fdf9ddc158ed2ed2860
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Grundlegendes zu Microsoft Intune Vorgänge mithilfe von Berichten
Verwenden Sie die Informationen in diesem Thema, mit deren Hilfe Sie das Erstellen und Verwalten von Microsoft Intune-Berichte, die Informationen zu Software, Hardware und Lizenzen für Software in Ihrer Organisation bereitstellen.

## Verwenden von Berichten
Intune-Berichte enthalten Informationen zu Software, Hardware und Lizenzen für Software in Ihrer Organisation. Berichte hilft Ihnen aktuelle Anforderungen bestätigen und Prognostizieren des zukünftigen Ausgaben. Der Arbeitsbereich **Berichte** bietet Ihnen Tools, um Berichte erstellen und verwalten. 

### Typen von Berichten

|Typ des Berichts|Beschreibung|
|---------------|---------------|
|**Aktualisieren von Berichten**|Zeigen Sie die Softwareupdates, die wurde erfolgreich abgeschlossen auf Computern in Ihrer Organisation ein. Außerdem wird gezeigt, die Updates, die fehlgeschlagen ist, sind Ausstehend oder erforderlich sind. Weitere Informationen zu Softwareupdates finden Sie unter [Beibehalten Windows PCs auf dem neuesten Stand mit Softwareupdates von Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Erkannte Software-Berichte**|Anzeigen von Software, die auf Computern in Ihrer Organisation installiert ist. Software-Versionen sind enthalten. Sie können die Informationen, die angezeigt werden, basierend auf den Herausgeber der Software und die Softwarekategorie filtern. Sie können die Updates in der Liste, um weitere Details (beispielsweise der Computer, auf denen ein Update installiert ist) anzeigen, indem Sie auf den Pfeil neben dem Element klicken erweitern.<br /><br />Wenn Sie Computern zurückziehen oder die Gruppenmitgliedschaft in Intune ändern, dauert es einige Minuten für diese Änderungen in der Software nicht erkannt Bericht widergespiegelt werden sollen. Warten Sie einige Minuten für die genauesten Software Inventory Daten nach dem Zurückziehen Computern oder deren Gruppenmitgliedschaft ändern, bevor Sie einen Bericht erkannte Software ausführen, der diesen Computern enthält.|
|**Computer Inventory-Berichte**|Informationen zu verwalteten Computern in Ihrer Organisation anzeigen. Verwenden Sie diesen Bericht aus, um Hardware Einkäufe planen und Weitere Informationen zu den Anforderungen Hardware Benutzer in Ihrer Organisation zu verstehen. Weitere Informationen zum Arbeiten mit verwalteten Computern finden Sie unter [Verwalten von Windows-PCs mit Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md).|
|**Mobiles Gerät Inventory-Berichte**|Informationen zu den mobilen Geräten in Ihrer Organisation anzeigen. Sie können die Informationen, die angezeigt werden, basierend auf Gruppen, ob das Gerät eine Jailbroken oder ab dem Stammverzeichnis Gerät und vom Betriebssystem filtern.|
|**Berichte zur Lizenzen erwerben**|Zeigen Sie die Softwaretitel für die gesamte lizenzierte Software in ausgewählten Lizenzgruppen, basierend auf deren Volumenlizenz-Verträgen an. Wenn Software Lizenzinformationen in mehr als 24 Stunden nicht aktualisiert wurde, wird diese aktualisieren wenn Sie einen Lizenzbericht generieren. Ein Lizenzbericht ist nicht Nachweis der Übereinstimmung mit Vereinbarungen oder eine exakte Berechnung der Software-Titel, die verwendet werden. Der Bericht ist ein Tool zur Lizenzierung Entscheidungen für Ihre Organisation hilft Ihnen an. Intune kann nicht einige Produkte erkennen, die in der Lage ist, dass ein Microsoft-Volumenlizenzierung sind. Die Filter verfügbar sind:<br /><br />**Alle Vereinbarungen** zeigt alle lizenzierte Softwareprodukte von Intune verwaltet werden.<br /><br />**Volumenlizenzen** zeigt nur die Softwareprodukte Volume Licensing Service Center (VLSC).<br /><br />**Andere Software zur Lizenzierung Vereinbarungen** zeigt Softwareprodukte, die außerhalb der VLSC verwaltet werden.|
|**Berichte zur Lizenzen**|Vergleichen Sie installierten Software auf Computern in Ihrer Organisation mit Ihrer aktuellen Lizenz Garantie, entsprechend der VLSC aus. Filter umfassen:<br /><br />**Alle Vereinbarungen** zeigt alle lizenzierte Softwareprodukte von Intune verwaltet werden.<br /><br />**Volumenlizenzen** zeigt nur VLSC Softwareprodukte.<br /><br />**Andere Software zur Lizenzierung Vereinbarungen** zeigt Softwareprodukte, die außerhalb der VLSC verwaltet werden.|
|**Begriffe und Berichte Bedingungen**|Anzeigen, ob der Benutzer akzeptiert die allgemeinen Geschäftsbedingungen, die Sie bereitgestellt, und welche Version sie akzeptiert. Sie können die Annahme für bis zu 10 Benutzer bereitgestellt waren Geschäftsbedingungen anzeigen oder anzeigen den Annahmestatus für einen bestimmten Begriff, der Ihnen bereitgestellt wurde.|
|**Nicht kompatible Apps-Berichte**|Anzeigen von Informationen zu den Benutzern, die apps installiert haben, die auf Ihre Listen von kompatible und nicht kompatible apps sind. Verwenden Sie diesen Bericht zum Suchen von Benutzern und Geräten, die keine Übereinstimmung mit der app Unternehmensrichtlinien sind.|
|**Zertifikat Compliance-Berichte**|Anzeigen, welche Zertifikate für Benutzer und Geräte über SCEP oder PKCS #12 ausgestellt wurden (. (PFX). Verwenden Sie diesen Bericht, um zu suchen, die ausgestellt, abgelaufen und widerrufen.|
|**Gerät Verlauf Berichte**|Anzeigen eines zurückliegenden Protokoll Außerkraftsetzungsrichtlinie, zurücksetzen und Löschaktionen. Verwenden Sie diesen Bericht, um anzuzeigen, die in der Vergangenheit Aktionen auf Geräten initiiert.|
|**Bescheinigung Verwendungsberichte**|Zeigen Sie die Integrität des mobilen Geräten.|
|**Mac OS X Hardware-Bericht**|Zeigt Hardwaredetails für alle registrierten Mac OS X-Geräte in den Gruppen, die Sie auswählen. Informationen zu der Hardwarebestand, die von diesen Geräten gesammelt werden, finden Sie unter [Ihre Geräte mit Beständen in Microsoft Intune verstehen](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Mac OS X Software Bericht**|Zeigt die Software, die auf alle Mac OS X-Geräte in den Gruppen installiert ist, die Sie ausgewählt haben. Der Bericht listet die Namen der Software (als Paket-ID), die Kurzfassung (oder freundlichen) Name, die Version und die Anzahl der Geräte mit der Software installiert.|

#### Zum Erstellen eines Berichts

1.  Wählen Sie in der Intune Admin-Verwaltungskonsole **Berichte**aus. Wählen Sie dann den Typ des Berichts, den generiert werden sollen, wie in der obigen Tabelle beschrieben.

2.  Übernehmen Sie auf der Seite **Neue Berichte erstellen** die Standardwerte oder bearbeiten Sie, um die Ergebnisse zu filtern, die vom Bericht zurückgegeben werden. Beispielsweise könnten Sie auswählen, dass nur die Software von Microsoft veröffentlichten im Bericht Software nicht erkannt angezeigt wird.

3.  Wählen Sie **Bericht anzeigen** , um den Bericht in einem neuen Fenster öffnen aus.

Um den Bericht anhand einer der angezeigten Spalten zu sortieren, wählen Sie die Spaltenüberschrift aus. Darüber hinaus können einige Berichte Sie Elemente in der Liste zum Anzeigen von mehr Details zu erweitern.

## Weitere Aktionen für den Bericht
Darüber hinaus unterstützen Berichte die folgenden Aktionen aus:

|Aktion|Weitere Informationen|
|----------|--------------------|
|**Drucken**|Wählen Sie in einer geöffneten Bericht das Symbol "Drucken" aus, und folgen Sie den Anweisungen.|
|**Exportieren**|Wählen Sie in einer geöffneten Bericht das Symbol "Exportieren", und folgen Sie den Anweisungen. Sie können einen Bericht durch Trennzeichen getrennt (CSV) oder HTML-Format exportieren.|
|**Speichern**|Auf der Seite **Neue Berichte erstellen** kann jeder Benutzer bis zu 100 Berichte speichern. Konfigurieren Sie die Berichtsparameter zu Ihren Anforderungen, und wählen Sie dann **Speichern** oder **Speichern unter** (Wenn Sie einen anderen Namen verwenden möchten).|
|**Beim Laden**|Wählen Sie auf der Seite **Neue Berichte erstellen** , **Laden** zum Abrufen eines zuvor gespeicherte Sätze von Berichtsparametern aus.|
|**Löschen**|Klicken Sie im Arbeitsbereich **Berichte** wählen Sie den gewünschten Berichtstyp aus, und wählen Sie **Laden**. Klicken Sie dann in der Liste der Berichte, wählen Sie das Löschsymbol (X) neben dem Bericht an.|

### Siehe auch
[Überwachung und Berichte mit Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
