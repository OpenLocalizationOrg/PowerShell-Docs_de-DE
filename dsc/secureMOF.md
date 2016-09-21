# Sichern der MOF-Datei

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC weist den Zielknoten welche Konfiguration sie durch eine MOF-Datei mit diesen Informationen an jeden Knoten zu senden, in dem die gewünschte Konfiguration implementiert der lokalen Konfigurations-Manager (KGV) sein soll. Da diese Datei die Details der Konfiguration enthält, ist es wichtig, um es zu schützen. Hierzu können Sie lokale Konfigurations-Manager, überprüfen Sie die Anmeldeinformationen eines Benutzers festlegen. In diesem Thema beschrieben, wie diese Anmeldeinformationen sicher zum Zielknoten mit Zertifikaten verschlüsseln übertragen.

## Erforderliche Komponenten

Die Anmeldeinformationen verwendet, um eine Konfiguration DSC secure erfolgreich Verschlüsselung, stellen Sie sicher, dass Sie über Folgendes verfügen:

* **Einige der Ausgabe und Verteilen von Zertifikaten bedeutet**. In diesem Thema und den zugehörigen Beispielen wird davon ausgegangen, dass Sie Active Directory-Zertifizierungsstelle verwenden. Weitere Hintergrundinformationen zu Active Directory Certificate Services finden Sie unter [Active Directory-Zertifikat Übersicht](https://technet.microsoft.com/library/hh831740.aspx) und [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Administrative den Zugriff auf das Ziel oder Knoten**.
* **Jeder Zielknoten hat ein Verschlüsselung Lage Zertifikat deren Personal Store gespeichert**. In Windows PowerShell lautet der Pfad zum Store Zertifikat: \LocalMachine\My. Die Beispiele in diesem Thema verwenden Sie die Vorlage "Arbeitsstationsauthentifizierung" (zusammen mit anderen urkundenvorlagen) finden Sie unter [Standard-Vorlagen](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx)können.
* Wenn Sie diese Konfiguration auf einem Computer die Zielknoten, die **den öffentlichen Schlüssel des Zertifikats exportieren**, außer ausgeführt werden und importieren Sie es auf dem Computer führen Sie die Konfiguration aus. Stellen Sie sicher, dass Sie nur den **öffentlichen** Schlüssel exportieren. Sichern des privaten Schlüssels.

## Generelle Prozess

1. Richten Sie die Zertifikate, Tasten und Fingerabdrücke, und stellen Sie sicher, dass jeder Zielknoten Kopien des Zertifikats und der Konfigurationscomputer über den öffentlichen Schlüssel und Fingerabdruck aus.
1. Erstellen Sie einen Datenblock Konfiguration, der den Pfad und den Fingerabdruck des öffentlichen Schlüssels enthält.
1. Erstellen Sie ein Konfigurationsskript, Ihre gewünschte Konfiguration für die Zielknoten definiert und richtet entschlüsseln auf die Zielknoten durch die lokale Konfiguration Befehle-Manager, um die Konfigurationsdaten mithilfe des Zertifikats und seinem Fingerabdruck entschlüsseln.
1. Führen Sie die Konfiguration, die beim Festlegen der Einstellungen für lokale Konfigurations-Manager und starten die Konfiguration DSC wird.

## Von Konfigurationsdaten

Das Konfiguration Datenblock definiert welche Zielknoten auf, ob die Steuerung oder nicht Verschlüsseln der Anmeldeinformationen, die bedeutet, dass der Verschlüsselung und anderen Informationen. Weitere Informationen über die Konfiguration Datenblock finden Sie unter [Konfiguration extrahieren und Umgebungsdaten](configData.md).

Dieses Beispiel zeigt einen Konfiguration Datenblock, der einen Zielknoten fungieren auf benannte TargetNode, den Pfad für die öffentliche Key Zertifikatsdatei (mit dem Namen targetNode.cer) und den Fingerabdruck für den öffentlichen Schlüssel angibt.

```powershell
$ConfigData= @{ 
    AllNodes = @(     
            @{  
                # The name of the node we are describing 
                NodeName = "targetNode" 

                # The path to the .cer file containing the 
                # public key of the Encryption Certificate 
                # used to encrypt credentials for this node 
                CertificateFile = "C:\publicKeys\targetNode.cer" 

         
                # The thumbprint of the Encryption Certificate 
                # used to decrypt the credentials on target node 
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8" 
            }; 
        );    
    }
```

## Konfigurationsskript

Verwenden Sie das Skript selbst, der `PsCredential` Parameter aus, um sicherzustellen, dass Anmeldeinformationen für kürzester Zeit gespeichert werden. Wenn Sie das bereitgestellte Beispiel ausführen, DSC fragt Sie Anmeldeinformationen und Verschlüsseln Sie die MOF-Datei mit der CertificateFile, die die Zielknoten in der Konfiguration Datenblock zugeordnet ist. In diesem Codebeispiel kopiert eine Datei aus einer freigeben, die gesichert wird für einen Benutzer.

```
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
    } 
}
```

## Einrichten von entschlüsseln

Bevor Sie `Start-DscConfiguration` arbeiten können, müssen Sie lokale Konfigurations-Manager auf den einzelnen Zielknoten feststellen, welches Zertifikat verwenden, um die Anmeldeinformationen entschlüsseln mithilfe der Ressource CertificateID zur Überprüfung der Fingerabdruck des Zertifikats. Diese Beispielfunktion findet das entsprechende lokale Zertifikat (möglicherweise müssen Sie es anpassen, damit sie das exakte Zertifikat gefunden werden, die, das Sie verwenden möchten):

```powershell
# Get the certificate that works for encryption 
function Get-LocalEncryptionCertificateThumbprint 
{ 
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid 
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify()) 
        { 
            return $_.Thumbprint 
        } 
    } 
}
```

Mit dem Zertifikat seinem Fingerabdruck identifizierten kann das Skript aktualisiert werden, um den Wert zu verwenden:

```powershell
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
        
        LocalConfigurationManager 
        { 
             CertificateId = $node.Thumbprint 
        } 
    } 
}
```

## Ausführen der Konfigurations

An diesem Punkt, führen Sie die Konfiguration, zwei Dateien ausgegeben wird:

* Einer *. meta.mof-Datei, die im lokalen Konfigurations-Manager, um die Anmeldeinformationen mithilfe des Zertifikats, das auf dem lokalen Speicherplatz gespeichert und seinem Fingerabdruck identifizierten entschlüsseln konfiguriert. Set-DscLocalConfigurationManager gilt für die *. meta.mof Datei.
* Eine MOF-Datei, die die Konfiguration tatsächlich angewendet wird. Start-DscConfiguration gilt die Konfiguration.

Diese Befehle werden diese Schritte ausführen:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Hier ist ein vollständiges Beispiel, bei das alle Schritte sowie eine Helper Cmdlet exportiert und übernimmt die öffentlichen Schlüssel übernimmt aus:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )
    

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }
        
        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key 
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"         

    $ConfigData=    @{
        AllNodes = @(     
                        @{  
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );    
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration") 

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer") 

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}
```