---
title: iOS MAM Richtlinieneinstellungen | Microsoft Intune
description: "In diesem Thema werden die Einstellungen mobile-app für die Informationsverwaltungsrichtlinie für iOS-Geräte."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 673ff872-943c-4076-931c-0be90363aea9
ms.reviewer: andcerat
ms.suite: ems
ms.openlocfilehash: ba258bfb3140ffc79aa38ef2f46497346cdc6bfa
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
#  iOS Einstellungen mobile-app für die Informationsverwaltungsrichtlinie
Die nachfolgend beschriebenen Richtlinieneinstellungen können für eine Richtlinie MAM auf das Blade **Einstellungen** im Azure-Portal [konfiguriert](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sein.

Es gibt zwei Feldkategorien für Richtlinieneinstellungen, Hand und Bedienung ein:

##  Einstellungen für Verlagerung von Daten
Der Begriff **, den Richtlinie verwaltet apps** auf apps verweisen verwendet, werden, die mit MAM konfiguriert.

- **Zu verhindern, dass iTunes und iCloud Sicherungen:** Wählen Sie **Ja** zu deaktivieren, oder **keine** Sicherung von Unternehmensdaten aus der Richtlinie dürfen verwaltete apps.

  **Standardwert = Ja**

- **Zulassen app übertragen von Daten auf anderen apps:**   Wählen Sie eine der Optionen an, dass die apps, die Daten von der Richtlinie verwaltet apps erhalten können:
  - **Richtlinie verwaltet apps**: Übergabe an nur apps, die die Richtlinie MAM aufweisen zulassen.
  - **Alle apps**: Übergabe an eine beliebige app zulassen
  - **Keiner**: Datenübertragung an eine beliebige app, einschließlich andere Richtlinie verwaltet apps nicht zulassen.

  Wenn Sie diese Option **Richtlinie verwaltet Apps** oder **keiner**festgelegt haben, werden darüber hinaus die iOS 9-Funktion, die Spotlight suchen, um Daten innerhalb von apps zu durchsuchen ermöglicht, blockiert.

  **Diese Einstellung steuert die Verwendung der Funktion "Öffnen In" auf mobilen Geräten nicht. Zum Öffnen In verwalten zu können, finden Sie [hier](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)**.

  **Standardwert = Richtlinie verwaltet apps**

- **Zulassen app Daten aus anderen apps zu erhalten:**  Angeben von apps, die Daten in der Richtlinie verwaltet apps zu übertragen:
  -  **Richtlinie verwaltet apps**: Datenübertragung nur von einer anderen Richtlinie zulassen apps verwaltet.
  -  **Alle apps**: Datenübertragung über eine beliebige app zulassen
  -  **Keine**: Datenübertragung von einem beliebigen app nicht zulassen.

  **Standardwert = alle apps**

- **Speichern unter verhindern:** Wählen Sie auf **Ja,** um die Verwendung der Option ' Speichern unter ' in eine beliebige app zu deaktivieren, die dieser Richtlinie verwendet. Wählen Sie **Nein** , wenn Sie zulassen, die Verwendung von Speichern unter möchten.

  **Standardwert = Ja**

- **Einschränken Ausschneiden, kopieren und Einfügen mit anderen apps:** Geben Sie beim Ausschneiden, kopieren und von Einfügeoperationen eingeschränkt werden soll. Wählen Sie aus:
  -   **Blockiert:** Lassen Sie nicht ausschneiden, kopieren und von Einfügeoperationen zwischen apps Richtlinie verwaltet.
  -   **Richtlinie verwaltet Apps**: nur ermöglichen, Ausschneiden, kopieren und von Einfügeoperationen zwischen apps Richtlinie verwaltet.
  -   **Fügen Sie Richtlinie verwaltet-Apps mit**: zulassen Ausschneiden oder Kopieren von zwischen apps Richtlinie verwaltet. Lassen Sie Ausschneiden oder kopierten Daten aus einem beliebigen app in diese app eingefügt werden.
  - **Jedes App**: keine Einschränkungen beim Ausschneiden, kopieren und Einfügen zwischen apps, die Vorgänge.

  **Standardwert = Richtlinie verwalteten-apps mit einfügen**

- **Einschränken von Webinhalten im Browser verwaltet angezeigt werden:** Wenn diese Einstellung aktiviert ist, werden alle Links in der app im Browser verwaltet geöffnet werden.

  Für Geräte, die nicht in Intune registriert sind, können die Weblinks Apps Richtlinie verwaltet nur in der verwalteten Browser-app verwenden die mobile-app zur Dokumentverwaltungsrichtlinie öffnen.

  Wenn Sie zum Verwalten Ihrer Geräte Intune verwenden, finden Sie unter [Verwendung von verwalteten Browserrichtlinien mit Microsoft Intune Zugriff auf das Internet verwalten](manage-internet-access-using-managed-browser-policies.md).

    **Standardwert = Ja**

- **Verschlüsseln Sie die app-Daten:** Für apps, die zugeordnet sind eine [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] mobile-app zur Dokumentverwaltungsrichtlinie, Daten auf Rest mit Verschlüsselung vom Betriebssystem bereitgestellten verschlüsselt ist. Wenn Sie eine PIN erforderlich ist, werden die Daten pro die Einstellungen in der mobilen app zur Dokumentverwaltungsrichtlinie verschlüsselt. Wie in Apple-Dokumentation, [die vom iOS 7 verwendeten Module FIPS 140-2, die zertifiziert sind](http://support.apple.com/en-us/HT202739)erwähnt wird.

  In den Richtlinieneinstellungen für die können Sie die PIN-Verschlüsselungswerte angeben.  Diese Werte bestimmen, wenn die Daten verschlüsselt sind. Die Optionen sind:
  - **Gerät ist gesperrt, wenn:** Alle app-Daten, die dieser Richtlinie zugeordnet ist verschlüsselt, während das Gerät gesperrt ist.
  -   **Beim Gerät ist gesperrt (mit Ausnahme von geöffneten Dateien):** Alle app-Daten, die dieser Richtlinie zugeordnet ist verschlüsselt, während das Gerät, eine Ausnahme bilden jedoch Daten gesperrt ist, die in den Dateien, die derzeit in der app zu öffnen.
  -   **Nach Gerät neu starten:** Alle app-Daten, die dieser Richtlinie zugeordnet ist verschlüsselt, wenn das Gerät neu gestartet wird, bis das Gerät zum ersten Mal aufgehoben wird.
  -   **Des Audiogeräts verwenden:** App-Daten ist verschlüsselt basierend auf die Standardeinstellungen auf dem Gerät.
  Wenn Sie diese Einstellung aktivieren, ist der Endbenutzer zum Einrichten und verwenden eine PIN Geräts Zugriff auf erforderlich.  Ist keine PIN, der apps nicht gestartet, und der Endbenutzer werden aufgefordert, legen Sie eine PIN mit einer Nachricht-"Ihr Unternehmen hat erforderlich ist, dass Sie zuerst ein Gerät ANHEFTEN Zugriff auf diese Anwendung aktiviert werden müssen."

  **Standard Wert - Verschlüsselung Option nicht ausgewählt ist.**
- **Kontaktsynchronisierung deaktivieren:**  Wählen Sie auf **Ja,** um Kontaktinformationen aus Synchronisierung mit der Adresse einer systemeigenen Adressbuch auf dem Gerät zu verhindern. Wenn Sie **keine**auswählen, wird die app die Kontaktinformationen mit der Adresse einer systemeigenen Adressbuch auf dem Gerät speichern.

  Wenn Sie eine selektiven zurücksetzen Unternehmensdaten entfernen ausführen, werden die Kontakte aus der app direkt auf der systemeigenen Adressbuch synchronisiert entfernt. Kontakte aus dem Adressbuch systemeigenen auf eine andere externe Quelle synchronisiert mit können nicht gelöscht. Dies ist zurzeit kann nur auf der **Microsoft Outlook** -app.

  **Standardwert = Ja**
##  iOS Richtlinie Bedienung
Der Begriff **, den Richtlinie verwaltet apps** auf apps verweisen verwendet, werden, die mit MAM Richtlinien konfiguriert.
- **Erfordern PIN für den Zugriff:**  Wählen Sie **Ja** , um eine PIN Richtlinie verwaltet apps verwendet werden müssen. Der Benutzer ist dies das erste Mal einrichten, die sie die app in einem Arbeitskontext ausführen aufgefordert.

  **Standardwert = Ja**
    -  **Einfache PIN zulassen:** Geben Sie an, ob Benutzer einfache PIN folgen, wie z. B. 1234 oder 1111 verwenden können. **Standardwert Ja =**.
    - **PIN-Länge:** Geben Sie die minimale Anzahl von Ziffern in eine PIN ein. **Standardwert = 4**
    - **Anzahl der Versuche vor dem Zurücksetzen der PIN:** Geben Sie die Anzahl der PIN-Eintrag Versuche, die vor der Benutzer die PIN zurücksetzen muss gemacht werden können.
  **Es gibt keinen Standardwert für diese Einstellung**.

  - **Erfordern Fingerabdrucks anstelle der PIN (iOS) 8.0 +:** Wählen Sie **Ja** eine Fingerabdruck Identität anstelle einer nummerierten PIN für Access app erforderlich ist.
Auf iOS-Geräte können Sie sich mithilfe von Fingerabdrucks auf iOS-Geräte anstelle einer nummerierten PIN identifizieren den Benutzer zulassen. Wenn der Benutzer versucht, diese app mit ihrem Konto Arbeit zugreifen, werden sie aufgefordert, um seine Identität Fingerabdrucks statt eine PIN-Nummer einzugeben bereitzustellen.

    **Standardwert = Ja**
- **Corporate Anmeldeinformationen für den Zugriff erforderlich:** Wählen Sie **Ja** corporate Anmeldeinformationen statt eine PIN für Access app erforderlich ist. **Wenn Sie dies auf Ja festgelegt haben, überschreibt diese Eigenschaft, die Anforderungen für PIN oder Touch-ID an.** Der Benutzer werden ihre corporate Anmeldeinformationen aufgefordert.

  **Standardwert = Nein**
- **Blockieren verwaltete apps Ausführung auf Jailbroken oder ab dem Stammverzeichnis Geräte:** Wählen Sie **Ja** , apps Ausführung auf Jailbroken oder ab dem Stammverzeichnis Geräte blockieren. Der Benutzer weiterhin der apps für persönliche Aufgaben verwenden können, aber für die Arbeit mit einem anderen Gerät haben.

  **Standardwert = Ja**
- **Überprüfen Sie die Access-Anforderungen nach (Minuten)**|-   **Timeout:** Uhrzeit (in Minuten), bevor Sie die Access-Anforderungen für die app erneut geprüft werden.
  -   **Offline Nachfrist:** Wenn das Gerät offline ist, Angeben der Zeit (in Minuten), bevor die Access-Anforderungen für die app werden erneut geprüft.

  **Standardwert = 30 Minuten Timeout und offline Nachfrist 720 Minute**
  - **Offline Intervall vor der app-Daten (Tage) bereinigt werden:** Sie können auch die Unternehmensdaten zurücksetzen aus, wenn ein Gerät während eines bestimmten Zeitraums offline war.  Geben Sie die Anzahl der Tage, die ein Gerät offline sein kann, bevor die Unternehmensdaten vom Gerät entfernt werden. **Einen Wert von 0 eingeben, wird diese Einstellung deaktivieren aktivieren**.

  **Standardwert = 90 Tage**
