# Zusammengesetzte Ressourcen: die Verwendung einer DSC Konfigurations als Ressource

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

In realen Situationen können Konfigurationen lang und komplex, vielen unterschiedliche Ressourcen aufrufen und Festlegen von eine große Anzahl von Eigenschaften werden. Damit diese Komplexität Adresse gewährleistet ist, können Sie eine Windows PowerShell gewünschten Zustand Konfiguration (DSC) Konfiguration für weitere Konfigurationen von als Ressource. Wir nennen dies eine zusammengesetzte Ressource. Eine zusammengesetzte Ressource ist eine DSC-Konfiguration, die Parameter akzeptiert. Die Parameter der Konfiguration fungieren als die Eigenschaften der Ressource. Die Konfiguration wird gespeichert, wie eine Datei mit einer **. schema.psm1** Erweiterung, und die Stelle des MOF-Schemas und der Ressource in einer typischen DSC Ressource Skript akzeptiert (Weitere Informationen zu DSC Ressourcen finden Sie unter [Windows PowerShell gewünschten Zustand Konfigurationsressourcen](resources.md).

## Erstellen zusammengesetzte Ressource

In unserem Beispiel erstellen wir eine Konfiguration, die eine Reihe von vorhandenen Ressourcen zum Konfigurieren von virtuellen Computern aufruft. Anstelle der Werte in Blöcke Konfiguration festgelegt werden soll, ist die Konfiguration eine Anzahl von Parameter, die klicken Sie dann in der Konfiguration Blöcke verwendet werden.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Creae VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### Speichern der Konfiguration als zusammengesetzte Ressource

Um die parametrisierte Konfiguration als eine Ressource DSC verwenden, speichern Sie sie in einer Verzeichnisstruktur wie, die von anderen MOF-basierte Ressource, und nennen Sie sie mit einer **. schema.psm1** Erweiterung. Für dieses Beispiel fügen wir der Datei **xVirtualMachine.schema.psm1**nennen. Sie müssen auch zum Erstellen einer Manifestdatei, die mit dem Namen **xVirtualMachine.psd1** , die die folgende Zeile enthält. Beachten Sie, dass dies zusätzlich zu **MyDscResources.psd1**, das Manifest Modul für alle Ressourcen unterhalb des Ordners **MyDscResources** ist.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Wenn Sie fertig sind, sollte die Ordnerstruktur wie folgt aussehen.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSC Resources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Die Ressource mithilfe des Cmdlets Get-DscResource jetzt sichtbar ist, und seine Eigenschaften werden sichtbar, indem entweder das Cmdlet oder **STRG + LEERTASTE** AutoVervollständigen in der Windows PowerShell ISE.

## Zusammengesetzte Ressource verwenden

Als Nächstes erstellen Sie eine Konfiguration, die zusammengesetzte Ressource aufruft. Diese Konfiguration Ruft die xVirtualMachine zusammengesetzte Ressource zum Erstellen eines virtuellen Computers und ruft dann die Ressource **xComputer** , um diese umzubenennen.

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## Siehe auch
### Konzepte
* [Schreiben eine benutzerdefinierte DSC Ressource mit MOF](authoringResourceMOF.md)
* [Erste Schritte mit Windows PowerShell gewünschte State-Konfiguration](overview.md)
