# DSC Log-Ressourcen 

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource __Log__ in Windows PowerShell gewünscht Zustand Konfiguration (DSC) stellt ein Verfahren zum Schreiben von Nachrichten in das Microsoft-Windows-optimalen Zustand Konfiguration/analytischen Ereignisprotokoll.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Nachricht| Zeigt an, die Nachricht, die Sie in der Microsoft-Windows-Desired Zustand Konfiguration/analytischen Ereignisprotokoll schreiben möchten.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Meldung Log geschrieben werden. Angenommen, die ID für die Ressource Konfiguration Skript Blöcke, das Sie ausführen möchten zuerst __Ressourcenname__ und deren __ResourceType__handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

Im folgenden Beispiel wird gezeigt, wie eine Nachricht im Ereignisprotokoll Microsoft-Windows-Desired Zustand Konfiguration/analytischen aufnehmen möchten.

> **Hinweis**: Wenn Sie mit dieser Ressource konfiguriert [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) ausführen, gibt es immer **$false**zurück.

```powershell 
Log LogExample
{
    Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
} 
```

