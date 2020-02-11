---
title: Host Schutz Attribute und Programmierung der CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 68f1f114002ab0ef38c7565a523723a06958048d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874344"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Hostschutzattribute und Programmierung der CLR-Integration
  Die CLR (Common Language Runtime) stellt Mechanismen zur Verfügung, um verwaltete Anwendungsprogrammierschnittstellen (Application Programming Interfaces, APIs), die Teil von .NET Framework sind, mit Anmerkungen in Form von bestimmten Attributen zu versehen, die für einen Host der CLR, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], von Interesse sein können. Beispiele für solche Hostschutzattribute sind:  
  
-   
  `SharedState`, das angibt, ob die API die Fähigkeit zur Verfügung stellt, einen Freigabezustand (z. B. statische Klassenfelder) zu erstellen oder zu verwalten.  
  
-   
  `Synchronization`, das angibt, ob die API die Fähigkeit zur Verfügung stellt, die Synchronisierung zwischen Threads auszuführen.  
  
-   
  `ExternalProcessMgmt`, das angibt, ob die API eine Möglichkeit zur Kontrolle des Hostprozesses zur Verfügung stellt.  
  
 Anhand dieser Attribute gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Liste mit Hostschutzattributen an, die in der gehosteten Umgebung von der Codezugriffssicherheit (CAS) nicht zugelassen werden. Die CAS-Anforderungen werden von einem von drei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Berechtigungssätzen angegeben: `SAFE`, `EXTERNAL_ACCESS` oder `UNSAFE`. Eine dieser drei Sicherheitsebenen wird beim Registrieren der Asssembly auf dem Server mit der `CREATE ASSEMBLY`-Anweisung festgelegt. Bei der Codeausführung innerhalb der Berechtigungssätze `SAFE` oder `EXTERNAL_ACCESS` müssen bestimmte Typen oder Elemente, auf die das `System.Security.Permissions.HostProtectionAttribute`-Attribut angewendet wurde, vermieden werden. Weitere Informationen finden Sie unter [Erstellen einer Assembly](../clr-integration/assemblies/creating-an-assembly.md) und [Einschränkungen für das Programmiermodell von CLR-Integration](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 Das `HostProtectionAttribute` ist keine Sicherheitsberechtigung, sondern eher eine Möglichkeit zur Verbesserung der Zuverlässigkeit, da es bestimmte Codekonstrukte (Typen oder Methoden) erkennt, die für den Host möglicherweise nicht zulässig sind. Die Verwendung des `HostProtectionAttribute` erzwingt ein Programmiermodell, mit dem die Stabilität des Hosts besser geschützt werden kann.  
  
## <a name="host-protection-attributes"></a>Hostschutzattribute  
 Hostschutzattribute geben die Typen oder Elemente an, die sich nicht für das Hostprogrammiermodell eignen und die folgenden Zuverlässigkeitsrisiken darstellen (ansteigende Gefährdung):  
  
-   Sie sind andernfalls ohne Auswirkung.  
  
-   Sie können zur Destabilisierung von serververwaltetem Benutzercode führen.  
  
-   Sie können zur Destabilisierung des Serverprozesses führen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]lässt die `HostProtectionAttribute` Verwendung eines Typs oder Members mit einem nicht zu, das eine- `System.Security.Permissions.HostProtectionResource` Enumeration mit dem Wert `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, `SharedState`, `Synchronization`oder `UI`angibt. Dies verhindert, dass Assemblys Elemente aufrufen, die die Freigabe des Zustands aktivieren, Synchronisierungen durchführen, einen Ressourcenverlust bei der Beendigung hervorrufen oder die Integrität des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozesses beeinträchtigen.  
  
### <a name="disallowed-types-and-members"></a>Unzulässige Typen und Member  
 In den folgenden Themen sind Typen und Elemente aufgeführt, deren `HostProtectionResource`-Werte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht zulässig sind.  
  
> [!NOTE]  
>  Die Listen in diesen Themen wurden von den unterstützten Assemblys generiert.  Weitere Informationen finden Sie [unter Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Unzulässige Typen und Elemente in "Microsoft.VisualBasic.dll"](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Listet die Typen und Elemente in Microsoft.VisualBasic.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in "mscorlib.dll"](disallowed-types-and-members-in-mscorlib-dll.md)  
 Listet die Typen und Elemente in mscorlib.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in "System.dll"](disallowed-types-and-members-in-system-dll.md)  
 Listet die Typen und Elemente in System.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in "System.Data.dll"](disallowed-types-and-members-in-system-data-dll.md)  
 Listet die Typen und Elemente in System.Data.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
 [Unzulässige Typen und Elemente in 'System.Core.dll'](disallowed-types-and-members-in-system-core-dll.md)  
 Listet die Typen und Elemente in System.Core.dll auf, deren Hostschutzattributwerte nicht zugelassen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Code Zugriffssicherheit für die CLR-Integration](../clr-integration/security/clr-integration-code-access-security.md)   
 [Einschränkungen für das Programmiermodell von CLR-Integration](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Erstellen von Assemblys](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
