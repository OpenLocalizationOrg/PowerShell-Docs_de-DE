# DSC für Linux NxScript Ressource

Die **NxScript** -Ressource im PowerShell gewünschten Zustand Konfiguration (DSC) bietet einen Mechanismus zum Ausführen von Linux-Skripts auf einem Linux-Knoten.

## Syntax

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    { Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| GetScript| Stellt ein Skript, das ausgeführt wird, wenn Sie das Cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) aufrufen. Das Skript muss mit einem Shebang, beispielsweise # beginnen! / bin/bash sein.| 
| SetScript| Bietet ein Skript. Wenn das Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) aufgerufen wird, wird die **TestScript** zuerst ausgeführt. Wenn der **TestScript** Block einen Code als 0 zurückgegeben wird, wird der **SetScript** -Block ausgeführt. Wenn die **TestScript** Exit-Code 0 zurückgibt, wird die **SetScript** nicht ausgeführt. Das Skript muss mit einem Shebang beginnen, wie `#!/bin/bash`.| 
| TestScript| Bietet ein Skript. Wenn Sie mit dem Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) aufrufen, wird dieses Skript ausgeführt. Wenn ein Exitcodes ungleich 0 zurückgegeben wird, wird der SetScript ausgeführt. Wenn sie einen Code 0 zurückgibt, wird die **SetScript** nicht ausgeführt. Die **TestScript** wird auch ausgeführt, wenn Sie das Cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aufrufen. Allerdings werden in diesem Fall die **SetScript** nicht ausgeführt unabhängig davon, welcher Exitcode aus der **TestScript**zurückgegeben wird. Die **TestScript** muss Exit-Code 0, wenn die aktuelle Konfiguration die aktuelle Konfiguration des gewünschten Zustand entspricht, und einen Code als 0 zurück, wenn nicht übereinstimmt. (Die aktuelle Konfiguration des gewünschten Zustand ist die letzte Konfiguration Stellvertreter für den Knoten, der DSC verwendet wird). Das Skript muss mit einer Shebang, wie 1#!/bin/bash.1 beginnen.| 
| User| Der Benutzer zum Ausführen des Skripts als.| 
| Group| Die Gruppe zum Ausführen des Skripts als.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die **ID** des den Skriptblock Ressource Konfiguration, die Sie ausführen möchten, zuerst **ResourceName** und dieses Typs **ResourceType**ist, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

Das folgende Beispiel veranschaulicht die Verwendung der Ressource **NxScript** Management zusätzliche Konfigurationsschritte ausführen...

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
} 
}
```
