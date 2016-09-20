
---
# erforderliche Metadaten

Titel: App bereitgestellt Profile | Microsoft Intune Beschreibung: Intune bietet Ihnen Tools, um die vorausschauende eine neue provisioning Profil Richtlinie Geräte bereitstellen, deren apps Ablauf nähern.
Schlüsselwörter: Author: Robstackmsft Manager: Angrobe ms.date: 07/19/2016 ms.topic: ms.prod Artikel: ms.service: Microsoft-Intune ms.technology: ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c

# optionale Metadaten

#ROBOTS:
#Zielgruppe:
#MS.DevLang:
MS.Reviewer: Mghadial ms.suite: Ems
#MS.tgt_pltfrm:
#MS.Custom:

---

# Verwenden von provisioning Profil Richtlinien mobile iOS um zu verhindern, dass Ihre apps läuft ab


Apple iOS Textzeile Geschäfts-apps, die auf iPhones und iPads bereitgestellt werden mit einer darin enthaltenen provisioning Profil und Code, der mit einem Zertifikat signiert ist erstellt wurden. Wenn die app ausgeführt wird, wird iOS bestätigt die Integrität des iOS-app und erzwingt Richtlinien, die durch die Bereitstellung Profil definiert sind. Die folgenden Validierungen Aktionen umgesetzt:

- **Integrität der Installation Datei** - iOS vergleicht des app Details mit dem Unternehmen des Zertifikats öffentlicher Schlüssel signieren. Wenn sie sich unterscheiden, des app Inhalten möglicherweise geändert haben, und die app nicht gestattet ist, führen.
- **Funktionen Durchsetzung** - iOS versucht, des app Funktionen aus der Enterprise-Bereitstellung Profil (keine einzelnen Entwickler provisioning Profile) erzwingen, die in der app-Installation (.ipa) enthalten sind.


Das Zertifikat, das Sie verwenden, um apps normalerweise melden Sie sich bei der Anmeldung Enterprise dauert nach drei Jahren. Jedoch läuft ab das provisioning Profil nach einem Jahr ein. Während das Zertifikat noch gültig ist, bietet Ihnen Intune Tools, um die vorausschauende eine neue provisioning Profil Richtlinie Geräte bereitstellen, deren apps Ablauf nähern.
Nach Ablauf des Zertifikats, müssen Sie die app erneut mit einem neuen Zertifikat anmelden und ein neues provisioning Profil mit dem Schlüssel des neuen Zertifikats einbetten.



## So finden Sie heraus, wenn eine Textzeile Business-app läuft ab

1. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), **Apps** > **Apps**.
2. Prüfen Sie in der Liste der apps die Spalte **Ablaufdatum** finden Sie das Ablaufdatum für die app aus. Sie können auch die Dropdownliste **Filter** festlegen, um **abgelaufen/zu abläuft** um nur die apps anzuzeigen, für die Sie abarbeiten müssen.

## So erstellen Sie eine iOS mobilen provisioning Profil Richtlinie


1. Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** > **Übersicht** > **Richtlinie hinzufügen**.
2. Wählen Sie im Dialogfeld **neue Richtlinie erstellen** , **iOS** > **Mobile Provisioning Profil Richtlinie**, und wählen Sie dann die **Richtlinie zu erstellen**.
3. Konfigurieren Sie auf der Registerkarte **Allgemein** die folgenden Werte ein:
    - **Namen** - Geben Sie einen Namen für diese mobilen provisioning Profil Richtlinie.
    - **Beschreibung** – Sie optional eine Beschreibung für die Richtlinie angeben.
    - **Profil Konfigurationsdatei** – klicken Sie auf **Importieren**, und wählen Sie dann einer Apple Mobile Konfiguration Profile-Datei (mit der Erweiterung **.mobileprovision**), dass Sie von der Apple Developer-Website heruntergeladen haben.
4. Wenn Sie fertig sind, wählen Sie die **Richtlinie speichern**.
5. Bringen Sie nun die Richtlinie auf die erforderlichen iOS-Geräte ein. Weitere Informationen finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).
