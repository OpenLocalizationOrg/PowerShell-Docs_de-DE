# Belohnung von PowerShell-Dokumentation

## Melden Sie sich ein CLA

Bevor Sie auf alle Repositories PowerShell teilnehmen können, müssen Sie [eine Microsoft Beitrag Lizenzierung Vereinbarung (CLA) anmelden](https://cla.microsoft.com/). Wenn Sie bereits zu PowerShell Repositories in der Vergangenheit Herzlichen Glückwunsch beigetragen haben! Sie haben diesen Schritt bereits durchgeführt.

## Schreiben von PowerShell-Dokumentation

Einer der am einfachsten PowerShell contribute ist beim Schreiben und Bearbeiten von Dokumentation hilft. Alle unsere Dokumentation auf GitHub gehostet wird die Verwendung von [GitHub Flavored Abzugsverteilung(en)](https://help.github.com/articles/github-flavored-markdown/)geschrieben.

Zum [Bearbeiten eine vorhandene Datei](https://help.github.com/articles/editing-files-in-another-user-s-repository/)navigieren Sie zu es und klicken auf die Bearbeitungsschaltfläche "". GitHub erstellt automatisch Ihre eigenen Verzweigung unsere Repository, in dem Sie die Änderungen vorgenommen haben können. Sobald Sie fertig sind, speichern Sie die Änderungen, und Übermitteln einer Anforderung Pull abzurufenden Ihre Änderungen vor-zusammengeführt. Nach Ihrer Pull wird die Anforderung erstellt, 

Wenn Sie neue Dokumentation teilnehmen möchten, überprüfen Sie zunächst für [Probleme, die als "in Bearbeitung" gekennzeichnet](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress) , um sicherzustellen, dass Sie nicht vorhaben duplizieren sind.
Wenn niemand scheint arbeiten, was Sie geplant haben:
* Öffnen Sie ein neues Problem als "in Bearbeitung" markiert Personen mitteilen was Sie gerade arbeiten
* Erstellen einer Verzweigung unseres Repositorys und Starten von neuen Abzugsverteilung(en)-basierte Dokumentation hinzugefügt
* Wenn Sie in der Dokumentation zu contribute bereit sind, senden Sie eine Pull-Anforderung an die *master* -Verzweigung

#### GitHub Flavored Abzugsverteilung(en) (GFM)

Alle Artikel in diesem Repository verwendet [GitHub Flavored Abzugsverteilung(en) (GFM)](https://help.github.com/articles/github-flavored-markdown/).

Wenn für einen guten-Editor angezeigt werden, außerdem Try [Abzugsverteilung(en)](http://markdownpad.com/) GitHub oder über eine Weboberfläche Abzugsverteilung(en) mit zur Bearbeitung Syntax markieren und die Möglichkeit, eine Vorschau Änderungen anzuzeigen. 

Einige der grundlegendere GFM Syntax enthält:

* **Zeilenumbrüche im Vergleich zu Absätzen:** In Abzugsverteilung(en) ist kein HTML `<br />` oder `<p />` Element. Stattdessen wird ein neuer Absatz durch eine leere Zeile zwischen zwei Blöcke von Text festgelegt.

> **Hinweis**: Fügen Sie nach jedem Satz vereinfacht die Befehlszeilenausgabe von Diffs und Verlauf einer einzelnen Zeilenumbruchzeichen hinzu.
Dies ist nicht aktuell in allen PowerShell-Dokumente eingeführt, aber wir arbeiten in Richtung er über einen Zeitraum. Helfen können. 

* **Kursiv:** Der HTML-Code `<em>some text</em>` als geschrieben wird `*some text*`
* **Fett:** Der HTML-Code `<strong>some text</strong>` Element wird als geschrieben. `**some text**`
* **Überschriften:** HTML-Überschriften werden mit benannt `#` Zeichen am Anfang der Linie. Die Anzahl der `#` Zeichen entspricht der hierarchischen Ebene der Überschrift (z. B. `#` = `<h1>` und `###` = ```<h3>```).
* **Nummerierte Listen:** So tätigen eine nummerierte (geordnete) Liste Starten Sie die Zeile mit `1. `.  
Wenn Sie mehrere Elemente innerhalb einer einzelnen List-Element möchten, formatieren Sie Ihrer Liste wie folgt:
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
Diese Ausgabe zu:

1.  Legen Sie für das erste Element (etwa folgende) einen Tabstopp nach die 1. 

    Ein zweites Element (wie dem folgenden) aufnehmen möchten, fügen Sie einen Zeilenumbruch nach dem ersten und richten Sie Einzüge aus.

* **Aufzählungen:** Listen mit Aufzählungszeichen (ungeordnete) sind fast identisch mit sortierte Listen abgesehen davon, dass die `1. ` ist entweder mit ersetzt `* `, `- `, oder `+ `. Mehrere Element Listen funktionieren die gleiche Weise wie bei sortierte Listen.
* **Links:** Die Syntax für einen Hyperlink lautet `[visible link text](link url)`.
Links kann auch Referenzen, haben "Link und Image Zeugnisse" unten im Abschnitt erläutert werden.