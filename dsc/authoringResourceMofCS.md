# Erstellen eine Ressource DSC in C##

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

In der Regel wird eine benutzerdefinierte Windows PowerShell gewünschten Zustand Konfiguration (DSC)-Ressource in einem Powershellskript implementiert. Jedoch können Sie die Funktionalität einer benutzerdefinierten DSC-Ressource implementieren, durch die Cmdlets in c# schreiben. Eine Einführung zum Schreiben von Cmdlets in c# finden Sie unter [Writing eines Windows PowerShell-Cmdlets](https://technet.microsoft.com/en-us/library/dd878294.aspx).

Abgesehen davon, dass die Ressource als den Prozess beim Erstellen des Schemas MOF-Cmdlets in c# implementieren sind die Ordnerstruktur erstellen, importieren und mithilfe der benutzerdefinierten DSC Ressource die gleichen wie beim Schreiben [einer benutzerdefinierten DSC Ressource mit MOF](authoringResourceMOF.md)beschrieben.

## Schreiben einer Ressource Cmdlet-basierten
In diesem Beispiel werden wir eine einfache Ressource implementieren, die eine Textdatei und seinen Inhalt verwaltet.

### Das Schema MOF-schreiben

Es folgt die Definition der Ressource MOF.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### Einrichten des Visual Studio-Projekts
#### Einrichten eines Projekts cmdlet

1. Öffnen Sie Visual Studio.
1. Erstellen Sie ein C#-Projekt, und geben Sie den Namen.
1. Wählen Sie aus den verfügbaren Projektvorlagen **Class Library** .
1. Klicken Sie auf **Ok**.
1. Fügen Sie einen Assemblyverweis auf System.Automation.Management.dll Sie Ihrem Projekt hinzu.
1. Ändern Sie den Assemblynamen Übereinstimmung mit dem Ressourcennamen. In diesem Fall sollten die Assembly **MSFT_XDemoFile**heißen.

### Mit dem Cmdlet Code schreiben

Der folgende C#-Code implementiert die Cmdlets **Get-TargetResource**, **Set-TargetResource**und **Test-TargetResource** .

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
           } 
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
        [Parameter(Mandatory = true)]
        public string Path { get; set; }
 
        [Parameter(Mandatory = false)]
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }
 
        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### Bereitstellen von Ressource

Die Datei kompilierte Dll sollte in einer Dateistruktur ähnlich einer Ressource Skript basierende gespeichert werden. Im folgenden finden die Ordnerstruktur für diese Ressource.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### Siehe auch
#### Konzepte
[Schreiben eine benutzerdefinierte DSC Ressource mit MOF](authoringResourceMOF.md)
#### Weitere Ressourcen
[Schreiben Sie ein Windows PowerShell-Cmdlet](https://msdn.microsoft.com/en-us/library/dd878294.aspx)