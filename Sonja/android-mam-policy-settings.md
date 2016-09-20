---
title: Android MAM Richtlinieneinstellungen | Microsoft Intune
description: "In diesem Thema werden die Einstellungen mobile-app für die Informationsverwaltungsrichtlinie für Android-Geräten."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ms.reviewer: andcerat
ms.suite: ems
ms.openlocfilehash: 652f3aac9bd0925bd8e8718df04c0eb4b5629902
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Android mobile-Appeinstellungen für die Informationsverwaltungsrichtlinie in Microsoft Intune
Die nachfolgend beschriebenen Richtlinien können für eine MAM Richtlinie auf das Blade **Einstellungen** im Azure-Portal [konfiguriert](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sein.
Es gibt zwei Feldkategorien für Richtlinieneinstellungen, Hand und Bedienung ein:

##  Einstellungen für Verlagerung von Daten
Der Begriff **, den Richtlinie verwaltet apps** auf apps verweisen verwendet, werden, die mit MAM konfiguriert.
- **Android verhindern, dass Sicherungskopien:** Wählen Sie **Ja,** um zu deaktivieren, oder **keine** Sicherungskopie des Unternehmensdaten von der Richtlinie dürfen verwaltete apps.

  **Standardwert = Ja**
- **Zulassen app übertragen von Daten auf anderen apps:** Wählen Sie eine der Optionen, um die apps anzugeben, die von der Richtlinie Unternehmensdaten erhalten können verwaltete apps:
  -   **Richtlinie verwaltet apps**: Übergabe an nur apps, die die Richtlinie MAM aufweisen zulassen
  -   **Alle apps**: Übergabe an eine beliebige app zulassen
  -   **Keine**: Datenübertragung an eine beliebige app nicht zulassen

  **Standardwert = Richtlinie verwaltet apps**
- **Zulassen-app Daten aus anderen apps zu erhalten:** Angeben von apps, die Daten in der Richtlinie verwaltet apps zu übertragen:
  -   **Richtlinie verwaltet apps**: zulassen Datenübertragung nur aus anderen Richtlinie verwaltet apps
  -   **Alle apps**: Datenübertragung über eine beliebige app zulassen
  -   **Keiner**: Datenübertragung über eine beliebige app, nicht zulassen

      **Standardwert = alle apps**

-   **Speichern unter verhindern:** Wählen Sie auf **Ja,** um die Verwendung der Option ' Speichern unter ' in eine beliebige app zu deaktivieren, die dieser Richtlinie verwendet. Wenn Sie die Verwendung von Speichern unter zulassen möchten, wählen Sie **Nein** .

  **Standardwert = Ja**
- **Einschränken Ausschneiden, kopieren und Einfügen mit anderen apps:** Geben Sie beim Ausschneiden, kopieren und von Einfügeoperationen eingeschränkt werden soll. Wählen Sie aus:
  -   **Blockiert:** Lassen Sie nicht ausschneiden, kopieren und von Einfügeoperationen zwischen apps Richtlinie verwaltet.
  -   **Richtlinie verwaltet Apps**: nur ermöglichen, Ausschneiden, kopieren und von Einfügeoperationen zwischen apps Richtlinie verwaltet.
  -   **Fügen Sie Richtlinie verwaltet-Apps mit**: zulassen Ausschneiden oder Kopieren von zwischen apps Richtlinie verwaltet. Lassen Sie Ausschneiden oder kopierten Daten aus einem beliebigen app in diese app eingefügt werden.
  -   **Jedes App**: keine Einschränkungen beim Ausschneiden, kopieren und Einfügen zwischen apps, die Vorgänge.

    **Standardwert = fügen Sie verwaltete-apps mit Richtlinie**
-   **Einschränken von Webinhalten im Browser verwaltet angezeigt werden:** Wenn diese Einstellung aktiviert ist, werden alle Links in der app im Browser verwaltet geöffnet werden.

  Für Geräte, die nicht in Intune registriert sind, öffnet apps Richtlinie verwaltet Weblinks nur in der verwalteten Browser-app verwenden die mobile-app zur Dokumentverwaltungsrichtlinie.

  Wenn Sie zum Verwalten Ihrer Geräte Intune verwenden, finden Sie unter [Verwendung von verwalteten Browserrichtlinien mit Microsoft Intune Zugriff auf das Internet verwalten](manage-internet-access-using-managed-browser-policies.md).

    **Standardwert = Ja**
- **Verschlüsseln Sie die app-Daten:** Wählen Sie **Ja** Verschlüsselung aktivieren. Wenn diese Einstellung aktiviert ist, für apps, die eine mobile-app zur Dokumentverwaltungsrichtlinie zugeordnet sind, wird die Verschlüsselung von Microsoft bereitgestellt. Daten werden während der Datei e/a-Vorgänge synchron verschlüsselt werden. Inhalt auf dem Gerätespeicher ist immer verschlüsselt werden.
  >[!NOTE]
  >Die Verschlüsselungsmethode ist nicht FIPS 140-2 zertifizierten

  **Standardwert = Ja**

- **Kontaktsynchronisierung deaktivieren:** Wählen Sie auf **Ja,** um zu verhindern, dass die Kontaktinformationen aus mit der Adresse einer systemeigenen Adressbuch-app auf dem Gerät synchronisiert. Wenn Sie **keine**auswählen, wird die app die Kontaktinformationen mit der Adresse einer systemeigenen Adressbuch auf dem Gerät speichern.<br/>In diesem Fall eines selektiven zurücksetzen Unternehmensdaten zu entfernen, werden die Kontakte, die direkt von der app auf der systemeigenen Adressbuch synchronisiert entfernt. Kontakte aus dem Adressbuch systemeigenen eine andere externe Quelle synchronisiert mit können nicht gelöscht. Dies ist derzeit nur für die app **Microsoft Outlook** verfügbar.

  **Standardwert = Ja**

##  Android Richtlinie Bedienung
Der Begriff **, den Richtlinie verwaltet apps** auf apps verweisen verwendet, werden, die mit MAM Richtlinien konfiguriert.

- **Erfordern PIN für den Zugriff:** Wählen Sie **Ja** , um eine PIN mit apps Richtlinie verwaltet werden müssen. Der Benutzer wird aufgefordert, dies das erste Mal einrichten, die sie die app in einem Arbeitskontext ausführen.

 **Standardwert = Ja**

 -  **Einfache PIN zulassen:** Geben Sie an, ob Benutzer einfache PIN folgen, wie z. B. 1234 oder 1111 verwenden können. **Standardwert Ja =**.
 - **PIN-Länge:** Geben Sie die minimale Anzahl von Ziffern in eine PIN ein. **Standardwert = 4**
 - **Anzahl der Versuche vor dem Zurücksetzen der PIN:** Geben Sie die Anzahl der PIN-Eintrag Versuche, die bereitgestellt werden kann, bevor der Benutzer die PIN zurücksetzen muss. **Es ist kein Standardwert für diese Einstellung ein.**
- **Corporate Anmeldeinformationen für den Zugriff erforderlich:** Wählen Sie **Ja** corporate Anmeldeinformationen statt eine PIN für Access app erforderlich ist.  Wenn Sie dies auf **Ja**festgelegt haben, überschreibt diese Eigenschaft zum ANHEFTEN oder einem Touch-ID an.  Der Benutzer werden aufgefordert, geben Sie ihre Anmeldeinformationen Ihres Unternehmens.

  **Standardwert = Nein**
- **Blockieren verwaltete apps Ausführung auf Jailbroken oder ab dem Stammverzeichnis Geräte:** Wählen Sie **Ja** , apps Ausführung auf Jailbroken oder ab dem Stammverzeichnis Geräte blockieren. Der Benutzer weiterhin verwenden der apps für persönliche Aufgaben können jedoch ein anderes Gerät für Arbeit verwendet haben.

  **Standardwert = Ja**
- **Überprüfen Sie die Access-Anforderungen nach (Minuten)**-   **Timeout:** Zeit (in Minuten), bevor Sie die Access-Anforderungen für die app erneut geprüft werden.
  -   **Offline Nachfrist:** Wenn das Gerät offline ist, geben Sie die Zeit (in Minuten) bevor Sie die Access-Anforderungen für die app erneut, sind geprüft.

    **Standardwerte = 30 Minuten Timeout und offline Nachfrist 720 Minute**

-   **Offline Intervall vor der app-Daten (Tage) bereinigt werden:** Sie können auch die Unternehmensdaten zurücksetzen aus, wenn ein Gerät während eines bestimmten Zeitraums offline war.  Geben Sie die Anzahl der Tage, die ein Gerät offline sein kann, bevor die Unternehmensdaten vom Gerät entfernt werden. **Tipp:** Eingeben der Wert 0 wird diese Einstellung zu deaktivieren.

  **Standardwert = 90 Tage**
- **Blockieren einen Bildschirmausschnitt und Android-Assistenten (Android 6 Kaugummi oder höher):** Wählen Sie Block einen Bildschirmausschnitt und **Android-Assistenten** Funktionen des Geräts **Ja** , wenn diese app zu verwenden.
