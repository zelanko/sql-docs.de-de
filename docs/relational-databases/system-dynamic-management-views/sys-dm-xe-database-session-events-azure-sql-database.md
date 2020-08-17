---
description: sys.dm_xe_database_session_events (Azure SQL-Datenbank)
title: sys.dm_xe_database_session_events
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 9e985a19-f93f-4c56-b644-12c529298011
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-lt-2019
ms.openlocfilehash: 06de1e7657008f924e80427b3e9bfa04eae225a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88323056"
---
# <a name="sysdm_xe_database_session_events-azure-sql-database"></a>sys.dm_xe_database_session_events (Azure SQL-Datenbank)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Gibt Informationen zu Sitzungsereignissen zurück. Ereignisse sind einzelne Ausführungspunkte. Auf Ereignisse können Prädikate angewendet werden, damit sie nicht mehr ausgelöst werden, wenn sie nicht die erforderlichen Informationen enthalten.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und spätere Versionen.|  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|event_name|**nvarchar(60)**|Der Name des Ereignisses, an das eine Aktion gebunden ist. Lässt keine NULL-Werte zu.|  
|event_package_guid|**uniqueidentifier**|Die GUID für das Paket, das das Ereignis enthält. Lässt keine NULL-Werte zu.|  
|event_predicate|**nvarchar (2048)**|Eine XML-Darstellung der Prädikatstruktur, die auf das Ereignis angewendet wird. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|An|Beziehung|  
|----------|--------|------------------|  
|sys. dm_xe_database_session_events. event_session_address|sys. dm_xe_database_sessions. Address|n:1|  
|sys. dm_xe_database_session_events. event_package_guid, sys. dm_xe_database_session_events. event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|n:1|  
  
  
