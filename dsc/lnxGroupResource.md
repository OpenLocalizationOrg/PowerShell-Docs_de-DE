# DSC für Linux NxGroup Ressourcen

Die **NxGroup** Ressource in PowerShell gewünscht Zustand Konfiguration (DSC) stellt ein Verfahren zum Verwalten von lokaler Gruppen auf einem Knoten Linux.

## Syntax

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| Gruppenname| Gibt den Namen der Gruppe für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Stellen Sie sicher| Bestimmt, ob Sie prüfen, ob die Gruppe vorhanden ist. Legen Sie diese Eigenschaft auf "Präsentieren", um sicherzustellen, dass die Gruppe vorhanden ist. Legen Sie dafür den "Abwesend", um sicherzustellen, dass die Gruppe nicht vorhanden ist. Der Standardwert ist "Präsentieren".| 
| Mitglieder| Gibt die Elemente, die die Gruppe Formular an.| 
| MembersToInclude| Gibt an, dass die Benutzer, die Sie sicherstellen möchten, die Mitglieder der Gruppe sind.| 
| MembersToExclude| Gibt an, dass die Benutzer, die Sie sicherstellen möchten, nicht Mitglieder der Gruppe sind.| 
| PreferredGroupID| Legt die Gruppen-Id nach Möglichkeit auf den bereitgestellten Wert. Wenn die Gruppen-Id aktuell verwendet wird, wird die nächste verfügbare Gruppe Id verwendet.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die **ID** für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

Im folgende Beispiel wird sichergestellt, dass der Benutzer "Monuser" vorhanden ist, und ein Mitglied der Gruppe "DBusers ist".

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```
