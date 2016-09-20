---
title: Mac OS X Richtlinieneinstellungen | Microsoft Intune
description: "Intune stellt einen Bereich von integrierten Allgemeine Einstellungen, die Sie, auf dem Mac OS X-Geräte konfigurieren können. Darüber hinaus können Sie das Tool Apple-Konfiguration zum Erstellen von benutzerdefinierter Einstellungen, die nicht von Intune verfügbar sind."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: c6b010e49b4e581dad056aa6e8bb17123030f7b0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Mac OS X-Konfiguration Richtlinieneinstellungen Microsoft Intune

Intune stellt einen Zellbereich integrierte Allgemeine Einstellungen, die Sie, auf dem Mac OS X-Geräte konfigurieren können. Darüber hinaus können Sie das Tool Apple-Konfiguration um benutzerdefinierte Einstellungen zu erstellen, die nicht Intune verfügbar sind.

## Allgemeine Konfiguration Richtlinieneinstellungen

Verwenden Sie die Microsoft Intune- **Mac OS X Konfiguration von allgemeinen Richtlinie** so konfigurieren Sie die Einstellungen für ein:

-   **Gerätesicherheitseinstellungen**. Wählen Sie aus einer Liste von vordefinierten Einstellungen, mit die Sie eine Reihe von Features und Funktionen auf dem Gerät steuern können.

-   **Compliance-gerecht und apps nicht kompatibel**. Geben Sie eine Liste der apps, die kompatibel oder in Ihrem Unternehmen nicht kompatibel sind. Nicht kompatible Apps Bericht können die Kompatibilität von apps anzeigen möchten, die Sie in der Liste anhand der apps angegeben, die Benutzer installiert haben haben (aber nicht möglich tatsächlich Blockieren der Installation der app) verwendet werden.

Wenn Sie die Einstellung für gesuchte in dieser Liste nicht angezeigt wird, können Sie möglicherweise erstellen sie mithilfe einer benutzerdefinierten Mac OS X-Richtlinie, die Sie können importieren, die Sie erstellt haben, mit dem Tool Apple-Konfiguration. Weitere Informationen finden Sie unter "Benutzerdefinierte Richtlinieneinstellungen" weiter unten in diesem Thema.

### Kennworteinstellungen

|Name der Einstellung|Details|
|----------------|---------------|
|**Anfordern eines Kennworts zum Entsperren von Geräten**|Geben Sie an, ob der Benutzer ein Kennwort verwenden muss, auf deren Computern Mac zugreifen. **Wichtige:** Im Gegensatz zu iOS-Geräte auf Mac OS X-Geräten wird der Benutzer nicht sofort aktualisieren Sie ihr Kennwort ein, um die Einhaltung von dieser Einstellung benachrichtigt.|
|**Kennwort geben erforderlich**|Angeben, ob das Kennwort nur **numerisch** sein kann, oder ob er **alphanumerisch** sein muss (Buchstaben und Zahlen enthalten). **Wichtige:** Diese Einstellung ist und höher unterstützt nur unter Mac OS X, Version 10.10.3.|
|**Anzahl der komplexe Zeichen im Feld Kennwort erforderlich**|Geben Sie die Anzahl der komplexe Zeichen in das Kennwort (**0** bis **4**) erforderlich.<br /><br />Eine komplexe Zeichen ist ein Symbol, z. B. **?**.|
|**Mindestlänge des Kennworts**|Geben Sie die Mindestlänge für das Kennwort (**4** **14** -Zeichen) an.|
|**Einfache Kennwörter zulassen**|Die Verwendung von einfachen Kennwörtern wie **0000** oder **1234**zulassen.|
|**Minuten nach der letzten vor dem Kennwort erforderlich ist.**|Geben Sie an, wie lange der Computer inaktiv sein muss, bevor Sie ein Kennwort zum Entsperren erforderlich ist.|
|**Kennwortablauf (Tage)**|Geben Sie an, wie viele Tage verstreichen müssen, bevor der Benutzer muss das Kennwort (**1** bis **255** Tage) ändern.|
|**Denken Sie daran Kennwortverlauf**|Verhindern, dass des Benutzers ein zuvor verwendetes Kennwort verwenden. Wenn dies festgelegt ist, können Sie auch festlegen, um anzugeben, dass die Anzahl der zuvor verwendete Kennwörter, die nicht möglich (**1** bis **24**) wiederverwendet **Wiederverwendung von vorherigen Kennwörter verhindern** .|
|**Minuten nach der letzten vor dem Bildschirmschoner aktiviert**|Geben Sie die Länge der Zeit, die der Computer im Leerlauf sein muss, bevor der Bildschirmschoner aktiviert ist.|

### Einstellungen für kompatible und nicht kompatible apps
In der **kompatibel &amp; nicht kompatible Apps-Liste für Mac OS X** **verwaltete Einstellungen für Geräte**aktivieren, und klicken Sie dann eine Liste der kompatiblen oder nicht kompatibel apps mithilfe der folgenden Informationen angeben.

> [!NOTE]
> Eine einzelne Richtlinie kann nur eine Liste der kompatiblen apps oder eine Liste der nicht kompatiblen apps enthalten. Sie können keine beide in der gleichen Richtlinie angeben.
>
> Intune ermöglicht Ihnen Geräte mit nicht kompatiblen apps zu melden. Nicht blockieren Installation oder Entfernen von apps nicht kompatibel.

|Name der Einstellung|Details|
|----------------|---------------|
|**Melden Sie bei nicht-Konformität, wenn der Benutzer der aufgeführten apps installieren**|Zeigt die Mac OS X-apps, die Benutzer dürfen nicht installieren. Wenn der Benutzer eine der folgenden apps installiert haben, werden sie in **Nicht kompatiblen Apps Berichten**gemeldet werden.|
|**Melden Sie bei nicht-Konformität, wenn Benutzer apps installieren, die nicht aufgeführt sind**|Zeigt die Mac OS X-apps, die Benutzern gestattet ist, zu installieren. Wenn der Benutzer eine beliebige andere apps installiert haben, werden sie in **Nicht kompatiblen Apps-Berichten**gemeldet werden.|
|**Hinzufügen**|Hinzufügen einer app der ausgewählten Liste an. Geben Sie einen Namen Ihrer Wahl, optional die app Publisher und die Paket-ID der app. **Tipp:** Um die app-Paket ID gefunden haben, gehen Sie folgendermaßen vor, auf einem Mac-Computer, der die Anwendung installiert ist:<ol><li>Öffnen Sie den Ordner, in dem die app ( **beispielsweise/Programme**) installiert ist.</li><li>Wählen Sie aus der * &lt;App-Name&gt;***.app** zu bündeln, und wählen Sie **Paketinhalt anzeigen**.</li><li>Öffnen Sie die Datei **"Info.plist"** ein.</li><li>Überprüfen Sie den Wert, der die Taste **CFBundleIdentifier**zugeordnet.</li></ol>Das Format für die Paket-ID ist **com.contoso.appname**.|
|**Importieren von Apps**|Importieren Sie eine Liste der apps, die Sie in eine CSV-Datei angegeben haben. Verwenden Sie dieses Format in der Datei: app-Name, Publisher, app-Paket-ID an.|
|**Bearbeiten**|Bearbeiten Sie den Namen, Publisher und app-Paket-ID der ausgewählten app.|
|**Löschen**|Löschen der ausgewählten app aus der Liste aus.|
> [!TIP]
> Weitere Informationen zu Berichten Intune finden Sie unter [grundlegende Informationen zu Microsoft Intune Vorgänge mithilfe von Berichten](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Wenn ein Mac OS X-Gerät in den Ruhemodus handelt, werden Richtlinien und Profile nicht übermittelt oder ermittelt. Daher möglicherweise die Intune-Verwaltungskonsole vorübergehend den Status **Richtlinieneinstellungen Fehler** erst beim nächsten Öffnen anzuzeigen, die das Gerät aus dem Energiesparmodus reaktivieren des.

### Überwachen der apps kompatible und nicht kompatible
Verwenden Sie **Nicht kompatible Apps-Berichte** , die Kompatibilität von apps anzeigen möchten, die Sie angegeben haben.

#### Zum Ausführen eines Berichts

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), **Berichte** &gt; **Nicht kompatible Apps-Berichte**.

2.  Wählen Sie die Gerätegruppen, die Sie überprüfen, ob Sie soll kompatiblen apps, apps nicht kompatible oder beides gesucht werden soll, und wählen Sie dann auf **Bericht anzeigen**möchten.

## Mac OS X benutzerdefinierte Richtlinieneinstellungen in Microsoft Intune
Verwenden Sie die Microsoft Intune- **Richtlinie für Mac OS X-Konfiguration mit benutzerdefinierten** Einstellungen bereitstellen, die Sie erstellt haben, indem Sie mit dem [Tool Apple-Konfiguration](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) in Mac OS X-Geräte. Diese-Tool können Sie viele Einstellungen erstellen, die Steuerung des Betriebs dieser Geräte und einem Konfiguration Profil zu exportieren. Dann können Sie dieses Konfigurationsprofil in einer benutzerdefinierten Intune Mac OS X-Richtlinie importieren und die Einstellungen für Benutzer und Geräte in Ihrer Organisation bereitstellen.

Diese Funktion können Sie Mac OS X-Einstellungen bereitstellen, die nicht mit der Intune Mac OS X-Konfiguration von allgemeinen Richtlinie konfiguriert werden.

### Erforderliche Komponenten
Bevor Sie beginnen, müssen Sie die Apple-Konfiguration installiert und eine Konfigurationsdatei, die Einstellungen enthält, die Sie für Benutzer oder Geräte bereitstellen möchten, erstellt haben. Sie können herunterladen und erfahren Sie mehr über die Apple-Konfiguration aus [Dem Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

> [!NOTE]
> Intune meldet nicht die Kompatibilität der einzelnen Einstellungen für eine benutzerdefinierte Richtlinie für Mac OS X. Jedoch ist die allgemeinen Vorschriften der Richtlinie gemeldet.

### Allgemeine Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Namen**|Geben Sie einen eindeutigen Namen für die benutzerdefinierte Richtlinie Mac OS X in der Intune Verwaltungskonsole erkennbar.|
    |**Beschreibung**|Geben Sie eine Beschreibung, die bietet einen Überblick über die benutzerdefinierten Mac OS X-Richtlinie und weitere relevante Informationen, die Sie danach zu suchen kann.|


### Benutzerdefinierte Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Benutzerdefinierte Konfiguration Profilname (für Benutzer angezeigt)**|Geben Sie einen Namen für die Richtlinie aus, wie er auf dem Gerät und in Berichten Intune angezeigt werden.|
    |**Konfigurationsdatei-Profil**|Wählen Sie **Importieren**aus, und wechseln Sie dann zu der Konfigurationsprofil, das Sie mithilfe der Apple-Konfiguration erstellt haben. **Tipp:** Finden Sie unter "erstellen eine Profils Konfigurationsdatei" in diesem Thema für die Hilfe in der Konfigurationsprofil erstellen.|
    |**Konfiguration von Profildetails**|Anzeigen des XML-Codes für das Konfigurationsprofil, das Sie importiert haben.|



### So erstellen Sie eine Profil Konfigurationsdatei
Sie können die Profil Konfigurationsdatei verwendet, die für die benutzerdefinierte Richtlinie auf zwei Arten erstellen:

-   Exportieren Sie die Datei (mit der Erweiterung **.mobileconfig**) auf das Tool Apple-Konfiguration aus.

-   Erstellen der Datei selbst mithilfe des entsprechenden Schemas aus der [Apple Konfiguration Profil Schlüssel verweisen](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


### Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
