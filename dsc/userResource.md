#DSC Benutzer Ressourcen#

 
>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0


Die __Benutzer__ Ressource in Windows PowerShell gewünscht Bundesstaat Konfiguration (DSC) stellt ein Verfahren zum Verwalten der lokalen Benutzerkonten auf die Zielknoten.


##Syntax##

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Benutzername| Zeigt an, den Namen des Kontos, für den Sie einen bestimmten Zustand sicherstellen möchten.| 
| Beschreibung| Zeigt an, die Beschreibung, die Sie für das Benutzerkonto verwenden möchten.| 
| Deaktiviert| Zeigt an, ob das Konto aktiviert ist. Legen Sie diese Eigenschaft auf __$true__ , um sicherzustellen, dass dieses Konto deaktiviert ist, und legen Sie ihn auf __$false__ um sicherzustellen, dass es aktiviert ist.| 
| Stellen Sie sicher| Zeigt an, ob das Konto vorhanden ist. Legen Sie diese Eigenschaft auf "Präsentieren", um sicherzustellen, dass das Konto vorhanden ist, und legen Sie ihn auf "Abwesend", um sicherzustellen, dass das Konto nicht vorhanden ist.| 
| FullName| Stellt eine Zeichenfolge mit dem vollständigen Namen, die, den Sie für das Benutzerkonto verwenden möchten.| 
| Kennwort| Zeigt an, das Kennwort ein, die, das Sie für dieses Konto verwenden möchten. | 
| PasswordChangeNotAllowed| Zeigt an, ob der Benutzer das Kennwort ändern kann. Legen Sie diese Eigenschaft auf __$true__ , um sicherzustellen, dass der Benutzer des Kennworts ändern nicht, und legen Sie ihn auf __$false__ Benutzer, das Kennwort ändern können. Der Standardwert ist __$false__.| 
| PasswordChangeRequired| Zeigt an, ob der Benutzer muss bei der nächsten Anmeldung das Kennwort ändern. Legen Sie diese Eigenschaft auf __$true__ an, wenn der Benutzer muss das Kennwort ändern. Der Standardwert ist __$true__.| 
| PasswordNeverExpires| Zeigt an, ob das Kennwort abläuft. Um sicherzustellen, dass das Kennwort für dieses Konto werden nie ablaufen, legen Sie diese Eigenschaft auf __$true__und auf __$false__ festzulegen, wenn das Kennwort abläuft. Der Standardwert ist __$false__.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die ID für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst __Ressourcenname__ und deren __ResourceType__handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = “[Group]GroupExample" # Configures GroupExample first
}
```
