---
title: Was neue Archiv ist | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
ms.openlocfilehash: 3e5ca7345aef574446d437bac25bffc0c3414c68
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
## Dezember 2015
### Änderungen und Updates an Microsoft Unternehmen Portal
Im Portal Unternehmen in dieser Version wurden die folgenden Änderungen vorgenommen.

**Portal Unternehmen Android-app**

Die Einhaltung der neuer Google-Anforderungen wurden folgenden Änderungen vorgenommen. Android 6.0 und über Geräte werden zwei neue Nachrichten an Benutzer angezeigt:
* Zulassen von Unternehmen Portal und Telefonanrufe verwalten?
* Aktivieren Sie die Option Unternehmen Portal Access Fotos, Medien und Dateien auf Ihrem Gerät?

Ausführliche Informationen über die beiden Nachrichten in den folgenden Tabellen finden Sie unter.



Nachrichtentext  |Zulassen von Unternehmen Portal und Telefonanrufe verwalten?  
---------|---------
Bedeutung der Nachricht     |  Ermöglicht des Benutzers Gerät Telefonnummer und IMEI an den Intune-Dienst gesendet werden und in der Administrator-Konsole auf der Seite Hardware angezeigt.   </br></br>**Hinweis: Die app Unternehmen Portal nie macht oder Telefonanrufe verwaltet!** Im Nachrichtentext wird gesteuert, indem Google und kann nicht geändert werden. </br></br>Wechseln Sie zum Anzeigen der **Hardware** -Seite zu **Gruppen** > **auf allen mobilen Geräten** > **Gerät**e. Wählen Sie das Gerät des Benutzers aus, und wechseln Sie zum **Anzeigen der Eigenschaften** > **Hardware**.    
Wann und wo Meldung angezeigt wird  | Die Meldung angezeigt wird, wenn der Benutzer zum ersten Mal starten registrieren Geräts mit der Firma Portal anmelden.|         
Was passiert, wenn Benutzer zugreifen dürfen  |  Telefonnummer und IMEI des Geräts wird auf der Seite Hardware in der Verwaltungskonsole angezeigt. |         
Was passiert, wenn Sie Benutzern den Zugriff verweigern     | Benutzer können weiterhin verwenden Sie die app Unternehmen Portal und Geräts zu registrieren, aber die Benutzer die Telefonnummer des Geräts und IMEI werden auf der Seite Hardware in der Administrator-Konsole leer.       </br></br> Der zweiten Zeitangabe, die Benutzer mit der Firma Portal melden Sie sich nach den Zugriff verweigern zeigt die Meldung das Kontrollkästchen **nie bestätigen erneut** angezeigt, die Benutzer auswählen können, damit die Nachricht nie wieder angezeigt.</br></br>Wenn Benutzer zulassen, aber später Zugriff verweigern, wird die Meldung mit dem Benutzer das nächste Mal nach der Registrierung bei der app Unternehmen Portal anmelden.</br></br>Wenn Benutzer später wieder zugreifen dürfen, wechseln sie zu **Einstellungen** > **Apps** > **Unternehmen Portal** > **Berechtigungen** > **Mobiltelefone**und deaktivieren Sie dann auf die Berechtigung.
Weitere Informationen     |  Für Ihre Benutzer: [Melden Sie sich mit dem Portal für Unternehmen](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>Für IT-Experten: Die Informationen in dieser Tabelle ist ebenfalls Hilfe für [Ihre Benutzer Unternehmen Portal app-Nachrichten zu verstehen.](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   

Nachrichtentext  |Aktivieren Sie die Option Unternehmen Portal Access Fotos, Medien und Dateien auf Ihrem Gerät?  
---------|---------
Bedeutung der Nachricht     |  Aktiviert das Gerät Daten Protokolle des Geräts SD Karte sowie das Schreiben in die Protokolle verschoben werden soll, indem Sie mit einem USB-Kabel ermöglicht.   </br></br>**Hinweis: Die app Unternehmen Portal greift nie auf, Fotos, Medien und Dateien Benutzer!** Im Nachrichtentext wird gesteuert von Google und kann nicht geändert werden.     
Wann und wo Meldung angezeigt wird  | Die Meldung angezeigt wird, wenn Benutzer Tippen Sie auf **Daten senden** , Daten Protokolle an ihre IT-Administrator senden|         
Was passiert, wenn Benutzer zugreifen dürfen  |  Die Protokolle werden auf der Karte SD kopiert. |         
Was passiert, wenn Sie Benutzern den Zugriff verweigern     | Sie können weiterhin Daten Protokolle senden, aber die Protokolle wird nicht auf SD-Karte des Geräts kopiert werden.       </br></br> Der zweiten Zeitangabe, die Benutzer mit der Firma Portal melden Sie sich nach den Zugriff verweigern zeigt die Meldung ein Kontrollkästchen **nie wieder bitten** , die Benutzer auswählen können, damit die Nachricht nie wieder angezeigt.</br></br>Wenn Benutzer zulassen, aber später Zugriff verweigern, wird die Meldung, dass Benutzer das nächste Mal versuchen, Protokolle zu senden.</br></br>Wenn Benutzer später wieder zugreifen dürfen, wechseln sie zu **Einstellungen** > **Apps** > **Unternehmen Portal** > **Berechtigungen** > **Speicher**und die Berechtigung dann aktivieren.
Weitere Informationen     |  Für Ihre Benutzer: [diagnostic Daten Sie Fehlerprotokolle an Ihr IT-Administrator per e-Mail senden](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>Für IT-Experten: Die Informationen in dieser Tabelle ist ebenfalls Hilfe für [Ihre Benutzer Unternehmen Portal app-Nachrichten zu verstehen.](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   


**Unternehmen Portal-app für iOS**
* Benutzer können jetzt Microsoft Outlook oder anderen e-Mail-apps zum Senden von Diagnoseprotokollen an den IT-Administrator verwenden. In früheren Versionen konnte nur die native app verwendet werden.
* Unterstützung wurde für Apple Gerät Registrierungs-Programm (DEP) und corporate registriert Geräte verbessert. Details finden Sie unter, [werden Sie aufgefordert, Identifizieren von Ihrem Gerät, wenn Sie versuchen, sich zu registrieren](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* In der Liste der registrierten Geräte des Benutzers wird ein grünes Häkchen neben dem Gerät, das der Benutzer aktuell verwendet wird nun angezeigt. Damit diese Häkchen hinzugefügt wurde, konnten nicht Benutzer auffordern, welches Gerät registrierten von verwendeten wurden.

**Portal Unternehmen Windows-app**

Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung des Portals zur Verbesserung von Microsoft-Produkte und-Services für Unternehmen. Endbenutzer können Sammlung von Daten mithilfe der Einstellung Verwendungsdaten Geräts deaktivieren, aber Administratoren haben keine Kontrolle über die Sammlung von Daten und der Endbenutzer Auswahl für diese Einstellung nicht ändern.



## November 2015
### App-Verwaltung
Intune unterstützt mobile-Anwendung (MAM) Informationsverwaltungsrichtlinien, die verhindern Unternehmensdaten wegen Consumer apps oder Dienste. In der Vergangenheit möchten diese Richtlinien nur auf mobilen Geräten, die auch registriert wurden für die Verwaltung mobiler Geräte (MDM) in Intune ausgeführt apps erzwungen werden.

Mit den Monat aktualisieren ist Intune seine MAM Funktionen in neuen Klassen Geräte erweitern. Zusätzlich zu Geräten in Intune registriert können Sie jetzt MAM Richtlinien auf erzwingen:
* Geräte von einem beliebigen Gerät Management (MDM) Lösung verwaltet werden
* Gerät, das nicht in einem beliebigen Gerät Management-System (BYO) Geräte in der Regel schalten eigener registriert sind

Weitere Informationen zu diesen neuen MAM Funktionen finden Sie in den folgenden Blogbeiträgen:
* [Verbessern der verwalteten mobile Produktivität](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Ankündigung neuer Funktionen von Microsoft Enterprise-Mobilität](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Darüber hinaus sind hier einige wichtige Elemente und Weitere Informationen zu Intunes MAM Features:
* Unternehmensdaten werden von apps für Intune einschließlich Office Mobile-apps, apps von Drittanbietern, die das SDK Intune eingeführt haben oder Branchen apps von Intune umschlossen Augenblick Consumer Daten isoliert.
* Unternehmensdaten können freigegebenen (**Ausschneiden, kopieren und Einfügen**) über Unternehmen apps, sein, und die gemeinsame Nutzung von Unternehmensdaten in persönlichen apps zu verhindern. Lesen Sie weitere Details [wie MAM Richtlinien schützen app-Daten](https://technet.microsoft.com/library/mt627825.aspx) . Dieses Beispielszenario [verwenden Microsoft Word-app für Arbeit und persönliche Aufgaben](https://technet.microsoft.com/library/mt627827.aspx)zeigt an, wie die Freigabe von Unternehmensdaten in persönlichen apps verhindert wird.
* Wichtige Datenverlust Prevention Richtlinien wie pro-App-PIN, eine Speichern-als-Steuerelemente und verwalteten Daten zwischen apps freigeben. Lesen [Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx) um eine Liste aller Richtlinien anzuzeigen.
* Word, Excel, PowerPoint, Outlook, OneNote und OneDrive for Business alle diese neuen Funktionen haben und mit und ohne Gerät Registrierung verwaltet werden können. Verlust die Datenschutzfunktionen systembedingt integriert den standardmäßigen Office-apps im Apple Store oder die Google Play Store, und app Umbruch oder Sideloading nicht erforderlich.
* Weitere Informationen zur Seite Erste Schritte finden Sie unter [Erste Schritte mit mobilen app Informationsverwaltungsrichtlinien Azure-Portal](https://technet.microsoft.com/library/mt627830.aspx). Informationen zum Konfigurieren und Bereitstellen von Informationsverwaltungsrichtlinien für mobile-app finden Sie unter [Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Wenn die app mit ihren Anmeldeinformationen corporate Endbenutzer authentifizieren, werden automatisch die Datenschutzfunktionen Verlust ausgerichtet. Das Thema [Endbenutzer erleben Sie apps Microsoft Intune mobile-app Informationsverwaltungsrichtlinien zugeordnet](https://technet.microsoft.com/library/mt627827.aspx) enthält einige Beispielszenarien für den Zugriff auf OneDrive für iOS und Android-Geräten.
* Works auf iOS und Android-Geräten.

Zum Anzeigen der neuesten apps wurde die Liste der [Microsoft-apps mit Microsoft Intune mobilen Anwendung Informationsverwaltungsrichtlinien verwendbare](https://technet.microsoft.com/library/dn708489.aspx) aktualisiert.

### Gerät-Verwaltung
 **Verwaltung von Mac OS X-Geräte** Mit Intune können Sie jetzt registrieren und Verwalten von Mac OS X Geräte. Sie können mit Ihrem Mac OS X-Geräten Folgendes ausführen:
* Registrieren Sie Geräte von Intune verwaltet werden. [Einrichten von iOS und Mac-Verwaltung mit Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx)finden Sie unter.
* Steuern des Audiogeräts mit einer Richtlinie allgemeine Konfiguration an. Finden Sie unter [Mac OS X-Konfiguration Richtlinieneinstellungen Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Bereitstellen von Mac OS X-Einstellungen, die Sie mit der Apple-Konfiguration erstellt haben. Finden Sie unter [Mac OS X benutzerdefinierte Richtlinieneinstellungen in Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Sammeln Sie Hard- und Software Inventory von Mac OS X-Geräten aus. [Verstehen der Geräte mit Beständen in Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx)finden Sie unter.
* Führen Sie die neuen Berichte, die Details zu den Mac OS X-Geräten angezeigt, die Sie verwalten. [Grundlegendes zu Microsoft Intune Vorgänge mithilfe von Berichten](https://technet.microsoft.com/library/dn646977.aspx)finden Sie.

**Neue Kante Browsereinstellungen für Windows 10 Geräte** Neue Einstellungen wurden die Windows-10-Konfiguration von allgemeinen Richtlinie hinzugefügt, mit die Sie die Einstellungen und Features des Browsers Microsoft Edge verwalten können. [Windows-10-Konfiguration Richtlinieneinstellungen Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)finden Sie unter.

**E-Mail-Profile** Eine neue e-Mail-Profile Richtlinie wurde für Windows 10 Desktop- und mobile Geräte Windows 10 hinzugefügt. Finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](https://technet.microsoft.com/library/dn646984.aspx).

**Neue Compliance-Richtlinieneinstellungen** Die folgenden neuen Sicherheit und Richtlinie Systemeinstellungen wurden in die Liste der Compliance-Richtlinien hinzugefügt:
* Um sicherzustellen, dass Windows 8.1 oder höher, die Zugriff auf Ihr Unternehmensressourcen die neuesten Updates installiert haben, verwenden Sie die Einstellung für **Automatische Updates erforderlich** . Sie können auch angeben, die Art des Updates automatisch installiert werden – entweder alle Updates installiert werden, wie wichtig, oder alle Updates markiert wichtige oder empfohlene. Die vollständige Liste der Compliance-Richtlinieneinstellungen finden Sie unter [Verwalten Gerät Compliance-Richtlinien für Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx).
* Die neue **Anfordern eines Kennworts, wenn Sie das Gerät aus den Leerlauf gibt** Einstellung in Kombination mit der Einstellung für vorhandene **Minuten nach der letzten vor dem Kennwort erforderlich ist** können Sie zum Erstellen einer Compliance-Einstellung, die die Endbenutzer zur Eingabe eines Kennworts, um ein Gerät verwenden, die für eine bestimmte Uhrzeit nicht aktiv war erfordert.

**Neue bedingte Richtlinie Zugriffsoptionen** Sie können bedingte Access Richtlinien für **alle Benutzer** in beiden neuen oder vorhandenen bedingte Richtlinien anwenden. Alle Benutzer, die für die Intune und Office 365 lizenziert ist erforderlich sein, um aktivierten Geräte registrieren, und wenn Plattform des von Intune nicht unterstützt wird, ist der Zugriff für Clientanwendungen mithilfe von [Active Directory-Authentifizierung (moderne Authentifizierung) anmelden basierend](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/)blockiert.

Sie können auch angeben, dass die bedingte Zugriffsrichtlinie auf **allen Plattformen**angewendet wird.  Jeder Clientanwendung mithilfe der [Active Directory-Authentifizierung (moderne Authentifizierung) anmelden Basis](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) unterliegt der bedingten Zugriffsrichtlinie, und wenn die Plattform von Intune nicht unterstützt wird, es blockiert werden.

### Änderungen und Updates an Microsoft Unternehmen Portal
Das Unternehmen Portal apps in dieser Version wurden die folgenden Änderungen vorgenommen:

* **Android**: eine Willkommenseite hinzugefügt wurde, dass die app Android Unternehmen Portal Hilfe Benutzer verstehen des Zwecks der app-Portal Unternehmen. Dieser Bildschirm soll verringern Downloads der app durch Benutzer, dessen Unternehmen nicht Intune Abonnenten sind.

* **iOS**: Intune unterstützt jetzt die Registrierung von Mac OS X Geräte mithilfe der [Firma Portal-Website](https://portal.manage.microsoft.com). Anweisungen finden Sie unter [Registrieren Intune Ihrem Mac OS X-Gerät](https://technet.microsoft.com/library/mt598622.aspx).

* **Unternehmen Portal Website**: Benutzer, die ihr Gerät in Intune registriert haben können ihren Kenncode über die Option **Kenncode zurücksetzen** klicken Sie auf der Website des Unternehmens Portal jetzt zurücksetzen. In früheren Versionen konnte IT-Administratoren Benutzer die Kennungen zurücksetzen. Die Option zurücksetzen Kenncode auf Windows 8.1 und Windows RT-Geräten nicht unterstützt wird, und die Option wird nur, wenn Geräte in mobilen Gerätemanagement (MDM) registriert sind oder MDM mit Exchange ActiveSync. Anweisungen für Benutzer finden Sie unter [der Kenncode zurücksetzen](https://technet.microsoft.com/library/mt590895.aspx).

### Ändert sich in die globale Administratoren Lizenzierung
Im Oktober freigegebene globale Administratoren (auch als Mandanten Administratoren bezeichnet) weiterhin konnte täglichen Verwaltungsaufgaben ohne separate Lizenz Intune oder Enterprise Mobilität Suite (EMS) zu führen. Jedoch wenn globale Administratoren Dienst, beispielsweise als zu verwenden, um eigene Gerät, eine corporate Gerät oder über das Intune Unternehmen Portal registrieren möchten, erforderlich wie ein anderer Benutzer eine Intune oder EMS-Lizenz. Nachstehend sind ein paar zusätzliche Details aus.
* Im Portal Intune Unternehmen ist, in dem Endbenutzer können:
    * Registrieren des Geräts
    * Hier wird der Status des Geräts
    * Herunterladen der Software, die globaler Administrator in der Organisation bereitgestellt hat
    * Suchen nach Links von der globalen Administrator für so wenden Sie sich an ihre IT-Abteilung veröffentlicht

    [Erfahren Sie mehr über das Unternehmen Portal](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) und Informationen zu [Methoden zum Anpassen des Portals Unternehmen](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* Die Person, die im Namen einer Organisation Intune oder EMS automatisch erwerben anmeldet, wird die erste globaler Administrator in ihrer Mandanten. Diese Herbst, Schritte Intune zu automatisch eine Lizenz Intune oder EMS zu dieser sehr ersten globalen Administrator als Teil der verschieben, um die [Office-365-Portal](http://portal.office.com/) und Rente des [Intune Kontoportal](http://account.manage.microsoft.com/)zuordnen. Alle zusätzlichen globale Administratoren hinzugefügt können weiterhin tägliche Verwaltung ohne separate Lizenz Intune oder EMS führen. Als Endbenutzer fungiert zurück, und ihre eigenen (oder corporate) Gerät oder vom Unternehmen-Portal herunterladen Software benötigt eine Lizenz, wie ein anderer Benutzer dann auslösen möchten.
* Die Änderung erfolgen in werden Phasen und wird jetzt im Januar 2016 gestartet.
* Für Microsoft Partners sollte diese Änderung nicht den Dienst für Kunden verwalten beeinträchtigen. Endbenutzer Vorgänge müssen ein Benutzer über eine Lizenz Intune oder EMS, um ein Gerät und Access registrieren oder Herunterladen von Software vom Unternehmen Portal verfügen.

Wenn Sie sich bei Fragen zum diese Änderung haben, sollten Sie gerne wenden Sie sich an Ihr Supportteam Intune:
* [Microsoft Intune-Support-Kanäle](https://technet.microsoft.com/library/jj839713.aspx)
* [Community-support](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Allgemeine Microsoft Intune Feedback, einschließlich Archivierung Entwurf ändern Anfragen (DCRs) oder Fehlern finden Sie auf [Intune Benutzer Voicemail](https://microsoftintune.uservoice.com/).


### Neuigkeiten in Intune Dokumentation--November 2015
**Neuen Inhalt**
* [Mac OS X-Konfiguration Richtlinieneinstellungen Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): Steuern des Audiogeräts und Features für Mac OS X-Geräte.
* [Mac OS X benutzerdefinierte Richtlinieneinstellungen in Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): wie Mac OS X des Audiogeräts bereitgestellt, die Sie mithilfe des Tools für Apple-Konfiguration erstellt.
* [Konfigurieren Data Loss Prevention app-Richtlinien mit Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): enthält Informationen zu den Szenarien, die mobile-app Management Richtlinien Support und wie funktioniert die Richtlinie, um Daten zu schützen.
* [Erste Schritte mit mobilen app Informationsverwaltungsrichtlinien Azure-Portal](https://technet.microsoft.com/library/mt627830.aspx): Sie müssen Einleitung zur Arbeit mit Azure Preview-Portal für mobile-app Informationsverwaltungsrichtlinien.
* [Erstellen und Bereitstellen von Informationsverwaltungsrichtlinien für mobile-app mit Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): enthält eine schrittweise Anleitung zum mobile-app im Portal Azure Preview Informationsverwaltungsrichtlinien erstellen.
* [Monitor mobile-app Informationsverwaltungsrichtlinien mit Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): Informationen wie Sie Ihre mobile-app Informationsverwaltungsrichtlinien, die über das Azure Preview-Portal überwachen können.
* [Microsoft Intune mobile-app Informationsverwaltungsrichtlinien und iOS öffnen In](https://technet.microsoft.com/library/mt627821.aspx): Informationen wie mobile app Management Richtlinien arbeiten mit iOS-Feature öffnen In.
* [Erleben Sie Endbenutzer apps Microsoft Intune mobile-app Informationsverwaltungsrichtlinien zugeordnet](https://technet.microsoft.com/library/mt627827.aspx): was durch der Endbenutzer ist bei Verwendung von apps mobile-app zur Dokumentverwaltungsrichtlinie zugeordnet.
* [Zurücksetzen verwaltete app-Daten mit Microsoft Intune Unternehmen](https://technet.microsoft.com/library/mt627826.aspx): wie Sie Unternehmen app-Daten entfernen können.

**Aktualisierte Inhalte**
* [Windows-10-Konfiguration Richtlinieneinstellungen Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): neue Kante Browsereinstellungen hinzugefügt.
* [Richten Sie iOS und Mac-Verwaltung mit Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): Informationen zur Verwendung von Mac OS X Geräte registrieren hinzugefügt.
* [Grundlegendes zu Ihren Geräten mit Beständen in Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): hinzugefügten Informationen zu den Bestand von Mac OS X-Geräten erfasst. Auch, aktualisiert das Thema mit den neuesten Informationen für alle Plattformen.
* [Grundlegendes zu Microsoft Intune Vorgänge mithilfe von Berichten](https://technet.microsoft.com/library/dn646977.aspx): Informationen zu den zwei neuen Berichten verwendet, um die Anzeige von Informationen zu Ihren verwalteten Mac OS X-Geräten hinzugefügt.
* [Verwalten Gerät Compliance-Richtlinien für Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): Informationen zu den neuen Compliance-Richtlinien für automatische Updates und kennwortanforderung erfordern, wenn Sie ein Gerät aus Leerlauf gibt hinzugefügt.
* [Verwalten von e-Mail-Zugriff mit Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): Informationen über die Möglichkeit zum Anwenden der bedingten Zugriffsrichtlinie für alle Plattformen und alle Benutzer hinzugefügt.
* [Verwalten von SharePoint Online-Zugriff mit Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): Informationen über die Möglichkeit zum Anwenden von bedingten Zugriffsrichtlinie für alle Plattformen und alle Benutzer hinzugefügt.

## Oktober 2015

### Updates für bedingten Zugriff für Exchange lokal
**Sie können jetzt den Zugriff auf Exchange ActiveSync-e-Mail kompatible Geräte registriert in Intune, wenn die globale Exchange-Regel auf Blockieren oder Quarantäne festgelegt wurde** Bis jetzt hat um e-Mail-Zugriff auf registrierten und kompatiblen Geräten ermöglichen Sie die standardmäßigen globale Exchange-Regel auf **Zulassen**festgelegt.

Mit diesem Dienstupdate ist diese Einstellung nicht mehr eine Vorbedingung für bedingten Zugriff. Wenn Ihre Exchange-Umgebung erfordert, dass die standardmäßige globale Regel zum **Blockieren/Quarantäne**, festgelegt werden einfach das **Standardmäßige Regel außer Kraft setzen** im Exchange Kontrollkästchen lokalen bedingte Richtlinie Datenzugriffsseite. Das Thema [Verwalten von e-Mail-Zugriff mit Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) verfügt über weitere Details auf die Regeln und die resultierende Endbenutzer Benachrichtigungen.

**Neue Quarantäne ein-Klick-Benutzeroberfläche** Wir haben die e-Mail-Oberfläche Quarantäne, um ein-Klick-Registrierung zulassen vereinfacht. Mit diesem Dienstupdate können Endbenutzer ein einzelnes Links in der Quarantäne e-Mail, um die Registrierung abzuschließen, innerhalb der Firma Portal app klicken.
### Mobile Geräte und app Management updates
**Android** Alle Intune Verwaltungsfunktionen unterstützt jetzt Android 6.0 (Kaugummi) in diesem Blogbeitrag beschriebenen: [Microsoft Intune bietet Tag 0 Unterstützung für Android Kaugummi](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)

**iOS** Sie können nicht mehr neue app-Bereitstellungen zu iOS-Geräte mit einer Version vor iOS 7.1 erstellen. Alle vorhandenen app-Bereitstellungen zu einer früheren Version als iOS 7.1 Geräte weiterhin arbeiten und vom Intune verwaltet werden.

**Windows-10** Intune unterstützt jetzt Bereitstellen von Windows 10 universeller apps, die mit den **Windows-app-Pakets** Software Installer-Typ aus. Details und Anforderungen finden Sie unter [Erste Schritte mit app-Bereitstellung in Microsoft Intune](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Änderungen und Updates an Microsoft Unternehmen Portal apps
Auf der Portalseite Unternehmen-apps in dieser Version die folgenden Änderungen vorgenommen wurden: **iOS** neue Schaltflächen für Benutzer zum Senden von Diagnoseprotokollen für ihre IT-Administratoren erleichtern die Unternehmen Portal app hinzugefügt wurden:

|Name der Schaltfläche|In dem es angezeigt wird.|
|------------|---------------|
|Bericht|Benachrichtigen Fehlermeldungen|
|Diagnosebericht senden|Der app-Portal Unternehmen Bildschirm ' Info '|



## September 2015
### Mobile Geräte und app Management updates
**Alle Intune iOS Features für die Verwaltung jetzt unterstützen iOS 9** Details zu iOS 9 Verwaltungsfunktionen finden Sie [diesen Blogbeitrag](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx).

**Neue Richtlinie zur Konfiguration von mobile-app für iOS** Verwenden Sie die Richtlinie für neue mobile-app-Konfiguration, um die automatisch Einstellungen angeben, die eine app für iOS muss, wenn er ausgeführt wird. Beispielsweise könnten Sie einen Netzwerk-Port oder einen Benutzernamen angeben. Details finden Sie unter [Konfigurieren von apps mit mobile-app-Konfiguration in Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx).

**Einfachere Verwaltung der app für iOS 9 Benutzer** 
 In dieser Version können Sie übertragen bereits bereitgestellt apps unter Intune Verwaltung für iOS 9 Benutzer. Für frühere Versionen von iOS auch noch eine nicht verwaltete Version der app bereits auf einem Gerät installiert ist, wenn Sie eine app bereitstellen bitten Sie den Benutzer, die app manuell zu deinstallieren, bevor Intune die verwaltete app installieren kann.

 Aber beginnend mit dieser Version von Intune, Sie können jetzt Benutzer auffordern, 9-iOS-Geräte Intune Verwaltung der app übernehmen und Anwenden einer beliebigen relevanten mobilen Anwendung Informationsverwaltungsrichtlinien zulassen.

 **Verwaltung von Windows-10** Verwenden Sie die neue [Windows-10-Konfiguration von allgemeinen Richtlinie](https://technet.microsoft.com/library/mt404697.aspx) so konfigurieren Sie Ihr Kennwort ein, Gerät, Browser und andere Einstellungen für registrierten Geräte, die Windows-10 und 10 unter Windows Mobile ausgeführt werden.

 **Erstellen und Bereitstellen von apps für registrierten Windows 10 Geräte** Geben Sie ein neues Softwareinstallationsprogramm, Windows Installer bis MDM (& #42;. MSI) können Sie das Erstellen und Bereitstellen von Windows Installer-apps für registrierten Geräte, die Windows-10 ausgeführt werden. Weitere Informationen finden Sie unter [Erste Schritte mit app-Bereitstellung in Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

### Änderungen und Updates an Microsoft Unternehmen Portal apps
Das Unternehmen Portal apps in dieser Version wurden die folgenden Änderungen vorgenommen:

**iOS**
* Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung des Portals zur Verbesserung von Microsoft-Produkte und-Services für Unternehmen. Endbenutzer können Sammlung von Daten mithilfe der Einstellung Verwendungsdaten Geräts deaktivieren, aber Administratoren haben keine Kontrolle über die Sammlung von Daten und der Endbenutzer Auswahl für diese Einstellung nicht ändern.
* Vollständige Bildschirm mit einer Auflösung von Support auf iPhones 6 und 6 Plus
* Fehler korrigiert zur Verbesserung der Sicherheit

### Was ist neu in Intune Dokumentation--September 2015
**Neue Themen**

|Namen|Details|
|----|--------|
|[Windows-10-Konfiguration Richtlinieneinstellungen Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)|Dies ist eine neue Konfigurationsrichtlinie, mit der Sie das Verwalten von Einstellungen und Features auf Geräten, die Windows-10 und 10 unter Windows Mobile ausgeführt werden.
| [Konfigurieren von apps mit mobilen app Konfigurationsrichtlinien in Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)|Dies ist eine neue Richtlinientyp, mit dem Sie automatisch Einstellungen angeben, die erforderlich sein können, wenn der Benutzer eine app für iOS ausgeführt wird. |

**Aktualisierte Themen**

|Namen|Details|
|----|-------|
|[Verwenden von Richtlinien zum Verwalten von Computern und mobilen Geräten mit Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)|Aktualisiert, um die neuesten Informationen dazu zu verstehen und Erstellen von Richtlinien enthalten.|

## August 2015
### Mobile Geräte und app Management updates
* **Geschäftsbedingungen** für Intune Registrierung und Unternehmen Access sind [jetzt verwaltete Richtlinien verwenden](https://technet.microsoft.com/library/mt405893.aspx). Sie können verschiedene Sätze von allgemeinen Geschäftsbedingungen zu bestimmten Benutzer Gruppe erfüllen Zielgruppen ausrichten. Beispielsweise können Sie die allgemeinen Geschäftsbedingungen in verschiedenen Sprachen geografischen definierten Benutzergruppen bereitstellen. Sie können auch [Bearbeiten der allgemeinen Geschäftsbedingungen](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) und angeben, ob die Versionsnummern, die Benutzer auffordern, bevor diese im Portal Unternehmen verwenden, können die neuen allgemeinen Geschäftsbedingungen stimmen zu erhöhen.
* **Wurden eine Anzahl von Intune-Richtlinien umbenannt** , sodass sie mehr über das Produkt konsistente und für Sie einfacher zu finden sind. Eine Liste aller verfügbaren Intune-Richtlinien werden finden Sie unter [Richtlinien zum Verwalten von Computern und mobile Geräte mit Microsoft Intune Verwendung](https://technet.microsoft.com/library/dn743712.aspx).
* **PKCS #12 (. PFX) Zertifikatsprofile** sind verfügbar für Android 4.0 oder höher und Windows-10 (Desktop und Mobile) und höher. Damit wird verhindert. PFX ist nicht mit einen Server NDES erforderlich. Informationen Sie zum verwenden. PFX Zertifikatsprofile in [Aktivieren des Zugriffs auf Unternehmensressourcen Zertifikatsprofile mit Microsoft Intune verwenden](http://technet.microsoft.com/library/dn818904.aspx)
* **Corporate Begrenzung Einstellungen für Windows 10 Desktop- und Mobile** aktivieren präzise VPN-Einstellungen, wie in [Verbindung mit ihrer Arbeit mit VPN Profile mit Microsoft Intune Benutzer Hilfe](https://technet.microsoft.com/library/dn818905.aspx) beschrieben
* **Die OneDrive-app für Android nun unterstützt mehrere Identität**. Dieses und andere Updates zu mobile-app Informationsverwaltungsrichtlinien werden in der [Liste der Microsoft-Programme, die Sie verwalten können](https://technet.microsoft.com/library/dn708489.aspx)beschrieben.
* **iOS umgehen Aktivierung Sperren**. Wenn im Besitz eines Unternehmens iOS-Geräte durch Aktivierung Sperren geschützt sind, müssen Sie Apple-ID und das Kennwort des Benutzers eingeben, bevor Sie gelöscht oder das Gerät reaktivieren können. Dies kann eine Herausforderung darstellen, wenn der Benutzer das Unternehmen verlassen und Zurückgeben eines Unternehmens Gerät ohne Aktivierung Sperren auszuschalten. Um dieses Problem zu lösen, können Sie [Intune Aktivierung Sperren umgehen](https://technet.microsoft.com/library/mt414176.aspx)

### Bedingte Zugriff für PCs
Sie können jetzt bedingte Richtlinien für PCs konfigurieren. Dadurch wird die Office-desktop-apps zu Exchange Online und SharePoint online-Dienste zuzugreifen.
Um bedingte Zugriffsrichtlinie für PCs aktivieren zu können, muss der PC sein Domäne beigetreten oder Antrag werden.
* Finden Sie unter **Erste Schritte** im Abschnitt [Verwalten-Zugriff auf e-Mail- und SharePoint mit Microsoft Intune](http://technet.microsoft.com/library/dn818907)aspx-) für die vollständige Liste der Anforderungen bedingten Zugriff für PCs aktivieren.
* Finden Sie unter [Verwalten von e-Mail-Zugriff mit Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) Optionen, die Sie zum Aktivieren des bedingten Zugriffs für e-Mail-Zugriff festlegen können.
* Finden Sie unter [Verwalten von SharePoint Online-Zugriff mit Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) Optionen können Sie festlegen, bedingten Zugriff für SharePoint Online zu aktivieren.

### Änderungen und Updates an Microsoft Unternehmen Portal apps
Das Unternehmen Portal apps in dieser Version wurden die folgenden Änderungen vorgenommen:

**Android**

Benutzer sehen nun Gerät Registrierungs-Anweisungen nach der Anmeldung, wenn diese Geräts für die Verwaltung noch nicht registriert haben.

### Was ist neu in Intune Dokumentation--August 2015
**Neue Themen**

|Titel|Details|
|-----|-------|
|[Schützen Sie iOS, Geräte mit Aktivierung Sperren für Microsoft Intune umgehen](https://technet.microsoft.com/library/mt414176.aspx)|Erfahren Sie, wie Sie Intune iOS Aktivierung Sperren umgehen, wenn ein Benutzer das Unternehmen verlässt und einem gesperrten Gerät gibt verwenden können.|

**Aktualisierte Themen**

|Titel|Details|
|-----|-------|
|[Microsoft-apps können Sie mit dem Microsoft Intune mobilen Anwendung Informationsverwaltungsrichtlinien](https://technet.microsoft.com/library/dn708489.aspx)|Aktualisiert mit den neuesten Informationen zu apps, die mit mobilen Anwendung Informationsverwaltungsrichtlinien verwaltet.
|[Verwenden von Richtlinien zum Verwalten von Computern und mobilen Geräten mit Microsoft Intune](http://technet.microsoft.com/library/dn743712.aspx)|Aktualisiert mit den neuesten Richtlinien Intune hinzugefügt.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->
