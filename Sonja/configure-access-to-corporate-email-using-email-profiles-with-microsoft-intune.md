---
title: Zugriff auf Firmen-e-Mail mit e-Mail-Profilen | Microsoft Intune
description: "So konfigurieren Sie e-Mail-Einstellungen für den Zugriff für bestimmte e-Mail-Clients auf mobilen Geräten, können für e-Mail-Profil verwendet werden."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
ms.openlocfilehash: 629836ef006e1c33c240f9daa373817a685c14bc
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren des Zugriffs auf Ihres Unternehmens-e-Mail-e-Mail-Profile mit Microsoft Intune verwenden
Viele mobile Plattformen einschließen einen systemeigenen e-Mail-Client, der als Teil des Betriebssystems enthalten ist. Einige der Clients können mithilfe von e-Mail-Profile eingerichtet werden, wie in diesem Artikel beschrieben.

Einrichten von e-Mail-Einstellungen für den Zugriff für bestimmte e-Mail-Clients auf mobilen Geräten, können e-Mail-einräumen verwendet werden. Auf unterstützten Plattformen können die systemeigene e-Mail-Clients von Microsoft Intune eingerichtet werden Sie Benutzern auf ihren persönlichen Geräten, ohne eine zusätzliche einrichten, deren Ihres Unternehmens-e-Mails.

Wenn Sie für den Schutz vor Datenverlust zusätzliche Maßnahmen ergreifen müssen, verwenden Sie [bedingte Access](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), dem Zugriff auf das Postfach des Benutzers für e-Mail-Clients, einschließlich der systemeigenen e-Mail-Clients gesteuert.

IT-Administratoren oder Benutzern möglicherweise auch So installieren Sie alternative e-Mail-Clients (beispielsweise Microsoft Outlook für Android oder iOS) auswählen. Diese e-Mail-Clients möglicherweise keine Unterstützung für e-Mail-Profile und nicht mithilfe von Intune-e-Mail-Profile eingerichtet werden.  

E-Mail-Profile können Sie um den systemeigene e-Mail-Client auf die folgenden Arten von Gerät zu konfigurieren:
-   Windows Phone 8 und höher
-   Windows-10 (für den Desktop), Windows Mobile 10 und höher
-   iOS 8.0 und höher
-   Samsung KNOX Standard (4.0 und höher)

Zusätzlich zur Einrichtung eines e-Mail-Kontos auf dem Gerät, können Sie festlegen von wie viel e-Mail synchronisieren möchten, und klicken Sie je nach Art des Geräts, die Inhalte von Datentypen für die Synchronisierung.
>[!NOTE]
>
>Wenn der Benutzer eine e-Mail-Profil vor dem installiert hat hängt Plattform des Einrichten eines Profils von Intune, das Ergebnis der Bereitstellung Intune e-Mail-Profil:

[Kommentar]: <> passiven Konstruktion in den nächsten drei Absätzen ist erforderlich, bis der Prozess der Erkennung von Duplikaten entfernen, indem PM hergestellt wird.

>**iOS**: eine vorhandene, doppelte e-Mail-Profil basierend auf dem Host Name und e-Mail-Adresse erkannt wird. Das vom Benutzer erstellt doppelte e-Mail-Profil blockiert die Bereitstellung eines Profils Intune Administrator erstellt. Dies ist ein häufig auftretendes Problem als iOS Benutzer in der Regel erstellen Sie ein e-Mail-Profil, und klicken Sie dann registrieren. Das Unternehmen Portal informiert den Benutzer, diese sind nicht kompatibel aufgrund manuell konfigurierten e-Mail-Profil, und der Benutzer aufgefordert, das Profil zu entfernen. Den Benutzer sollten ihre e-Mail-Profil zu entfernen, damit das Profil Intune eingerichtet werden kann. Weisen Sie die Benutzer, die vor der Neuinstallation eines e-Mail-Profils registrieren und Intune einrichten, das Profil zu ermöglichen, um das Problem zu vermeiden.

>**Windows**: ein vorhandenen, doppelte e-Mail-Profils erkannt wird, basierend auf dem Host Name und e-Mail-Adresse. Intune überschreibt das vorhandene e-Mail-Profil, die vom Benutzer erstellt.

>**Samsung KNOX**: eine vorhandene, doppelte e-Mail-Profil basierend auf der e-Mail-Adresse erkannt wird, und mit dem Profil Intune überschrieben. Wenn der Benutzer von diesem Konto festlegt, wird sie erneut vom Intune Profil überschrieben. Beachten Sie, dass dies möglicherweise einige Verwirrung, für dem Benutzer verursachen.

>Da Samsung KNOX nicht Hostname für das Profil ein verwenden, wird empfohlen, dass Sie mehrere e-Mail-Profile auf derselben e-Mail-Adresse auf verschiedenen Hosts verwenden nicht erstellen, wie diese miteinander zu überschreiben.


## Sicheren e-Mail-Profile
Sichern Sie e-Mail-Profile mithilfe einer der beiden folgenden Methoden: durch ein Zertifikat oder ein Kennwort.

### Zertifikate
Wenn Sie das e-Mail-Profil erstellen, wählen Sie ein Zertifikatsprofil, das Sie zuvor in Intune erstellt haben. Dies ist als das Zertifikat zur Identifizierung bezeichnet, und wird verwendet, um die Authentifizierung über ein Profil vertrauenswürdigen Zertifikat (oder ein Zertifikat einer Stammzertifizierungsstelle), um festzulegen, dass das Gerät des Benutzers eine Verbindung herstellen. Auf dem Computer, der die e-Mail-Verbindung, in der Regel, die native Mailserver authentifiziert, ist das vertrauenswürdige Zertifikat bereitgestellt.

Weitere Informationen zum Erstellen und Verwenden von Zertifikatsprofile in Intune finden Sie unter [sicheren Ressourcenzugriff mit Zertifikatsprofile](secure-resource-access-with-certificate-profiles.md).

### Benutzername und Kennwort
Der Benutzer authentifiziert zum systemeigenen Mailserver können, indem Sie ihren Benutzernamen und Ihr Kennwort ein.

Der Benutzer muss dies angeben, wenn sie mit e-Mail herstellen das Kennwort nicht im e-Mail-Profil enthalten ist.

### Erstellen eines e-Mail-Profils

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** &gt; **Richtlinie hinzufügen**.

2.  Richten Sie einen der folgenden Tabstopptypen Richtlinie:

    -   **E-Mail-Profil für Samsung KNOX Standard (4.0 und höher)**

    -   **E-Mail-Profil (iOS 8.0 und höher)**

    -   **E-Mail-Profil (Windows Phone 8 und höher)**

    -   **E-Mail-Profil (Windows-10-Desktop und Mobile und höher)**

    Sie können nur erstellen und Bereitstellen eine benutzerdefinierten e-Mail-Profil Richtlinie. Empfohlene Einstellungen sind nicht verfügbar.

3.  Anhand der folgenden Tabelle Sie e-Mail-einräumen einrichten:

|Name der Einstellung | Weitere Informationen|
| ----------- | --------------- |
    |**Namen**|Eindeutigen Namen für das e-Mail-Profil.|
    |**Beschreibung**|Eine Beschreibung, die Ihnen dabei hilft, Identifizieren dieses Profil.|
    |**Host**|Der Hostname Ihres Unternehmens-Servers ein, der den systemeigenen e-Mail-Dienst hostet.|
    |**Kontoname**|Der Anzeigenamen für die e-Mail-Konto wie er wird für Benutzer auf ihren Geräten angezeigt.|
    |**Benutzername**|Wie der Benutzername für das e-Mail-Konto abgerufen werden. Wählen Sie für einen lokalen Exchange-Server **Benutzernamen** aus, oder wählen Sie **Benutzerprinzipalnamen** für Office 365.|
    |**E-Mail-Adresse**|Wie die e-Mail-Adresse für den Benutzer auf jedem Gerät generiert wird. Wählen Sie **Primäre SMTP-Adresse** an, mit der primären SMTP-Adresse melden Sie sich bei Exchange oder **Benutzerprinzipalnamen** verwenden, um die vollständige Benutzerprinzipalnamen als die e-Mail-Adresse zu verwenden.|
    |**Authentifizierungsmethode** (Samsung KNOX und iOS)|Wählen Sie **Benutzername und Kennwort** oder **Zertifikate** als Authentifizierungsmethode vom e-Mail-Profil ein.|
    |**Wählen Sie ein Clientzertifikat für Client-Authentifizierung (Identität Zertifikat)** (Samsung KNOX und iOS)|Wählen Sie das Client SCEP Zertifikat, das Sie zuvor erstellt haben, das zur Authentifizierung der Exchange-Verbindung verwendet wird. Weitere Informationen zur Verwendung von Zertifikatsprofilen in Intune finden Sie unter [sicheren Ressourcenzugriff mit Zertifikatsprofile](secure-resource-access-with-certificate-profiles.md). Diese Option wird nur angezeigt, wenn die Authentifizierungsmethode **Zertifikate**ist.|
    |**Verwenden Sie S/MIME** (Samsung KNOX und iOS)|Ausgehende e-Mail mit S/MIME-Verschlüsselung zu senden.|
    |**Signaturzertifikat** (Samsung KNOX und iOS)|Auswählen des Signaturzertifikats, das zum Signieren von ausgehenden e-Mails verwendet wird. Diese Option ist nur angezeigt, wenn Sie **Verwenden S/MIME**auswählen.|
    |**Anzahl der Tage der e-Mails an synchronisieren**|Die Anzahl der Tage der e-Mail, die Sie synchronisieren, oder wählen Sie **unbeschränkt** alle verfügbaren Nachrichten synchronisieren möchten.|
    |**Synchronisierungszeitplan** (Samsung KNOX, Windows Phone 8 und höher, Windows 10)|Wählen Sie den Zeitplan, die keinesfalls Geräte Daten aus dem Exchange-Server synchronisiert werden. Sie können auch **als Nachrichten eintreffen**, der Daten synchronisiert, sobald sie eintreffen, oder **manuellen**, Stelle, an der der Benutzer des Geräts starten muss der Synchronisierung auswählen.|
    |**Verwenden von SSL**|Verwenden Sie beim Senden von e-Mails, Empfang von e-Mails und zum Kommunizieren mit dem Exchange-Server Kommunikation Secure Sockets Layer (SSL). Geräte ausführen, die Samsung KNOX 4.0 oder höher müssen Sie exportieren Ihrer Exchange Server SSL-Zertifikat, und stellen Sie es als Android vertrauenswürdige Zertifikatsprofil in Intune. Intune unterstützt Zugriff auf dieses Zertifikat installiert ist, auf dem Exchange-Server anderweitig wird nicht.|
    |**Inhaltstyp für die Synchronisierung**|Wählen Sie die Inhaltstypen, die Sie Geräte synchronisieren möchten.|
    |**Zulassen von e-Mails von Drittanbieter-Anwendungen gesendet werden** (nur für iOS)|Lässt des Benutzers wählen Sie dieses Profil als Standardkonto zum Senden von e-Mail, und Drittanbieter-Anwendungen-e-Mail in der systemeigenen-e-Mail-app, beispielsweise öffnen, um Dateien an e-Mail anzufügen.|
    > [!IMPORTANT]
    > If you have deployed an email profile and then wish to change the values for **host** or **Email address**, you must delete the existing email profile and create a new one with the required values.

4.  Wenn Sie fertig sind, klicken Sie auf **Richtlinie speichern**.

Die neue Richtlinie zeigt in den Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** .

## Die Richtlinie bereitstellen

1.  Wählen Sie die Richtlinie, die Sie bereitstellen möchten, und wählen Sie dann die **Bereitstellung verwalten**, klicken Sie im Arbeitsbereich **Richtlinie** .

2.  Klicken Sie im Dialogfeld **Bereitstellung verwalten** :

    -   **Die Richtlinie bereitstellen** - wählen Sie eine oder mehrere Gruppen, dem Sie die Richtlinie bereitstellen möchten, und wählen Sie dann auf **Hinzufügen** &gt; **OK**.

    -   **Zum Schließen des Dialogfelds ohne es** - wählen Sie **Abbrechen**aus.

Eine Zusammenfassung Status und Benachrichtigungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie** identifizieren Sie Probleme mit der Richtlinie, die Ihre Aufmerksamkeit erfordern. Darüber hinaus wird ein Zusammenfassung Status im Dashboard-Arbeitsbereich ein.

> [!NOTE]
> Wenn Sie ein e-Mail-Profil auf einem Gerät entfernen möchten, bearbeiten Sie die Bereitstellung und entfernen Sie alle Gruppen, mit denen das Gerät ein Mitglied ist.
