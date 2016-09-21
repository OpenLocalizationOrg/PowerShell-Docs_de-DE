# DSC Skript-Ressourcen

 
> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **Skript** in Windows PowerShell gewünscht Bundesstaat Konfiguration (DSC) stellt ein Verfahren zum Ausführen von Windows PowerShell-Skriptblöcke auf die Zielknoten.

## Syntax

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| GetScript| Stellt einen Block von Windows PowerShell-Skript, das ausgeführt wird, wenn Sie das Cmdlet " [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) " aufrufen. Dieses Zeitraums muss eine Tabelle zurück.| 
| SetScript| Stellt einen Block von Windows PowerShell-Skript an. Wenn Sie das Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) aufrufen, wird der Block **TestScript** zuerst ausgeführt. Die **TestScript** blockieren **$false**zurück, wird die **SetScript** blockieren ausgeführt. Des Zeitraums **TestScript** **$true**zurück, wird die **SetScript** blockieren nicht ausgeführt.| 
| TestScript| Stellt einen Block von Windows PowerShell-Skript an. Wenn Sie das Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) aufrufen, wird dieser Block ausgeführt. Wenn **$false**zurückgegeben wird, wird der SetScript Block ausgeführt. Wenn **$true**zurückgegeben wird, wird die SetScript blockieren nicht ausgeführt. Des Zeitraums **TestScript** wird auch ausgeführt, wenn Sie das Cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aufrufen. Jedoch in diesem Fall funktionieren des Zeitraums **SetScript** nicht unabhängig davon, welcher Wert des Zeitraums TestScript gibt. Des Zeitraums **TestScript** muss True zurück, wenn die tatsächliche Konfiguration der aktuellen Konfiguration der gewünschten Status und falsch übereinstimmt, wenn es nicht übereinstimmt. (Die aktuelle gewünschten Statuskonfiguration wird der letzten Stellvertreter den Knoten, der DSC verwendet wird.)| 
| Anmeldeinformationen| Zeigt an, die Anmeldeinformationen ein, verwenden zum Ausführen dieses Skripts, wenn Anmeldeinformationen erforderlich sind.| 
| DependsOn| Zeigt an, dass die Konfiguration von einer anderen Ressource ausführen muss, bevor diese Ressource konfiguriert ist. Angenommen, die ID für die Ressource Konfiguration Skript Blöcke, das Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.

## Beispiel
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

