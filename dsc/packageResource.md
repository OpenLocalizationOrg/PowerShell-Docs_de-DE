# DSC Paket Ressource

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **Paket** in Windows PowerShell gewünscht Zustand Konfiguration (DSC) stellt ein Verfahren zum Installieren oder Deinstallieren von Paketen, wie z. B. Windows Installer und setup.exe Pakete auf einem Zielknoten.

## Syntax

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Namen| Gibt den Namen des Pakets für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Pfad| Gibt den Pfad, in dem sich das Paket befindet.| 
| "ProductID"| Gibt das Produkt-ID, die das Paket eindeutig an.| 
| Argumente auf:| Enthält eine Zeichenfolge Argumente, die das Paket genau bereitgestellten übergeben wird.| 
| Anmeldeinformationen| Ermöglicht den Zugriff auf das Paket auf eine remote-Quelle. Diese Eigenschaft wird nicht verwendet, das Paket zu installieren. Das Paket wird immer auf dem lokalen System installiert.| 
| Vergewissern Sie sich| Zeigt an, ob das Paket installiert ist. Legen Sie diese Eigenschaft auf "Abwesend", um sicherzustellen, dass das Paket nicht installiert ist (oder deinstallieren das Paket ein, falls es installiert ist). Legen Sie ihn (den Standardwert) "präsentieren", um sicherzustellen, dass das Paket installiert ist.| 
| LogPath| Gibt den vollständigen Pfad, den Anbieter, um eine Protokolldatei zum Installieren oder deinstallieren das Paket speichern möchten.| 
| DependsOn | Zeigt an, dass die Konfiguration von einer anderen Ressource ausführen muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die ID des Ressource Konfiguration Script-Blocks, die Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax zur Verwendung dieser Eigenschaft ist "DependsOn"[ResourceType] Ressourcenname"=''.| 
| Rückgabecode| Zeigt die erwarteten Rückgabetyp Code an. Wenn die tatsächliche Code zurück entspricht nicht der Erwartungswert hier bereitgestellt die Konfiguration, einen Fehler zurückgeben.| 

## Beispiel

In diesem Beispiel wird das MSI-Installationsprogramm, das befindet sich unter dem angegebenen Pfad und weist die angegebene Produkt-ID an.

```powershell
Package PackageExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path  = "$Env:SystemDrive\TestFolder\TestProject.msi"
    Name = "TestPackage"
    ProductId = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
} 
```
