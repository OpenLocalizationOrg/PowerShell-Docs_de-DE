# DSC WindowsFeature Ressourcen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **WindowsFeature** in Windows PowerShell gewünscht Zustand Konfiguration (DSC) stellt ein Verfahren, um sicherzustellen, dass die Rollen und Features hinzufügen oder Entfernen von auf einem Zielknoten.

## Syntax

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Namen| Zeigt an, der Namen der Rolle oder Features, die Sie sicherstellen möchten, hinzugefügt oder entfernt wird. Dies ist der __Name__ -Eigenschaft aus dem Cmdlet [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) und nicht den Anzeigenamen für die Rolle oder das Feature entspricht.| 
| Anmeldeinformationen| Gibt die Anmeldeinformationen zum Hinzufügen oder Entfernen der Rolle oder das Feature an.| 
| Vergewissern Sie sich| Zeigt an, ob die Rolle oder das Feature hinzugefügt wird. Um sicherzustellen, dass die Rolle oder das Feature wird hinzugefügt, legen diese Eigenschaft auf "Präsentieren", um sicherzustellen, dass die Rolle oder das Feature entfernt wird, legen Sie die Eigenschaft auf "Abwesend".| 
| IncludeAllSubFeature| Legen Sie diese Eigenschaft auf __$true__ , um den Status der erforderlichen alles mit den Status des Features sicherzustellen, die Sie, durch die __Name__ -Eigenschaft angeben.| 
| LogPath| Gibt den Pfad zu einer Protokolldatei den Anbieter für die Anmeldung bei der Vorgang Ressourcen werden soll.| 
| DependsOn| Zeigt an, dass die Konfiguration von einer anderen Ressource ausführen muss, bevor diese Ressource konfiguriert ist. Angenommen, die ID für die Ressource Konfiguration Skript Blöcke, das Sie ausführen möchten zuerst __Ressourcenname__ und deren __ResourceType__handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 
| Datenquelle| Gibt den Speicherort der Quelldatei für die Installation verwendet werden soll, falls erforderlich.| 

## Beispiel
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

