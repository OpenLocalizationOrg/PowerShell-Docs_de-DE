---
title: "Konfigurieren von Zertifikatinfrastruktur für SCEP | Microsoft Intune"
description: "Infrastruktur für das Erstellen und Bereitstellen von SCEP Zertifikatsprofile."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4ae137ae-34e5-4a45-950c-983de831270f
ms.reviewer: kmyrup
ms.suite: ems
ms.openlocfilehash: adef720c31eea978dc899f62e1eef60af2812a3d
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren von Zertifikatinfrastruktur für SCEP
Dieses Thema wird beschrieben, welche Infrastruktur, die Sie erstellen und Bereitstellen von SCEP Zertifikatsprofile benötigen.

### Lokale Infrastruktur

-    **Active Directory-Domäne**: alle in diesem Abschnitt (mit Ausnahme der Web-Anwendung Proxyserver) aufgeführten Server müssen mit Ihrer Active Directory-Domäne verbunden werden.

-  **Zertifizierungsstelle** (Zertifizierungsstelle CA): ein Enterprise Zertifizierungsstelle (CA), die für eine Enterprise-Edition von Windows Server 2008 R2 oder höher ausgeführt wird. Einer eigenständigen Zertifizierungsstelle wird nicht unterstützt. Anweisungen zum Einrichten einer Zertifizierungsstelle finden Sie unter [Installieren der Zertifizierungsstelle](http://technet.microsoft.com/library/jj125375.aspx).
    Wenn Ihre Zertifizierungsstelle Windows Server 2008 R2 ausgeführt wird, müssen Sie [das Update aus KB2483564 installieren](http://support.microsoft.com/kb/2483564/).
Ich
-  **NDES Server**: auf einem Server, Windows Server 2012 R2 ausgeführt wird, oder höher, richten Sie oben im Netzwerk Gerät Registrierung Service (NDES). Intune unterstützt NDES verwenden, wenn es auf einem Server ausgeführt wird, der auch die Enterprise-Zertifizierungsstelle ausgeführt wird nicht. Anweisungen zum Konfigurieren von Windows Server 2012 R2 die Registrierungsdiensts hosten finden Sie unter [Netzwerk Gerät Registrierungs-Dienst Anleitungen](http://technet.microsoft.com/library/hh831498.aspx) . Der Server NDES Domäne der Domäne, die die Zertifizierungsstelle gehostet werden, und nicht auf dem gleichen Server wie die Zertifizierungsstelle. Weitere Informationen zur Bereitstellung des Servers NDES in einer getrennten Struktur, die isoliert Netzwerk oder den internen Domänennamen finden Sie im [mit Richtlinie-Modul mit dem Netzwerk Gerät Registrierungs-Dienst](https://technet.microsoft.com/en-us/library/dn473016.aspx).

-  **Microsoft Intune Zertifikat Verbinder**: Sie verwenden die Intune-Verwaltungskonsole aus, um das **Zertifikat Connector** -Installationsprogramm (**ndesconnectorssetup.exe**) herunterladen. Anschließend können Sie ausführen **ndesconnectorssetup.exe** auf dem Computer, wo Sie den Verbinder Zertifikat installieren möchten.
-  **Web-Anwendung Proxyserver** (optional): Sie können einen Server, Windows Server 2012 R2 ausführt, oder höher als Server Web Application Proxy (WAP). Diese Konfiguration:
    -  Ermöglicht Geräten Zertifikate mit Verbindung zum Internet erhalten.
    -  Ist Sicherheit empfohlen, wenn Geräte verbinden, über das Internet erhalten und Zertifikate erneuern.

 > [!NOTE]           
> -    Servers, WAP [installieren müssen Sie ein Update](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) hostet, die Unterstützung für lange URLs ermöglicht, die vom Netzwerk Gerät Registrierungs-Dienst verwendet werden. Dieses Update ist enthalten, mit der [Dezember 2014 aktualisieren Rollup](http://support.microsoft.com/kb/3013769)oder einzeln aus [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Darüber hinaus entspricht dem Server, dass Hosts WAP ein Zertifikat einer Zertifizierungsstelle müssen den Namen für die externe Clients ebenso wie Trust das SSL-Zertifikat, das auf dem Server NDES verwendet wird veröffentlicht wird. Diese Zertifikate können Sie den WAP-Server die SSL-Verbindung von Clients beendet, und erstellen eine neue SSL-Verbindung auf dem Server NDES.
    Informationen zu Zertifikaten für die WAP finden Sie im Abschnitt **Planen Zertifikate** , der [zum Veröffentlichen von Applications mithilfe von Web Anwendungsproxy planen](https://technet.microsoft.com/library/dn383650.aspx). Allgemeine Informationen zu WAP-Servern finden Sie unter [Arbeiten mit Web Anwendungsproxy](http://technet.microsoft.com/library/dn584113.aspx). |

### Netzwerk-Anforderungen

Aus dem Internet Umfang Netzwerk wird auf dem Server NDES zulassen Sie Port 443 von alle Hosts/IP-Adressen im Internet.

Ermöglichen Sie in den Rand herum Netzwerk vertrauenswürdigen Netzwerk alle Ports und Protokolle für Domänenzugriff auf dem Server für die Domäne NDES erforderlich. Der Server NDES benötigt Zugriff auf das Zertifikatsservern, DNS-Server, Server-Konfigurations-Manager und Domain Controller.

Es empfiehlt sich den NDES Server über einen Proxy, wie der [Azure AD-Anwendungsproxy](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-proxy-publish/), [Web Access Proxy](https://technet.microsoft.com/en-us/library/dn584107.aspx)oder einer Drittanbieter-Proxy veröffentlichen.


### <a name="BKMK_CertsAndTemplates"></a>Zertifikate und Vorlagen

|Objekt|Details|
|----------|-----------|
|**Zertifikatvorlage**|Mit dieser Vorlage konfiguriert auf Ihrer Zertifizierungsstelle.|
|**Client-Authentifizierungszertifikat**|Angefordert von Ihrem ausstellenden CA oder öffentliche Zertifizierungsstelle, installieren Sie dieses Zertifikat auf dem Server NDES.|
|**Serverzertifikat-Authentifizierung**|In der Lage, Ihre angefordert oder öffentliche Zertifizierungsstelle, installieren und binden diese SSL-Zertifikat in IIS auf dem Server NDES.|
|**Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle**|Sie exportieren dies als eine **CER** -Datei aus der Stammzertifizierungsstelle oder einem beliebigen Gerät aus dem die Stammzertifizierungsstelle vertraut, und unter Verwendung des vertrauenswürdige CA Zertifikat Profils an Geräte bereitstellen.<br /><br />Sie verwenden ein einzelnes vertrauenswürdige Stammzertifizierungsstelle Zertifikat pro Betriebssystemplattform, und ordnen es bei jedem Trusted Root Zertifikat-Profil, das Sie erstellen.<br /><br />Zusätzliche vertrauenswürdige Stammzertifizierungsstelle Zertifikate bei Bedarf können. Angenommen, Sie ist sinnvoll, diese Option, um eine Vertrauensstellung einer Zertifizierungsstelle zur Verfügung stellen, die den Server meldet Authentifizierungszertifikate für Ihre Access-Punkte Wi-Fi.|

### <a name="BKMK_Accounts"></a>Konten

|Namen|Details|
|--------|-----------|
|**NDES Dienstkontos**|Ein Domänenbenutzerkonto als NDES Dienstkonto verwendet werden soll.|

## <a name="BKMK_ConfigureInfrastructure"></a>Konfigurieren der Infrastruktur
Zertifikatsprofile konfigurieren zu können müssen Sie die folgenden Aufgaben ausführen, die Kenntnisse in Windows Server 2012 R2 und Active Directory Certificate Services (MDE) erforderlich ist:

**Aufgabe 1**: erstellen ein NDES Service-Kontos

**Aufgabe 2**: Konfigurieren von urkundenvorlagen auf der Zertifizierungsstelle

**Aufgabe 3**: Konfigurieren von erforderlichen Komponenten auf dem Server NDES

**Aufgabe 4**: Konfigurieren von NDES zur Verwendung mit Intune

**Aufgabe 5**: aktivieren, installieren und Konfigurieren der Intune Zertifikat Verbinder

### Aufgabe 1: Erstellen eines NDES Service-Kontos

Erstellen eines Benutzerkontos Domäne als Dienstkonto NDES verwenden. Vorlagen auf CA, die Sie konfigurieren, bevor Sie installieren und Konfigurieren von NDES werden Sie dieses Konto angeben. Stellen Sie sicher, dass der Benutzer über die Standardberechtigungen, die **Anmeldung lokal**, **Melden Sie sich als einen Dienst** und **Melden Sie sich als eine Stapelverarbeitung** Rechte verfügt. Einige Organisationen haben Sichern von Richtlinien, die australischen deaktivieren.




### Aufgabe 2: Konfigurieren von Vorlagen auf der Zertifizierungsstelle
In dieser Aufgabe werden Sie folgende Aufgaben ausführen:

-   Konfigurieren einer Zertifikatvorlage für NDES

-   Veröffentlichen Sie die Vorlage für NDES

##### Konfigurieren die Zertifizierungsstelle

1.  Melden Sie sich als Administrator der Organisation an. 

2.  Verwenden Sie auf der Ausstellerzertifizierungsstelle das Zertifikatvorlagen-Snap-in in eine neue benutzerdefinierte Vorlage erstellen oder eine vorhandene Vorlage kopieren und dann Bearbeiten einer vorhandenen Vorlage (wie die Vorlage Benutzer) für die Verwendung mit NDES.

    Die Vorlage müssen die folgenden Konfigurationen:

    -   Geben Sie eine angezeigter **Anzeigename der Vorlage** für die Vorlage.

    -   Wählen Sie auf der Registerkarte **Betreff Namen** **in der Anforderung angeben**. (Sicherheit wird durch die Richtlinie Intune-Modul für NDES erzwungen).

    -   Klicken Sie auf der Registerkarte **Erweiterungen** stellen Sie sicher, dass die **Beschreibung der Anwendungsrichtlinien** **Client-Authentifizierung**enthält.

        > [!IMPORTANT]
        > Bearbeiten Sie für iOS und Mac OS X urkundenvorlagen, und klicken Sie auf der Registerkarte **Erweiterungen** **Key Usage** und sicherstellen Sie, dass die **Signatur ist Ursprungsnachweis** nicht aktiviert ist.

    -   Klicken Sie auf der Registerkarte **Sicherheit** fügen Sie des Dienstkontos NDES hinzu, und probieren Sie es **Registrieren** Berechtigungen zur Verwaltung der Vorlage. Intune-Administratoren, die SCEP Profile erstellen werden erfordern **Leseberechtigungen** , damit sie die Vorlage beim Erstellen von Profilen SCEP wechseln können.
    
    > [!NOTE]
    > Um widerrufen service Zertifikate der NDES Konto Anforderungen Rechte *Problem und Verwalten von Zertifikaten* für jede ein Zertifikatsprofil verwendeten Zertifikatsvorlage.

3.  Überprüfen Sie die **Gültigkeitsdauer** auf der Registerkarte **Allgemein** der Vorlage ein. Standardmäßig verwendet Intune den Wert in der Vorlage konfiguriert. Jedoch müssen Sie die Option zum Konfigurieren der Zertifizierungsstelle zulassen an einen anderen Wert angeben, der Sie dann innerhalb der Intune-Verwaltungskonsole festlegen können. Wenn Sie immer den Wert in der Vorlage verwenden möchten, überspringen Sie den Rest dieses Schritts.

    > [!IMPORTANT]
    > Das iOS und Mac OS X-Plattformen, stellen Sie immer verwendet, die der Wert in der Vorlage unabhängig von den anderen Konfigurationen Sie festgelegt werden.

Hier sind Screenshots der Konfiguration eine Beispiel-Vorlage.

![Vorlage Anforderung Behandlung Registerkarte](..\media\scep_ndes_request_handling.png) 

![Vorlage, Betreff Namen Registerkarte](..\media\scep_ndes_subject_name.jpg) 

![Vorlage, Sicherheitsregisterkarte](..\media\scep_ndes_security.jpg) 

![Vorlage Erweiterungen Registerkarte](..\media\scep_ndes_extensions.jpg) 

![Vorlage, Emission Anforderungen Registerkarte](..\media\scep_ndes_issuance_reqs.jpg) 

>   [!IMPORTANT]
    > Anwendungsrichtlinien (in den 4. Screenshot) fügen Sie nur die Anwendungsrichtlinien erforderlich hinzu. Bestätigen Sie Ihre Auswahl mit Ihrer Administratoren Sicherheit.
   


So konfigurieren Sie die Zertifizierungsstelle zulässig an die Gültigkeitsdauer angeben, in der Zertifizierungsstelle führen Sie die folgenden Befehle:

   1.  **Certutil - Setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**
   2.  **Netto Stop certsvc**

   3.  **Netto Start certsvc**

4.  Verwenden Sie die Ausstellerzertifizierungsstelle Zertifizierungsstellen-Snap-in aus, veröffentlichen Sie die Vorlage.

    1.  Wählen Sie den Knoten **Urkundenvorlagen** , klicken Sie auf die **Aktion** -&gt; **neu** &gt; **Problem Zertifikatvorlage**, und aktivieren Sie die Vorlage, die Sie in Schritt 2 erstellt haben.

    2.  Überprüfen Sie, dass die Vorlage veröffentlicht werden, indem Sie sie unter dem Ordner **Vorlagen** anzeigen.


### Aufgabe 3 – Konfigurieren Sie erforderliche Komponenten auf dem Server NDES
In dieser Aufgabe werden Sie folgende Aufgaben ausführen:

-   NDES auf einem Windows-Server hinzufügen und Konfigurieren von IIS NDES unterstützen

-   Hinzufügen des NDES Dienstkontos in der Gruppe IIS_IUSR

-   Festlegen Sie den SPN für das NDES Dienstkonto




   1.  Auf dem Server, die Hosts NDES wird, müssen Sie Anmelden als eine einen **Unternehmensadministrator**und verwenden Sie dann das [Hinzufügen von Rollen und Features-Assistenten](https://technet.microsoft.com/library/hh831809.aspx) , NDES zu installieren:

    1.  Wählen Sie im Assistenten **Active Directory Certificate Services** , auf die AD CS Rollendienste zuzugreifen. Wählen Sie den **Registrierungsdiensts**, deaktivieren Sie **Zertifizierungsstelle**, und schließen Sie den Assistenten.

        > [!TIP]
        > Klicken Sie auf den **Installationsvorgang** Seite des Assistenten nicht auf **Schließen**. Klicken Sie stattdessen auf den Link für **Konfigurieren Active Directory Certificate Services auf dem Zielserver**. Daraufhin wird der **AD CS Konfigurations** -Assistent, die für den nächsten Vorgang verwendet. Nachdem AD CS Konfiguration geöffnet wurde, können Sie den Assistenten zum Hinzufügen von Rollen und Features schließen.

    2.  Wenn auf dem Server NDES hinzugefügt wurde, installiert der Assistent auch IIS aus. Stellen Sie sicher, dass IIS die folgenden Konfigurationen hat:

        -   **Webserver** &gt; **Security** &gt; **anfordern Filtern**

        -   **Webserver** &gt; **Application Development** &gt; **ASP.NET 3.5**. ASP.NET 3.5 installieren, installieren Sie .NET Framework 3.5. Bei der Installation von .NET Framework 3.5 Installieren der Core **.NET Framework 3.5** -Funktion und die **Http-Aktivierung**.

        -   **Webserver** &gt; **Application Development** &gt; **ASP.NET 4.5**. Installieren von ASP.NET 4.5 wird .NET Framework 4.5 installiert. Bei der Installation von .NET Framework 4.5 Installieren der Core **.NET Framework 4.5** Feature, **ASP.NET 4.5**und der **WCF-Dienste** &gt; Feature **Http-Aktivierung** .

        -   **Tools zum Projektmanagement** &gt; **IIS 6 Management Compatibility** &gt; **IIS 6 Metabasiskompatibilität**

        -   **Tools zum Projektmanagement** &gt; **IIS 6 Management Compatibility** &gt; **IIS 6 WMI-Kompatibilität**

  2.  Fügen Sie auf dem Server das Dienstkonto NDES als Mitglied der Gruppe **IIS_IUSR** hinzu.

   3.  Führen Sie in ein erweitertes Eingabeaufforderungsfenster zum Festlegen des SPN des NDES Dienstkontos den folgenden Befehl aus:

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   Wenn der Server NDES **Server01**heißt, Ihre Domäne ist **Contoso.com**ein, und das Dienstkonto ist **NDESService**, verwenden:

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

### Task 4 - NDES für die Verwendung mit Intune konfigurieren
In dieser Aufgabe werden Sie folgende Aufgaben ausführen:

-   Konfigurieren von NDES für die Verwendung mit CA, die

-   Binden des Serverzertifikats Authentifizierung (SSL) in IIS

-   Konfigurieren von Filtern in IIS Anforderung

##### So konfigurieren Sie NDES für die Verwendung mit Intune

1.  Auf dem Server NDES den AD CS Konfigurations-Assistenten zu öffnen, und klicken Sie dann die folgenden Konfigurationen vornehmen.

    > [!TIP]
    > Wenn Sie den Link in der vorherigen Aufgabe geklickt haben, ist mit diesem Assistenten bereits geöffnet. Öffnen Sie andernfalls Server-Manager, um die Konfiguration nach der Bereitstellung für Active Directory Certificate Services zuzugreifen.

    -   Wählen Sie auf der Seite **Rolle Services** **Registrierungsdiensts**aus.

    -   Geben Sie auf der Seite **Dienstkonto für NDES** des Dienstkontos NDES aus.

    -   Klicken Sie auf der Seite **Zertifizierungsstelle für NDES** klicken Sie auf **auswählen**, und wählen Sie dann auf Zertifizierungsstelle, die Stelle, an der Sie die Vorlage konfiguriert.

    -   Legen Sie auf der Seite **Verschlüsselung für NDES** die wichtige Länge in Ihrem Unternehmen zu erfüllen.

    Klicken Sie auf der Seite **Bestätigung** auf **Konfigurieren** , um den Assistenten zu beenden.

2.  Bearbeiten Sie nach Abschluss des Assistenten, auf dem Server NDES den folgenden Registrierungsschlüssel:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    Schlüssel bearbeiten, der Zertifikatvorlage **Zweck**, wie er auf der Registerkarte **Behandlung anfordern** , und klicken Sie dann den entsprechenden Eintrag in der Registrierung bearbeiten, indem Sie ersetzt die vorhandenen Daten mit dem Namen der Zertifikat-Vorlage (nicht der Anzeigename der Vorlage), die Sie in Aufgabe 1 angegeben haben. In der folgenden Tabelle ordnet die Werte in der Registrierung Zertifikat Vorlage Zweck:

    |Zertifikatvorlage Zweck (Registerkarte "auf das anfordern Handling")|Registrierungseintrag bearbeiten|Wert der Intune-Verwaltungskonsole für das Profil SCEP angezeigt|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Signatur|SignatureTemplate|Digitale Signatur|
    |Verschlüsselung|EncryptionTemplate|Key-Chiffrierung|
    |Signatur und Verschlüsselung|GeneralPurposeTemplate|Key-Chiffrierung<br /><br />Digitale Signatur|
    Beispielsweise ist der Zweck der Zertifikatvorlage **Verschlüsselung**, klicken Sie dann bearbeiten Sie den Wert **EncryptionTemplate** , um den Namen der Zertifikatvorlage werden.

3. Der Server NDES erhalten sehr lange URLs (Abfragen), die erfordern, dass Sie zwei Registrierungseinträge hinzufügen:

    |Speicherort|Wert|Typ|Daten|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (dezimal)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (dezimal)|


4. Wählen Sie in IIS-Manager **Standardwebsite** -> **Filtern anfordern** -> **Feature Einstellung bearbeiten**, und ändern Sie die **Maximale URL-Länge** und **Maximum Abfragezeichenfolge** bis *65534*, wie gezeigt.

    ![IIS max URL und Abfrage Länge](..\media\SCEP_IIS_max_URL.png) 

5.  Starten Sie den Server ein. **Iisreset** ausführen, auf dem Server werden nicht ausreichend, um diese Änderungen Fertigstellen.
6. Navigieren Sie zu http://*FULLY*/certsrv/mscep/mscep.dll. Eine NDES Seite vergleichbar ist sollte angezeigt werden:

    ![Test NDES](..\media\SCEP_NDES_URL.png) 

    Wenn ein **503 Dienst nicht verfügbar**angezeigt wird, überprüfen Sie die Nachrichtendatei. Ist zu rechnen, dass die Anwendung Ressourcenpool aufgrund einer fehlender rechts für den Benutzer NDES beendet wird. In Aufgabe 1 werden australischen beschrieben.

##### Zum Installieren und Zertifikate auf dem Server NDES binden

1.  Klicken Sie auf dem Server NDES fordern Sie an, und installieren Sie ein Zertifikat für die **Serverauthentifizierung** von Ihrem internen oder öffentlichen Zertifizierungsstelle. Klicken Sie dann binden Sie diese SSL-Zertifikat in IIS.

    > [!TIP]
    > Nachdem Sie das SSL-Zertifikat in IIS binden, installieren Sie auch ein Client-Authentifizierungszertifikat. Dieser Urkunde kann von einem beliebigen Zertifizierungsstelle ausgestellt werden, die vom Server NDES vertrauenswürdig ist. Obwohl es sich nicht um eine bewährte Methode ist, können Sie das gleiche Zertifikat für Server- und Authentifizierung verwenden, solange das Zertifikat beide verbessern Schlüsselverwendungen (EKU) verfügt. Überprüfen Sie die folgenden Schritte aus, Informationen zu diesen Authentifizierungszertifikaten.

    1.  Nachdem Sie das Authentifizierung Serverzertifikat erhalten haben, öffnen Sie **IIS-Manager**zu, wählen Sie im Bereich **Verbindungen** der **Standard-Website** aus und klicken Sie im Bereich **Aktionen** auf **Bindungen** .

    2.  Klicken Sie auf **Hinzufügen**, **Geben** auf **Https**festgelegt, und dann stellen Sie sicher, dass der Port **443**verwendet wird. (Nur Port 443 wird eigenständigen Intune unterstützt.

    3.  Geben Sie für **SSL-Zertifikat**das Serverzertifikat für die Authentifizierung ein.

        > [!NOTE]
        > Wenn der Server NDES sowohl einen internen und externen Namen für eine einzelne Netzwerkadresse verwendet, müssen das Authentifizierung Serverzertifikat einen **Betreff Namen** mit einem externen öffentlichen Servernamen und einen **Alternativen Namen** , die den internen Servernamen enthält.

2.  Klicken Sie auf dem Server NDES fordern Sie an, und installieren Sie ein Zertifikat **Client-Authentifizierung** von Ihrer internen Zertifizierungsstelle oder einer öffentlichen Zertifizierungsstelle. Dies kann das gleiche Zertifikat als der Authentifizierung Serverzertifikat sein, wenn das Zertifikat beide Funktionen aufweist.

    Das Zertifikat der Client-Authentifizierung müssen die folgenden Eigenschaften auf:

    **Erweiterte Verwendung des Schlüssels** – Dies darf **Client-Authentifizierung**enthalten.

    **Name der Betreff** - Dies muss gleich der DNS-Name des Servers, in dem Sie das Zertifikat (der Server NDES) installieren.

##### So konfigurieren Sie IIS Filterung anfordern

1.  Öffnen Sie auf dem Server NDES **IIS-Manager**zu, wählen Sie die **Standard-Website** im Bereich **Verbindungen** und **Filtern anfordern**zu öffnen.

2.  Klicken Sie auf **Edit Feature Settings**, und legen Sie Folgendes:

    **Zeichenfolge (Byte) Abfragen** = **65534**

    **Maximale Länge der URL (Bytes)** = **65534**

3.  Überprüfen Sie den folgenden Registrierungsschlüssel:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Stellen Sie sicher, dass die folgenden Werte als DWORD-Einträge festgelegt sind:

    Name: **MaxFieldLength**, mit einem Dezimalwert von **65534**

    Name: **MaxRequestBytes**, mit einem Dezimalwert von **65534**

4.  Starten Sie den NDES Server an. Der Server ist nun zur Unterstützung der Verbinder Zertifikat bereit.

### Aufgabe 5: aktivieren, installieren und Konfigurieren der Intune Zertifikat Verbinder
In dieser Aufgabe werden Sie folgende Aufgaben ausführen:

Aktivieren der Unterstützung für NDES in Intune.

Herunterladen, installieren und Konfigurieren der Verbinder Zertifikat auf dem Server NDES.

##### Zum Aktivieren der Unterstützung für das Zertifikat Verbinder

1.  Öffnen Sie die [Intune-Verwaltungskonsole](https://manage.microsoft.com), klicken Sie auf **Administrator** &gt; **Zertifikat Verbinder**.

2.  Klicken Sie auf **lokale Zertifikat Connector konfigurieren**.

3.  Wählen Sie **Aktivieren Zertifikat Verbinder**aus, und klicken Sie dann auf **OK**.

##### Zum Herunterladen, installieren und Konfigurieren der Zertifikat Verbinder

1.  Öffnen Sie die [Intune-Verwaltungskonsole](https://manage.microsoft.com), und klicken Sie dann auf **Admin** &gt; **Verwaltung mobiler Geräte** &gt; **Zertifikat Verbinder** &gt; **Zertifikat Verbinder herunterladen**.

2.  Nachdem der Download abgeschlossen ist, führen Sie das heruntergeladene Installationsprogramm (**ndesconnectorssetup.exe**) auf einem Windows Server 2012 R2-Server aus. Das Installationsprogramm installiert auch das Richtlinienmodul für NDES und den Webdienst CRP. (Der CRP-Webdienst, CertificateRegistrationSvc, wird als Anwendung in IIS ausgeführt.)

    > [!NOTE]
    > Bei der Installation NDES für eigenständigen Intune installiert CRP Dienst automatisch mit der Verbinder Zertifikat. Wenn Sie mit dem Konfigurations-Manager Intune verwenden, installieren Sie das Zertifikat Registrierung Punkt als separate Website Systemrolle aus.

3.  Wenn Sie für das Client-Zertifikat für das Zertifikat Verbinder aufgefordert werden, klicken Sie auf **auswählen**, und wählen Sie das **Client-Authentifizierung** Zertifikat, das Sie auf dem Server NDES in Aufgabe 3 installiert haben.

    Nachdem Sie das Zertifikat der Client-Authentifizierung auswählen, werden Sie auf die **Client-Zertifikat für Microsoft Intune Zertifikat Connector** -Oberfläche zurückgegeben. Obwohl das Zertifikat, das Sie ausgewählt haben, nicht angezeigt wird, klicken Sie auf **Weiter** , wenn Sie die Eigenschaften des Zertifikats anzuzeigen. Klicken Sie auf **Weiter**, und klicken Sie dann auf **Installieren**.

4.  Nach Abschluss des Assistenten, aber vor den Assistenten zu schließen, klicken Sie auf **das Zertifikat Connector-Benutzeroberfläche zu starten**.

    > [!TIP]
    > Wenn Sie vor dem Start der Zertifikat Connector-Benutzeroberfläche den Assistenten zu schließen, können Sie ihn erneut öffnen, indem Sie den folgenden Befehl ausführen:
    >
    > **&lt;Install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  In der Benutzeroberfläche des **Zertifikats Verbinder** :

    Klicken Sie auf **Anmelden** , und geben Sie Ihre Anmeldeinformationen für Intune-Administrator oder Anmeldeinformationen für einen mandantenadministrator mit der Berechtigung zum globale Verwaltung.

    Wenn Ihre Organisation einen Proxyserver verwendet, und der Proxy für den Zugriff auf das Internet NDES-Server erforderlich ist, klicken Sie auf **Proxyserver verwenden** , und geben Sie dann den Namen des Proxyservers, Anschluss und Anmeldeinformationen für die Verbindung.

    Wählen Sie die Registerkarte **Erweitert** , und klicken Sie dann die Anmeldeinformationen für ein Konto mit der Berechtigung **Emission und Verwalten von Zertifikaten** auf Ihre Zertifikataussteller und klicken Sie dann auf **Übernehmen**.

    Sie können jetzt das Zertifikat Connector-Benutzeroberfläche schließen.

6.  Öffnen Sie ein Eingabeaufforderungsfenster und geben Sie **Services.msc ein**, und klicken Sie dann drücken Sie die **EINGABETASTE**, mit der rechten Maustaste **Intune Connector-Dienst**, und klicken Sie dann auf **neu starten**.

Um zu überprüfen, dass der Dienst ausgeführt wird, öffnen Sie einen Browser, und geben Sie die folgende URL, der einen Fehler **403** zurückgegeben werden soll:

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

## Nächste Schritte
Sie können nun zum Konfigurieren von Benutzerprofilen Zertifikat, wie in [Konfigurieren Zertifikatsprofile](Configure-Intune-certificate-profiles.md)beschrieben.
