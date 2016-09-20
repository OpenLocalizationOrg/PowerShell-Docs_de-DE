---
title: "Compliance-Richtlinien für Android-Geräten | Microsoft Intune"
description: "In diesem Thema werden die Einstellungen für Audiogeräte Compliance Richtlinie für Android-Geräten."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: cf1fde5b5ed55552e573c724b6165203033683da
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Compliance-Richtlinien für Android-Geräten in Microsoft Intune

In diesem Artikel beschriebenen Einstellungen für die Informationsverwaltungsrichtlinie gelten für Geräte, auf denen Android 4.0 und höher oder Samsung KNOX 4.0 und höher.

Wenn Sie Informationen zu anderen Plattformen suchen, wählen Sie eine der folgenden Aktionen aus:
> [!div class="op_single_selector"]
- [Compliance-Richtlinien für iOS-Geräte](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Compliance-Richtlinien für Windows-Geräten](windows-compliance-policy-settings-in-microsoft-intune.md)

## Sicherheit Systemeinstellungen
### Kennwort
- **Anfordern eines Kennworts zum Entsperren von mobiler Geräten:** Legen Sie den **Ja** zum Festlegen, dass Benutzer ein Kennwort eingeben, bevor sie ihr Gerät zugreifen können.

-  **Kennwort Mindestlänge:** Geben Sie die minimale Anzahl von Ziffern oder Zeichen, die das Kennwort des Benutzers enthalten muss.

- **Kennwort Qualität:** Aktivieren Sie diese Einstellung Kennwort Anforderungen für Android-Geräten konfigurieren. Wählen Sie aus:
  -   **Biometrische niedriger Sicherheit**
  - **Erforderlich**
  -   **AT mindestens numerische**
  -   **Mindestens alphabetischen**
  -   **Mindestens alphanumerische**
  -   **Mit Symbolen alphanumerische**

- **Minuten nach der letzten vor dem Kennwort erforderlich ist:**  Gibt die im Leerlauf Zeit, bevor der Benutzer das Kennwort erneut eingegeben werden muss.

- **Kennwortablauf (Tage):** Wählen Sie die Anzahl der Tage, bevor das Kennwort des Benutzers abläuft, und sie müssen einen neuen erstellen.

- **Kennwortverlauf Denken Sie daran:** Verwenden Sie diese Einstellung in Verbindung mit **zu verhindern, dass Wiederverwendung von vorherigen Kennwörter** zu verhindern, dass den Benutzer zuvor verwendete Kennwörter erstellen.

- **Verhindern, dass Wiederverwendung von vorherigen Kennwörtern:** Wenn **Speichern Kennwortverlauf** ausgewählt ist, geben Sie die Anzahl der zuvor verwendete Kennwörter, die wieder verwendet werden kann.

- **Anfordern eines Kennworts, wenn das Gerät aus dem Leerlauf zurückkehrt:** Diese Einstellung sollte verwendet werden, zusammen mit der in der Einstellung **Minuten nach der letzten vor dem Kennwort erforderlich ist** . Geben Sie ein Kennwort ein, um ein Gerät zugreifen, die nicht aktiv, für die der Einstellung **Minuten nach der letzten vor dem Kennwort erforderlich ist** angegebene Zeit war werden die Endbenutzer aufgefordert.

### Verschlüsselung
- **Verschlüsselung auf dem mobilen Gerät anfordern:** Legen Sie den **Ja** zu Geräte verschlüsselt werden, um eine Verbindung mit Ressourcen erfordern. Geräte, die verschlüsselt sind, wenn Sie die Einstellung **Anfordern eines Kennworts zum Entsperren von mobiler Geräten**konfigurieren.

## Gesundheit und Sicherheit des Audiogeräts

- **Gerät muss nicht Jailbroken oder einen Stamm:** Wenn Sie diese Einstellung aktivieren, werden Jailbroken Geräte als nicht kompatible ausgewertet werden.
- **Erfordern, dass Geräte verhindern, dass die Installation von apps von unbekannten Quellen (Android 4.0 oder höher)** Geräte sperren, die die **Sicherheit > unbekannten Quellen** auf dem Gerät aktiviert, aktivieren Sie diese Einstellung, und legen Sie ihn auf **Ja**.  
>[!IMPORTANT]
>Seite Laden von Applications erfordert, dass die **unbekannten Quellen** -Einstellung aktiviert ist.  Sie sollten nur dieser Richtlinie Kompatibilität erzwingen, wenn Sie nicht die Seite geladen Android-apps auf Geräten sind.

- **Erfordern, dass USB-Debuggen deaktiviert ist (Android 4.2 oder höher)**: Diese Einstellung gibt an, ob erkennen, der für das Debuggen auf dem Gerät Option USB aktiviert ist.
- **Erfordern Geräte Scan Gerät für Sicherheitsrisiken (Android 4.2-4,4) aktiviert haben**: Diese Einstellung gibt an, dass das Feature **Überprüfen apps** auf dem Gerät aktiviert ist.
- **Minimalen Android Sicherheit patch Ebene (Android 6.0 oder höher)**: Verwenden Sie diese Einstellung, um die minimale Android Patch anzugeben.  Geräte, die nicht mindestens diese Patch Ebene sind, werden nicht kompatibel. Das Datum muss das Format angegeben: JJJJ-MM-TT.
- **Erfordern Gerät Virenschutz aktiviert werden**: mit dieser Einstellung können Sie die risikobewertung aus der Lösung Lookout MTP als Bedingung für die Kompatibilität optimieren. Wählen Sie die maximal zulässige Bedrohung Ebene, also eine der folgenden Aktionen aus:

  - **Keine (gesicherten)** Dies ist die sicherste. Dies bedeutet, dass das Gerät alle Risiken haben kann. Wenn das Gerät erkannt wird, als hätten Sie beliebigen Ebenen von Risiken, wird sie als inkompatibel ausgewertet werden.
  - **Niedrig:** Gerät wird als kompatibel ausgewertet, wenn nur niedrige Ebene Risiken vorhanden sind. Nichts höheren versetzt das Gerät in ein-kompatiblen Status aus.
  - **Mittel:** Gerät wird als kompatibel, wenn die Risiken, die auf dem Gerät vorhanden sind, Niedrig oder Mittel Ebene sind ausgewertet. Wenn das Gerät hohe Ebene Risiken erkannt wurde, wird es als inkompatibel bestimmt.
  - **Hoch:** Dies ist die unsicherste. Im Wesentlichen auf diese Weise können alle Verfahren zum Erstellen von Ebenen, und nur vielleicht nützlich Wenn Sie bei Verwendung dieser Lösung nur für Berichtszwecke.

  Weitere Informationen hierzu finden Sie unter [Gerät Bedrohung Schutzregel in die Compliance-Richtlinien zu aktivieren](enable-device-threat-protection-rule-in-compliance-policy.md).

## Eigenschaft des Audiogeräts
- **Minimum OS erforderlich:** Wenn ein Gerät den OS Version Mindestanforderungen nicht erfüllt, wird er nicht als kompatible gemeldet.
  Von Links zu Informationen zum upgrade wird angezeigt. Der Endbenutzer können Geräts upgrade, nach denen sie Unternehmensressourcen zugreifen können.

- **Zulässige maximale Betriebssystemversion:** Wenn ein Gerät später als den in der Regel eine Version des Betriebssystems verwendet wird, Zugriff auf Unternehmensressourcen ist gesperrt, und der Benutzer wird aufgefordert, wenden Sie sich an ihre IT-Administrator. Bis es eine Änderung in der Regel ist, die die Version des Betriebssystems zulässt, kann diese Gerät Zugriff auf Unternehmensressourcen verwendet werden.
