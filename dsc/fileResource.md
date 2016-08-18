# DSC File-Ressource

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

File-Ressource in Windows PowerShell gewünschten Zustand Konfiguration (DSC) bietet einen Mechanismus zum Verwalten von Dateien und Ordner auf dem Zielknoten.

## Syntax
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ] 
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ] 
    [ MatchSource = [bool] ]
}
```

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| DestinationPath| Gibt den Speicherort, in dem Sie den Status einer Datei oder eines Verzeichnisses sicherstellen wollen.| 
| Attribute| Gibt den gewünschten Zustand der Attribute für die Zieldatei oder das Verzeichnis an.| 
| Prüfsumme| Gibt den Typ der Prüfsumme beim bestimmen, ob zwei Dateien identisch sind verwendet werden. Wenn __Prüfsumme__ nicht angegeben wird, wird nur der Name Datei oder ein Verzeichnis für den Vergleich verwendet. Gültige Werte sind: SHA-1, SHA-256, SHA-512, CreatedDate, ModifiedDate.| 
| Inhalt| Gibt den Inhalt einer Datei, wie etwa einer bestimmten Zeichenfolge.| 
| Credential| Gibt an die Anmeldeinformationen, die auf Ressourcen zugreifen, beispielsweise Quelldateien, die erforderlich sind, wenn eine solche Zugriff erforderlich ist.| 
| Stellen Sie sicher| Gibt an, ob die Datei oder das Verzeichnis vorhanden ist. Legen Sie diese Eigenschaft auf "Abwesend", um sicherzustellen, dass die Datei oder das Verzeichnis nicht vorhanden ist. Legen Sie es auf "Vorhanden", um sicherzustellen, dass die Datei oder das Verzeichnis vorhanden ist. Der Standardwert ist "Vorhanden".| 
| Kraft| Bestimmte Dateioperationen (wie eine Datei überschreiben oder Löschen eines Verzeichnisses an, das nicht leer ist) führt einen Fehler. Mithilfe der Force-Eigenschaft wird diese Fehler außer Kraft gesetzt. Der Standardwert lautet __$false__.| 
| Recurse| Gibt an, wenn Unterverzeichnissen enthalten sind. Legen Sie diese Eigenschaft auf __$true__ , um anzugeben, dass Sie Unterverzeichnisse eingeschlossen werden soll. Der Standardpfad lautet __$false__. **Hinweis**: Diese Eigenschaft ist nur gültig, wenn die Eigenschaft Typ in Verzeichnis festgelegt ist.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die ID eines den Skriptblock Ressource Konfiguration, die Sie ausführen möchten, zunächst __ResourceName ist__ und dieses Typs __ResourceType ist__, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 
| SourcePath| Gibt den Pfad aus dem File- oder Folder-Ressource kopiert.| 
| Typ| Gibt an, ob die Ressource konfiguriert wird, ein Verzeichnis oder eine Datei ist. Legen Sie diese Eigenschaft auf "Verzeichnis", um anzugeben, dass die Ressource ein Verzeichnis ist. Legen Sie ihn auf "Datei", um anzugeben, dass die Ressource um eine Datei handelt. Der Standardwert ist "Datei".| 
| MatchSource| Wenn auf den Standardwert __$false__festgelegt, klicken Sie dann alle Dateien auf dem Quellserver (beispielsweise die Dateien A, B und C) an das Ziel der ersten hinzugefügt werden die Konfiguration wird angewendet. Wenn die Quelle eine neue Datei (D) hinzugefügt wird, wird es an das Ziel nicht hinzugefügt werden, auch wenn die Konfiguration später erneut angewendet wird. Wenn der Wert __$true__ist, werden jedes Mal, wenn die Konfiguration angewendet wird, an das Ziel neue Dateien, die anschließend finden Sie auf der Quelle (wie in diesem Beispiel D Datei) hinzugefügt.| 

## Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die-Ressource verwenden, um sicherzustellen, dass ein Verzeichnis mit dem Pfad `C:\Users\Public\Documents\DSCDemo\DemoSource` auf eine Datenquelle Computer (wie der Server "Pull") ist auch vorhanden (zusammen mit allen Unterverzeichnissen) auf dem Zielknoten. Außerdem schreibt eine Nachricht Bestätigungstest in das Protokoll nach Abschluss des Vorgangs, und enthält eine Anweisung, um sicherzustellen, dass der Vorgang Überprüfung der Datei vor der Protokollierung ausgeführt wird.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```
