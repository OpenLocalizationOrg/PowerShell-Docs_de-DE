# DSC Umgebung Ressource

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

Die __Umgebung__ Ressource in Windows PowerShell gewünschten Zustand Konfiguration (DSC) bietet einen Mechanismus zum Verwalten von Umgebungsvariablen des Systems.

## Syntax
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen der Umgebungsvariablen für die Sie einen bestimmten Status sicherstellen möchten.| 
| Stellen Sie sicher| Gibt an, ob eine Variable vorhanden ist. Legen Sie diese Eigenschaft auf __vorhanden__ Umgebungsvariablen erstellen, wenn es ist nicht vorhanden, oder um sicherzustellen, dass den Wert ermittelt, was durch die __Value__ -Eigenschaft bereitgestellt wird, wenn die Variable bereits vorhanden ist. Legen Sie es auf __Abwesend__ an die Variable löschen, sofern vorhanden.| 
| Path| Definiert die Umgebungsvariable, die konfiguriert wird. Diese Eigenschaft auf __$true__ festgelegt, wenn die Variable __Path__ -Variablen ist; anderenfalls auf __$false__festgelegt. Der Standardwert ist __$false__. Wenn die Variable konfiguriert wird der __Pfad__ ist, wird der durch die __Value__ -Eigenschaft angegebene Wert den vorhandenen Wert angefügt werden.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Beispielsweise wenn zunächst die ID des Resource-Skriptblock Konfiguration, die Sie ausführen möchten, __ResourceName wird__ und dieses Typs __ResourceType ist__, die Syntax für die Verwendung dieser Eigenschaft lautet `DependsOn = "[ResourceType]ResourceName"`.| 
| Wert| Der Wert der Umgebungsvariablen zugewiesen.| 

## Beispiel

Im folgende Beispiel wird sichergestellt, dass __TestEnvironmentVariable__ vorhanden ist und es den Wert __TestValue hat__. Wenn es nicht vorhanden ist, wird er erstellt.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
