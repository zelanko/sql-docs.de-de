---
title: CLR-Hostschutzattribute (Common Language Runtime)
description: Die CLR stellt einen Mechanismus zum Kommentieren verwalteter APIs in .NET Framework mit Attributen wie SharedState, Synchronization und ExternalProcessMgmt bereit.
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 2aeaeb5d4eb06d6d632a59300225d01cc4376369
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488055"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Hostschutzattribute und Programmierung der CLR-Integration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die CLR (Common Language Runtime) stellt Mechanismen zur Verfügung, um verwaltete Anwendungsprogrammierschnittstellen (Application Programming Interfaces, APIs), die Teil von .NET Framework sind, mit Anmerkungen in Form von bestimmten Attributen zu versehen, die für einen Host der CLR, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], von Interesse sein können. Beispiele für solche Hostschutzattribute sind:  
  
-   **SharedState**, der angibt, ob die API die Möglichkeit zum Erstellen oder Verwalten eines freigegebenen Status (z. B. statische Klassenfelder) verfügbar macht.  
  
-   **Synchronisierung**, die angibt, ob die API die Möglichkeit bereitstellt, die Synchronisierung zwischen Threads durchzuführen.  
  
-   **ExternalProcessMgmt**, die angibt, ob die API eine Möglichkeit zum Steuern des Hostprozesses verfügbar macht.  
  
 Anhand dieser Attribute gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Liste mit Hostschutzattributen an, die in der gehosteten Umgebung von der Codezugriffssicherheit (CAS) nicht zugelassen werden. Die CAS-Anforderungen werden durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen von drei Berechtigungssätzen festgelegt: **SAFE**, **EXTERNAL_ACCESS**oder **UNSAFE**. Eine dieser drei Sicherheitsstufen wird angegeben, wenn die Assembly auf dem Server registriert wird, indem die **CREATE ASSEMBLY-Anweisung** verwendet wird. Code, der innerhalb der **SAFE-** oder EXTERNAL_ACCESS-Berechtigungssätze ausgeführt wird, muss bestimmte Typen oder Member vermeiden, auf die das **Attribut System.Security.Permissions.HostProtectionAttribute** angewendet wurde. **EXTERNAL_ACCESS** Weitere Informationen finden Sie unter [Erstellen von Einschränkungen für Assembly-](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) und [CLR-Integrationsprogrammmodelle](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 **Das HostProtectionAttribute** ist keine Sicherheitsberechtigung, sondern eine Möglichkeit, die Zuverlässigkeit zu verbessern, da es bestimmte Codekonstrukte identifiziert, entweder Typen oder Methoden, die der Host möglicherweise nicht zulässt. Die Verwendung von **HostProtectionAttribute** erzwingt ein Programmiermodell, das die Stabilität des Hosts schützt.  
  
## <a name="host-protection-attributes"></a>Hostschutzattribute  
 Hostschutzattribute geben die Typen oder Elemente an, die sich nicht für das Hostprogrammiermodell eignen und die folgenden Zuverlässigkeitsrisiken darstellen (ansteigende Gefährdung):  
  
-   Sie sind andernfalls ohne Auswirkung.  
  
-   Sie können zur Destabilisierung von serververwaltetem Benutzercode führen.  
  
-   Sie können zur Destabilisierung des Serverprozesses führen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]lehnt die Verwendung eines Typs oder Members mit einem **HostProtectionAttribute** ab, das eine **System.Security.Permissions.HostProtectionResource-Enumeration** mit dem Wert **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronization**oder **UI angibt.** Dies verhindert, dass Assemblys Elemente aufrufen, die die Freigabe des Zustands aktivieren, Synchronisierungen durchführen, einen Ressourcenverlust bei der Beendigung hervorrufen oder die Integrität des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozesses beeinträchtigen.  
  
### <a name="disallowed-types-and-members"></a>Unzulässige Typen und Member  
 In den folgenden Themen werden Typen und Member [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]identifiziert, deren **HostProtectionResource-Werte** von nicht zulässig sind.  
  
> [!NOTE]  
>  Die Listen in diesen Themen wurden von den unterstützten Assemblys generiert.  Weitere Informationen finden Sie unter [Unterstützte .NET Framework-Bibliotheken](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Unzulässige Typen und Elemente in "Microsoft.VisualBasic.dll"](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Listet die Typen und Elemente in Microsoft.VisualBasic.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in "mscorlib.dll"](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 Listet die Typen und Elemente in mscorlib.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in "System.dll"](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 Listet die Typen und Elemente in System.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in "System.Data.dll"](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 Listet die Typen und Elemente in System.Data.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in 'System.Core.dll'](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 Listet die Typen und Elemente in System.Core.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-Integrationscodezugriffssicherheit](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Einschränkungen des CLR-Integrationsprogrammierungsmodells](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Erstellen von Assemblys](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
