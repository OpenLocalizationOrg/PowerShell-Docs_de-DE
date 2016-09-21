# DSC WindowsProcess Ressourcen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die **WindowsProcess** Ressource in Windows PowerShell gewünscht Bundesstaat Konfiguration (DSC) stellt ein Verfahren zum Konfigurieren von Prozessen auf einem Zielknoten.

## Syntax

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Argumente auf:| Zeigt an, an den Prozess als zu übergebenden Argumente eine Zeichenfolge-ist. Wenn Sie mehrere Argumente übergeben müssen, setzen sie alle in dieser Zeichenfolge.| 
| Pfad| Zeigt den Pfad für die ausführbare Prozess an. Wenn Sie diese Eigenschaft auf den Namen des Programms festlegen, wird in der Variablen __Path__ DSC suchen. Wenn Sie einen vollqualifizierten Domänennamen eingeben, muss der Prozess es vorhanden sein, da DSC nicht die Variable __Path__ in diesem Fall prüfen.| 
| Anmeldeinformationen| Zeigt an, die Anmeldeinformationen für den Vorgang starten.| 
| Vergewissern Sie sich| Zeigt an, ob der Vorgang vorhanden ist. Legen Sie diese Eigenschaft auf "Präsentieren", um sicherzustellen, dass der Prozess vorhanden ist. Legen Sie sie andernfalls auf "Abwesend" ein. Die Standardeinstellung ist "Präsentieren".| 
| DependsOn | Zeigt an, dass die Konfiguration von einer anderen Ressource ausführen muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die ID für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst __Ressourcenname__ und deren __ResourceType__handelt, die Syntax für die Verwendung dieser Eigenschaft ist "DependsOn"[ResourceType] Ressourcenname"=''.| 
| StandardErrorPath| Gibt den Pfad zum Schreiben des Standardfehlers an. Gibt es eine vorhandene Datei wird überschrieben.| 
| StandardInputPath| Gibt den Standardspeicherort für die Eingabewerte an.| 
| StandardOutputPath| Gibt den Speicherort für die standardmäßige Ausgabe schreiben an. Gibt es eine vorhandene Datei wird überschrieben.| 
| WorkingDirectory| Gibt die Position, die als aktuell geöffneten Verzeichnis für den Prozess verwendet wird.| 
