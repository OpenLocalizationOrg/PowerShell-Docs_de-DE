# DSC für Linux NxSshAuthorizedKeys Ressourcen

Die **NxAuthorizedKeys** Ressource in PowerShell gewünscht Zustand Konfiguration (DSC) bietet ein Verfahren zum Verwalten von ssh Schlüssel für einen bestimmten Benutzer berechtigt.

## Syntax

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| KeyComment| Einen eindeutigen Kommentar für die-Taste. Hiermit wird Schlüssel eindeutig identifizieren.| 
| Stellen Sie sicher| Gibt an, ob die Taste definiert ist. Legen Sie diese Eigenschaft auf "Abwesend", um sicherzustellen, dass der Schlüssel des Benutzers autorisierte Tasten Datei nicht vorhanden ist. Legen Sie dafür den "Präsentieren", um sicherzustellen, dass der Schlüssel autorisierte Key Datei des Benutzers definiert ist.| 
| Benutzername| Der Benutzername ssh verwalten berechtigt Tasten zum. Wenn nicht definiert, ist der Standardbenutzer "root".| 
| Schlüssel| Der Inhalt des Schlüssels. Dies ist erforderlich, wenn **sicherstellen, dass** "Präsentieren" festgelegt ist.| 
| DependsOn | Gibt an, dass die Konfiguration von einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Angenommen, wenn die **ID** für die Ressource Konfiguration Skript Blöcke, die Sie ausführen möchten zuerst **Ressourcenname** und deren **ResourceType**handelt, die Syntax für die Verwendung dieser Eigenschaft ist `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

Das folgende Beispiel definiert eine öffentliche ssh autorisiert Key für den Benutzer "Monuser".

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```

