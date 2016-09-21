# DSC Service-Ressourcen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0


Die **Dienst** Ressource in Windows PowerShell gewünscht Zustand Konfiguration (DSC) stellt ein Verfahren zum Verwalten von Diensten auf dem Zielknoten.

## Syntax

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
}
```

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Namen| Zeigt den Dienstnamen an. Beachten Sie, dass manchmal anders als der angezeigte Name hier. Sie können eine Liste der Dienste und deren aktuellen Status mit dem Cmdlet Get-Dienst erhalten.| 
| BuiltInAccount| Zeigt an, das Konto anmelden für den Dienst verwendet werden soll. Sind die Werte, die für diese Eigenschaft zulässig sind: **Lokaler Dienst**, **LocalSystem**und **Netzwerkdienst**.| 
| Anmeldeinformationen| Zeigt an, für das Konto, dem der Dienst, klicken Sie unter ausgeführt wird Anmeldeinformationen. Diese Eigenschaft und die Eigenschaft __BuiltinAccount__ können nicht gemeinsam verwendet werden.| 
| DependsOn| Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die ID für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst __Ressourcenname__ und deren __ResourceType__handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 
| StartupType| Gibt den Starttyp für den Dienst an. Sind die Werte, die für diese Eigenschaft zulässig sind: **Automatische**, **Manuelle** und **deaktiviert**| 
| Bundesstaat| Gibt den Status, die, den Sie für den Dienst sicherstellen möchten.| 

## Beispiel

```powershell
Service ServiceExample
{
    Name = "TermService"
    StartupType = "Manual"
    State = "Running"
} 
```
