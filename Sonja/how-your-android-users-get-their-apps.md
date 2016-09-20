---
title: Wie Android Benutzer ihre apps aufrufen | Microsoft Intune
description: "Methoden zum Bereitstellen von Android apps für Endbenutzer"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: d34bdc9839ea7785a429bc70cba15cc85da56ee1
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Wie ihre apps zu Ihrem Android-Benutzer erhalten
Verwenden Sie diese Informationen um zu verstehen, wie und wo Ihre Android Endbenutzer holen Sie sich die apps, die Sie verteilen über Microsoft Intune. Die Informationen kann für systemeigene Android-Geräten im Vergleich zu Samsung Knox Geräte abweichen.

## Android-Geräten einheitlichen (nicht Samsung Knox)

| App-Datentyp | Linie-von-branchenspezifische apps | Play Store-apps  |
| ------------- |-------------| -----|
| Verfügbare apps      | Benutzer Tippen Sie auf das Unternehmen-Portal **Installieren** . Eine Benachrichtigung angezeigt wird, welche Benutzer dann ' tippen, um die Installation zu starten. Nachdem die Installation erfolgreich ist, wird die Benachrichtigung entfernt. | Benutzer, tippen Sie auf die app im Portal für Unternehmen und werden entnommen zu einer app-Seite im Store wiedergeben, in dem sie die Installation zu starten können.|
| Erforderliche apps      | Benutzer sind eine Benachrichtigung, die sie zu beenden, nicht möglich, aufgeführt und gibt an, dass sie eine app installieren müssen. Benutzer Tippen Sie auf die Benachrichtigung, um die Installation zu starten. Nachdem die Installation erfolgreich ist, wird die Benachrichtigung entfernt.    | Benutzer sind eine Benachrichtigung, die sie zu beenden, nicht möglich, aufgeführt und gibt an, dass sie eine app installieren müssen. Benutzer, tippen Sie auf die Benachrichtigung und werden entnommen zu einer app-Seite im Store wiedergeben, in dem sie die Installation zu starten können. Nachdem die Installation erfolgreich ist, wird die Benachrichtigung entfernt. |

## Samsung Knox Android-Geräten

| App-Datentyp | Linie-von-branchenspezifische apps | Play Store-apps  |
| ------------- |-------------| -----|
| Verfügbare apps      | Benutzer Tippen Sie auf das Unternehmen-Portal **Installieren** . Die app-Installationen ohne weiteren Eingriff. | Benutzer, tippen Sie auf die app im Portal für Unternehmen und werden entnommen zu einer app-Seite im Store wiedergeben, in dem sie die Installation zu starten können.|
| Erforderliche apps      | Die app wird ohne Eingriff installiert.    | Benutzer sind eine Benachrichtigung, die sie zu beenden, nicht möglich, aufgeführt und gibt an, dass sie eine app installieren müssen. Benutzer, tippen Sie auf die Benachrichtigung und werden entnommen zu einer app-Seite im Store wiedergeben, in dem sie die Installation zu starten können. Nachdem die Installation erfolgreich ist, wird die Benachrichtigung entfernt. |

Apps können verwaltet oder nicht verwaltet, wie nachstehend beschrieben werden. Die Verfahren zum Bereitstellen von apps verwaltete gilt für alle Arten von Android-Geräten.

**Verwaltete apps** - Apps, die über Richtlinien und die verwaltet werden können, wurden "umgebrochen" von Intune oder mit Intune Mobile Anwendung Management (MAM) Software Development Kit (SDK) erstellt wurden. Diese apps können von Intune verwaltet werden, und Anwendungsrichtlinien angewendet werden können.

**Nicht verwaltete apps** - Apps, die über Richtlinien verwaltet werden können und die wurden nicht von Intune umgebrochen oder, die nicht im Intune MAM SDK einbinden. Anwendungsrichtlinien können nicht auf diese apps angewendet werden.

### Siehe auch
[Hinzufügen von apps mit Microsoft Intune](/intune/deploy-use/add-apps)
[wie Ihre Benutzer iOS Abrufen ihrer apps](how-your-ios-users-get-their-apps.md)
[wie die Windows-Benutzern ihre apps abrufen](how-your-windows-users-get-their-apps.md)
