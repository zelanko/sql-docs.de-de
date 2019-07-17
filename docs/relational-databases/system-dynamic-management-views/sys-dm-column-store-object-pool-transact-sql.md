---
title: Sys.dm_column_store_object_pool (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a8a58ca7-0a7d-4786-bfd9-e8894bd345dd
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 83369736ee18c36b3967bbbd129e0fd64574a2ed
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265991"
---
# <a name="sysdmcolumnstoreobjectpool-transact-sql"></a>Sys.dm_column_store_object_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Gibt die Anzahl verschiedener Arten von Objekt Pool arbeitsspeichernutzung für columnstore-Index-Objekten.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|Die ID der Datenbank. Dies ist eindeutig innerhalb einer Instanz von SQL Server-Datenbank oder eine Azure SQL-Datenbank-Server. |  
|`object_id`|`int`|ID des Objekts. Das Objekt ist eines der object_types auf. | 
|`index_id`|`int`|ID des columnstore-Indexes.|  
|`partition_number`|`bigint`|Auf 1 basierende Partitionsnummer im Index oder Heap. Jede Tabelle oder Sicht verfügt über mindestens eine Partition aus.| 
|`column_id`|`int`|ID der columnstore-Spalte. Dies ist NULL für DELETE_BITMAP.| 
|`row_group_id`|`int`|Die ID der Zeilengruppe.|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT - ein Spaltensegment. `object_id` ist die Segment-ID. Ein Segment werden alle Werte für eine Spalte innerhalb einer Zeilengruppe gespeichert. Wenn eine Tabelle 10 Spalten haben, stehen beispielsweise 10 spaltensegmente pro Zeilengruppe. <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY – ein globaler Wörterbuch, das Informationen für alle spaltensegmente in der Tabelle enthält.<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY – ein lokales Wörterbuch, das eine Spalte zugeordnet.<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY – eine andere Darstellung der globalen Wörterbuch. Dies stellt eine umgekehrte Nachschlagen des Werts an Dictionary_id bereit. Zum Erstellen von komprimierte Segmente als Teil der Tuple Mover "oder" Massenladen verwendet.<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP - Löscht ein Bitmuster, mit dem Segment nachverfolgt. Es gibt eine Delete-Bitmap pro Partition.|  
|`access_count`|`int`|Anzahl der lesen oder Schreiben greift auf dieses Objekt.|  
|`memory_used_in_bytes`|`bigint`|Arbeitsspeicher, die von diesem Objekt im-Objektpool verwendet werden.|  
|`object_load_time`|`datetime`|Uhrzeit für die beim Object_id in den-Objektpool eingebunden wurde.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarife, erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard und Basic-Version, erfordert die **Serveradministrator** oder **Azure Active Directory-Administrator** Konto.   
 
## <a name="see-also"></a>Siehe auch  
  
 [Index Related Dynamic Management Views and Functions (Transact-SQL) (Indexbezogene dynamische Verwaltungssichten und -funktionen (Transact-SQL))](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  
