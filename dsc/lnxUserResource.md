# DSC für Linux NxUser Ressource

**NxUser** Ressource in PowerShell gewünscht Zustand Konfiguration (DSC) bietet ein Verfahren zum Verwalten der lokale Benutzer auf einem Knoten Linux.

## Syntax

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ Mode = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Eigenschaften

|  Eigenschaft |  Zeigt an, den Namen des Kontos, für den Sie einen bestimmten Zustand sicherstellen möchten. | 
|---|---|
| Benutzername| Gibt den Speicherort, in den Zustand für eine Datei oder ein Verzeichnis sicherstellen möchten.| 
| Vergewissern Sie sich| Gibt an, ob das Konto vorhanden ist. Legen Sie diese Eigenschaft auf "Präsentieren", um sicherzustellen, dass das Konto vorhanden ist, und legen Sie ihn auf "Abwesend", um sicherzustellen, dass das Konto nicht vorhanden ist.| 
| FullName| Eine Zeichenfolge, die den vollständigen Namen für das Benutzerkonto mit enthält.| 
| Beschreibung| Die Beschreibung für das Benutzerkonto.| 
| Kennwort| Der Hash des Benutzerkennworts im entsprechenden Formular für den Computer Linux. Normalerweise ist dies eine salted SHA-256 und SHA-512 Hash. Auf Debian und Ubuntu Linux kann diesen Wert mit dem Befehl Mkpasswd erstellt werden. Für andere Distros Linux kann die Crypt Berechnungsmethode des Python Crypt Bibliothek zu erstellen verwendet werden.| 
| Deaktiviert| Zeigt an, ob das Konto aktiviert ist. Legen Sie diese Eigenschaft auf **$true** , um sicherzustellen, dass dieses Konto deaktiviert ist, und legen Sie ihn auf **$false** um sicherzustellen, dass es aktiviert ist.| 
| PasswordChangeRequired| Zeigt an, ob der Benutzer das Kennwort ändern kann. Legen Sie diese Eigenschaft auf **$true** , um sicherzustellen, dass der Benutzer des Kennworts ändern nicht, und legen Sie ihn auf **$false** Benutzer, das Kennwort ändern können. Der Standardwert ist **$false**. Diese Eigenschaft wird nur ausgewertet, wenn das Benutzerkonto war zuvor nicht vorhanden ist, und erstellt wird.| 
| HomeDirectory| Der Start-Verzeichnis für den Benutzer.| 
| Gruppen-ID| Die primäre Gruppe-ID für den Benutzer.| 
| DependsOn | Zeigt an, dass die Konfiguration von einer anderen Ressource ausführen muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die ID für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst "Ressourcenname" und seinen Typ ist "ResourceType", die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

Im folgende Beispiel wird sichergestellt, dass die Benutzer "Monuser" vorhanden ist, und ein Mitglied der Gruppe "DBusers ist".

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
