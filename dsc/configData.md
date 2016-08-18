# Trennung der Konfiguration und Umgebungsdaten

>Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

In Windows PowerShell gewünschten Zustand Konfiguration (DSC), ist es möglich, die Daten zur Konfiguration von die Logik der Konfiguration zu trennen. Eine andere Möglichkeit, dies ist die strukturelle Konfiguration berücksichtigen (beispielsweise eine Konfiguration möglicherweise muss IIS installiert sein) aus der Umwelt Konfiguration als separate (d. h., ob die Situation einer testumgebung im Vergleich zu einer Produktion eine ist – die Namen der Knoten wäre verschiedene, aber die Konfiguration, die angewendet wird, würde der gleiche sein). Dies bietet die folgenden Vorteile:

* Es können Sie die Konfigurationsdaten für verschiedene Ressourcen, Knoten und Konfigurationen wiederverwenden.
* Konfigurationslogik ist besser wieder, wenn es keine hartcodierte Daten enthält. Dies entspricht eine gute Skripting Richtlinien für Funktionen.
* Wenn einige der Daten geändert werden muss, können Sie die Änderungen an einem Speicherort vornehmen, wodurch Zeit eingespart und Verringern von Fehlern.

## Grundlegende Konzepte und Beispiele

Zum Angeben des Umwelt Teils der Konfiguration verwendet DSC den **ConfigurationData** -Parameter eine Hashtabelle ist (oder eine .psd1-Datei mit der Hashtabelle an akzeptiert). Dieser Hashtabelle benötigen Sie mindestens einen Key **AllNodes**, dessen strukturierten Wert. Beispiel:

```powershell
$MyData = 
@{
    AllNodes = @();
    NonNodeData = ""   
}
```

Beachten Sie die AllNodes-Taste, deren Wert ein Array ist. Jedes Element des dieses Array wird auch eine Hashtabelle, die als Schlüssel Knotenname erforderlich sind:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

Jeder Eintrag des Hash-Tabelle in AllNodes entspricht Konfigurationsdaten an einen Knoten in der Konfiguration. Zusätzlich zu den erforderlichen Knotenname Schlüssel können Sie andere Schlüssel der Hashtabelle sowie, beispielsweise hinzufügen:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1";
            
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

DSC bietet drei spezielle Variablen in das Skript verwenden:

* **$AllNodes**: bezieht sich auf alle Knoten. Sie können mit **filtern. WHERE()** und **. ForEach()**, sodass anstelle von hartcodierten Knoten Objektnamen bestimmte Knoten für die Aktion, Sie etwas Ähnliches VM-1 und VM-3 im obigen Beispiel auswählen schreiben:

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node**: Nachdem der Satz der Knoten gefiltert wird, können Sie $Node verwenden, um auf bestimmten Eintrag verweisen. Beispiel:

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

Wenn eine Eigenschaft, die alle Knoten anwenden möchten, können Sie festlegen, Knotenname = "*". Beispielsweise könnte Wenn alle Knoten die LogPath-Eigenschaft übergeben möchten, Sie so vorgehen:

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData**: Sie können diese Variable innerhalb einer Konfiguration verwenden, Zugriff auf die Konfiguration Daten Hash-Tabelle als Parameter übergeben. Beispiel:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

Finden Sie ein vollständiges Beispiel in das [Modul xWebAdministration](https://powershellgallery.com/packages/xWebAdministration)enthalten.