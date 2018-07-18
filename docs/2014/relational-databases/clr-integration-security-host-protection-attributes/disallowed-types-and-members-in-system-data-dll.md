---
title: Unzulässige Typen und Member in "System.Data.dll" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 728de68145c4deb7b259c7b59687e29e960c822a
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353972"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Unzulässige Typen und Elemente in "System.Data.dll"
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Programmierung der Common Language-Integration (CLR) lässt die Verwendung von einem Typ oder Member, die eine `HostProtectionAttribute` , der angibt eine `System.Security.Permissions.HostProtectionResource` Enumeration mit einem Wert von `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, oder `UI`. In der folgenden Tabelle sind die Elemente und Typen der System.Data.dll-Assembly aufgeführt, deren Hostschutzattributwerte nicht zulässig sind.  
  
> [!NOTE]  
>  Diese Liste wurde von den unterstützten Assemblys generiert. Weitere Informationen finden Sie unter [unterstützt .NET Framework-Bibliotheken](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
 [Hostschutzattribute und Programmierung der CLR-Integration](host-protection-attributes-and-clr-integration-programming.md)   
 [Unzulässige Typen und Elemente in "Microsoft.VisualBasic.dll"](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Unzulässige Typen und Elemente in "mscorlib.dll"](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Unzulässige Typen und Elemente in "System.dll"](disallowed-types-and-members-in-system-dll.md)   
 [Unzulässige Typen und Elemente in „System.Core.dll“](disallowed-types-and-members-in-system-core-dll.md)  
  
  
