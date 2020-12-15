---
description: sys.dm_xe_database_session_object_columns (Azure SQL-Datenbank)
title: sys.dm_xe_database_session_object_columns
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 0e6adc54-4d97-4ef0-bf4f-b4538d69f136
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-current
ms.custom: seo-dt-2019
ms.openlocfilehash: 92d1bb472d9d8369e116501b31f78dd2c5d3c8ff
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440705"
---
# <a name="sysdm_xe_database_session_object_columns-azure-sql-database"></a>sys.dm_xe_database_session_object_columns (Azure SQL-Datenbank)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  Zeigt die Konfigurationswerte für Objekte an, die an eine Sitzung gebunden sind.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 und spätere Versionen.|  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Hat eine n:1-Beziehung mit sys.dm_xe_database_sessions. Address. Lässt keine NULL-Werte zu.|  
|column_name|**nvarchar(60)**|Der Name des Konfigurationswerts. Lässt keine NULL-Werte zu.|  
|column_id|**int**|Die ID der Spalte. Ist eindeutig innerhalb des Objekts. Lässt keine NULL-Werte zu.|  
|column_value|**nvarchar (2048)**|Der konfigurierte Wert der Spalte. Lässt NULL-Werte zu.|  
|object_type|**nvarchar(60)**|Der Typ des Objekts.  Ist nicht Nullable.object_type ist eine von:<br /><br /> Ereignis<br /><br /> target|  
|object_name|**nvarchar(60)**|Der Name des Objekts, zu dem diese Spalte gehört. Lässt keine NULL-Werte zu.|  
|object_package_guid|**uniqueidentifier**|Die GUID des Pakets, das das Objekt enthält. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Beschreibung|Beziehung|  
|----------|--------|------------------|  
|dm_xe_database_session_object_columns dm_xe_database_session_object_columns.object_name<br /><br /> dm_xe_database_session_object_columns dm_xe_database_session_object_columns.object_package_guid|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|n:1|  
|dm_xe_database_session_object_columns dm_xe_database_session_object_columns.column_name<br /><br /> dm_xe_database_session_object_columns dm_xe_database_session_object_columns.column_id|sys.dm_xe_object_columns.name<br /><br /> sys.dm_xe_object_columns.column_id|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)  
  
  
