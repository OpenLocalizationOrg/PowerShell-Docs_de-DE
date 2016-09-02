# DSC für Linux NxArchive Ressource

Die **NxArchive** Ressource in PowerShell gewünschten Zustand Konfiguration (DSC) bietet einen Mechanismus zum Entpacken (TAR, ZIP) Archivdateien an einen bestimmten Pfad auf einem Linux-Knoten.

## Syntax

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| SourcePath| Gibt den Quellpfad der Archivdatei. Dies sollte eine TAR ZIP, oder. weswegen Datei. | 
| DestinationPath| Gibt den Speicherort, stellen Sie sicher, dass das Archiv Inhalt extrahiert werden soll.| 
| Prüfsumme| Definiert den Typ zu verwenden, wenn Sie feststellen, ob das Archiv der Quelle aktualisiert wurde. Werte sind: "Ctime", "Mtime," oder "md5". Der Standardwert ist "md5".| 
| Kraft| Bestimmte Dateioperationen (beispielsweise eine Datei überschreiben oder Löschen eines Verzeichnisses an, das nicht leer ist) führt einen Fehler. Mithilfe der **Force** -Eigenschaft überschreibt derartige Fehler. Der Standardwert lautet **$false**.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Beispielsweise wenn die **ID** des den Skriptblock Ressource Konfiguration, die Sie ausführen möchten, zuerst **ResourceName** und dieses Typs **ResourceType**ist, ist die Syntax für die Verwendung dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 
| Stellen Sie sicher| Bestimmt, ob überprüfen Sie, ob die Inhalte des Archivs am **Ziel**vorhanden sind. Legen Sie diese Eigenschaft auf "Vorhanden", um sicherzustellen, dass der Inhalt vorhanden sein. Legen Sie ihn auf "Abwesend", um sicherzustellen, dass sie nicht vorhanden sind. Der Standardwert ist "Vorhanden".| 

## Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die **NxArchive** Ressource verwenden, stellen Sie sicher, dass der Inhalt der Archivdatei aufgerufen `website.tar` vorhanden und an ein bestimmtes Ziel extrahiert werden.

```
Import-DSCResource -Module nx 

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
} 
```
