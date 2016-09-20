---
title: "Konflikte lösen Gruppenrichtlinienobjekt und Intune Richtlinie | Microsoft Intune"
description: "Informationen Sie zum Lösen von Konflikten zwischen Gruppenrichtlinien und Intune Konfigurationsrichtlinien."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: bf5198f352e71e818e56a5c757951da2575dea8b
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Lösen Sie (Gruppe Gruppenrichtlinienobjekt Objekte) und Microsoft Intune Richtlinie Konflikte
Intune verwendet Richtlinien zur Verfügung, die Ihnen helfen Einstellungen auf Windows-PCs verwalten. Beispielsweise können Sie eine Richtlinie Steuerelement Einstellungen für die Windows-Firewall auf PCs. Viele Intune Einstellungen ähneln Einstellungen, die Sie mit Windows-Gruppenrichtlinien konfigurieren können. Es ist jedoch möglich, dass von Zeit zu Zeit die beiden Methoden mit einem anderen in Konflikt stehen möglicherweise.

Wenn Konflikte auftreten, Vorrang Domäne Ebene Gruppenrichtlinien Intune Richtlinie, es sei denn, Sie dem Computer bei der Domäne anmelden kann. In diesem Fall wird Intune-Richtlinie auf dem Client-PC angewendet.

## Was zu tun ist, wenn Sie Gruppenrichtlinien verwenden
Stellen Sie sicher, dass keine Richtlinien, die Sie Anwenden von Gruppenrichtlinien verwaltet werden. Um Konflikte zu verhindern, können Sie eine oder mehrere der folgenden Methoden verwenden:

-   Verschieben Sie Ihre PCs mit einer Active Directory Organisationseinheit (Organisationseinheit), die keine Gruppenrichtlinieneinstellungen für die vor der Installation auf des Clients Intune angewendet haben. Sie können außerdem Gruppenrichtlinien Blockieren der Vererbung für OUs, die PCs enthalten Intune registriert, dem Sie nicht Gruppenrichtlinien anwenden möchten.

-   Verwenden eines Wertpapiers Gruppe Filters Gruppenrichtlinienobjekte nur an PCs einschränken, die nicht von Intune verwaltet werden.

-   Deaktivieren Sie oder entfernen Sie die Richtlinienobjekte gruppieren, die in Konflikt mit Intune-Richtlinien.

Weitere Informationen zu Active Directory und Windows-Gruppenrichtlinien finden Sie unter Windows Server-Dokumentation.

## Zum Filtern von vorhandener Gruppenrichtlinien, um Konflikte mit Intune Richtlinie zu vermeiden
Wenn Sie Gruppenrichtlinienobjekte, deren Einstellungen Konflikt mit Intune-Richtlinien ermittelt haben, können Sie Filter für die Sicherheit, um diese Objekte nur auf PCs einzuschränken, die nicht von Intune verwaltet werden.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Sie können nur diese Sicherheitsgruppen Gruppenrichtlinienobjekte anwenden, die im Bereich **Sicherheit zu filtern** , der die Gruppenrichtlinien-Verwaltungskonsole für eine ausgewählte Gruppenrichtlinienobjekt angegeben sind. Standardmäßig wird Gruppenrichtlinienobjekte auf *Authentifizierte Benutzer*anwenden.

-   Erstellen Sie eine neue Sicherheitsgruppe mit Computern und Benutzerkonten, die Sie nicht Intune verwalten möchten, in den **Active Directory-Benutzer und Computer** -Snap-in. Beispielsweise können Sie die Gruppe *Nicht In Microsoft Intune*nennen.

-   In der Gruppenrichtlinien-Verwaltungskonsole, klicken Sie auf die Registerkarte **Delegierung** für das ausgewählte Gruppenrichtlinienobjekt mit der rechten Maustaste um die entsprechende Berechtigungen zum **Lesen** und **Anwenden von Gruppenrichtlinien** Benutzern und Computer in der Sicherheitsgruppe Delegieren der neuen Sicherheitsgruppe. (**Gruppenrichtlinien anwenden von** Berechtigungen stehen im Dialogfeld " **Erweitert** ".)

-   Klicken Sie dann den neuen Sicherheit Gruppenfilter mit einem ausgewählten Gruppenrichtlinienobjekt anwenden, und den Standardfilter **Authentifizierte Benutzer** entfernen.

Die neue Sicherheitsgruppe muss als Registrierungs Intune Dienst Änderungen beibehalten werden.

### Siehe auch
[Verwalten von Windows-PCs mit Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
