# Verwenden das Tool Ressourcen-Designer

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

Das Ressourcen-Designer-Tool ist eine Gruppe von Cmdlets, die durch das Modul **xDscResourceDesigner** verfügbar gemacht werden, das Erstellen von Windows PowerShell gewünschten Zustand Konfiguration (DSC) Ressourcen zu erleichtern. Die Cmdlets in dieser Ressource können MOF-Schemas, das Skriptmodul und der Verzeichnisstruktur für die neue Ressource zu erstellen. Weitere Informationen zu DSC Ressourcen finden Sie unter [Erstellen benutzerdefinierter Windows PowerShell gewünschten Zustand Konfigurationsressourcen](authoringResource.md).
In diesem Thema erstellen wir eine DSC Ressource, die Active Directory-Benutzer verwaltet werden.
Verwenden Sie das Cmdlet [Install-Modul](https://technet.microsoft.com/en-us/library/dn807162.aspx) , um das **xDscResourceDesigner** -Modul installieren.

>**Hinweis**: **Install-Modul** befindet sich auf das Modul **PowerShellGet** an, die in PowerShell 5.0 enthalten ist. Sie können das **PowerShellGet** -Modul für PowerShell 3.0 und 4.0 am [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186)herunterladen.

## Erstellen von Ressourceneigenschaften
Wir müssen zuerst ist entscheiden, klicken Sie auf Eigenschaften, die die Ressource verfügbar macht. In diesem Beispiel werden wir einen Active Directory-Benutzer mit den folgenden Eigenschaften definieren.
 
Parametername Beschreibung
* **Benutzername**: Key-Eigenschaft, die einen Benutzer eindeutig identifiziert.
* **Sicherstellen, dass**: Gibt an, ob das Benutzerkonto vorhanden sein soll oder nicht vorhanden ist. Dieser Parameter wird nur zwei mögliche Werte aufweisen.
* **DomainCredential**: das Kennwort für den Benutzer.
* **Kennwort**: das gewünschte Kennwort für den Benutzer um eine Konfiguration zum Ändern des Benutzerkennworts bei Bedarf zu ermöglichen.

Um die Eigenschaften zu erstellen, verwenden wir das Cmdlet " **New-xDscResourceProperty** ". Die folgenden PowerShell-Befehle erstellen Sie die oben beschriebenen Eigenschaften.

```powershell
PS C:\> $UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
PS C:\> $Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
PS C:\> $DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
PS C:\> $Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## Erstellen der Ressource

In den Ressourceneigenschaften erstellt wurden, können wir das Cmdlet **New-xDscResource** zum Erstellen der Ressource aufrufen. Mit dem Cmdlet **New-xDscResource** übernimmt die Liste der Eigenschaften als Parameter. Es werden außerdem den Pfad, in dem das Modul erstellt werden soll, der Name der neuen Ressource und den Namen des Moduls in der es enthalten ist. Der folgende PowerShell-Befehl wird die Ressource erstellt.

```powershell
PS C:\> New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

Mit dem Cmdlet **New-xDscResource** erstellt das Schema MOF, eines Skripts Skelett Ressource, die erforderliche Verzeichnisstruktur für die neue Ressource und ein Manifest für das Modul, das die neue Ressource verfügbar macht.

Die MOF-Schemadatei ist unter **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**und sein Inhalt werden wie folgt.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
[Key] string UserName;
[Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
[Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
[Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

Das Ressourcenskript ist unter **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Es ist nicht enthalten, die eigentliche Logik zum Implementieren der Ressource müssen Sie sich selbst hinzufügen. Die Inhalte des Skelett Skripts sind wie folgt.

```powershell
function Get-TargetResource
{
[CmdletBinding()]
[OutputType([System.Collections.Hashtable])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$returnValue = @{
UserName = [System.String]
Ensure = [System.String]
DomainAdminCredential = [System.Management.Automation.PSCredential]
Password = [System.Management.Automation.PSCredential]
}

$returnValue
#>
}


function Set-TargetResource
{
[CmdletBinding()]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."

#Include this line if the resource requires a system reboot.
#$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$result = [System.Boolean]

$result
#>
}


Export-ModuleMember -Function *-TargetResource
```

## Aktualisieren der Ressource

Wenn Sie zum Hinzufügen oder Ändern der Parameterliste der Ressource müssen, können Sie das Cmdlet **Update-xDscResource** aufrufen. Mit dem Cmdlet aktualisiert Ressource mit einer Liste der neuen Parameter. Wenn Sie bereits Logik in Ihr Ressourcenskript hinzugefügt haben, ist es intakt.

Angenommen Sie, dass das letzte Protokoll in der Zeit für den Benutzer im unsere Ressource enthalten sein sollen. Statt die Ressource erneut vollständig schreiben, können Sie das **New-xDscResourceProperty** , um die neue Eigenschaft erstellen und Aufrufen von **Update xDscResource** und die neue Eigenschaft der Eigenschaftenliste hinzufügen aufrufen.

```powershell
PS C:\> $lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
PS C:\> Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## Testen ein Resource-schema

Das Tool Ressourcen-Designer macht eine weitere-Cmdlet, das verwendet werden kann, um die Gültigkeit eines Schemas MOF testen, die Sie manuell geschrieben haben. Rufen Sie das Cmdlet **Test-xDscSchema** der Pfad eines Schemas Ressource MOF als Parameter übergeben. Das Cmdlet wird im Schema Fehler ausgegeben.

### Siehe auch

#### Konzepte
[Erstellen von benutzerdefinierten Windows PowerShell gewünscht State Konfigurationsressourcen](authoringResource.md)

#### Weitere Ressourcen
[xDscResourceDesigner Modul](https://powershellgallery.com/packages/xDscResourceDesigner)
