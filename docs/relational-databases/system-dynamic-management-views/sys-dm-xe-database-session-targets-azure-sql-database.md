---
title: Sys. dm_xe_database_session_targets (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 7f353e2a-f8fc-4366-97e4-aa1c49eadaf4
author: MightyPen
ms.author: genemi
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 60d26d76f4d158799fe52e28be9927744ca98745
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090423"
---
# <a name="sysdmxedatabasesessiontargets-azure-sql-database"></a>sys.dm_xe_database_session_targets (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über Sitzungsziele zurück.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und allen zukünftigen Versionen.|  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Verfügt über eine n: 1 Beziehung mit sys.dm_xe_database_sessions.address aus. Lässt keine NULL-Werte zu.|  
|target_name|**nvarchar(60)**|Der Name des Ziels innerhalb einer Sitzung. Lässt keine NULL-Werte zu.|  
|target_package_guid|**uniqueidentifier**|Die GUID des Pakets, das das Ziel enthält Lässt keine NULL-Werte zu.|  
|execution_count|**bigint**|Die Häufigkeit, mit der das Ziel für die Sitzung ausgeführt wurde. Lässt keine NULL-Werte zu.|  
|execution_duration_ms|**bigint**|Die gesamte Zeit in Millisekunden, für die das Ziel ausgeführt wurde. Lässt keine NULL-Werte zu.|  
|target_data|**nvarchar(max)**|Die Daten, die das Ziel beibehält, z. B. Ereignisaggregationsinformationen. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Beschreibung|Beziehung|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_targets.event_session_address|sys.dm_xe_database_sessions.address|n:1|  
  
  
