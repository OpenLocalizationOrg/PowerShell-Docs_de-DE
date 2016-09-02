# DSC für Linux NxFile Ressource

Die **NxFile** Ressource in PowerShell gewünschten Zustand Konfiguration (DSC) bietet einen Mechanismus zum zum Verwalten von Dateien und Verzeichnisse auf einem Linux-Knoten.

## Syntax

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| DestinationPath| Gibt den Speicherort, in dem Sie den Status für eine Datei oder ein Verzeichnis sicherstellen wollen.| 
| SourcePath| Gibt den Pfad aus dem die Ressource Datei oder einen Ordner kopiert. Dieser Pfad ist möglicherweise ein lokaler Pfad oder einem `http/https/ftp` URL. Remote `http/https/ftp` URLs werden nur unterstützt, wenn der Wert der **Type** -Eigenschaft Datei ist.| 
| Stellen Sie sicher| Bestimmt, ob überprüfen Sie, ob die Datei vorhanden ist. Legen Sie diese Eigenschaft auf "Vorhanden", um sicherzustellen, dass die Datei vorhanden ist. Legen Sie ihn auf "Abwesend", um sicherzustellen, dass die Datei nicht vorhanden ist. Der Standardwert ist "Vorhanden".| 
| Typ| Gibt an, ob die Ressource konfiguriert wird ein Verzeichnis oder eine Datei ist. Legen Sie diese Eigenschaft auf "Verzeichnis", um anzugeben, dass die Ressource ein Verzeichnis ist. Legen Sie sie in "Datei", um anzugeben, dass die Ressource eine Datei ist. Der Standardwert ist "Datei"| 
| Inhalt| Gibt den Inhalt einer Datei, wie etwa einer bestimmten Zeichenfolge.| 
| Prüfsumme| Definiert den Typ verwenden, wenn Sie bestimmen, ob zwei Dateien identisch sind. Wenn **Prüfsumme** nicht angegeben ist, wird nur der Name-Datei oder ein Verzeichnis für den Vergleich verwendet. Werte sind: "Ctime", "Mtime," oder "md5".| 
| Recurse| Gibt an, ob Unterverzeichnissen enthalten sind. Legen Sie diese Eigenschaft auf **$true** an dem Sie Unterverzeichnissen enthalten sein soll. Der Standardwert ist **$false**. **Hinweis:** Diese Eigenschaft ist nur gültig, wenn die **Type** -Eigenschaft zum Verzeichnis festgelegt ist.| 
| Kraft| Bestimmte Dateioperationen (beispielsweise eine Datei überschreiben oder Löschen eines Verzeichnisses an, das nicht leer ist) führt einen Fehler. Mithilfe der **Force** -Eigenschaft überschreibt derartige Fehler. Der Standardwert lautet **$false**.| 
| Verknüpfungen| Gibt an, das gewünschte Verhalten für symbolische Links. Legen Sie diese Eigenschaft auf "führen", um führen symbolische Links und wirken sich auf das Ziel des Hyperlinks (z. b. Kopieren Sie die Datei anstelle der Link). Legen Sie diese Eigenschaft auf "verwalten" auf den Link (z. b. fungieren Kopieren Sie den Link selbst). Legen Sie diese Eigenschaft auf "ignorieren", um symbolische Links zu ignorieren.| 
| Group| Der Name der **Gruppe** für die Datei oder das Verzeichnis zu ändern.| 
| Modus| Gibt die gewünschten Berechtigungen für die Ressource in eine oktale Zahl oder symbolische Notation an. (beispielsweise 777 oder Rwxrwxrwx). Wenn symbolische Notation verwenden, bieten Sie nicht das erste Zeichen, das Verzeichnis oder eine Datei angibt.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Beispielsweise wenn die **ID** des den Skriptblock Ressource Konfiguration, die Sie ausführen möchten, zuerst **ResourceName** und dieses Typs **ResourceType**ist, ist die Syntax für die Verwendung dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 

## Weitere Informationen


Linux und Windows verwenden unterschiedliche Zeilenumbruchzeichen in Textdateien standardmäßig, und dies kann unerwartete Ergebnisse verursachen, wenn Sie einige Dateien auf einem Linux-Computer mit __NxFile__konfigurieren. Es gibt mehrere Möglichkeiten zum Verwalten von des Inhalts der Datei Linux während der Vermeidung von Problemen mit unerwarteter Zeilenumbruchzeichen zurückzuführen:

Schritt 1: Kopieren Sie die Datei aus einer remote-Quelle (http, Https oder ftp): Erstellen Sie eine Datei unter Linux mit dem gewünschten Inhalt und Phase es die Knoten Sie konfigurieren auf einem Web- oder FTP-Server zugegriffen werden. __SourcePath__ -Eigenschaft in der Ressource __NxFile__ mit dem Web definieren oder FTP-URL zu der Datei.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    
}
        
}
```


Schritt 2: Lesen Sie den Inhalt der Datei in die PowerShell-Skript mit [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) nach dem Festlegen der Eigenschaft __$OFS__ das Linux Zeilenumbruch Zeichen verwenden.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = "$Contents"
}

}
```


Schritt 3: Verwenden einer PowerShell-Funktion zum Ersetzen Sie Windows Zeilenumbrüche mit Linux Zeilenumbruchzeichen.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = $Contents
    
}
}
```

## Beispiel

Im folgende Beispiel wird sichergestellt, dass das Verzeichnis `/opt/mydir` vorhanden ist, und eine Datei mit dem angegebenen Inhalt dieses Verzeichnis vorhanden sind.

```
Import-DSCResource -Module nx 

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@ 
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```

