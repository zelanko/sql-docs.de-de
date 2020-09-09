---
description: sys.dm_xe_database_session_event_actions (Azure SQL-Datenbank)
title: sys.dm_xe_database_session_event_actions
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 48519fd9-c7c2-434b-848d-ccbf41133fdd
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-lt-2019
ms.openlocfilehash: 750bfeae27269acf4b8d3fb1e64b7f8944f8ebbe
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546419"
---
# <a name="sysdm_xe_database_session_event_actions-azure-sql-database"></a>sys.dm_xe_database_session_event_actions (Azure SQL-Datenbank)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Gibt Informationen zu Ereignissitzungsaktionen zurück. Aktionen werden ausgeführt, wenn Ereignisse ausgelöst werden. Diese Verwaltungssicht aggregiert Statistiken über die Anzahl der Ausführungen einer Aktion und die Gesamtausführungszeit der Aktion.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und zukünftige Versionen.|  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Lässt keine NULL-Werte zu.|  
|action_name|**nvarchar(60)**|Der Name der Aktion Lässt keine NULL-Werte zu.|  
|action_package_guid|**uniqueidentifier**|Die GUID für das Paket, das die Aktion enthält. Lässt keine NULL-Werte zu.|  
|event_name|**nvarchar(60)**|Der Name des Ereignisses, an das die Aktion gebunden ist Lässt keine NULL-Werte zu.|  
|event_package_guid|**uniqueidentifier**|Die GUID für das Paket, das das Ereignis enthält Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|From|To|Beziehung|  
|----------|--------|------------------|  
|sys. dm_xe_database_session_event_actions. event_session_address|sys. dm_xe_database_sessions. Address|n:1|  
|sys. dm_xe_database_session_event_actions. action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> sys. dm_xe_database_session_events. event_package_guid|n:1|  
|sys. dm_xe_database_session_event_actions. event_name<br /><br /> sys. dm_xe_database_session_event_actions. event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
