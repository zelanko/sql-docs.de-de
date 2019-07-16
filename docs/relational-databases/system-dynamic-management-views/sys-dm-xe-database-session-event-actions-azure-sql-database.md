---
title: Sys. dm_xe_database_session_event_actions (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 48519fd9-c7c2-434b-848d-ccbf41133fdd
author: MightyPen
ms.author: genemi
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 40587866b77e67947a1658c742ceed9f9e71b581
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090439"
---
# <a name="sysdmxedatabasesessioneventactions-azure-sql-database"></a>sys.dm_xe_database_session_event_actions (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu Ereignissitzungsaktionen zurück. Aktionen werden ausgeführt, wenn Ereignisse ausgelöst werden. Diese Verwaltungssicht aggregiert Statistiken über die Anzahl der Ausführungen einer Aktion und die Gesamtausführungszeit der Aktion.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und allen zukünftigen Versionen.|  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|action_name|**nvarchar(60)**|Der Name der Aktion. Lässt keine NULL-Werte zu.|  
|action_package_guid|**uniqueidentifier**|Die GUID für das Paket, das die Aktion enthält. Lässt keine NULL-Werte zu.|  
|event_name|**nvarchar(60)**|Der Name des Ereignisses, an das die Aktion gebunden ist Lässt keine NULL-Werte zu.|  
|event_package_guid|**uniqueidentifier**|Die GUID für das Paket, das das Ereignis enthält Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Beschreibung|Beziehung|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_event_actions.event_session_address|sys.dm_xe_database_sessions.address|n:1|  
|sys.dm_xe_database_session_event_actions.action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_database_session_events.event_package_guid|n:1|  
|sys.dm_xe_database_session_event_actions.event_name<br /><br /> sys.dm_xe_database_session_event_actions.event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|n:1|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
