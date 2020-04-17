---
title: Unzulässige Typen und Member in System.Data.dll | Microsoft Docs
descriptions: SQL Server CLR programming disallows a type or member with some values for the HostProtectionResource enum. This article lists System.Data.dll disallowed values.
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
ms.openlocfilehash: a8f875476d5509c538b2fb47575b94369a5e1186
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486868"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Unzulässige Typen und Elemente in "System.Data.dll"
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Die Common Language Integration (CLR)-Programmierung verbietet die Verwendung eines Typs oder Members mit einem **HostProtectionAttribute,** das eine **System.Security.Permissions.HostProtectionResource-Enumeration** mit dem Wert **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronization**oder **UI**angibt. In der folgenden Tabelle sind die Elemente und Typen der System.Data.dll-Assembly aufgeführt, deren Hostschutzattributwerte nicht zulässig sind.  
  
> [!NOTE]  
>  Diese Liste wurde von den unterstützten Assemblys generiert. Weitere Informationen finden Sie unter [Unterstützte .NET Framework-Bibliotheken](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
 [Host Protection-Attribute und CLR-Integrationsprogrammierung](../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Unzulässige Typen und Member in Microsoft.VisualBasic.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Unzulässige Typen und Member in mscorlib.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)   
 [Unzulässige Typen und Member in System.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)   
 [Unzulässige Typen und Elemente in 'System.Core.dll'](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
  
  
