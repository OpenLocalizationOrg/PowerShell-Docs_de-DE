# Windows PowerShell gewünscht staatliche Konfiguration Übersicht Test 3

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Dieses Thema beschreibt das Feature für Windows PowerShell gewünscht Bundesstaat Konfiguration (DSC) in Windows PowerShell. Sie können in diesem Thema verwenden, können Sie einen Überblick über DSC zu gelangen und die Dokumentationsressourcen zu finden, die Sie verstehen und DSC verwenden müssen.

## Beschreibung der Features
DSC ist eine neue Managementplattform in Windows PowerShell, mit dem Bereitstellen und Verwalten von Konfigurationsdaten für die Software Services und Verwalten der Umgebung, in der diese Dienste ausgeführt werden, können.

DSC bietet eine Reihe von Windows PowerShell-Sprache-Erweiterungen, neue Windows PowerShell-Cmdlets und Ressourcen, die Sie verwenden können, um deklarativ angeben, wie Ihre Software-Umgebung konfiguriert werden soll. Darüber hinaus eine Möglichkeit zum Verwalten und vorhandene Konfigurationen zu verwalten.

## In der Praxis
Es folgen einige Beispielszenarien, in dem Sie integrierte DSC Ressourcen zum Konfigurieren und Verwalten einer Gruppe von Computern (auch bekannt als Zielknoten) in addiert verwenden können:

* Aktivieren oder Deaktivieren von Serverrollen und features
* Verwalten von registrierungseinstellungen
* Verwalten von Dateien und Verzeichnisse durchsuchen
* Starten, beenden und Verwalten von Prozessen und Diensten
* Verwalten von Gruppen und Benutzerkonten
* Neue Software bereitstellen
* Verwalten von Umgebungsvariablen
* Ausführen von Windows PowerShell-Skripts
* Beheben von einer Konfiguration weist nicht an der gewünschten Status drifted.
* Entdecken den Konfigurationsstatus der ist-auf einem bestimmten Knoten

## Grundlegende Konzepte
DSC ist eine deklarative Plattform für Konfiguration, Bereitstellung und Verwaltung von Systeme verwendet. Es besteht aus drei primären Komponenten:

* [Konfigurationen](configurations.md) sind deklarative PowerShell-Skripts das Definieren und Konfigurieren von Instanzen von Ressourcen an. Bei der Ausführung der Konfiguration, DSC (und den Ressourcen, die durch die Konfiguration aufgerufen wird) wird einfach "gestalten können", um sicherzustellen, dass das System in den Status, die durch die Konfiguration angeordnet vorhanden ist. DSC Konfigurationen sind auch Idempotent: lokale Konfigurations-Manager (KGV) weiterhin um sicherzustellen, dass Computer konfiguriert sind, in welchen besagen, dass die Konfiguration deklariert.
* Ressourcen sind die unbedingt erforderlich Bausteine des DSC das Modellieren der verschiedenen Komponenten eines Systems untergeordnete und deren Status ändern des Ablaufs Steuerelement implementieren geschrieben werden. Sie befinden sich in der PowerShell-Module und als generische als eine Datei oder ein Windows-Prozess oder so genau wie ein IIS-Server oder eines virtuellen Computers in Azure ausgeführt modellieren geschrieben werden können.
* Die lokale Konfigurations-Manager (KGV) ist die-Engine keinesfalls DSC die Interaktion zwischen Ressourcen und Konfigurationen erleichtert. Die KGV fragt regelmäßig das System Fluss des Steuerelements, die von Ressourcen implementiert verwenden, um sicherzustellen, dass der Zustand angeordnet, indem Sie eine Konfiguration verwaltet wird. Ist das System aus Zustand, verwendet der KGV weitere Logik innerhalb der Ressourcen ", dies gemäß der Konfiguration Deklaration wird". 

DSC enthält darüber hinaus eine Reihe von neuen Schlüsselwörter, Cmdlets und Tools, die Erstellung von Konfigurationen, Hilfe Build DSC Ressourcen zulassen, Konfigurationen aufzurufen und die KGV verwalten. Viele dieser Cmdlets finden Sie in Windows 8.1 als Bestandteil des Moduls PsDesiredStateConfig (einschließlich `Start-DscConfiguration`, `Set-DscLocalConfigurationManager`, und `Get-DscResource`). Den xDscResourceDesigner (finden Sie in der [PowerShell-Katalog](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)) ist eine Sammlung von Cmdlets, die die Entwicklung von DSC Ressourcen zu vereinfachen.

## Siehe auch
* [DSC Konfigurationen](configurations.md)
* [DSC Ressourcen](resources.md)
* [Konfigurieren der lokalen Konfigurations-Manager](metaconfig.md)

