---
title: "Einschränken des Zugriffs auf e-Mail-Beispielszenarien | Microsoft Intune"
description: Einige Beispielszenarien und wie sie mit bedingten Zugriff implementiert werden konnte.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 6b4751a67414a0b8a16886070b323a0296eeb829
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Einschränken des Zugriffs auf e-Mail mit Microsoft Intune: Beispielszenarien

## Verhindern Sie, dass Benutzer mit nicht kompatiblen Geräte auf Exchange Online zuzugreifen.
### Szenario-Anforderungen
- Alle Benutzer in Active Directory-Sicherheitsgruppe **Accounting** müssen für den Zugriff auf Exchange Online, wenn ihr Gerät nicht mit einer Richtlinie Compliance kompatibel ist, die Sie bereitgestellt blockiert werden.
- Wenn Sie alle Benutzer in dieser Gruppe vorhanden sind, deren Geräte nicht unterstützt, indem Sie werden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], sie den Zugriff auf das Gerät auf Exchange Online blockiert werden müssen.
- Benutzer in der **Finanzen** Active Directory-Sicherheitsgruppe muss von der Richtlinie ausgenommen, auch wenn sie auch in der Sicherheitsgruppe **Accounting** sind.

Konfigurieren Sie zu diesem Zweck einer bedingten Zugriffsrichtlinie für Exchange Online mit den folgenden Einstellungen:

-   Wählen Sie **bedingte Zugriffsrichtlinie aktivieren**.

- Wählen Sie die Plattformen, die Sie Access-apps mit modernen Authentifizierung zulassen möchten.
- Wählen Sie Exchange ActiveSync-apps, **Blockieren nicht kompatible Geräte auf von Microsoft Intune unterstützte Plattformen** und **Blockieren allen anderen Geräten auf Plattformen von Microsoft Intune nicht unterstützt.**
-   Wählen Sie im Abschnitt **Gruppe gezielte** unter **ausgewählte Sicherheitsgruppen** Benutzergruppe **"Buchhaltung"** ein.

-   Wählen Sie im Abschnitt **Gruppe Exempted** unter **ausgewählte Sicherheitsgruppen** **Finanzen** Benutzergruppe aus.


Entscheiden, welche Geräte Exchange Online zugreifen können, wird der folgende Fluss verwendet:

![Zugriff auf den Datenfluss Gerät](./media/ConditionalAccess8-5.png)

## Alle iOS-Geräte, die Exchange lokal zugreifen müssen von Intune verwaltet werden
### Szenario-Anforderungen
- Nur Geräte, die iOS ausgeführt werden sollte zulässige Zugriff auf Exchange lokal.
- Die Geräte müssen auch in Intune registriert werden und die Einhaltung von Vorschriften Richtlinienregeln entsprechen, bevor sie Zugriff auf Exchange verwendet werden können.

Konfigurieren Sie hierzu die folgenden bedingten Zugriffsrichtlinie für Exchange lokal mit den folgenden Einstellungen:

-   Wählen Sie die Option **Blockieren e-Mail-apps, den Zugriff auf lokale Exchange, wenn das Gerät nicht kompatibel oder nicht in Microsoft Intune registrierten**. Indem Sie diese Option auswählen, wird die bedingte Zugriffsrichtlinie aktiviert die setzt voraus, dass alle Geräte in Microsoft Intune registriert sein müssen, und die Konformität Richtlinienregeln entsprechen, bevor sie Exchange zugreifen können.

-   A: für erweiterte Exchange ActiveSync-Einstellungen zu erstellen

  -   Eine Ausnahme Plattform, die Geräte ermöglicht, die den Zugriff auf Exchange iOS ausgeführt werden.   

  -   Eine Standardregel, die angibt, wenn ein Gerät nicht über die Plattform Ausnahme sind Regel, den Zugriff auf Exchange gesperrt werden müssen. Mit dieser Regel wird sichergestellt, dass nicht ausgeführt iOS Geräte blockiert werden, den Zugriff auf Exchange.

Entscheiden, welche Geräte auf Exchange zugreifen können, wird der folgende Fluss verwendet:

![Zugriff auf den Datenfluss Gerät](./media/ConditionalAccess8-3.png)

## Android-Geräten können Exchange lokal zugreifen.
### Szenario-Anforderungen
- Alle Android-Geräten sollte blockiert den Zugriff auf Exchange.
- Alle anderen unterstützten Geräten auf Exchange zugreifen, solange sie von verwaltet werden [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Um dies zu erreichen, konfigurieren Sie eine bedingte Zugriffsrichtlinie für Exchange lokal mit den folgenden Einstellungen aus:

-   Wählen Sie die Option **Blockieren e-Mail-apps, den Zugriff auf lokale, wenn das Gerät nicht kompatibel ist Microsoft Intune registriert Exchange**. Wenn Sie diese Option auswählen, erfordern sie, dass jedem Gerät muss in Intune registriert sein und Einhaltung von der Richtlinie Richtlinien.

- A: für erweiterte Exchange ActiveSync-Einstellungen zu erstellen
  -   Plattform-Ausnahme, die Geräte, die Android ausgeführt werden blockiert, den Zugriff auf Exchange. Mit dieser Regel wird sichergestellt, dass Android-Geräten Zugriff auf Exchange verwendet werden können.

  -   Standardregel, die angibt, wenn ein Gerät nicht durch andere Regeln abgedeckt ist es dürfen, Exchange zugreifen. Mit dieser Standardregel stellt sicher, dass Geräte Plattformen als Android ausgeführt, jedoch von Microsoft Intune unterstützt Zugriff auf Exchange verwendet werden können. Sie müssen jedoch in Intune registriert und Einhaltung von der Richtlinie Richtlinien.

Der folgende Fluss wird verwendet, um die entscheiden, welche Geräte auf Exchange zugreifen können:

![Zugriff auf den Datenfluss Gerät](./media/ConditionalAccess8-4.png)
