# DSC für Linux NxService Ressource

Die **NxService** Ressource in PowerShell gewünscht Bundesstaat Konfiguration (DSC) stellt ein Verfahren zum Verwalten der Dienste auf einem Knoten Linux.

## Syntax

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | system }  ]
    [ Enambled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## Eigenschaften
|  Eigenschaft |  Beschreibung | 
|---|---|
| Namen| Der Name des den Dienst/Dämon zu konfigurieren.| 
| Controller| Die Art des Service Controller beim Konfigurieren des Diensts verwenden.| 
| Aktiviert| Gibt an, ob der Dienst gestartet, klicken Sie auf Start wird.| 
| Bundesstaat| Gibt an, ob der Dienst ausgeführt wird. Legen Sie diese Eigenschaft auf "Beendet", um sicherzustellen, dass der Dienst nicht ausgeführt wird. Legen Sie dafür den "Ausführen", um sicherzustellen, dass der Dienst nicht ausgeführt wird.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die **ID** für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 


## Weitere Informationen

**NxService** Ressource wird nicht erstellen, ein Dienstdefinition oder das Skript für den Dienst, wenn er nicht vorhanden ist. Die Konfiguration des PowerShell gewünscht **NxFile** Ressource Ressource können Sie vorhanden ist oder die Definition Dienstdatei oder das Skript Inhalt verwalten.

## Beispiel

Im folgenden Beispiel wird die Konfiguration des Diensts "Httpd" (für Apache HTTP-Server), mit dem **SystemD** Dienstcontroller registriert.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```
