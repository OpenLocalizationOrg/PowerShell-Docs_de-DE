# DSC Konfigurationen

>Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC Konfigurationen sind PowerShell-Skripts, die einen bestimmten Typ der Funktion zu definieren. Um eine Konfiguration zu definieren, verwenden Sie das PowerShell-Schlüsselwort __Konfiguration__.

```powershell
Configuration MyDscConfiguration {

    Node “TEST-PC1” {
        WindowsFeature MyFeatureInstance {
            Ensure = “Present”
            Name =  “RSAT”
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = “Present”
            Name = “Bitlocker”
        }
    }
}
```

Speichern Sie das Skript als. ps1-Datei.

## Die Syntax der Konfiguration

Ein Konfigurationsskript besteht aus den folgenden Teilen:

- Der **Konfigurations** -Block. Dies ist die äußerste Skriptblock. Definieren Sie sie, indem Sie mithilfe des **Konfigurations** -Schlüsselworts und einen Namen angeben. In diesem Fall ist der Name der Konfiguration "MyDscConfiguration".
- Eine oder mehrere **Knoten** wird blockiert. Diese definieren die Knoten (Computer oder VMs), die Sie konfigurieren. In der obigen Konfiguration ist ein **Knoten** blockieren, die auf einen Computer mit dem Namen "TEST-PC1" abzielt.
- Eine oder mehrere Ressourcen wird blockiert. Dies ist, auf dem die Konfiguration die Eigenschaften für die Ressourcen festgelegt wird, der Konfiguration ist. In diesem Fall stehen zwei Ressource Blöcke, von denen jedes rufen Sie die Ressource "WindowsFeature".

In einem Block **Konfiguration** können Sie alle Aktionen, die Sie normalerweise in einer Funktion PoweShell konnte. Beispielsweise im vorherigen Beispiel, können Wenn Sie nicht den Namen des Computers Ziel in der Konfiguration codieren möchten Sie einen Parameter für den Knoten ein hinzufügen:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$computerName="localhost"
    )
    Node $computerName {
        WindowsFeature MyFeatureInstance {
            Ensure = “Present”
            Name =  “RSAT”
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = “Present”
            Name = “Bitlocker”
        }
    }
}
```

In diesem Beispiel geben Sie den Namen des Knotens, indem Sie es als $computerName-Parameter übergeben wenn Sie [die Konfigurationsdateiunterschiede kompilieren](# Compiling the configuration). Der Name wird standardmäßig auf "Localhost".

## Kompilieren die Konfiguration
Bevor Sie eine Konfiguration widersprechenden können, müssen Sie es in ein Dokument MOF kompiliert werden sollen. Dazu müssen Sie die Konfiguration aufrufen, wie Sie eine Funktion PowerShell.
>__Hinweis:__ Um eine Konfiguration aufrufen möchten, muss die Funktion in globaler Ebene (wie bei jeder anderen PowerShell-Funktion). Sie können entweder hierfür tätigen "Dot-sourcing" des Skripts oder durch Ausführen des Konfigurationsskripts durch Drücken von F5 oder durch Klicken auf das __Skript ausführen__ die Schaltfläche in der ISE. Punkt-Quelle das Skript, führen Sie den Befehl `. .\myConfig.ps1` , in dem `myConfig.ps1` ist der Name der Skriptdatei, die die Konfiguration enthält.

Beim Aufruf der Konfigurations erstellt:

- Ein Ordner im aktuellen Verzeichnis mit dem gleichen Namen wie die Konfiguration.
- Eine Datei namens _Knotenname_MOF im neuen Verzeichnis, wobei _Knotenname_ der Name des Knotens Ziel der Konfiguration ist. Wenn mehr als ein Knoten vorhanden sind, wird eine MOF-Datei für jeden Knoten erstellt werden.

>__Hinweis__: das MOF-Datei enthält alle Konfigurationsinformationen für den Zielknoten. Aus diesem Grund ist es wichtig, um es zu schützen. Weitere Informationen finden Sie unter [Sichern der MOF-Datei](secureMOF.md).

Kompilieren die erste Konfiguration oberhalb der Suchergebnisse in der folgenden Ordnerstruktur:

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

Wenn die Konfiguration einen Parameter, wie im zweiten Beispiel verwendet wurde, die zur Kompilierzeit bereitgestellt werden. Sieht aus wie, die aussehen würde:

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -computerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## DependsOn verwenden
Eine nützliche DSC-Schlüsselwort ist __DependsOn__. In der Regel (jedoch nicht unbedingt immer), DSC gilt die Ressourcen in der Reihenfolge, die sie innerhalb der Konfiguration angezeigt werden. Allerdings __DependsOn__ gibt an, welche Ressourcen von anderen Ressourcen abhängen und LCM wird sichergestellt, dass sie in der richtigen Reihenfolge, unabhängig von der Reihenfolge angewendet werden, in denen die Ressourcen Instanzen definiert sind. Beispielsweise möglicherweise eine Konfiguration angeben, dass eine Instanz der Ressource __Benutzer__ auf dem Vorhandensein einer Instanz einer __Gruppe__ abhängt:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = “Present”
            GroupName = “TestGroup”
        }
User UserExample {
Ensure = “Present”
FullName = “TestUser”
DependsOn = “GroupExample”
}
    }
}
```

## Verwenden von neuen Ressourcen in Ihrer Konfiguration
Wenn Sie die vorherigen Beispielen ausgeführt haben, Sie möglicherweise bemerkt, dass Sie eine Warnung wurden, dass Sie eine Ressource verwendet wurden, ohne explizit zu importieren.
Heute, im Lieferumfang von DSC 12 Ressourcen im Rahmen des Moduls PSDesiredStateConfiguration. Andere Ressourcen in externen Modulen müssen in platziert werden `$env:PSModulePath` , um von der LCM erkannt werden. Einem neuen-Cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), kann verwendet werden, um zu bestimmen, welche Ressourcen auf dem System installiert und bereit zur Verwendung durch den LCM sind. Nachdem diese Module in abgelegt wurden `$env:PSModulePath` ordnungsgemäß von erkannt werden [Get DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), müssen sie dennoch innerhalb Ihrer Konfiguration geladen werden. __Import-DscResource__ ist eine dynamische Schlüsselwort, das nur innerhalb eines __Configuration__ -Blocks erkannt werden kann (d. h. ist es kein Cmdlet). __Import-DscResource__ unterstützt zwei Parameter:
* __Modulname__ ist das empfohlene Verfahren der __Import DscResource__Verwendung. Er akzeptiert den Namen des Moduls, enthält die Ressourcen (sowie ein Zeichenfolgenarray mit Modulnamen) importiert werden. 
* __Name__ ist der Name der Ressource zu importieren. Dies ist nicht den Anzeigenamen von [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)als "Name" zurückgegeben, aber der Klassenname verwendet, wenn das Schema der Resource (von [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)als __ResourceType__ zurückgegeben) zu definieren. 

## Siehe auch
* [Windows PowerShell gewünschten Zustand (Übersicht)](overview.md)
* [DSC Ressourcen](resources.md)
* [Konfigurieren von lokalen Konfigurations-Manager](metaconfig.md)