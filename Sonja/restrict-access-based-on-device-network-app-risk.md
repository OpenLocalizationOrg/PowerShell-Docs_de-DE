---
title: "Einschränken des Zugriffs für Mobilgeräte-Schutz mit | Microsoft Intune"
description: "Unternehmensressourcen basierend auf dem Gerät, Netzwerk und Anwendung Risiko schränken Sie Zugriff ein."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: f5e05805d363d43e067f7281ccf545823c83ecb3
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einschränken des Zugriffs auf Unternehmens Ressourcen basierend auf dem Gerät, Netzwerk- und Anwendung Risiko
Sie können Steuern des Zugriffs von mobilen Geräten auf Ressourcen des Unternehmens, basierend auf risikobewertung von Lookout, eine für Mobilgeräte Schutz (MTP) Lösung, die mit Microsoft Intune integriert ist durchgeführt. Das Risiko basiert auf werden, die der Lookout MTP-Dienst von Geräten für Betriebssystem (BS) Anfälligkeiten installierten bösartiger apps und Netzwerkprofile erfasst. Auf der Grundlage der risikobewertung können Sie dann bedingte Richtlinien in Intune konfigurieren und zulassen oder blockieren-Geräten, die nicht kompatibel aufgrund von Risiken auf diesen Geräten erkannt bestimmt wurden.  Dies ist aktuell nur für **Android** -Geräten mit **4.1 und höher** unterstützt und in Microsoft Intune registriert.  
## Werden dies welche Problem behoben?
Unternehmen und Organisationen müssen neu auftretender Risiken vertrauliche Daten gewarnt werden, die physische, app-basierten und Netzwerk-basierten Risiken sowie OS-Sicherheitslücken enthalten.

In der Vergangenheit haben Unternehmen und Organisationen eine aktive Position zum Schutz von PCs gegen Angriffen übernommen. Mobile ist ein neuer Bereich, der häufig ungeschützte wechselt. Obwohl die mobilen Plattformen integrierten Schutz des Betriebssystems mithilfe von Verfahren wie app Isolation und Neuware Consumer app Stores verfügen, weiterhin diese Plattformen anspruchsvolle Angriffen gefährdet. Wie mobile Geräte zunehmend von Mitarbeitern verwendeten arbeiten und Zugriff auf Informationen, die vertrauliche und wertvolle werden kann, müssen diese Geräte aus einer Vielzahl von anspruchsvolle Angriffen geschützt werden.

Intune bietet Ihnen die Möglichkeit zum Steuern des Zugriffs auf Unternehmensressourcen und Daten basierend auf risikobewertung, dass MTP Lösungen Lookout wie bereitstellt.

## Wie sich die Intune und Lookout für Mobilgeräte Schutz Unternehmensressourcen schützen?
Lookout des mobile-app (achten Arbeit), auf mobilen Geräten ausgeführt, erfasst Dateisystem, Netzwerkstapel und Gerät und Anwendung werden (sofern verfügbar) und an die Lookout für Mobilgeräte Schutz (MTP) Cloud-Dienst ein Aggregat Gerät Risiko für mobile Risiken zu berechnen. Sie können auch die Einstufung der Risiken Ebene für die Risiken in der Verwaltungskonsole MTP für Ihren Anforderungen entsprechend ändern.  
Die Compliance-Richtlinien in Intune enthält nun eine neue Regel für Lookout für Mobilgeräte Schutz, die auf die Lookout MTP risikobewertung basiert. Wenn diese Regel aktiviert ist, wertet Microsoft Intune klicken Sie dann die Gerät Einhaltung der Richtlinie, die Sie aktiviert.

Wenn das Gerät als nicht kompatibel mit der Compliance-Richtlinie bestimmt wird, blockiert Zugriff auf Ressourcen wie Exchange Online und SharePoint Online können bedingte Richtlinien verwenden. Wenn Access blockiert wird, sind die Endbenutzer im Lieferumfang einer Exemplarische Vorgehensweise besser kann das Problem beheben und auf Unternehmensressourcen zuzugreifen. Diese exemplarische Vorgehensweise wird durch Ausschau für Arbeit app gestartet.

## Beispielszenarien
Im folgenden werden einige häufige Szenarien:
### Bedrohung durch bösartige apps:
Wenn bösartiger apps, wie etwa Schadsoftware auf dem Gerät erkannt wird, können Sie solche Geräte aus sperren:
* Herstellen einer Verbindung mit corporate E-mail, bevor Sie das Risiko beheben.
* Synchronisieren von corporate Dateien, die mithilfe der OneDrive für Arbeit app aus.
* Zugreifen auf geschäftlich relevante apps.

**Access blockiert werden, wenn bösartiger apps erkannt werden:**
![Diagram, in dem bedingte Access Richtlinie Blockieren des Zugriffs aus, wenn das Gerät bestimmt ist aufgrund bösartiger apps auf dem Gerät nicht kompatibel sein](../media/mtp/malicious-apps-blocked.png)

**Gerät nicht mehr blockiert und kann auf Unternehmensressourcen zugreifen, wenn das Risiko diese beseitigt ist:**

![Diagram, in dem bedingte Zugriffsrichtlinie gewähren des Zugriffs beim Gerät bestimmt wird, nach Behebung kompatibel sein](../media/mtp/malicious-apps-unblocked.png)
### Risiko für Netzwerk:
Erkennen von Risiken mit Ihrem Netzwerk, wie Man in Mitte Angriffen und Einschränken des Zugriffs auf basierend auf dem Gerät Risiko WiFi-Netzwerke.

**Zugriff auf Netzwerk über WiFi blockiert:**
![Diagram, in dem bedingten Zugriff blockieren WiFi des Zugriffs basierend auf Netzwerk Risiken](../media/mtp/network-wifi-blocked.png)

**Zugriff auf die Behebung gewährt:**

![Diagram, in dem bedingten Zugriff zulassen des Zugriffs auf das Risiko Behebung](../media/mtp/network-wifi-unblocked.png)
### Risiko für Netzwerk, die (Verhindern des Zugriffs auf SharePoint Online):

Erkennen von Risiken mit Ihrem Netzwerk, wie Man in zweiter Angriffen und Synchronisierung corporate Dateien basierend auf dem Gerät Risiko verhindern.

**Access blockiert SharePoint Online basierend auf Netzwerk Bedrohung auf dem Gerät:**

![Diagram, in dem bedingten Zugriff blockieren Gerätezugriff auf SharePoint Online auf der Grundlage von Erkennung](../media/mtp/network-spo-blocked.png)


**Zugriff auf die Behebung gewährt:**

![Diagram, in dem bedingten Zugriff gewähren des Zugriffs nach das Risiko Netzwerk diese beseitigt ist](../media/mtp/network-spo-unblocked.png)

## Nächste Schritte
Hier sind die wichtigsten Schritte, die Sie ausführen müssen, um diese Lösung implementieren:
1.  [Richten Sie Ihr Abonnement mit Lookout für Mobilgeräte Schutz](set-up-your-subscription-with-lookout-mtp.md)
2.  [Aktivieren Sie in Intune Lookout MTP-Verbindung](enable-lookout-mtp-connection-in-intune.md)
3.  [Konfigurieren und Bereitstellen von Lookout für Arbeit Anwendung](configure-and-deploy-lookout-for-work-apps.md)
4.  [Konfigurieren von Compliance-Richtlinien](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Behandeln von Problemen mit Lookout-Integration](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)
