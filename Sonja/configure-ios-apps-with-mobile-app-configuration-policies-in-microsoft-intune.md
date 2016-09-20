---
title: "Verwenden von Richtlinien für iOS mobile-app-Konfiguration | Microsoft Intune"
description: "Verwenden von Richtlinien für mobile-app-Konfiguration in Intune Einstellungen angeben, die beim Ausführen der Benutzer einer app für iOS erforderlich sein können."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: c7fe00828108ac3f84e91a0eeb3ed4c344228588
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Konfigurieren von iOS-apps mit mobilen app Konfigurationsrichtlinien in Microsoft Intune
Verwenden Sie Richtlinien für mobile-app-Konfiguration in Microsoft Intune Einstellungen angeben, die beim Ausführen der Benutzer einer app erforderlich sein können. Eine app benötigen möglicherweise Benutzer angeben:

-   Eine benutzerdefinierte Port Zahl.

-   Spracheinstellungen.

-   Sicherheitseinstellungen.

-   Branding Einstellungen wie ein Firmenlogo.

Wenn Benutzer diese Einstellungen eingeben falsch, dies die Belastung für den Helpdesk erhöhen und die Leistung der Annahme neue apps kann.

Richtlinien für Mobile-app-Konfiguration helfen Ihnen diese Probleme beseitigen, mit deren Hilfe Sie diese Einstellungen für Benutzer in einer Richtlinie bereitstellen, bevor sie die app ausgeführt werden. Die Einstellungen werden dann automatisch bereitgestellt, und Benutzer keine Aktion ausführen müssen.

Stellen Sie diese Richtlinien nicht direkt an Benutzer und Geräte. Stattdessen Sie zuordnen eine Richtlinie mit einer app, und klicken Sie dann die app bereitstellen. Die Richtlinieneinstellungen werden verwendet werden, wenn die app überprüft für diese (normalerweise beim ersten Ausführen sind).

> [!TIP]
> Dieser Richtlinie ist aktuell nur bei Geräten mit dem iOS 8.0 verfügbar und höher. Die folgenden Arten von app-Installation unterstützt:
>
> -   **IOS-app aus dem app Store verwaltet**
> -   **App-Pakets für iOS**
>
> Weitere Informationen zu den Typen der app-Installation finden Sie unter [Bereitstellen von apps mit Microsoft Intune](deploy-apps.md).

## Konfigurieren einer Richtlinie für mobile-app-Konfiguration

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), die **Richtlinie** &gt; **Übersicht** &gt; **Richtlinie hinzufügen**.

2.  Klicken Sie in der Liste der Richtlinien erweitern Sie **iOS**, wählen Sie **Mobile-App-Konfiguration**, und wählen Sie die **Richtlinie erstellen**.

    > [!TIP]
    > Sie können nur benutzerdefinierte Einstellungen für diese Richtlinie Art konfigurieren. Empfohlene Einstellungen sind nicht verfügbar.

3.  Geben Sie im Abschnitt **Allgemein** der Seite **Richtlinie erstellen** einen Namen und optional eine Beschreibung für die Richtlinie für mobile-app-Konfiguration aus.

4.  Geben Sie im Abschnitt **Richtlinie für Mobile App-Konfiguration** auf der Seite im Feld oder fügen Sie eine XML-Eigenschaftenliste, die die Einstellungen für die app-Konfiguration gewünschte enthält. Das Format der XML-Eigenschaftenliste variieren je nach der app, die Sie konfigurieren. Ausführliche Informationen über die zu verwendende genaue Format wenden Sie sich an den Hersteller der app.

    > [!TIP]
    > Weitere Informationen zu XML-Eigenschaftenlisten finden Sie finden Sie unter [Grundlegendes zu XML-Eigenschaft](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) in der iOS Entwicklertools Bibliothek.

5.  Klicken Sie auf **Überprüfen** , um sicherzustellen, dass die XML-Daten, die Sie eingegeben in einer Liste gültige Eigenschaft ist.

    > [!IMPORTANT]
    > Wenn Sie **Überprüfen**klicken, Intune überprüft, ob die eingegebenen XML-Daten in einem gültigen Format. Es wird nicht überprüft, dass die Liste der XML-Eigenschaft mit der app funktionieren, dem sie zugeordnet ist.

6.  Wenn Sie fertig sind, klicken Sie auf **Richtlinie speichern**.

Die neue Richtlinie wird in den Knoten **Konfiguration-Richtlinien** angezeigt.

## Informationen zu den XML-Dateiformat

Intune unterstützt die folgenden Arten von Daten in einer Eigenschaftenliste:
    
- &lt;ganze Zahl&gt;
- &lt;Real&gt;
- &lt;Zeichenfolge&gt;
- &lt;Matrix&gt;
- &lt;dict&gt;
- &lt;WAHR /&gt; oder &lt;falsch /&gt;
     
Weitere Informationen zu Datentypen finden Sie unter [Informationen über Listen Eigenschaft](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) in der iOS Entwicklertools Bibliothek.

Darüber hinaus unterstützt Intune folgende token in der Eigenschaftenliste:
- \{\{UserPrincipalName\}\} -(Beispiel: **John@contoso.com**)
- \{\{Mail\}\} -(Beispiel: **John@contoso.com**)
- \{\{Partialupn\}\} -(Beispiel: **Jens**)
- \{\{AccountID\}\} -(Beispiel: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{Geräte-ID\}\} -(Beispiel: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{Benutzer-ID\}\} -(Beispiel: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{Benutzername\}\} -(Beispiel: **Max Mustermann**)
- \{\{Seriennummer\}\} -(Beispiel: **F4KN99ZUG5V2**) für iOS-Geräte
- \{\{serialnumberlast4digits\}\} -(Beispiel: **G5V2**) für iOS-Geräte
    
Die \{\{ und \}\} Zeichen von nur token Typen verwendet werden und nicht für andere Zwecke verwendet werden.

## Zuordnen einer mobilen app Konfigurationsrichtlinie mit einer app
Nachdem Sie eine mobile-app Konfigurationsrichtlinie erstellt haben, müssen Sie sie mit der app für iOS verknüpfen, die Sie die Einstellungen in der Konfigurationsrichtlinie anwenden möchten.

Führen Sie hierzu die Schritte zum Erstellen einer app-bereitstellungs in [Hinzufügen von apps für mobile Geräte in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) und [Bereitstellen-apps mit Microsoft Intune](deploy-apps-in-microsoft-intune.md)aus. Wenn Sie die **Mobile-App-Konfiguration** Seite des Assistenten erreicht haben, wählen Sie die Richtlinie, die Sie die app aus der Dropdownliste **Konfiguration-App-Richtlinie** zuordnen möchten.

Klicken Sie dann weiter bereitstellen und überwachen die app-Bereitstellung wie gewohnt.

Wenn Sie die bereitgestellte app auf einem Gerät ausgeführt wird, wird er mit den Einstellungen ausgeführt, die Sie in der mobilen app Konfigurationsrichtlinie konfiguriert.

> [!TIP]
> Wenn eine oder mehrere Konfigurationsrichtlinien für mobile-app in Konflikt stehen, wird weder Richtlinie erzwungen. Der Konflikt werden in der Intune-Verwaltungskonsole **Dashboard**gemeldet.

## Beispiel für eine XML-Datei für mobile-app-format

Wenn Sie eine Konfigurationsdatei mobile-app erstellen, können Sie mithilfe dieses Format eine oder mehrere der folgenden Werte angeben:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```
