---
title: "Konfigurieren von Zertifikatinfrastruktur für PFX | Microsoft Intune"
description: Erstellen und bereitstellen. PFX Zertifikatsprofile.
keywords: 
author: nbigman
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ms.reviewer: vinaybha
ms.suite: ems
ms.openlocfilehash: da988778ab1156597fe19ac40bab155be6046d75
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren von Zertifikatinfrastruktur
In diesem Thema werden müssen, um zu erstellen und bereitstellen müssen. PFX Zertifikatsprofile.

Zum Ausführen einer beliebigen Zertifikaten basierende Authentifizierung in Ihrer Organisation benötigen Sie eine Enterprise-Zertifizierungsstelle aus.

Verwenden. PFX-Zertifikat Profile sowie die Enterprise-Zertifizierungsstelle, müssen Sie auch aus:

-   Ein Computer, der mit der Zertifizierungsstelle, oder Sie kommunizieren kann können den Zertifizierungsstelle Computer selbst.

-  Der Intune Zertifikat-Verbinder, die auf dem Computer ausgeführt wird, die mit der Zertifizierungsstelle kommunizieren zu können.

## Lokale Infrastruktur Beschreibung


-    **Active Directory-Domäne**: alle in diesem Abschnitt (mit Ausnahme der Web-Anwendung Proxyserver) aufgeführten Server müssen mit Ihrer Active Directory-Domäne verbunden werden.

-  **Zertifizierungsstelle**: ein Enterprise Zertifizierungsstelle (CA), die für eine Enterprise-Edition von Windows Server 2008 R2 oder höher ausgeführt wird. Einer eigenständigen Zertifizierungsstelle wird nicht unterstützt. Anweisungen zum Einrichten einer Zertifizierungsstelle finden Sie unter [Installieren der Zertifizierungsstelle](http://technet.microsoft.com/library/jj125375.aspx).
    Wenn Ihre Zertifizierungsstelle Windows Server 2008 R2 ausgeführt wird, müssen Sie [das Update aus KB2483564 installieren](http://support.microsoft.com/kb/2483564/).

-  **Computer, die mit Zertifizierungsstelle kommunizieren können**: Alternativ selbst Zertifizierungsstelle Computer verwenden.
-  **Microsoft Intune Zertifikat Verbinder**: Sie verwenden die Intune-Verwaltungskonsole aus, um das **Zertifikat Connector** -Installationsprogramm (**ndesconnectorssetup.exe**) herunterladen. Anschließend können Sie ausführen **ndesconnectorssetup.exe** auf dem Computer, wo Sie den Verbinder Zertifikat installieren möchten. Für. PFX-Zertifikat Profile Installieren der Verbinder Zertifikat auf dem Computer, mit der die Zertifizierungsstelle kommuniziert.
-  **Web-Anwendung Proxyserver** (optional): Sie können einen Server, Windows Server 2012 R2 ausführt, oder höher als Server Web Application Proxy (WAP). Diese Konfiguration:
    -  Ermöglicht Geräten Zertifikate mit Verbindung zum Internet erhalten.
    -  Ist Sicherheit empfohlen, wenn Geräte verbinden, über das Internet erhalten und Zertifikate erneuern.

 > [!NOTE]           
> -    Servers, WAP [installieren müssen Sie ein Update](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) hostet, die Unterstützung für lange URLs ermöglicht, die Netzwerk Gerät Registrierung Service (NDES) verwendet werden. Dieses Update ist enthalten, mit der [Dezember 2014 aktualisieren Rollup](http://support.microsoft.com/kb/3013769)oder einzeln aus [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Darüber hinaus entspricht dem Server, dass Hosts WAP ein SSL-Zertifikat müssen den Namen für die externe Clients ebenso wie Trust das SSL-Zertifikat, das auf dem Server NDES verwendet wird veröffentlicht wird. Diese Zertifikate können Sie den WAP-Server die SSL-Verbindung von Clients beendet, und erstellen eine neue SSL-Verbindung auf dem Server NDES.
    Informationen zu Zertifikaten für die WAP finden Sie im Abschnitt **Planen Zertifikate** , der [zum Veröffentlichen von Applications mithilfe von Web Anwendungsproxy planen](https://technet.microsoft.com/library/dn383650.aspx). Allgemeine Informationen zu WAP-Servern finden Sie unter [Arbeiten mit Web Anwendungsproxy](http://technet.microsoft.com/library/dn584113.aspx). |


### Zertifikate und Vorlagen

|Objekt|Details|
|----------|-----------|
|**Zertifikatvorlage**|Mit dieser Vorlage konfiguriert auf Ihrer Zertifizierungsstelle.|
|**Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle**|Sie exportieren dies als eine **CER** -Datei durch die Ausgabe Zertifizierungsstelle oder einem beliebigen Gerät die Zertifizierungsstelle vertraut, und auf Geräte mithilfe des vertrauenswürdige CA Zertifikat Profils bereitstellen.<br /><br />Sie verwenden ein einzelnes vertrauenswürdige Stammzertifizierungsstelle Zertifikat pro Betriebssystemplattform, und ordnen es bei jedem Trusted Root Zertifikat-Profil, das Sie erstellen.<br /><br />Zusätzliche vertrauenswürdige Stammzertifizierungsstelle Zertifikate bei Bedarf können. Angenommen, Sie ist sinnvoll, diese Option, um eine Vertrauensstellung einer Zertifizierungsstelle zur Verfügung stellen, die den Server meldet Authentifizierungszertifikate für Ihre Access-Punkte Wi-Fi.|


## Konfigurieren der Infrastruktur
Bevor Sie Zertifikatsprofile konfigurieren können, müssen Sie die folgenden Aufgaben ausführen. Diese Aufgaben erfordern Kenntnisse in Windows Server 2012 R2 und Active Directory Certificate Services (MDE):

- **Aufgabe 1** : Konfigurieren von Vorlagen auf der Zertifizierungsstelle.
- **Aufgabe 2** : aktivieren, installieren und Konfigurieren der Intune Zertifikat Verbinder.

### Aufgabe 1: Konfigurieren von urkundenvorlagen auf der Zertifizierungsstelle
In dieser Aufgabe veröffentlichen Sie die Vorlage.

##### Konfigurieren die Zertifizierungsstelle

1.  Verwenden Sie auf die Ausstellerzertifizierungsstelle das Urkundenvorlagen-Snap-in eine neue benutzerdefinierte Vorlage erstellen oder kopieren und bearbeiten eine vorhandene Vorlage (wie die Vorlage Benutzer) für die Verwendung mit. PFX.

    Die Vorlage muss Folgendes enthalten:

    -   Geben Sie eine angezeigter **Anzeigename der Vorlage** für die Vorlage.

    -   Wählen Sie auf der Registerkarte **Betreff Namen** **in der Anforderung angeben**. (Sicherheit wird durch die Richtlinie Intune-Modul für NDES erzwungen).

    -   Klicken Sie auf der Registerkarte **Erweiterungen** stellen Sie sicher, dass die **Beschreibung der Anwendungsrichtlinien** **Client-Authentifizierung**enthält.

        > [!IMPORTANT]
        > IOS und urkundenvorlagen Mac OS X, klicken Sie auf der Registerkarte **Erweiterungen** **Key Usage** bearbeiten und dass **Signatur vom Ursprungspunkt Nachweis ist** nicht ausgewählt ist.

2.  Überprüfen Sie die **Gültigkeitsdauer** auf der Registerkarte **Allgemein** der Vorlage ein. Standardmäßig verwendet Intune den Wert in der Vorlage konfiguriert. Jedoch müssen Sie die Option zum Konfigurieren der Zertifizierungsstelle zulassen an einen anderen Wert angeben, der Sie dann innerhalb der Intune-Verwaltungskonsole festlegen können. Wenn Sie immer den Wert in der Vorlage verwenden möchten, überspringen Sie den Rest dieses Schritts.

    > [!IMPORTANT]
    > Das iOS und Mac OS X-Plattformen, stellen Sie immer verwendet, die der Wert in der Vorlage, unabhängig von den anderen Konfigurationen Sie festgelegt werden.

    Führen Sie folgende Befehle auf der CA, die Zertifizierungsstelle damit an die Gültigkeitsdauer angeben können um zu konfigurieren:

    ein.  **Certutil - Setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**

    b.  **Netto Stop certsvc**

    c.  **Netto Start certsvc**

3.  Verwenden Sie die Ausstellerzertifizierungsstelle Zertifizierungsstellen-Snap-in aus, veröffentlichen Sie die Vorlage.

    ein.  Wählen Sie den Knoten **Urkundenvorlagen** , klicken Sie auf die **Aktion** -&gt; **neu** &gt; **Problem Zertifikatvorlage**, und aktivieren Sie die Vorlage, die Sie in Schritt 2 erstellt haben.

    b.  Überprüfen Sie, dass die Vorlage veröffentlicht werden, indem Sie sie unter dem Ordner **Vorlagen** anzeigen.

4.  Auf dem Computer CA, stellen Sie sicher, dass der Computer, der Intune Zertifikat Verbinder befindet, weist Berechtigung registrieren, damit sie die Vorlage zum Erstellen von zugreifen kann die. PFX-Profil. Legen Sie die Berechtigung auf der Registerkarte **Sicherheit** die Eigenschaften der CA Computer an.

### Aufgabe 2: aktivieren, installieren und Konfigurieren der Intune Zertifikat Verbinder
In dieser Aufgabe werden Sie folgende Aufgaben ausführen:

Herunterladen, installieren und Konfigurieren der Verbinder Zertifikat.

##### Zum Aktivieren der Unterstützung für das Zertifikat Verbinder

1.  Öffnen Sie die [Intune-Verwaltungskonsole](https://manage.microsoft.com), und wählen Sie **Administrator** &gt; **Zertifikat Verbinder**.

2.  Wählen Sie aus **lokalen Zertifikat Verbinder konfigurieren**.

3.  Wählen Sie **Aktivieren Zertifikat Verbinder**aus, und wählen Sie dann auf **OK**.

##### Zum Herunterladen, installieren und Konfigurieren der Zertifikat Verbinder

1.  Öffnen Sie die [Intune-Verwaltungskonsole](https://manage.microsoft.com), und wählen Sie **Administrator** &gt; **Verwaltung mobiler Geräte** &gt; **Zertifikat Verbinder** &gt; **Zertifikat Verbinder herunterladen**.

2.  Nachdem der Download abgeschlossen ist, führen Sie das heruntergeladene Installationsprogramm (**ndesconnectorssetup.exe**).

  Führen Sie das Installationsprogramm auf dem Computer, der Verbindung mit der Zertifizierungsstelle herstellen kann. Wählen Sie aus der. PFX-Verteilung option, und wählen Sie dann auf **Installieren**. Nach Abschluss die Installation weiterhin durch das Erstellen eines Profils Zertifikat [Konfigurieren Zertifikatsprofile](configure-intune-certificate-profiles.md)beschrieben.

   <!-- Not sure about step 3 below -->

3.  Wenn Sie für das Client-Zertifikat für das Zertifikat Verbinder aufgefordert werden, wählen Sie aus, **Wählen Sie aus**, und wählen Sie das **Client-Authentifizierung** Zertifikat, das Sie in Aufgabe 3 installiert haben.

    Nachdem Sie das Zertifikat der Client-Authentifizierung auswählen, werden Sie auf die **Client-Zertifikat für Microsoft Intune Zertifikat Connector** -Oberfläche zurückgegeben. Obwohl das Zertifikat, das Sie ausgewählt haben, nicht angezeigt wird, wählen Sie **Weiter** , die Eigenschaften des Zertifikats anzuzeigen. Wählen Sie dann **Weiter**und dann auf **Installieren**.

4.  Nach Abschluss des Assistenten, aber vor den Assistenten zu schließen, klicken Sie auf **das Zertifikat Connector-Benutzeroberfläche zu starten**.

    > [!TIP]
    > Wenn Sie vor dem Start der Zertifikat Connector-Benutzeroberfläche den Assistenten zu schließen, können Sie ihn erneut öffnen, indem Sie den folgenden Befehl ausführen:
    >
    > **&lt;Install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  In der Benutzeroberfläche des **Zertifikats Verbinder** :

    ein. Geben Sie Ihre Anmeldeinformationen für Intune-Administrator oder Anmeldeinformationen für mandantenadministrator mit der Berechtigung zum globale Verwaltung, und wählen Sie **Anmelden** aus.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b. Wählen Sie die Registerkarte **Erweitert** , und klicken Sie dann die Anmeldeinformationen für eine Firma, die die Berechtigung **Emission und Verwalten von Zertifikaten** der ausstellenden Zertifizierungsstelle definiert wurde.

    c. Wählen Sie **anwenden**aus.

    Sie können jetzt das Zertifikat Connector-Benutzeroberfläche schließen.

6.  Öffnen Sie ein Eingabeaufforderungsfenster, und geben Sie **Services.msc ein**. Drücken Sie dann die **EINGABETASTE**, mit der rechten Maustaste **Intune Connector-Dienst**, und wählen Sie **neu starten**.

Um zu überprüfen, dass der Dienst ausgeführt wird, öffnen Sie einen Browser, und geben Sie die folgende URL, der einen Fehler **403** zurückgegeben werden soll:

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Nächste Schritte
Sie können nun zum Zertifikatsprofile einrichten wie in [Konfigurieren Zertifikatsprofilen](Configure-Intune-certificate-profiles.md)beschrieben.
