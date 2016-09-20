---
title: "Compliance-Richtlinien für iOS-Geräte | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: a2f98bbd34cf8b0c86531ae6ff40b1044c15d8bd
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Compliance-Richtlinien für iOS-Geräte in Microsoft Intune

In diesem Artikel beschriebenen Einstellungen für die Informationsverwaltungsrichtlinie gelten für Geräte dem iOS 8.0 und höher ausgeführt wird.

Wenn Sie Informationen zu anderen Plattformen suchen, wählen Sie eine der folgenden Aktionen aus:
> [!div class="op_single_selector"]
- [Compliance-Richtlinien für Android-Geräten](android-compliance-policy-settings-in-microsoft-intune.md)
- [Compliance-Richtlinien für Windows-Geräten](windows-compliance-policy-settings-in-microsoft-intune.md)

## Sicherheit Systemeinstellungen
### Kennwort
- **Anfordern eines Kennworts zum Entsperren von mobiler Geräten:**    Legen Sie den **Ja** zum Festlegen, dass Benutzer ein Kennwort eingeben, bevor sie ihr Gerät zugreifen können. iOS-Geräte, die Kennwort verschlüsselt werden.

- **Einfache Kennwörter zulassen:**    Legen Sie den **Ja** zum Erstellen von einfacher Kennwörtern wie '**1234**' oder '**1111**' Benutzer können.

-  **Kennwort Mindestlänge:** Geben Sie die minimale Anzahl von Ziffern oder Zeichen, die das Kennwort des Benutzers enthalten muss.
- **Kennworttyp erforderlich:** Angeben, ob Benutzer eine **alphanumerisch**oder einer **numerischen** Kennwort erstellen müssen.

- **Minimale Anzahl von Zeichensätzen:** Wenn Sie **erforderliche Kennworttyp** in **alphanumerischen**festlegen möchten, verwenden Sie diese Einstellung die minimale Anzahl von Zeichensätzen angeben, die das Kennwort enthalten muss. Die vier Zeichen sind:
  -   Kleinbuchstaben
  -   Großbuchstaben
  -   Symbole
  -   Zahlen

  Festlegen von eine höhere Anzahl für diese Einstellung erfordern Benutzer Kennwörter erstellen, die komplexere sind.

  Für iOS-Geräte, diese Einstellung bezieht sich auf die Anzahl von Sonderzeichen (z. B. **!**, **#**, **&amp;**), die in das Kennwort enthalten sein müssen.
- **Minuten nach der letzten vor dem Kennwort erforderlich ist:**  Geben Sie im Leerlauf, der Benutzer das Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):** Wählen Sie die Anzahl der Tage, bevor das Kennwort des Benutzers abläuft, und sie müssen einen neuen erstellen.

- **Kennwortverlauf Denken Sie daran:** Verwenden Sie diese Einstellung in Verbindung mit **zu verhindern, dass Wiederverwendung von vorherigen Kennwörter** zu verhindern, dass den Benutzer zuvor verwendete Kennwörter erstellen.

- **Verhindern, dass Wiederverwendung von vorherigen Kennwörtern:** Wenn **Speichern Kennwortverlauf** ausgewählt ist, geben Sie die Anzahl der zuvor verwendete Kennwörter, die wieder verwendet werden kann.

- **Anfordern eines Kennworts, wenn das Gerät aus dem Leerlauf zurückkehrt:** Diese Einstellung sollte verwendet werden, zusammen mit der in der Einstellung **Minuten nach der letzten vor dem Kennwort erforderlich ist** . Die Endbenutzer werden aufgefordert, geben Sie ein Kennwort ein, um ein Gerät zugreifen, die nicht aktiv, für die angegebene der Einstellung **Minuten nach der letzten vor dem Kennwort erforderlich ist war** .

### E-Mail-Profil
- **E-Mail-Konto verwaltet werden muss, indem Sie Intune:** Wenn diese Option auf **Ja**festgelegt ist, muss das Gerät die nicht kompatible e-Mail auf dem Gerät bereitgestellt verwenden. Das Gerät wird nicht in den folgenden Situationen kompatible betrachtet:
  - Die e-Mail-Profils auch der gleichen Benutzergruppe unter Benutzergruppe Ziel von Compliance-Richtlinien bereitgestellt werden muss, werden andernfalls Geräte des Benutzers nicht kompatible angesehen.
  - Das Gerät wird gemeldet, als nicht kompatible, wenn der Benutzer bereits ein e-Mail-Konto auf dem Gerät eingerichtet hat, die das auf dem Gerät bereitgestellte Intune-e-Mail-Profil entspricht. Intune kann nicht überschrieben werden das Profil Benutzer bereitgestellt und können daher nicht verwalten sie. Um Compliance sicherzustellen, muss der Benutzer die vorhandene-e-Mail-Einstellungen entfernen, und klicken Sie dann Intune kann das verwaltete e-Mail-Profil installieren.


- **Wählen Sie das e-Mail-Profil, die vom Intune verwaltet werden muss:** 
   Wenn die **e-Mail-Konto verwaltet werden muss, indem Sie Intune** -Einstellung aktiviert ist, wählen Sie **Wählen Sie aus** , um das Intune-e-Mail-Profil festzulegen. Das e-Mail-Profil muss auf dem Gerät vorhanden sein.

     Weitere Informationen zu e-Mail-Profilen finden Sie unter [Konfigurieren des Zugriffs auf Ihres Unternehmens-e-Mail-e-Mail-Profile mit Microsoft Intune verwenden](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## Integrität des Audiogeräts

- **Gerät muss nicht Jailbroken oder einen Stamm:** Wenn Sie diese Einstellung aktivieren, werden Jailbroken Geräten nicht kompatibel.

##  Eigenschaften des Geräts
- **Minimum OS erforderlich:** Wenn ein Gerät den OS Version Mindestanforderungen nicht erfüllt, wird er nicht als kompatible gemeldet.
Von Links zu Informationen zum upgrade wird angezeigt. Endbenutzer können auswählen, Geräts Upgrade nach dem sie Unternehmen-Ressourcen zugreifen können soll.

- **Zulässige maximale Betriebssystemversion:** Wenn ein Gerät später als den in der Regel eine Version des Betriebssystems verwendet wird, Zugriff auf Unternehmensressourcen ist gesperrt, und der Benutzer wird aufgefordert, wenden Sie sich an ihre IT-Administrator. Bis es eine Änderung in der Regel ist, die die Version des Betriebssystems zulässt, kann diese Gerät Zugriff auf Unternehmensressourcen verwendet werden.
