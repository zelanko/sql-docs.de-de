---
title: Common Language Runtime (CLR)-Host Schutz Attribute
description: Die CLR bietet einen Mechanismus zum kommentieren verwalteter APIs in der .NET Framework mit Attributen wie SharedState, Synchronisierung und ExternalProcessMgmt.
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488055"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Hostschutzattribute und Programmierung der CLR-Integration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die CLR (Common Language Runtime) stellt Mechanismen zur Verfügung, um verwaltete Anwendungsprogrammierschnittstellen (Application Programming Interfaces, APIs), die Teil von .NET Framework sind, mit Anmerkungen in Form von bestimmten Attributen zu versehen, die für einen Host der CLR, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], von Interesse sein können. Beispiele für solche Hostschutzattribute sind:  
  
-   **SharedState**: gibt an, ob die API die Fähigkeit zur Erstellung oder Verwaltung eines freigegebenen Zustands (z. b. statische Klassen Felder) verfügbar macht.  
  
-   **Synchronisierung**, die angibt, ob die API die Möglichkeit zur Synchronisierung zwischen Threads bereitstellt.  
  
-   **ExternalProcessMgmt**, das angibt, ob die API eine Möglichkeit zur Steuerung des Host Prozesses bereitstellt.  
  
 Anhand dieser Attribute gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Liste mit Hostschutzattributen an, die in der gehosteten Umgebung von der Codezugriffssicherheit (CAS) nicht zugelassen werden. Die CAS-Anforderungen werden durch einen von drei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Berechtigungs Sätzen angegeben: " **Safe**", " **EXTERNAL_ACCESS**" oder " **unsicher**". Eine dieser drei Sicherheitsstufen wird angegeben, wenn die Assembly mithilfe der **Create Assembly** -Anweisung auf dem Server registriert wird. Code, der innerhalb der **Safe** -oder **EXTERNAL_ACCESS** -Berechtigungs Sätze ausgeführt wird, muss bestimmte Typen oder Member vermeiden, für die das **System. Security. Berechtigungs Attribut-Attribut (System. Security.** Weitere Informationen finden Sie unter [Erstellen einer Assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) und [Einschränkungen für das Programmiermodell von CLR-Integration](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 Das **Host Schutz Attribut** ist keine Sicherheits Berechtigung, sondern eine Möglichkeit, die Zuverlässigkeit zu verbessern, da es bestimmte Codekonstrukte identifiziert, entweder Typen oder Methoden, die der Host möglicherweise nicht zulässt. Die Verwendung von **Hostschutzattribute** erzwingt ein Programmiermodell, mit dem die Stabilität des Hosts geschützt wird.  
  
## <a name="host-protection-attributes"></a>Hostschutzattribute  
 Hostschutzattribute geben die Typen oder Elemente an, die sich nicht für das Hostprogrammiermodell eignen und die folgenden Zuverlässigkeitsrisiken darstellen (ansteigende Gefährdung):  
  
-   Sie sind andernfalls ohne Auswirkung.  
  
-   Sie können zur Destabilisierung von serververwaltetem Benutzercode führen.  
  
-   Sie können zur Destabilisierung des Serverprozesses führen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]lässt die Verwendung eines Typs oder Members mit einem **Hostschutzattribute** , das ein System angibt, nicht zu **. Security. Berechtigungs-und hostschutzressourcenenumeration** mit einem Wert von **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronisierung**oder **UI**. Dies verhindert, dass Assemblys Elemente aufrufen, die die Freigabe des Zustands aktivieren, Synchronisierungen durchführen, einen Ressourcenverlust bei der Beendigung hervorrufen oder die Integrität des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozesses beeinträchtigen.  
  
### <a name="disallowed-types-and-members"></a>Unzulässige Typen und Member  
 In den folgenden Themen werden Typen und Member identifiziert, deren **hostschutzressourcenwerte** durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht zulässig sind.  
  
> [!NOTE]  
>  Die Listen in diesen Themen wurden von den unterstützten Assemblys generiert.  Weitere Informationen finden Sie [unter Supported .NET Framework Libraries](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
 [Code Zugriffssicherheit für die CLR-Integration](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Einschränkungen für das Programmiermodell von CLR-Integration](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Erstellen von Assemblys](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
