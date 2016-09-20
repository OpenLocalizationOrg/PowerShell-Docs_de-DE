---
title: "Compliance-Richtlinien für Windows-Geräten | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 12239464012029e3ffff3a9bed4f4ccb2cebe633
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Compliance-Richtlinien für Windows Geräte in Microsoft Intune

In diesem Artikel beschriebenen Einstellungen für die Informationsverwaltungsrichtlinie gilt für Geräte, die das Windows-Betriebssystem ausführen. Die spezifische Windows-Version unterstützt wird in den folgenden Abschnitten Hervorhebung.

Wenn Sie Informationen zu anderen Plattformen suchen, wählen Sie eine der folgenden Aktionen aus:
> [!div class="op_single_selector"]
- [Compliance-Richtlinien für iOS-Geräte](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Compliance-Richtlinien für Android-Geräten](android-compliance-policy-settings-in-microsoft-intune.md)

## Compliance-Richtlinien für Windows Phone-Geräte
Die Einstellungen, die in diesem Abschnitt werden unter Windows Phone 8.1 und höher unterstützt.

## Sicherheit Systemeinstellungen
### Kennwort
- **Anfordern eines Kennworts zum Entsperren von mobiler Geräten:**    Legen Sie den **Ja** zum Festlegen, dass Benutzer ein Kennwort eingeben, bevor sie ihr Gerät zugreifen können.

- **Einfache Kennwörter zulassen:**    Legen Sie den **Ja** zum Erstellen von einfacher Kennwörtern wie '**1234**' oder '**1111**' Benutzer können.

-  **Kennwort Mindestlänge:** Geben Sie die minimale Anzahl von Ziffern oder Zeichen, die das Kennwort des Benutzers enthalten muss.
- **Kennworttyp erforderlich:** Angeben, ob Benutzer eine **alphanumerisch**oder einer **numerischen** Kennwort erstellen müssen.

  Für Geräte mit Windows ausführen und auf das mit einem Microsoft-Konto, die Compliance-Richtlinien kann nicht ordnungsgemäß ausgewertet wird, ist Mindestlänge größer als acht Zeichen oder mehr als zwei ist Mindestanzahl von Zeichensätzen.

- **Minimale Anzahl von Zeichensätzen:** Wenn **Kennworttyp erforderlich** in **alphanumerischen**festgelegt ist, gibt diese Einstellung die minimale Anzahl von Zeichensätzen, die das Kennwort enthalten muss. Die vier Zeichen sind:
  -   Kleinbuchstaben
  -   Großbuchstaben
  -   Symbole
  -   Zahlen

  Festlegen von eine höhere Anzahl für diese Einstellung erfordern Benutzer Kennwörter erstellen, die komplexere sind. Für Geräte mit Windows ausführen und mit einem Microsoft-Konto zugegriffen, die Compliance-Richtlinien kann nicht ordnungsgemäß ausgewertet wird, ist Mindestlänge größer als acht Zeichen oder mehr als zwei ist Mindestanzahl von Zeichensätzen.
- **Minuten nach der letzten vor dem Kennwort erforderlich ist:**  Gibt die im Leerlauf Zeit, bevor der Benutzer das Kennwort erneut eingegeben werden muss.

- **Kennwortablauf (Tage):** Wählen Sie die Anzahl der Tage, bevor das Kennwort des Benutzers läuft ab und sie müssen einen neuen erstellen.

- **Kennwortverlauf Denken Sie daran:** Verwenden Sie diese Einstellung in Verbindung mit **zu verhindern, dass Wiederverwendung von vorherigen Kennwörter** zu verhindern, dass den Benutzer zuvor verwendete Kennwörter erstellen.

- **Zu verhindern, dass Wiederverwendung von vorherigen Kennwörtern:** Wenn **Speichern Kennwortverlauf** ausgewählt wurde, geben Sie die Anzahl der zuvor verwendeten Kennwörter, die wieder verwendet werden kann.
- **Verlangen eines Kennworts aus, wenn das Gerät aus dem Leerlauf zurückkehrt:** Diese Einstellung sollte zusammen mit der Einstellung **Minuten nach der letzten bevor Kennwort erforderlich wird** verwendet werden. Die Endbenutzer werden aufgefordert, geben Sie ein Kennwort ein, um ein Gerät zugreifen, die nicht aktiv, für die angegebene der Einstellung **Minuten nach der letzten vor dem Kennwort erforderlich ist war** .

  **Diese Einstellung gilt nur für 10 unter Windows Mobile Geräte.**
### Verschlüsselung
- **Verschlüsselung auf dem mobilen Gerät anfordern:** Legen Sie den **Ja,** um das Gerät verschlüsselt werden, um eine Verbindung mit Ressourcen erfordern.

## Integrität des Audiogeräts
- **Geräte als fehlerfrei zu meldende erforderlich:** Sie können festlegen, dass eine Regel erfordern, dass **10 unter Windows Mobile** Geräte als fehlerfrei in einer neuen oder vorhandenen Compliance-Richtlinien gemeldet werden müssen.  Wenn diese Einstellung aktiviert ist, werden Windows 10 Geräte über den Dienststatus Befähigungsnachweis Service (HAS) für die folgenden Datenpunkte ausgewertet:
  -  **BitLocker aktiviert ist:** Wenn BitLocker aktiviert ist, kann das Gerät zum Schützen von Daten, die auf das Laufwerk vor unbefugtem Zugriff gespeichert sind, wenn das System deaktiviert ist oder zum Ruhezustand wechselt. Der BitLocker verschlüsselt alle Daten, die auf dem Windows-Betriebssystem Datenträger gespeichert. BitLocker verwendet das TPM zum Schutz der Windows-Betriebssystem und Benutzerdaten und wird sichergestellt, dass es sich bei ein Computer nicht manipuliert wurde, auch wenn es unbeaufsichtigten, verloren oder gestohlen offen steht. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM die Verschlüsselung Tasten sperren, die die Daten zu schützen. Daher werden das TPM im Zustand des Computers überprüft wurde die Tasten, nicht zugegriffen
  -  **Codeintegrität aktiviert ist:** Integrität des Codes ist ein Feature, das die Integrität einer Datei oder Systemdienst jedes Mal überprüft, wenn es in den Speicher geladen wird. Integrität des Codes erkennt, ob in den Kernel eine nicht signierte Treiber oder im externen System Datei geladen wird, oder ob eine Systemdatei durch Schadsoftware geändert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.
  - **Secure Boot aktiviert ist:** Wenn Secure Boot aktiviert ist, wird für das System erzwungen, einem Factory vertrauenswürdige Zustand zu starten. Auch bei aktiviertem Secure Boot müssen die Hauptkomponenten zum Starten des Computers verwendet richtige cryptographic Signaturen, die die Organisation als vertrauenswürdig eingestuft werden, die das Gerät gefertigt. Die UEFI Firmware wird dadurch überprüft, bevor sie den Computer starten können. Wenn Sie alle Dateien manipuliert wurden, startet unterbrechen seine Signatur, das System nicht.

  Informationen über die Funktionsweise des Diensts HAS finden Sie unter [Dienststatus Befähigungsnachweis CSP](https://msdn.microsoft.com/library/dn934876.aspx).
##  Eigenschaft des Audiogeräts
- **Minimum OS erforderlich:** Wenn ein Gerät den OS Version Mindestanforderungen nicht erfüllt, wird er nicht als kompatible gemeldet.
    Eine Verknüpfung mit Informationen zum upgrade wird angezeigt. Die Endbenutzer können Geräts upgrade, nach denen sie Unternehmensressourcen zugreifen können.

- **Zulässige maximale Betriebssystemversion:** Wenn ein Gerät später als den in der Regel eine Version des Betriebssystems verwendet wird, Zugriff auf Unternehmensressourcen ist gesperrt, und der Benutzer wird aufgefordert, wenden Sie sich an ihre IT-Administrator. Bis es eine Änderung in der Regel ist, die die Version des Betriebssystems zulässt, kann diese Gerät Zugriff auf Unternehmensressourcen verwendet werden.


## Compliance-Richtlinien für Windows-PCs
Die Einstellungen, die in diesem Abschnitt werden auf Windows-PCs unterstützt.
## Sicherheit Systemeinstellungen
### Kennwort
- **Kennwort Mindestlänge:** – auf Windows 8.1 unterstützt.

  Geben Sie die minimale Anzahl von Ziffern oder Zeichen, die das Kennwort des Benutzers enthalten muss.

  Für Geräte, die mit einem Microsoft-Account zugegriffen werden, tritt die Compliance-Richtlinien ordnungsgemäß ausgewertet, wenn **Minimale Kennwortlänge** größer als 8 Zeichen ist oder wenn **minimale Anzahl von Zeichen legt** mehr als zwei Zeichen.

- **Kennworttyp erforderlich:** – unterstützte auf Windows RT, Windows RT 8.1 und Windows 8.1

  Angeben, ob Benutzer eine **alphanumerisch**oder einer **numerischen** Kennwort erstellen müssen.

- **Minimale Anzahl von Zeichensätzen:** – auf Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt. Wenn **Kennworttyp erforderlich** in **alphanumerischen**festgelegt ist, gibt diese Einstellung die minimale Anzahl von Zeichensätzen, die das Kennwort enthalten muss. Die vier Zeichen sind:
  -   Kleinbuchstaben
  -   Großbuchstaben
  -   Symbole
  -   Zahlen: Festlegen von eine höhere Anzahl für diese Einstellung benötigen Benutzer Kennwörter erstellen, die komplexere sind.

  Für Geräte, die mit einem Microsoft-Account zugegriffen werden, tritt die Compliance-Richtlinien ordnungsgemäß ausgewertet wird, ist **das Kennwort Mindestlänge** größer als 8 Zeichen oder **legt minimale Anzahl von Zeichen** mehr als 2 Zeichen ist.
- **Minuten nach der letzten vor dem Kennwort erforderlich ist:** – unterstützte auf Windows RT, Windows RT 8.1 und Windows 8.1

  Geben Sie im Leerlauf, der Benutzer das Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):** -unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

  Wählen Sie die Anzahl der Tage, bevor das Kennwort des Benutzers läuft ab und sie müssen einen neuen erstellen.

- **Kennwortverlauf Denken Sie daran:** – auf Windows RT, Windows 8.1 und Windows RT unterstützt.

  Verwenden Sie diese Einstellung in Verbindung mit **zu verhindern, dass Wiederverwendung von vorherigen Kennwörter** zu verhindern, dass den Benutzer zuvor verwendete Kennwörter erstellen.
- **Zu verhindern, dass Wiederverwendung von vorherigen Kennwörter:** – unterstützte Windows RT, Windows RT 8.1 und Windows 8.1

  Wenn **Kennwortverlauf Denken Sie daran:** ist ausgewählt haben, geben Sie die Anzahl der zuvor verwendete Kennwörter, die wieder verwendet werden kann.

## Integrität des Audiogeräts
- **Erfordern Geräte als fehlerfrei zu meldende:** – auf Windows-10-Geräten unterstützt.
Sie können eine Regel, um festzulegen, dass Windows 10 Geräte gemeldet werden müssen als fehlerfrei festlegen, in der neuen oder vorhandenen Compliance-Richtlinien.  Wenn diese Einstellung aktiviert ist, werden Windows 10 Geräte über den Dienststatus Befähigungsnachweis Service (HAS) für die folgenden Datenpunkte ausgewertet:
  -  **BitLocker aktiviert ist:** Wenn BitLocker aktiviert ist, kann das Gerät zum Schützen von Daten, die auf das Laufwerk vor unbefugtem Zugriff gespeichert sind, wenn das System deaktiviert ist oder zum Ruhezustand wechselt. Der BitLocker verschlüsselt alle Daten, die auf dem Windows-Betriebssystem Datenträger gespeichert. BitLocker verwendet das TPM zum Schutz der Windows-Betriebssystem und Benutzerdaten und wird sichergestellt, dass es sich bei ein Computer nicht manipuliert wurde, auch wenn es unbeaufsichtigten, verloren oder gestohlen offen steht. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM die Verschlüsselung Tasten sperren, die die Daten zu schützen. Daher werden das TPM im Zustand des Computers überprüft wurde die Tasten, nicht zugegriffen
  -  **Codeintegrität aktiviert ist:** Integrität des Codes ist ein Feature, das die Integrität einer Datei oder Systemdienst jedes Mal überprüft, wenn es in den Speicher geladen wird. Integrität des Codes erkennt, ob in den Kernel eine nicht signierte Treiber oder im externen System Datei geladen wird, oder ob eine Systemdatei durch Schadsoftware geändert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.
  - **Secure Boot aktiviert ist:** Wenn Secure Boot aktiviert ist, wird für das System erzwungen, einem Factory vertrauenswürdige Zustand zu starten. Auch bei aktiviertem Secure Boot müssen die Hauptkomponenten zum Starten des Computers verwendet richtige cryptographic Signaturen, die die Organisation als vertrauenswürdig eingestuft werden, die das Gerät gefertigt. Die UEFI Firmware wird dadurch überprüft, bevor sie den Computer starten können. Wenn Sie alle Dateien manipuliert wurden, startet unterbrechen seine Signatur, das System nicht.
  - **Early-Launch-Modul aktiviert ist:** Frühestes Launch Anti-Schadsoftware (ELAM) bietet Schutz für Computer in Ihrem Netzwerk aus, und beim start vor Initialisierung Drittanbieter-Treiber.

  Informationen über die Funktionsweise des Diensts HAS finden Sie unter [Dienststatus Befähigungsnachweis CSP](https://msdn.microsoft.com/library/dn934876.aspx).

## Eigenschaft des Audiogeräts
- **Minimum OS erforderlich:** – auf Windows 8.1 und Windows 10 unterstützt.

  Geben Sie die Anzahl der Haupt.neben.Build hier. Die Versionsnummer muss die Version, die zurückgegeben werden, indem Sie den Befehl Winver entsprechen.

  Wenn ein Gerät hat eine frühere Version, dass die angegebene OS Version als gemeldet ist nicht kompatibel. Eine Verknüpfung mit Informationen zum upgrade wird angezeigt. Die Endbenutzer können Geräts upgrade, nach denen sie Unternehmensressourcen zugreifen können.

- **Zulässige maximale Betriebssystemversion:** – auf Windows 8.1 und Windows 10 unterstützt.

  Wenn ein Gerät später als den in der Regel eine Version des Betriebssystems verwendet wird, Zugriff auf Unternehmensressourcen ist gesperrt, und der Benutzer wird aufgefordert, wenden Sie sich an ihre IT-Administrator. Bis es eine Änderung in der Regel ist, die die Version des Betriebssystems zulässt, kann diese Gerät Zugriff auf Unternehmensressourcen verwendet werden.

Um finden die Version des Betriebssystems für das **Minimum OS erforderlich**, und **zulässige maximale Betriebssystemversion** Einstellungen verwenden, führen Sie den Befehl **Winver** über die Befehlszeile. Der Befehl Winver gibt die gemeldete Version des Betriebssystems.
- Windows 8.1 PCs Rückkehr einer Version **6.3**.    Wenn die Regel für OS Version Windows 8.1 für Windows festgelegt ist, wird das Gerät als nicht kompatible gemeldet, auch wenn das Gerät Windows 8.1 hat.
- PCs 10 Windows ausführen, sollte die Version als "10.0" + OS erstellen Anzahl den Befehl Winver zurückgegebene festgelegt werden. Beispielsweise könnte es ungefähr wie folgt 10.0.10586.
> ![CA_Win10OSVersion](./media/ca_win10-os-version.png)
