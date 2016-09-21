# DSC für Linux NxFileLine Ressource

**NxFileLine** Ressource in PowerShell gewünscht Bundesstaat Konfiguration (DSC) bietet ein Verfahren zum Verwalten Linien innerhalb einer Konfigurationsdatei auf einem Knoten Linux.

## Syntax

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| Dateipfad| Der vollständige Pfad zu der Datei zum Verwalten von Zeilen auf dem Zielknoten.| 
| ContainsLine| Eine Linie, um sicherzustellen, die in der Datei vorhanden ist. Wenn es nicht in der Datei vorhanden ist, wird diese Zeile zu der Datei angefügt. **ContainsLine** obligatorisch ist, aber auf eine leere Zeichenfolge festgelegt werden können ('ContainsLine = ''') Wenn sie nicht benötigt wird.| 
| DoesNotContainPattern| Muster eines regulären Ausdrucks für Zeilen, die nicht in der Datei vorhanden sein sollten. Für alle Zeilen, die in der Datei vorhanden sind, die diesem regulären Ausdruck übereinstimmen, werden die Zeile aus der Datei entfernt.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die **ID** für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

In diesem Beispiel wird veranschaulicht, wie mit der Ressource **NxFileLine** Konfigurieren der `/etc/sudoers` Datei sicherstellen, dass des Benutzers: Monuser als nicht Requiretty konfiguriert ist.

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

