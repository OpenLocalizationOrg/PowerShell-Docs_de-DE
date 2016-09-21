# DSC Registrierung Ressourcen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die **Registrierung** Ressource in Windows PowerShell gewünscht Zustand Konfiguration (DSC) stellt ein Verfahren zum Verwalten von Registrierungsschlüsseln und Werte auf einem Zielknoten.

## Syntax

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Schlüssel| Gibt den Pfad des Registrierungsschlüssels für die Sie einen bestimmten Zustand sicherstellen möchten. Dieser Pfad muss die Struktur enthalten.| 
| Wert| Zeigt den Namen des den Registrierungseintrag an.| 
| Stellen Sie sicher| Zeigt an, ob die Taste und Wert vorhanden sind. Um sicherzustellen, dass dies der Fall, legen Sie diese Eigenschaft auf "Präsentieren" ein. Um sicherzustellen, dass sie nicht vorhanden sind, legen Sie die Eigenschaft "Abwesend" ein. Der Standardwert ist "Präsentieren".| 
| Erzwingen, dass| Wenn der angegebene Registrierungsschlüssel vorhanden ist, wird Sie __sofort__ mit dem neuen Wert überschrieben.| 
| Hex| Zeigt an, ob Daten im hexadezimalen Format ausgedrückt werden. Wenn angegeben, werden die DWORD-/ QWORD Wertdaten in hexadezimale Format angezeigt. Nicht gültig für andere Typen. Der Standardwert ist __$false__.| 
| DependsOn| Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die ID für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst __Ressourcenname__ und deren __ResourceType__handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| Die Daten für den Wert.| 
| Werttyp| Zeigt den Typ des Werts an. Die unterstützten Typen sind: 
<ul><li>Zeichenfolge (REG_SZ)</li>


<li>Binärdatei (REG-BINARY)</li>


<li>DWORD 32-Bit (REG_DWORD)</li>


<li>QWORD 64-Bit (REG_QWORD)</li>


<li>Mit mehreren Zeichenfolgen (REG_MULTI_SZ)</li>


<li>Erweiterbar Zeichenfolge (REG_EXPAND_SZ)</li></ul>

## Beispiel
```powershell
Registry RegistryExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Key = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
    ValueName = "TestValue"
    ValueData = "TestData"
}
```

