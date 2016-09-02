# Umsetzung Konfigurationen

>Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

Es gibt zwei Methoden darin, PowerShell gewünschten Zustand Konfiguration (DSC) Konfigurationen: push-Modus und Pull-Modus.

## Push-Modus
![Push-Modus](images/Push.png "How push mode works")

Push-Modus bezieht sich auf einen Benutzer aktiv eine Konfiguration mit einem Zielknoten durch Aufrufen des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) anwenden.

Nach dem Erstellen und Kompilieren eine Konfiguration, Sie können widersprechenden es im Push-Modus durch Aufrufen des Cmdlets [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Festlegen der - Parameter Path des Cmdlets auf den Pfad die Konfiguration MOF gespeichert ist. Wenn die Konfiguration MOF Locted am ist beispielsweise `C:\DSC\Configurations\localhost.mof`, wenden Sie es auf dem lokalen Computer mit dem folgenden Befehl:
`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Hinweis__: in der Standardeinstellung führt DSC eine Konfiguration im Hintergrund. Um die Konfiguration interaktiv ausgeführt werden soll, rufen Sie die [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) mit der __-Warten__ Parameter.

## Pull-Modus
![Pull-Modus](images/Pull.png "How pull mode works") im Modus "Pull" Pull-Clients sind so konfiguriert, dass ihre gewünschten Zustand Konfigurationen aus einem remote Pull-Server abzurufen. Entsprechend der Pull-Server Dienst hosten der DSC eingerichtet wurde, und hat bereitgestellt wurde, mit der Konfigurationen und Ressourcen, die von den Clients Pull erforderlich sind.
Jeweils Pull-Clients hat eine geplante Aufgabe, die eine periodische Compliance-Überprüfung nach der Konfiguration des Knotens ausgeführt wird. Beim Auslösen des Ereignisses beim ersten wird die lokale Configuration Manager (LCM) auf dem Client abrufen, um die Konfiguration zu überprüfen. Wenn der Pull-Client, als konfiguriert ist gewünscht werden soll, passiert nichts. Anderenfalls: LCM sendet eine Anforderung an dem Server Pull zu eine bestimmte Konfiguration erhalten. Wenn die Konfiguration auf dem Server Pull vorhanden ist, und anfänglichen Überprüfung wird übergibt, wird die Konfiguration an den Client Pull übertragen, wo es dann vom LCM ausgeführt wird.

Die folgenden Themen wird erläutert, wie eingerichtet Pull-Servern und Clients:

- [Einrichten von einem Pull-Webserver](pullServer.md)
- [Einrichten eines SMB Pull-Servers](pullServerSMB.md)
- [Konfigurieren einer Pull-Clients](pullClientConfigID.md)