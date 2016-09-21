# Beginnen Sie mit gewünscht Zustand Konfiguration (DSC) für Linux

In diesem Thema wird erläutert, wie Einleitung zur Arbeit mit PowerShell gewünscht Zustand Konfiguration (DSC) für Linux. Allgemeine Informationen zu DSC finden Sie unter [Erste Schritte mit Windows PowerShell gewünscht Bundesstaat Konfiguration](overview.md).

## Unterstützte Linux Vorgang System-Versionen

Die folgenden Linux Betriebssystemversionen werden für DSC für Linux unterstützt.
- CentOS 5, 6 und 7 (X86/X64)
- Debian GNU/Linux 6 und 7 (X86/X64)
- Oracle-Linux 5, 6 und 7 (X86/X64)
- Red Hat Enterprise Linux Server 5, 6 und 7 (X86/X64)
- SUSE Linux Enterprise Server 10, 11 und 12 (X86/X64)
- Ubuntu Server 12.04 LTS und 14.04 LTS (X86/X64)

Die folgende Tabelle beschreibt die erforderlichen aket Abhängigkeiten für DSC für Linux.

|  Erforderliches Paket |  Beschreibung |  Mindestversion | 
|---|---|---|
| glibc| GNU-Bibliothek| 2... 4 – 31.30| 
| Python| Python| 2.4 – 3.4| 
| omiserver| Open-Infrastruktur| 1.0.8.1| 
| OpenSSL| OpenSSL-Bibliotheken| 0.9.8 oder 1.0| 
| ctypes| Python CTypes-Bibliothek| Muss Python Version übereinstimmen| 
| libcurl| Aufrollen http-Client-Bibliothek| 7.15.1| 

## Installieren von DSC für Linux

Sie müssen die [Open Management Infrastructure (OMI)](https://collaboration.opengroup.org/omi/) vor der Neuinstallation DSC für Linux installieren.

### Installieren von OMI

Gewünschte Konfiguration für Linux erfordert öffnen Management Infrastructure (OMI) CIM-Server, Version 1.0.8.1. OMI heruntergeladen werden kann, aus der Gruppe öffnen: [Open Management Infrastructure (OMI)](https://collaboration.opengroup.org/omi/).

Um OMI installiert haben, installieren Sie das Paket, das für Ihre Linux-System (.rpm oder .deb) und OpenSSL-Version (ssl_098 oder ssl_100) und Architektur (X64/X86) geeignet ist. U/Min-Paketen eignen sich für CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Oracle Linux. DEB Pakete eignen sich für Debian GNU/Linux und Ubuntu-Server. Die ssl_098 Pakete eignen sich auf Computern mit OpenSSL 0.9.8 installiert, während die ssl_100 Pakete mit im 1.0 installiert für Computern geeignet sind.

> **Hinweis**: ermitteln die installierte Version des OpenSSL, führen Sie den Befehl `openssl version`.

Führen Sie den folgenden Befehl, OMI auf einem System CentOS 7 X64 zu installieren.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### DSC installieren

Um DSC installiert haben, installieren Sie das Paket, das für Ihre Linux System (.rpm oder .deb) und OpenSSL Version (ssl_098 oder ssl_100) und Architektur (X64/X86) geeignet ist. U/Min-Paketen eignen sich für CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Oracle Linux. DEB Pakete eignen sich für Debian GNU/Linux und Ubuntu-Server. Die ssl_098 Pakete eignen sich auf Computern mit OpenSSL 0.9.8 installiert, während die ssl_100 Pakete mit im 1.0 installiert für Computern geeignet sind.

> **Hinweis**: für die Ermittlung die installierte Version des OpenSSL ausführen die Befehl Openssl Version.
 
Führen Sie den folgenden Befehl zur Installation von DSC auf einer CentOS 7 X64 System.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## DSC verwenden für Linux

In den folgenden Abschnitten erläutern das Erstellen und Ausführen von DSC Konfigurationen auf Computern Linux.

### Erstellen ein Dokument MOF

Das Windows PowerShell-Konfiguration Schlüsselwort dient zum Erstellen von einer Konfigurations für Linux-Computer wie für Windows-Computer. Die folgenden Schritte beschreiben die Erstellung eines Dokuments Konfiguration für einen Linux-Computer mithilfe von Windows PowerShell.

1. Importieren des n x-Moduls. Das Windows PowerShell-Modul n x muss enthält das Schema für integrierte Ressourcen für DSC für Linux, und mit Ihrem lokalen Computer installiert und in der Konfiguration importiert werden.

    -Kopieren Sie zum Installieren des Moduls n x n x Modulverzeichnis entweder `%UserProfile%\Documents\WindowsPowerShell\Modules\` oder `C:\windows\system32\WindowsPowerShell\v1.0\Modules`. Das Modul n x ist in der DSC für Linux-Installationspaket (MSI) enthalten. Informationen zum Importieren des Moduls n x in der Konfiguration verwenden Sie den __Import-DSCResource__ -Befehl:
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. Definieren einer Konfigurations und Generieren des Dokuments Konfiguration aus:

```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### Drücken Sie die Konfiguration, um dem Linux-computer

Konfiguration von Dokumenten (MOF-Dateien) können auf den Linux-Computer mithilfe des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) abgelegt werden. Damit Sie dieses Cmdlet, zusammen mit dem [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379)ASPX- oder [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) -Cmdlets per Remotezugriff auf einem Linux-Computer verwenden können, müssen Sie eine CIMSession verwenden. Das Cmdlet " [New-CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) " dient zum Erstellen einer CIMSession an den Computer Linux.

Mit dem folgende Code veranschaulicht, wie eine CIMSession für DSC für Linux zu erstellen.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **Hinweis**:
* Für den Modus "Drücken" muss die Benutzeranmeldeinformationen Root-Benutzer auf dem Computer Linux.
* Nur SSL/TLS-Verbindungen werden DSC unterstützt Linux, die neu-CimSession mit dem Festlegen auf $true – UseSSL-Parameter verwendet werden muss.
* Das Zertifikat SSL durch OMI (für DSC) in der Datei angegeben ist: `/opt/omi/etc/omiserver.conf` mit den Eigenschaften: Pemfile und Keyfile.
Wenn dieses Zertifikat nicht durch die Windows-Computer als, die Sie vertrauenswürdig ist auf das [Neue CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) Cmdlet ausgeführt werden, können Sie auswählen, um Überprüfung des Zertifikats mit den Optionen CIMSession ignorieren: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Führen Sie den folgenden Befehl die Konfiguration DSC an den Linux Knoten übertragen.

`Start-DSCConfiguration -Path:"C:\temp" -cimsession:$sess -wait -verbose`

### Verteilen Sie die Konfiguration mit einem Server abrufen

Konfigurationen können in einem Linux-Computer mit einem Server abrufen, genau wie für Windows-Computer verteilt. Leitfaden für die Nutzung von einem Server Abruf finden Sie unter [Windows PowerShell gewünscht Zustand Konfiguration Abruf-Servern](pullServer.md). Zusätzliche Informationen und Einschränkungen im Zusammenhang mit Linux Computern mit einem Abruf Server verwenden finden Sie unter den Versionsinformationen für gewünscht Zustand Konfiguration für Linux.

### Arbeiten mit Konfigurationen lokal

DSC für Linux enthält Skripts für die Arbeit mit Konfiguration vom lokalen Computer Linux. Suchen Sie diese Skripts werden `/opt/microsoft/dsc/Scripts` und umfassen Folgendes:
* GetConfiguration.py

 Gibt die aktuelle Konfiguration auf dem Computer angewendet. Ähnlich wie der Windows PowerShell-Cmdlet "Get-DscConfiguration"-Cmdlet.

`# sudo ./GetConfiguration.py`

* GetMetaConfiguration.py

 Gibt die aktuelle Metatag-Konfiguration auf dem Computer angewendet. Ähnlich wie das Cmdlet " [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) Cmdlet".

`# sudo ./GetMetaConfiguration.py`

* InstallModule.py

 Ein benutzerdefiniertes DSC Ressourcenmodul-Installationen. Erfordert den Pfad Schema MOF-Dateien zu einer ZIP-Datei, die die freigegebenen Modul-Objektbibliothek enthält.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Entfernt ein benutzerdefiniertes DSC Ressourcenmodul. Ist der Name des Moduls entfernen erforderlich.

`# sudo ./RemoveModule.py cnx_Resource`

* SendConfigurationApply.py

 Gilt eine Konfiguration MOF-Datei für den Computer an. Ähnlich wie mit dem [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) -Cmdlet. Erfordert den Pfad für die Konfiguration MOF anwenden.

`# sudo ./RemoveModule.py cnx_Resource`

* SendMetaConfiguration.py

 Gilt eine Metatag Konfiguration MOF-Datei für den Computer an. Ähnlich wie das Cmdlet " [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) ". Erfordert den Pfad für das Metatag Konfiguration MOF anwenden.

`# sudo ./SendMetaConfiguration.py –configurationmof /tmp/localhost.meta.mof`

## PowerShell gewünscht staatliche Konfiguration für Linux-Protokolldateien

Die folgenden Protokolldateien werden für DSC für Linux Nachrichten generiert.

|Protokolldatei|Verzeichnis|Beschreibung|
|---|---|---|
|omiserver.log|/ Suchbegriffen/Omi/Var/Log /|Nachrichten, die für den Vorgang des Servers OMI CIM.|
|DSC.log|/ Suchbegriffen/Omi/Var/Log /|Nachrichten, die für den Vorgang der lokalen Konfigurations-Manager (KGV) und DSC Ressourcenvorgänge.|
