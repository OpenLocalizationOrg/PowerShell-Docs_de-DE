---
title: Einrichten Ihres Abonnements mit Lookout MTP | Microsoft Intune
description: Dieser Themen finden Informationen zum Konfigurieren von Lookout MTP.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: 8e2c71127801afc21d52e08d13dd9099b263e801
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Richten Sie Ihr Abonnement für Lookout für Mobilgeräte Schutz
Wenn Sie Ihr Abonnement für den Dienst Lookout MTP vorbereiten, benötigen Lookout-Unterstützung (enterprisesupport@lookout.com) die folgende Informationen über Ihre Azure Active Directory (Azure AD). 

* Azure AD-Mandanten-ID
* Azure AD-Gruppe Objekt-ID für den Lookout MTP Console Vollzugriff
* Azure AD-Gruppe Objekt-ID für beschränkten Lookout MTP Console-Zugriff (optional)

Verwenden Sie die Informationen zum Sammeln von Informationen, die Sie auf das Supportteam Lookout gewähren müssen die folgenden Abschnitte enthalten.  

## Abrufen Ihrer Azure AD-Informationen
### Erste Sie Azure AD-Mandanten-ID
Melden Sie sich bei der Azure AD-Verwaltungsportal: https://manage.windowsazure.com, und wählen Sie Ihr Abonnement. 

![Screenshot der Azure AD-Seite mit dem Namen des den Mandanten](../media/mtp/aad_tenant_name.png) Wenn Sie den Namen Ihres Abonnements auswählen, enthält die resultierende URL die Abonnement-ID an.  Wenn Sie Probleme beim Suchen Ihr Abonnement-ID verfügen, enthält das [Microsoft support-Artikel](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) zusätzliche Tipps.   
### Erste Ihre Azure AD-Gruppe-ID
Die Konsole Lookout MTP unterstützt 2 Zugriffsebenen:  
* **Vollzugriff:** Azure AD-Administrator kann eine Gruppe für Benutzer, die Vollzugriff erstellen und optional können sie eine Gruppe für Benutzer, die eingeschränkter Zugriff erstellen.  Nur Benutzer in diesen Gruppen werden bei der **Lookout MTP Konsole**anmelden können.
* **Zugriff eingeschränkt:** Keinen Zugriff auf mehrere Konfiguration und Registrierung Zusammenhang Module der Lookout MTP-Konsole; schreibgeschützten Zugriff auf das Modul **Sicherheitsrichtlinie** der Lookout MTP Konsole.  

Weitere Informationen zu den Berechtigungen finden Sie [in diesem Artikel](https://personal.support.lookout.com/hc/en-us/articles/114094105653) auf der Website Lookout.

Die **Gruppe Objekt-ID** finden Sie auf der Eigenschaftenseite der Gruppe in der Azure AD-Verwaltungskonsole.

![Screenshot der Eigenschaftenseite mit hervorgehobenem Gruppen-ID-Feld](../media/mtp/aad_group_object_id.png)

Nachdem Sie diese Informationen gesammelt haben, wenden Sie sich an den Support Lookout (-e-Mail: enterprisesupport@lookout.com).

Lookout Support wird arbeiten mit den integrierten primäre Kontakt Ihres Abonnements und Ihrem Lookout MTP Enterprise-Konto mithilfe den von Ihnen erfassten Informationen erstellen.


## Konfigurieren Sie Ihr Abonnement mit Lookout MTP
### Schritt 1: Einrichten Sie Ihrer MTP
Nachdem Ihr Konto Lookout MTP Enterprise Lookout Support erstellt hat, können Sie zur Lookout MTP Konsole anmelden.   Eine e-Mail von Lookout wird an der primären Kontakts für Ihr Unternehmen mit einem Link zu der Login-Url: https://aad.lookout.com/les?action=consent gesendet.

Sie müssen ein Benutzerkonto mit der Azure AD-Rolle des globalen Administrators verwenden, wenn Sie zuerst zur Konsole Lookout MTP, melden Sie sich seit dem MTP Lookout diese Option, um Ihre Azure AD-Mandanten registrieren erfordert.   Die Benutzer erhalten dieser Berechtigungsstufe Azure AD-erforderlich nachfolgende Benutzernamen keinen.  In dieser ersten Anmeldung wird eine Seite Zustimmung angezeigt. Wählen Sie zur Durchführung der Registrierung **zu übernehmen** .

![Screenshot der ersten Mal Anmeldeseite der Konsole Lookout MTP](../media/mtp/lookout_mtp_initial_login.png) sobald Sie akzeptiert haben und zugestimmt, werden Sie zu der Lookout MTP Konsole weitergeleitet. Nachfolgende Benutzernamen nach der ersten Registrierung ist möglich, verwenden die URL: https://aad.lookout.com

Wenn Probleme beim Anmelden auftreten, finden Sie unter die [Artikel behandeln](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration) .

Die nächsten Schritte gliedern Sie die Aufgaben, die ausgeführt werden müssen, um die innerhalb der [Lookout MTP Console](https://aad.lookout.com)-einrichten Lookout MTP abzuschließen.

### Schritt 2: Konfigurieren des Intune Verbinders

Klicken Sie in der Verwaltungskonsole Lookout MTP wechseln Sie zu der **System** -Modul, wählen Sie die Registerkarte **Verbinder** , und wählen Sie **Intune**.

![Screenshot der Lookout MTP Console mit der Verbinder Registerkarte öffnen und hervorgehobene Intune-option](../media/mtp/lookout_mtp_setup-intune-connector.png)

Konfigurieren Sie die Option Verbindung Einstellungen der Heartbeat Häufigkeit in Minuten ein.  Mit der Durchführung dieses Schritts ist nun der Verbinder Intune bereit.  

![Screenshot der Registerkarte Verbindung Einstellungen mit mit Heartbeat Häufigkeit konfiguriert](../media/mtp/lookout-mtp-connection-settings.png)

### Schritt 3: Konfigurieren von Gruppen zur Registrierung
Klicken Sie auf die Option zur **Verwaltung der Registrierung** definieren Sie eine Reihe von Benutzern, deren Geräte mit Lookout registriert werden soll.   Bewährte Methode ist, beginnen Sie mit einer kleine Gruppe von Benutzern zu testen, und machen Sie sich mit der Funktionsweise der Integration vertraut.  Nachdem Sie Ihre Testergebnisse befinden, können Sie die Registrierung auf weiteren Gruppen von Benutzern verlängern.

Um mit diesen Gruppen beginnen, müssen Sie zuerst definieren Sie eine Azure AD-Sicherheitsgruppe, die einem guten ersten Satz von Benutzern die Registrierung in Lookout MTP. Nachdem Sie die Gruppe in Azure AD, in der Verwaltungskonsole Lookout MTP erstellt haben wechseln Sie zu der **Enrollement** Verwaltungsoption, und fügen Sie der Sicherheitsgruppe Azure AD- **Anzeigen oder Namen** für die Registrierung.

Wenn ein Benutzer in einer Gruppe Registrierung ist, eine der aktivierten Geräte, die in Azure AD unterstützt und identifiziert registriert ist und ist für die Aktivierung in Lookout MTP berechtigt.  Zum ersten Mal, das Sie Ausschau für Arbeit app unterstützte Geräts öffnen, die es in Lookout MTP aktiviert ist.
![Screenshot der Intune Verbinder Registrierungs-Webseite](../media/mtp/lookout-mtp-enrollment.png)

Bewährte Methode ist das Inkrement zu prüfen, ob die Standardeinstellung 5 Minuten werden neue Geräte zu verlassen.

>[!IMPORTANT]
> Der angezeigte Name wird die Groß-/Kleinschreibung beachtet.  Verwenden Sie den **Anzeigenamen** ein, wie dargestellt die auf der Seite **Eigenschaften** der Sicherheitsgruppe Azure-Portal. Beachten Sie in der Abbildung unten, dass die Seite **Eigenschaften** der Sicherheitsgruppe, der Anzeigename groß-.  Der Titel jedoch in Kleinbuchstaben angezeigt wird und sollte nicht verwendet werden, um in der Konsole Lookout MTP eingeben.
>![Screenshot des Azure-Portal, Azure-Active Directory-Dienst, der Eigenschaftenseite](../media/mtp/aad-group-display-name.png)

Die aktuelle Version weist die folgenden Einschränkungen:  
* Es gibt keine Validierung für die Namen der Gruppe anzeigen aus.  Vergewissern Sie sich mit den Wert in das Feld **ANZEIGENAME** Azure-Portal für die Sicherheitsgruppe Azure Ad-angezeigt.
* Erstellen von Gruppen in Gruppen wird derzeit nicht unterstützt.  Azure AD-Sicherheitsgruppen angegebenen darf nur Benutzer und nicht geschachtelte Gruppen enthalten.


### Schritt 4: Konfigurieren von Bundesstaat synchronisieren
Geben Sie die Option **Zustand synchronisieren** , dass der Typ der Daten an Intune gesendet werden soll.  Aktuell, müssen Sie sowohl Gerät Status- und Bedrohung in Reihenfolge für die Integration Lookout Intune ordnungsgemäß funktioniert aktivieren.  Diese sind standardmäßig aktiviert.
### Schritt 5: Konfigurieren von Bericht e-Mail-Empfänger Fehlerinformationen
Geben Sie die Option zur **Verwaltung der Fehler** die e-Mail-Adresse, die den Fehlerberichte erhalten sollen.

![Screenshot der Intune Verbinder Management Fehlerseite](../media/mtp/lookout-mtp-connector-error-notifications.png)

### Schritt 6: Konfigurieren von e-Mails Benachrichtigungen
Wenn Sie e-Mail-Benachrichtigungen für Risiken erhalten möchten, melden Sie sich an die [Lookout MTP Console](https://aad.lookout.com)mit das Benutzerkonto, das die Benachrichtigungen gesendet werden sollen.  Wechseln Sie in das **System** -Modul, und klicken Sie auf der Registerkarte **Einstellungen** , wählen Sie die gewünschten Benachrichtigungen aus, und legen Sie diese **auf**. Die Änderungen zu speichern.

![Screenshot der Seite Einstellungen für das Benutzerkonto angezeigt](../media/mtp/lookout-mtp-email-notifications.png) , wenn Sie nicht mehr e-Mail-Benachrichtigungen erhalten möchten, legen Sie die Benachrichtigungen auf **aus** , und die Änderungen zu speichern.
### Schritt 7: Konfigurieren von Klassifizierung
Lookout MTP klassifiziert mobile Risiken verschiedener Typen. Die [Lookout MTP etablieren](http://personal.support.lookout.com/hc/en-us/articles/114094130693) haben Standardberechtigungsstufen Risiko zugeordnet. Dies können zu einem beliebigen Zeitpunkt der Suite Ihren Anforderungen Unternehmen geändert werden.

![Screenshot der Richtlinienseite mit Bedrohung und Klassifizierung](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Die Risiko Ebenen angegeben, dass hier ist ein wichtiger Aspekt der MTP, da die Integration Intune Gerät Compliance gemäß folgenden Risiko Ebenen zur Laufzeit berechnet. Kurzum, Intune Administrator legt eine Regel in Richtlinie zu ermitteln, ein Gerät nicht kompatible, wenn sie ein aktives Risiko mit mindestens hat Ebene der: hoch, Mittel oder niedrig. Die Bedrohung Klassifizierung Richtlinie in MTP Laufwerke die Gerät Compliance Berechnung direkt in Intune.

## Registrierung heraus
Nach Abschluss die Installation startet Lookout MTP Azure AD für Geräte abgefragt werden soll, die den angegebenen Registrierungsgruppen entsprechen.  Informationen zu den Geräten registriert finden Sie im Geräte-Modul.  Der anfängliche Status für Geräte werden als ausstehend.  Der Gerätestatus ändert sich nachdem Ausschau für Arbeit app installiert wurde, geöffnet und auf dem Gerät aktiviert ist.  Details zum Abrufen Ausschau für Arbeit app auf dem Gerät abgelegt finden Sie im Thema [Konfigurieren und dafür Arbeit apps bereitstellen](configure-and-deploy-lookout-for-work-apps.md) .
## Nächste Schritte
[Aktivieren von Lookout MTP Verbindung Intune](enable-lookout-mtp-connection-in-intune.md)
