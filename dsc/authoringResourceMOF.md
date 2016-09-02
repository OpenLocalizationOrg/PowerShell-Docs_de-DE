# Schreiben eine benutzerdefinierte DSC Ressource mit MOF

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

In diesem Thema werden wir das Schema für eine benutzerdefinierte Ressource von Windows PowerShell gewünschten Zustand Konfiguration (DSC) in eine Datei MOF definieren und implementieren Sie die Ressource in einer Windows PowerShell-Skriptdatei. Diese benutzerdefinierte Ressource ist zum Erstellen und Verwalten einer Website.

## Erstellen des Schemas MOF

Das Schema definiert die Eigenschaften der Ressource, die von einem DSC Konfigurationsskript konfiguriert werden können.

### Ordnerstruktur für eine Ressource MOF

Um eine benutzerdefinierte DSC-Ressource mit einem Schema MOF implementieren möchten, erstellen Sie die folgende Ordnerstruktur. Das MOF-Schema wird in der Datei Demo_IISWebsite.schema.mof definiert, und das Ressourcenskript in Demo_IISWebsite.ps1 definiert ist. Optional können Sie eine Modul Manifest (psd1)-Datei erstellen.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Beachten Sie, dass es notwendig ist, erstellen Sie einen Ordner namens DSCResources unterhalb des Ordners auf oberster Ebene und der Ordner für jede Ressource benötigen, die denselben Namen wie die Ressource.

### Der Inhalt der Datei MOF

Es folgt ein Beispiel MOF-Datei, die für eine benutzerdefinierte Website Ressource verwendet werden kann. Führen in diesem Beispiel wird, dieses Schema in einer Datei speichern, und rufen Sie die Datei *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")] 
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Beachten Sie folgende Aspekte im vorherigen Code:

* `FriendlyName` definiert den Namen, den Sie verwenden können, um auf diese benutzerdefinierte Ressource in DSC Konfigurationsskripts verweisen. In diesem Beispiel `Website` entspricht den Anzeigenamen `Archive` für die integrierten Archiv-Ressource.
* Die Klasse, die Sie definieren die benutzerdefinierte Ressource Ableitung muss `OMI_BaseResource`.
* Der Typbezeichner `[Key]`auf eine Eigenschaft gibt an, dass diese Eigenschaft die Ressourceninstanz eindeutig identifiziert wird. Ein `[Key]` -Eigenschaft ist auch erforderlich.
* Die `[Required]` -Kennzeichner gibt an, dass die Eigenschaft erforderlich ist (ein Wert muss in jeder Konfigurationsskripts, das diese Ressource verwendet angegeben).
* Die `[write]` -Kennzeichner gibt an, dass diese Eigenschaft optional ist bei Verwendung die benutzerdefinierte Ressource in einem Konfigurationsskript. Die `[read]` Qualifizierer gibt an, dass eine Eigenschaft nicht werden, indem eine Konfiguration festgelegt kann und wird nur zu Berichtszwecken.
* `Values` Schränkt die Werte, die die Eigenschaft der Liste der definierten Werte zugewiesen werden können `ValueMap`. Weitere Informationen finden Sie unter [ValueMap und Wert Qualifizierer](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* Einschließlich einer Eigenschaft aufgerufen `Ensure` in Ihre Ressource wird als eine Möglichkeit zum Verwalten ein konsistentes Format mit integrierten DSC Ressourcen empfohlen.
* Nennen Sie die Schemadatei für Ihre benutzerdefinierten Ressource wie folgt: `classname.schema.mof`, wobei `classname` ist der Bezeichner, der bildet die `class` -Schlüsselwort in der Schemadefinition.

### Schreiben das Ressourcenskript

Das Ressourcenskript implementiert die Logik der Ressource. In diesem Modul müssen Sie drei Funktionen aufgerufen, **Get-TargetResource**, **Set-TargetResource**und **Test-TargetResource**einbeziehen. Alle drei Funktionen müssen ein Parametersatz aufnehmen identisch mit der Gruppe von Eigenschaften definiert im Schema MOF, das Sie für die Ressource erstellt haben. In diesem Dokument wird diese Sammlung von Eigenschaften als die "Ressourceneigenschaften." bezeichnet. Diese drei Funktionen in einer Datei namens Store <ResourceName>.psm1. Im folgenden Beispiel werden die Funktionen in einer Datei namens Demo_IISWebsite.psm1 gespeichert.

> **Hinweis**: Wenn Sie das Skript für dieselbe nur einmal auf die Ressource ausführen, Sie keine Fehler erhalten sollten und die Ressource in dem Zustand als einmal Ausführen des Skripts bleiben soll. Um dies zu erreichen, stellen Sie sicher, dass Ihre **Get-TargetResource** und **Test-TargetResource** Funktionen die Ressource unverändert lassen und nur einmal Aufrufen der **Set-TargetResource** -Funktion in einer Sequenz mit den gleichen Parameterwerten immer einmal aufrufen entspricht.

Verwenden Sie die wichtigsten Ressourcen-Eigenschaftswerte, die bereitgestellt werden in die Implementierung der **Get TargetResource** als Parameter Überprüfen des Status der angegebenen Ressourceninstanz. Diese Funktion muss eine Hashtabelle zurück, die alle Ressourceneigenschaften als Schlüssel und der tatsächlichen Werte dieser Eigenschaften als die entsprechenden Werte enthält. Der folgende Code enthält ein Beispiel.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource 
{
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name; 
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }
  
        $getTargetResourceResult;
}
```

Abhängig von den Werten, die für die Ressourceneigenschaften in das Skript angegeben sind, müssen die **Set-TargetResource** einen der folgenden Schritte ausführen:

* Erstellen einer neuen website
* Aktualisieren einer vorhandenen website
* Löschen einer vorhandenen website

Das folgende Beispiel veranschaulicht dies.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine. 
function Set-TargetResource 
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )
 
    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Schließlich muss die **Test-TargetResource** -Funktion der gleichen Parametersatz als **Get-TargetResource** und **Set-TargetResource**nehmen. Die Implementierung von **Test TargetResource**überprüfen Sie den Status der Ressourceninstanz, die in die wichtigen Parameter angegeben ist. Wenn der aktuelle Status der Ressourceninstanz nicht die in der Parametersatz angegebenen Werte übereinstimmt, geben Sie **$false**zurück. **$True**andernfalls zurück.

Der folgende Code implementiert die **Test-TargetResource** -Funktion.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to 
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result 
}
```

**Hinweis**: für einfacheres Debuggen, verwenden Sie das Cmdlet **Write-Verbose** in der Implementierung der vorherigen drei Funktionen. Dieses Cmdlet schreibt Text in die ausführliche Meldungsstream. Der ausführliche Meldungsstream wird standardmäßig nicht angezeigt, jedoch können angezeigt wird, indem Sie den Wert der Variablen **$VerbosePreference** ändern oder mithilfe des Parameters **Verbose** in den Cmdlets DSC = new.

### Erstellen der Manifestdatei Modul

Verwenden Sie das Cmdlet **New-ModuleManifest** schließlich so definieren Sie eine <ResourceName>.psd1-Datei für benutzerdefinierte Ressource Moduls. Wenn Sie dieses Cmdlet aufrufen, verweisen auf die Skriptdatei-Modul (.psm1) im vorherigen Abschnitt beschrieben. Einschließen Sie **Get TargetResource** **Set TargetResource**und **Test TargetResource** in der Liste der Funktionen für den export. Es folgt eine Beispiel-Manifestdatei.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```