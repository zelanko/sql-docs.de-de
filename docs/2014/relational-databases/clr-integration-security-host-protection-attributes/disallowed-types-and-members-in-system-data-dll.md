---
title: Unzulässige Typen und Member in "System. Data. dll" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4233bc1ddd98d6fe678d9d37f1acd7a4b66b687e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874367"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Unzulässige Typen und Elemente in "System.Data.dll"
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die CLR- `HostProtectionAttribute` Programmierung (Common Language Integration) lässt die Verwendung eines Typs oder Members mit einem nicht zu, das `System.Security.Permissions.HostProtectionResource` eine-Enumeration mit dem `ExternalProcessMgmt`Wert `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`,, **SharedState**, `Synchronization`oder `UI`angibt. In der folgenden Tabelle sind die Elemente und Typen der System.Data.dll-Assembly aufgeführt, deren Hostschutzattributwerte nicht zulässig sind.  
  
> [!NOTE]  
>  Diese Liste wurde von den unterstützten Assemblys generiert. Weitere Informationen finden Sie [unter Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Host Schutz Attribute und Programmierung der CLR-Integration](host-protection-attributes-and-clr-integration-programming.md)   
 [Unzulässige Typen und Member in "Microsoft. VisualBasic. dll"](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Unzulässige Typen und Member in "mscorlib. dll"](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Unzulässige Typen und Member in "System. dll"](disallowed-types-and-members-in-system-dll.md)   
 [Unzulässige Typen und Elemente in 'System.Core.dll'](disallowed-types-and-members-in-system-core-dll.md)  
  
  
