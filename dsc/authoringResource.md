# Erstellen Sie benutzerdefinierte Windows PowerShell Desired Zustand Konfiguration Ressourcen Test6 - testen

> Betrifft: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell gewünschten Zustand Konfiguration (DSC) verfügt über integrierte Ressourcen, mit denen Sie Ihre Umgebung konfigurieren. (Weitere Informationen finden Sie unter [Integrierte Windows PowerShell gewünschten Zustand Konfigurationsressourcen](builtInResource.md)). Dieses Thema bietet eine Übersicht über die Entwicklung von Ressourcen und Links zu Themen mit bestimmten Informationen und Beispiele.

## DSC Ressource Komponenten

Eine Ressource DSC ist ein Windows PowerShell-Modul. Das Modul enthält das Schema (die Definition der konfigurierbaren Eigenschaften) und die Implementierung (der Code, die die eigentliche durch eine Konfiguration angegebenen Arbeit) für die Ressource. Ein DSC Ressourcenschema kann in einer MOF-Datei definiert werden, und die Implementierung von einem Skriptmodul erfolgt. Beginnen mit der Unterstützung von PowerShell-Klassen in Version 5, können das Schema und die Implementierung in einer Klasse definiert werden. Die folgenden Themen wird ausführlich beschrieben, wie DSC Ressourcen erstellen.

* [Schreiben eine benutzerdefinierte DSC Ressource mit MOF](authoringResourceMOF.md) 
* [Implementieren eine Ressource DSC in C##](authoringResourceMofCS.md) 
* [Schreiben eine benutzerdefinierte DSC Ressource mit PowerShell Klassen](authoringResourceClass.md) 
* [Zusammengesetzte Ressourcen: die Verwendung einer DSC Konfigurations als Ressource](authoringResourceComposite.md) 
* [Verwenden das Tool Ressourcen-Designer](authoringResourceMofDesigner.md) 
