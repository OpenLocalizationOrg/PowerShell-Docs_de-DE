---
title: Volumen gekauft iOS-apps verwalten | Microsoft Intune
description: Verwenden Sie Intune zum Verwalten von apps dieser Sie gekauften Menge von Apple durch Importieren der Lizenzinformationen aus dem app Store, nachverfolgen, wie viele Lizenzen Sie verwendet haben und verhindern, dass Sie der Installation von mehr Kopien der app, als Sie besitzen.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: a5c37c470f937c682d9138a636d1211f641da784
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Verwalten von iOS-apps, die Sie über ein Language Pack für Lautstärke--Programm mit Microsoft Intune erworben haben
IOS-app Store bietet Ihnen mehrere Lizenzen für eine app erwerben, die Sie in Ihrem Unternehmen ausführen möchten. Auf diese Weise können Sie mehrere Kopien erworbene apps nachverfolgen den Verwaltungsaufwand verringern.

Verwalten von apps, die Sie über dieses Programm erworben haben, durch die Lizenzinformationen aus der app Importieren von Microsoft Intune hilft speichern, nachverfolgen, wie viele Lizenzen Sie verwendet haben und verhindern, dass Sie der Installation von mehr Kopien der app als Sie eigene.

> [!Important]
> Derzeit weist Intune iOS Lautstärke Language Pack für-Programm für Business (VPP) app-Lizenzen für Benutzer und nicht Geräte. Daher müssen Benutzer, dessen Kennwort Apple-ID, um die app installieren eingeben.

## Verwalten von Volumen gekauft apps für iOS-Geräte
Sie kaufen mehrere Lizenzen für iOS-apps über das [Apple Lautstärke kaufen-Programm für Unternehmen](http://www.apple.com/business/vpp/). Dazu muss ein Apple VPP-Konto einrichten, aus der Apple-Website und das Apple VPP Token in Intune hochladen.  Dann können Sie synchronisieren Ihre Lautstärke Erwerbsinformationen mit Intune und Nachverfolgen Ihrer app Lautstärke gekauft verwenden.

## Bevor Sie beginnen
Bevor Sie beginnen, müssen Sie ein VPP Token aus Apple abrufen und diese mit Ihrem Konto Intune hochladen. Darüber hinaus, sollten Sie die folgenden vertraut machen:

* Jede Organisation kann nur eine VPP-Konto und Token verwenden.
* Nachdem Sie ein Konto Apple VPP Intune zugeordnet haben, nicht Sie später ein anderes Konto zugeordnet. Aus diesem Grund ist es wichtig, dass mehr als eine Person, die Details des Kontos hat, die Sie verwenden.
* Wenn Sie bereits ein VPP Token mit einem anderen Programm verwendet, müssen Sie eine neue zur Verwendung mit Intune generieren.
* Jedes Token gilt für ein Jahr.
* Standardmäßig synchronisiert Intune mit dem Dienst Apple VPP zweimal am Tag. Sie können jederzeit eine manuelle Synchronisierung starten.
* Nachdem Sie das Token VPP in Intune importiert haben, importieren Sie das gleiche Token nicht in einem beliebigen Gerät-Lösung. Auf diese Weise kann dazu führen, dass der Verlust der Lizenz Zuordnungs- und Benutzer Datensätze.
* Bevor Sie beginnen, iOS VPP mit Intune verwenden, entfernen Sie alle vorhandenen VPP Benutzerkonten erstellt mit anderen Anbietern des mobilen Geräts Management (MDM). Intune werden diese Benutzerkonten in Intune aus Sicherheitsgründen nicht synchronisiert. Intune werden nur Daten aus dem Dienst Apple VPP synchronisiert, die Intune erstellt.
* Sie können keine Geräte iOS VPP apps bereitstellen, die mit dem Gerät Registrierungs-Protokoll (DEP) registriert wurden.

## Zum Abrufen und Hochladen einer Apple VPP token

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), **Administrator** &gt; **iOS und Mac OS X** &gt; **Volume Language Pack für-Programm**.  

2.  Wählen Sie den Link **Apple VPP Konto** aus. Wenn Sie noch nicht geschehen ist, melden Sie sich für die Lautstärke kaufen-Programm für Business an. Nachdem Sie sich haben registriert, laden Sie das Apple VPP Token für Ihr Konto.

3.  Wählen Sie auf der Seite der Konsole Intune **Verwalten Apple Lautstärke Language Pack für-Programm (VPP)** aus, **das Token VPP hochladen**.

4.  Klicken Sie im Dialogfeld **Hochladen das VPP Token** Geben Sie oder fügen Sie den Namen der VPP und Ihrem Apple-ID, und wählen Sie dann auf **Hochladen**.

5.  Aktivieren Sie das Kontrollkästchen, um anzugeben, dass Sie wissen, dass Sie nicht an ein anderes VPP Konto später ändern und wählen Sie dann auf **Ja**, klicken Sie im Dialogfeld Warnung.

Auf der Seite **Volume Language Pack für-Programm** können Sie jetzt Informationen über das Apple VPP Token, wann sie zuletzt aktualisiert wurde, wenn es abläuft, oder wenn sie zuletzt mit Intune synchronisiert wurde, anzeigen.

Sie können die Daten frei, Apple mit Intune zu einem beliebigen Zeitpunkt durch Auswählen von **Jetzt synchronisieren**synchronisieren.

## Bereitstellen eine app Lautstärke erworben

1.  Wählen Sie in der [Microsoft-Intune-Verwaltungskonsole](https://manage.microsoft.com), **Apps** &gt; **Verwaltete Software** &gt; **apps Lautstärke gekauft**. Diese Liste zeigt alle apps, die vom Dienst Apple VPP synchronisiert wurden.

2.  Wählen Sie die app, die Sie bereitstellen, wählen **Bereitstellung verwalten**, und verwenden Sie dann die Anweisungen in der [apps bereitstellen, in Microsoft Intune](deploy-apps-in-microsoft-intune.md) Thema zu Ende hochladen, und der Bereitstellung der app möchten.

> [!TIP]
> Wählen Sie eine Aktion für die Bereitstellung von **erforderlich**aus. Verfügbare Installationen werden derzeit nicht unterstützt.

Wenn Sie die app als **erforderlich** Installation bereitstellen, verwendet jeder Benutzer, der die app installiert eine Lizenz aus.

Wenn Sie eine Lizenz freizugeben, müssen Sie die Bereitstellungsaktion zu **Deinstallieren**ändern. Nachdem Sie die app deinstalliert wurde, wird die Lizenz freigegeben werden.

Wenn ein Benutzer mit einem berechtigt Gerät eine VPP app installieren erstmals, werden sie aufgefordert, das Language Pack für Apple Volumen-Programm beizutreten. Sie müssen dies tun, bevor die app-Installation fortgesetzt wird.

> [!TIP]
> Schauen Sie sich die Statusspalte von **VPP Ausdrücke** , den Annahmestatus für jeden Benutzer anzuzeigen, denen die app bereitgestellt wurde.

Wenn keine weitere Lizenzen verfügbar sind, schlägt die Bereitstellung fehl.

## Zum Überwachen der apps Apple VPP in
Sie können überwachen, welche apps VPP bereitgestellt wurden, und wie viele Lizenzen verwendet werden, aus dem Arbeitsbereich **Apps** in die **Verwaltete Software** &gt; **Volume-Purchased Apps** -Knoten.

> [!TIP]
> Sie können auch die app **Filter** verwenden, um den Status der einzelnen Installationen app untersuchen.

### Siehe auch
[In Microsoft Intune apps bereitstellen](deploy-apps-in-microsoft-intune.md)
