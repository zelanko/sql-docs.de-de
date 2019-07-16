---
title: Unzulässige Typen und Member in "System.Data.dll" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: 50f7f8aacfc61b55e969ea0d57f82d58e50e093b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028121"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Unzulässige Typen und Elemente in "System.Data.dll"
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Common Language-integrationsprogrammierung (CLR) lässt die Verwendung von einem Typ oder Member, die eine **HostProtectionAttribute** gibt, die eine **System.Security.Permissions.HostProtectionResource** Enumeration mit einem Wert von **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronisierung**, oder **UI**. In der folgenden Tabelle sind die Elemente und Typen der System.Data.dll-Assembly aufgeführt, deren Hostschutzattributwerte nicht zulässig sind.  
  
> [!NOTE]  
>  Diese Liste wurde von den unterstützten Assemblys generiert. Weitere Informationen finden Sie unter [unterstützt .NET Framework-Bibliotheken](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Typ oder Element|Hostschutzattribut-Wert(e)|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|Synchronization|  
  
## <a name="see-also"></a>Siehe auch  
 [Hostschutzattribute und Programmierung der CLR-Integration](../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Unzulässige Typen und Elemente in "Microsoft.VisualBasic.dll"](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Unzulässige Typen und Elemente in "mscorlib.dll"](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)   
 [Unzulässige Typen und Elemente in "System.dll"](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)   
 [Unzulässige Typen und Elemente in „System.Core.dll“](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
  
  
