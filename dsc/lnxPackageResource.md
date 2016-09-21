# DSC für Linux NxPackage Ressource

Die **NxPackage** Ressource in PowerShell gewünscht Zustand Konfiguration (DSC) stellt ein Verfahren zum Verwalten von Paketen auf einem Knoten Linux.

## Syntax

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| Namen| Der Name des Pakets für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Stellen Sie sicher| Bestimmt, ob Sie prüfen, ob das Paket vorhanden ist. Legen Sie diese Eigenschaft auf "Präsentieren", um sicherzustellen, dass das Paket vorhanden ist. Legen Sie dafür den "Abwesend", um sicherzustellen, dass das Paket nicht vorhanden ist. Der Standardwert ist "Präsentieren".|  
| PackageManager| Unterstützte Werte sind "Yum", "apt" und "Zypper". Gibt die Paketmanager, verwenden Sie beim Installieren von Paketen an. Wenn der **Dateipfad** angegeben wird, wird des angegebenen Pfads zum Installieren des Pakets verwendet werden. Andernfalls wird ein Paket-Manager zur Installation des Pakets aus einem vorkonfiguriertes Repository verwendet werden. Wenn weder **PackageManager** noch **Dateipfad** angegeben werden, wird das Standard-Paket-Manager für das System verwendet werden.| 
| Dateipfad| Der Dateipfad, in dem sich das Paket befindet| 
| PackageGroup| Wenn **$true**, den **Namen** erwartet wird, um den Namen einer Gruppe Paket für die Verwendung mit einem **PackageManager**handeln. **PacakgeGroup** ist nicht gültig, wenn ein **Dateipfad**bereitstellen.| 
| Argumente auf:| Eine Textzeichenfolge Argumente, bei die das Paket genau bereitgestellten übergeben wird.| 
| Rückgabecode| Die erwarteten zurück Code. Wenn die tatsächliche Code zurück entspricht nicht der Erwartungswert hier bereitgestellt, die Konfiguration, einen Fehler zurückgeben.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die **ID** für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

Im folgende Beispiel wird sichergestellt, dass das Paket mit dem Namen "Httpd" auf einem Linux-Computer mit dem "Yum" Paket-Manager installiert ist.

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```
