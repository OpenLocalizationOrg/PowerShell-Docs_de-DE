---
title: "Verwalten von Software-Lizenzvertrag für PCs mit dem Intune Software Client | Microsoft Intune"
description: "Intune können Sie verwalten Lizenzvertrag für Software über Microsoft Volume Licensing Vereinbarungen erworben und für Software, die anderweitig erworben wurde."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 4af08b38716e04766175e2ab55db1a0dba788c20
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwalten von-Lizenzvertrag für Windows-PC-Software in Microsoft Intune
Microsoft Intune können Sie das Hinzufügen und Verwalten von Informationen über den Lizenzvertrag für Software, die über die Microsoft Volume Licensing Vereinbarungen erworben wurde. Sie können Sie hierzu auch für Microsoft oder nicht-Microsoft-Software, die anderweitig erworben haben. Sie können diese Informationen in logischen Gruppen organisieren.

> [!IMPORTANT]
> Dieses Feature ist nur Komfort vorgesehenen und Genauigkeit ist nicht unbedingt. Sie sollten nicht auf, um zu bestätigen Konformität mit Microsoft Volume Licensing Vereinbarungen verlassen. Microsoft werden mögliche gegen untersuchen erfassten Daten, oder Einhaltung Lizenzvertrag, die Sie mit uns möglicherweise nicht verwenden.
>
> Lizenzen, die Sie Intune hinzufügen wirken sich nicht auf Ihre Lizenz Vereinbarungen oder Ansprüche die Software verwenden aus. Beispielsweise, wenn Sie ein paar Lizenzvertrag/aus Intune löschen möchten, führen Sie nicht zu löschen oder nicht mehr beantworten Lizenzvertrag, die zwischen Ihnen und Microsoft vorhanden sind.

Klicken Sie im Arbeitsbereich **Lizenzen** der Intune-Verwaltungskonsole können Sie folgende Aktionen ausführen:

-   Hinzufügen und Bearbeiten von Microsoft Volume Licensing Agreements.

-   Hinzufügen und Bearbeiten von anderen Vereinbarungen licensing Software.

-   Verwalten von Lizenzen und Gruppen.

-   Vergleichen Sie die Berechtigungsinformationen, die Intune über Volume Licensing Service Center (VLSC) den Bestand einer Microsoft-Software, die auf den verwalteten PCs für Windows Intune Programm erkennt abruft.

Darüber hinaus können Sie Berichte, die Installation anzeigen generieren und Anzahl der Lizenzen für Software-Titel. Lizenz Berichte können Sie Ihre Position abgeschlossen Lizenz für Microsoft-Software und nicht-Microsoft-Software-Titel bewerten helfen.

> [!TIP]
> Im Arbeitsbereich für **Lizenzen** wird nicht in der Verwaltungskonsole angezeigt, bis Sie mindestens ein Windows-PC mit dem Computer mit Windows Intune-Client verwalten.

## Hinzufügen von Vereinbarungen Microsoft-Volumenlizenzierung
Vereinbarungen Intune Volume Licensing bieten Lizenzinformationen für Software, die über die Microsoft Volume Licensing Vereinbarungen erworben wurde. Durch die Bereitstellung zugeordnete Paare Vertrag Zahlen können Intune Microsoft Volume Licensing Vereinbarungen hinzugefügt werden. Die Zahlen Vertrag oder Autorisierung müssen die richtige Lizenz oder Registrierung Zahlen übereinstimmen. Vertrag Zahl Paare werden abgerufen werden, wenn Sie Ihre Lizenz Agreements aus der [Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842)erwerben.

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://account.manage.microsoft.com/admin/default.aspx) **Lizenzen**aus.

2.  Wählen Sie auf der Seite **Hinzufügen Vereinbarungen** unter **Vertragstyp auswählen** **Volume Licensing-Vertrag**ein.

3.  Wählen Sie im Abschnitt **Vertrag Einzelheiten hinzufügen** , ob Sie eine Datei hochladen oder die Details manuell hinzufügen möchten.

    -   **Hochladen einer CSV-Datei, die Vertrag Details enthält**. Wählen Sie **Durchsuchen** , und wählen Sie die CSV-Datei, die Sie hochladen möchten.

        -   Die Datei kann entweder zwei oder drei Spalten enthalten. zwei für Vertrag Paare allein oder drei, wenn Sie einen Anzeigenamen für jedes Paar Vertrag hinzufügen möchten.

        -   Die Gesamtzahl der Zeichen in ein paar Vertrag darf 16 ASCII-Zeichen nicht überschreiten.

        -   Nur ASCII-Zeichen werden unterstützt.

        -   Die folgenden Zeichen dürfen nicht in den Vertrag Namen: **~! @ # $ ^ &amp; & #42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Leerzeichen sind in den Namen zulässig.

        -   Der Dateinamen darf maximal 128 Zeichen lang sein.

        -   Die Datei muss mindestens einen Vertrag Paar enthalten und kann nicht mehr als 5.000 Vertrag-Paare enthalten.

        **Format für die Datei**

        Sie können diese Datei erstellen, indem Sie eine nur-Text-Dokument in einem der folgenden Formate, je nach Organisationstyp, den Sie bei der VLSC registriert haben Ihre Vertrag-Paare hinzu. Angeben eines Vertrag Zahl pro Zeile an.

        -   **Öffnen Wert für den Kunden:** *Vertrag Zahl*, *Wiederholen Sie die Anzahl der Vereinbarung*, *Vertrag Namen*

        -   **Kunden öffnen:** *Autorisierung Zahl*, *Verwandte Lizenz Zahl*; *Vertrag Namen*

        -   **Auswählen und Enterprise-Kunden:** *Vertrag Zahl*, *Verwandte Registrierungs-Anzahl*, *Vertrag Namen*

        Das Formular **Hinzufügen Vereinbarungen** aufgefordert, die für diese Datei zu navigieren, wenn Sie eine neue Vereinbarung hinzufügen.

        So sieht ein Beispiel für die CSV-Dateiinhalt für einen Kunden Wert öffnen.

        `01-07001, 01-07001, Office agreements`

    -   **Details der Vereinbarung zum manuell hinzufügen**. Geben Sie die folgende Informationen ein, und geben Sie dann den Vertrag Paare Zahl in den Feldern **Autorisierung/Vertrag Zahl** und **Lizenz/Registrierung/Kundennummer** . Nachdem Sie beide Zahlen eingeben möchten, wählen Sie das Symbol **Hinzufügen Paar** Speichern Ihrer Rufnummern, und fügen Sie ein neues Paar optional.

        -   **Namen Vertrag** - Geben Sie einen eindeutigen Namen für den Vertrag.

            Der Name Vertrag kann maximal 256 Zeichen, und die folgenden Zeichen nicht enthalten: **~! @ # $ ^ &amp; & #42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Leerzeichen sind in den Namen zulässig.

        -   **Autorisierung/Vertrag Zahl** – Geben Sie die Anzahl der Lizenz Paar Autorisierung/Vertrag.

        -   **Lizenz/Registrierung/Kundennummer** – Geben Sie die Lizenz/Registrierung/Kunden Anzahl der Lizenz Paar.

        > [!NOTE]
        > Wenn Sie mehrere Vertrag Zahl Paare hinzufügen, erstellt Intune einen Vertrag mit dem Namen, den Sie angeben, und alle Paare, die Sie hinzugefügt haben, sind ein Teil dieses Vertrags an.

    Sie können auswählen, **+** auf einem anderen Vertrag Zahl Paar hinzuzufügen oder **-** So entfernen Sie ein paar Vertrag bereits eingegeben haben.

4.  Führen Sie im Bereich **Lizenz Gruppe wählen Sie** eine der folgenden Aktionen aus:

    -   **Hinzufügen von den Verträgen der Gruppe nicht zugewiesene Agreements**. Wählen Sie diese Option, wenn Sie nicht die neue Kaufverträge einer Lizenzgruppe hinzufügen möchten.

    -   **Hinzufügen die Vereinbarungen zu einer neuen Lizenzgruppe**. Geben Sie einen Namen für die neue Lizenzgruppe.

    -   **Hinzufügen von den Verträgen zu einer vorhandenen Lizenzgruppe**. Wählen Sie in der Liste **Gruppenname** der Lizenzgruppe, die Sie die Verträgen hinzufügen möchten.

5.  Wählen Sie **OK**aus.

Die Ansicht **Alle Vereinbarungen** wird angezeigt, und Intune Verbindung mit der Microsoft-VLSC den Vertrag Zahl Paare überprüft, die Sie zur Verfügung gestellt wurde.

Wählen Sie **Jetzt aktualisieren**, um die Lautstärke Lizenzinformationen zu aktualisieren, nachdem Sie auf der Seite **Lizenzen Übersicht** Lizenzvertrag in Intune, hinzugefügt haben. Diese Aktion ruft die aktuellen Lizenzinformationen von der [Microsoft Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT]
> Bis Sie Informationen über die Volumenlizenzierung aktualisieren, wird möglicherweise andere Informationen in der Liste Agreements und die Informationen zum Anspruch auf der Seite **Übersicht Vereinbarungen** angezeigt.

Nachdem Sie die Lautstärke Lizenzinformationen aktualisieren, können Sie die Lizenzinformationen für Ihre erkannt Microsoft-Software im Arbeitsbereich **Apps** vergleichen. Sie können außerdem die folgenden Lizenz Berichte ausführen:

-   **Berichte zur Lizenzen erwerben** – können Sie die lizenzierte Software in Lizenzgruppen, die Sie auswählen, um Lücken in Schutz finden anzeigen.

-   **Berichte zur Lizenzen** – hilft Ihnen, festzustellen, ob Sie ausreichende Garantie Lizenz verfügen.

> [!NOTE]
> Das **Produkttitel** für alle Microsoft-Volumenlizenzierung Vereinbarungen angezeigt wird, ist **nicht verfügbar**.

## Hinzufügen und Bearbeiten von anderen Vereinbarungen licensing software
Sie können auch Intune andere Typen von Lizenzvertrag nachsehen zusätzlich zu Microsoft-Volumenlizenzierung Vereinbarungen hinzufügen. Nicht-Microsoft-Software oder Microsoft-Software, die bei einem Einzelhändler erworben wurde, können diese Vereinbarungen einbeziehen.

> [!IMPORTANT]
> Sie müssen mindestens ein Windows-PC in Intune registriert ist, bevor Sie eine Vereinbarung hinzufügen können.  Darüber hinaus muss mindestens einen registrierten Computer ein bürgerliches Software-Paket hochgeladen haben, die Sie verwenden, um einen Lizenzvertrag hinzufügen möchten.

### Hinzufügen von anderen Vereinbarungen software

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://account.manage.microsoft.com/admin/default.aspx) **Lizenzen**aus.

2.  Wählen Sie im Abschnitt **Andere Software Lizenzierung Vereinbarungen** **Vereinbarungen hinzufügen** aus.

3.  Wählen Sie unter **Vertragstyp auswählen** der Seite **Hinzufügen Vereinbarungen** **anderen Software-Lizenzvertrag** aus.

4.  Geben Sie im Bereich **Vertrag Einzelheiten hinzufügen** Folgendes ein:

    -   **Vertrag Namen** (erforderlich). Der Name Vertrag kann maximal 256 Zeichen, und die folgenden Zeichen nicht enthalten: **~! @ # $ ^ &amp; & #42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Leerzeichen sind in den Namen zulässig.

    -   **Publisher** (erforderlich). Beim Starten einen Publisher-Namen eingeben, ruft der Dienst alle Publisher-Namen, die die Buchstaben enthalten, die Sie eingeben. Wenn Sie "Weiche" eingeben, ruft Dienst beispielsweise alle Publisher-Namen, die als Teil des Namens, wie etwa "Microsoft" und "Microsoft Research." "Weiche" enthalten. Die Namen von Publisher werden aus dem Katalog der Software Anlage abgerufen. Sie müssen den Herausgeber aktivieren, bevor Sie den Produkttitel eingeben können.

        > [!IMPORTANT]
        > Das Unternehmen, das Sie hinzufügen möchten, möglicherweise in dieser Liste nicht angezeigt. Sie können nur Software Agreements für Unternehmen hinzufügen, die bereits im Katalog Anlage Software vorhanden sind. Microsoft versucht kontinuierlich die am häufigsten verwendeten Softwaretitel hinzuzufügen. Wenn Sie eine Einladung zu einem Unternehmen, die in der Liste senden möchten, möchten auf der [Website Intune Uservoice](https://microsoftintune.uservoice.com/).

    -   **Produkttitel** (erforderlich). Beim Starten des Produkttitel eingeben, ruft der Dienst alle Produkt-Titel, die Buchstaben enthalten, die Sie eingeben. Bevor Sie einen **Titel Produkt**angeben können, müssen Sie eine **Publisher** angeben.

    -   **Lizenzanzahl** (erforderlich). Geben Sie die Anzahl der erworbenen Lizenzen aus.

    -   **Lizenz beginnt am**. Geben Sie das Anfangsdatum Lizenz.

    -   **Lizenz Enddatum ein**. Geben Sie das Enddatum Lizenz.

    -   **Vertrag Details**. Optional können Sie Kontaktinformationen, Registrierungsschlüssel und andere Informationen angeben.

5.  Führen Sie im Bereich **Lizenz Gruppe wählen Sie** eine der folgenden Aktionen aus:

    -   Wählen Sie **die Verträgen in der Gruppe nicht zugewiesene Vereinbarungen hinzufügen** , wenn Sie nicht die neue Kaufverträge für eine Lizenz für neuen oder vorhandenen Gruppe hinzufügen möchten. Sie können die Vereinbarungen zu einem beliebigen Zeitpunkt Lizenz benutzerdefinierte Gruppen hinzufügen.

    -   Wählen Sie die neue Kaufverträge für zu einer neuen Lizenzgruppe hinzufügen **die Verträgen zu einer neuen Lizenzgruppe hinzufügen** . Sie werden aufgefordert, einen Namen für die neue Lizenzgruppe anzugeben.

    -   Wählen Sie die neue Kaufverträge zu einer vorhandenen Lizenzgruppe hinzufügen **die Vereinbarungen zu einer vorhandenen Lizenzgruppe hinzufügen** . Wählen Sie in der Liste **Gruppenname** der Lizenzgruppe, die Sie die Verträgen hinzufügen möchten.

6.  Wählen Sie **OK**aus.

Die Listenansicht **Alle Vereinbarungen** wird angezeigt.

## Verwalten von Vereinbarungen Lizenz
Software zur Lizenzierung Vereinbarungen Lizenzgruppen hinzugefügt werden können. Lizenzgruppen können Sie Ihre Lizenz Agreements in einer anderen Einheit organisieren, die für Ihre Organisation Wahrheitswert sind. Darüber hinaus können Sie Lizenzvertrag löschen, die Sie zuvor erstellt haben.

|||
|-|-|
|Aufgabe|Details|
|Erstellen einer Lizenzgruppe|Wählen Sie auf der Seite **Übersicht** des Arbeitsbereichs **Lizenzen** **Lizenz Gruppe erstellen** aus dem Menü **Aufgaben** . **Hinweis:** Sie können maximale insgesamt 500 Lizenzgruppen erstellen.|
|Umbenennen einer Lizenzgruppe|Klicken Sie im Arbeitsbereich **Lizenzen** wählen Sie eine Lizenzgruppe aus, und wählen Sie dann im Menü **Tasks** **Lizenz Gruppe bearbeiten** .|
|Löschen einer Lizenzgruppe|Klicken Sie im Arbeitsbereich **Lizenzen** wählen Sie eine Lizenzgruppe aus, und wählen Sie dann im Menü **Tasks** **Lizenz Gruppe löschen** . **Tipp:** Noch Lizenzen, die in der Gruppe gelöscht wurden, werden in der Gruppe **nicht zugewiesene Vereinbarungen** Lizenz verschoben.|
|Löschen eines-Lizenzvertrags|Klicken Sie im Arbeitsbereich **Lizenzen** wählen Sie eine Vereinbarung aus, und wählen Sie dann auf **Löschen**. **Tipp:** Nach dem Löschen von Volume Licensing Vereinbarungen zum Aktualisieren der Lizenzinformationen wählen Sie **Jetzt aktualisieren** auf der Seite **Lizenzen** oder auf der Registerkarte **Allgemein** für eine bestimmte Lizenzgruppe.|
