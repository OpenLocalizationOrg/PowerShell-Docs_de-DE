# Schreiben eine benutzerdefinierte DSC Ressource mit PowerShell Klassen

> Betrifft: Windows Windows PowerShell 5.0

Mit der Einführung von PowerShell Klassen in Windows PowerShell 5.0 können Sie jetzt eine Ressource DSC definieren, durch Erstellen einer Klasse. Die Klasse definiert das Schema und die Implementierung der Ressource, damit besteht keine Notwendigkeit eine separate MOF-Datei zu erstellen. Die Ordnerstruktur für eine Ressource Klassen basierende ist auch einfacher, da ein **DSCResources** Ordner nicht erforderlich ist.

In einer Klasse basierende DSC Ressource ist das Schema als Eigenschaften der Klasse definiert die Attribute, geben Sie die Eigenschaft geändert werden kann. Die Ressource wird durch (vergleichbar mit der **Get-TargetResource**, **Set-TargetResource**und **Test-TargetResource** -Funktionen in einer Skriptressource. **Get()**, **DISTINCT**und **Test()** Methoden implementiert.

In diesem Thema erstellen wir eine einfache Ressource mit dem Namen **FileResource** , der eine Datei in einem angegebenen Pfad verwaltet.

Weitere Informationen zu DSC Ressourcen finden Sie unter [Erstellen benutzerdefinierter Windows PowerShell gewünschten Zustand Konfigurationsressourcen](authoringResource.md)

## Ordnerstruktur für eine Klassenressource

Um eine benutzerdefinierte DSC Ressource mit einer PowerShell-Klasse implementieren möchten, erstellen Sie die folgende Ordnerstruktur. Die Klasse ist in **MyDscResource.psm1** und das Modul Manifest in **MyDscResource.psd1**definiert ist.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## Erstellen Sie die Klasse

Verwenden Sie das Schlüsselwort Class zum Erstellen einer PowerShell-Klasse. Um anzugeben, dass eine Klasse eine DSC Ressource ist, verwenden Sie das **DscResource()** -Attribut. Der Namen der Klasse ist der Name der Ressource DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### Deklarieren von Eigenschaften

Das Schema der DSC Resource wird als Eigenschaften der Klasse definiert. Wir haben drei Eigenschaften wie folgt deklarieren.

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

Beachten Sie, dass die Eigenschaften von Attributen geändert werden. Die Bedeutung der Attribute lautet wie folgt:

- **DscProperty(Key)**: die Eigenschaft erforderlich ist. Die Eigenschaft ist ein Schlüssel. Die Werte aller Eigenschaften als Schlüssel kombinieren müssen, um eine Ressourceninstanz innerhalb einer Konfiguration eindeutig zu identifizieren markiert.
- **DscProperty(Mandatory)**: die Eigenschaft erforderlich ist.
- **DscProperty(NotConfigurable)**: die Eigenschaft ist schreibgeschützt. Eigenschaften mit diesem Attribut markiert sind, können nicht durch eine Konfiguration festgelegt werden, jedoch werden durch **die Get()-Methode roleseite** aufgefüllt.
- **DscProperty()**: die-Eigenschaft kann konfiguriert werden, aber es ist nicht erforderlich.

Die Eigenschaften **$Path** und **$SourcePath** sind beide Zeichenfolgen. Die **$CreationTime** ist eine [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) -Eigenschaft. Die **$Ensure** -Eigenschaft ist ein Enumerationstyp wie folgt definiert sind.

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### Implementieren von Methoden

Die **Get()**, **DISTINCT**und **Test()** Methoden sind vergleichbar mit der **Get-TargetResource**, **Set-TargetResource**und **Test-TargetResource** -Funktionen in einer Skriptressource.

Dieser Code enthält auch die CopyFile()"Funktion, eine Hilfsfunktion, die die Datei aus **$SourcePath** in **$Path**kopiert. 

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### Die vollständigen Datei
Die vollständigen Klassendatei folgt.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## Erstellen einer Manifestdatei

Um eine Ressource Klassen basierende das Modul DSC zur Verfügung stellen, müssen Sie eine **DscResourcesToExport** Anweisung in der Manifestdatei einschließen, die das zu exportierende Ressource Modul anweist. Unsere Manifest sieht folgendermaßen aus:

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

## Testen Sie die Ressource

Nach dem Speichern der Klasse und der Manifestdateien innerhalb der Ordnerstruktur wie oben beschrieben, können Sie eine Konfiguration erstellen, die die neue Ressource verwendet. Informationen zum Ausführen einer DSC Konfigurations finden Sie unter [Enacting Konfigurationen](enactingConfigurations.md). Die folgende Konfiguration wird überprüft, ob die Datei unter `c:\test\test.txt` vorhanden ist, und wenn nicht, kopiert diese Methode der Datei aus `c:\test.txt` (erstellen Sie `c:\test.txt` vor dem Ausführen der Konfigurations).

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    } 
}
Test
Start-DscConfiguration -Wait -Force Test
```

## Siehe auch
### Konzepte
[Erstellen von benutzerdefinierten Windows PowerShell gewünscht State Konfigurationsressourcen](authoringResource.md)
