# DSC für Linux NxEnvironment Ressource

**NxEnvironment** Ressource in PowerShell gewünscht Bundesstaat Konfiguration (DSC) bietet ein Verfahren zum Verwalten Systemumgebungsvariablen auf einem Knoten Linux.

## Syntax

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| Namen| Gibt den Namen der Umgebungsvariablen für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Wert| Der Wert, der Umgebungsvariablen zuweisen.| 
| Stellen Sie sicher| Bestimmt, ob Sie prüfen, ob die Variable vorhanden ist. Legen Sie diese Eigenschaft auf "Präsentieren", um sicherzustellen, dass die Variable vorhanden ist. Legen Sie dafür den "Abwesend", um sicherzustellen, dass die Variable nicht vorhanden ist. Der Standardwert ist "Präsentieren".| 
| Pfad| Definiert die Umgebungsvariable, die konfiguriert wird. Legen Sie diese Eigenschaft auf **$true** an, wenn die Variable den **Pfad** ist; Legen Sie sie andernfalls auf **$false**ein. Die Standardeinstellung ist **$false**. Wenn die Variable wird so konfiguriert, dass der **Pfad** ist, wird der Wert der **Value** -Eigenschaft gebotenen an den vorhandenen Wert angehängt.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die **ID** für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Weitere Informationen

* Ist **Pfad** Abwesenheit oder auf **$false**festgelegt ist, werden verwaltet Umgebungsvariablen `/etc/environment`. Ihre Programme oder Skripts zu Quelle Konfiguration erfordern möglicherweise die `/etc/environment` Datei auf die verwaltete Umgebungsvariablen zugreifen.
* Wenn der **Pfad** auf **$true**festgelegt ist, wird die Umgebungsvariable in der Datei verwaltet `/etc/profile.d/DSCenvironment.sh`. Diese Datei wird erstellt, wenn er nicht vorhanden ist. Wenn Sie **sicherstellen, dass** festgelegt wurde, "Abwesend", und **der Pfad** ist festgelegt auf **$true**, eine vorhandene Umgebungsvariable wird nur von entfernt `/etc/profile.d/DSCenvironment.sh` und nicht aus anderen Dateien.

## Beispiel

Das folgende Beispiel veranschaulicht, wie die **NxEnvironment** Ressource verwenden, um sicherzustellen, dass **TestEnvironmentVariable** vorhanden ist, und den Wert "Test-Wert hat". Wenn **TestEnvironmentVariable** nicht vorhanden ist, wird er erstellt.

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```


