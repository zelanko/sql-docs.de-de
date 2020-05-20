---
title: sys.dm_xe_database_session_targets
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 7f353e2a-f8fc-4366-97e4-aa1c49eadaf4
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: ac4b9b01b85b6c8b4832a591ba18654ac58e9125
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826689"
---
# <a name="sysdm_xe_database_session_targets-azure-sql-database"></a>sys.dm_xe_database_session_targets (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu Sitzungszielen zurück.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und zukünftige Versionen.|  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Hat eine n:1-Beziehung mit sys. dm_xe_database_sessions. Address. Lässt keine NULL-Werte zu.|  
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
|sys. dm_xe_database_session_targets. event_session_address|sys. dm_xe_database_sessions. Address|n:1|  
  
  
