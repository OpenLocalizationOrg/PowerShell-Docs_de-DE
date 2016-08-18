# DSC Group-Ressource

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Group-Ressource in Windows PowerShell gewünschten Zustand Konfiguration (DSC) bietet einen Mechanismus zum Verwalten von lokaler Gruppen auf dem Zielknoten.

##Syntax##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| GroupName| Gibt den Namen der Gruppe, der für die Sie einen bestimmten Status sicherstellen möchten.| 
| Credential| Gibt die Anmeldeinformationen erforderlich, um remote-Ressourcen zugreifen. **Hinweis**: dieses Konto muss verfügen die entsprechenden Active Directory-Berechtigungen, um der Gruppe; alle nicht lokalen Konten hinzuzufügen andernfalls, tritt ein Fehler auf.
| Beschreibung| Gibt die Beschreibung der Gruppe an.| 
| Stellen Sie sicher| Gibt an, ob die Gruppe vorhanden ist. Legen Sie diese Eigenschaft auf "Abwesend", um sicherzustellen, dass die Gruppe nicht vorhanden ist. Festlegen der Steuerelementvorlage "(Standardwert) vorhanden" wird sichergestellt, dass die Gruppe vorhanden ist.| 
| Member| Gibt an, dass Sie sicherstellen möchten, dass diese Mitglieder die Gruppe bilden.| 
| MembersToExclude| Gibt an, dass die Benutzer, die gewährleisten sollen nicht Mitglieder dieser Gruppe sind.| 
| MembersToInclude| Gibt an, dass die Benutzer, die Sie sicherstellen möchten, Mitglied der Gruppe sind.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Beispielsweise wenn zunächst die ID des Resource-Skriptblock Konfiguration, die Sie ausführen möchten, __ResourceName wird__ und dieses Typs __ResourceType ist__, die Syntax für die Verwendung dieser Eigenschaft lautet "DependsOn"[ResourceType] ResourceName"=".| 

## Beispiel

Im folgenden Beispiel wird gezeigt, wie Sie sicherstellen, dass eine Gruppe namens TestGroup nicht vorhanden ist. 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
