---
title: sys.dm_db_column_store_row_group_operational_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31b71c68-50a0-4fd8-a7fe-2d2292be1163
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 73c83151f27338d8d96046e11d9406d751f5aa17
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43100626"
---
# <a name="sysdmdbcolumnstorerowgroupoperationalstats-transact-sql"></a>sys.dm_db_column_store_row_group_operational_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Gibt aktuelle e/a, Sperren auf Zeilenebene und Zugriff auf die Aktivität für Methode für die komprimierten Zeilengruppen in eine columnstore-Index. Verwendung **sys.dm_db_column_store_row_group_operational_stats** die Zeitspanne nachverfolgen eine Benutzerabfrage warten, bis die lesen oder Schreiben in eine komprimierte Zeilengruppe oder eine Partition eines columnstore-Indexes werden muss, und welche Zeilengruppen, die auftreten umfangreiche e/a-Aktivitäten oder Hotspots.  
  
 In-Memory-Columnstore-Indizes werden in dieser DMV nicht angezeigt.  
 
 
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID der Tabelle mit der columnstore-Index.|  
|**index_id**|**int**|ID des columnstore-Indexes.|  
|**partition_number**|**int**|Auf 1 basierende Partitionsnummer im Index oder Heap.|  
|**row_group_id**|**int**|Die ID der Zeilengruppe im columnstore-Index. Dies ist eindeutig innerhalb einer Partition.|  
|**scan_count**|**int**|Anzahl von Scanvorgängen durch die seit dem letzten Neustart der SQL-Zeilengruppe.|  
|**delete_buffer_scan_count**|**int**|Anzahl von Wiederholungen des löschpuffers wurde verwendet, um zu bestimmen, gelöschte Zeilen in diese Zeilengruppe aufgenommen. Dies schließt den Zugriff auf die Hashtabelle im Arbeitsspeicher und der zugrunde liegenden BTree-Struktur.|  
|**index_scan_count**|**int**|Wie oft der columnstore-index, Partition wurde überprüft. Dies ist für alle Zeilengruppen in der Partition identisch.|  
|**rowgroup_lock_count**|**bigint**|Kumulierte Anzahl der sperranforderungen, für die dieser Zeilengruppe seit dem letzten Neustart von SQL.|  
|**rowgroup_lock_wait_count**|**bigint**|Gesamthäufigkeit, mit die Datenbank-Engine wird auf diesem Rowgroup-Sperre gewartet hat, seit dem letzten Neustart von SQL.|  
|**rowgroup_lock_wait_in_ms**|**bigint**|Die kumulative Anzahl der Millisekunden die Datenbank-Engine wird auf diesem Rowgroup-Sperre gewartet hat, seit dem letzten Neustart von SQL.|  
  
## <a name="permissions"></a>Berechtigungen  
 Folgende Berechtigungen sind erforderlich:  
  
-   CONTROL-Berechtigung für die Tabelle, die innerhalb von Object_id.  
  
-   VIEW DATABASE STATE-Berechtigung zum Zurückgeben von Informationen zu allen Objekten innerhalb der Datenbank, mit der Objekt-Platzhalter @*Object_id* = NULL  
  
 Wenn die VIEW DATABASE STATE-Berechtigung erteilt wurde, ist die Rückgabe für alle Objekte in der Datenbank zulässig, unabhängig davon, ob CONTROL-Berechtigungen für bestimmte Objekte verweigert wurden.  
  
 Nach dem Verweigern der VIEW DATABASE STATE-Berechtigung können keine Objekte in der Datenbank zurückgegeben werden, unabhängig von möglicherweise erteilten CONTROL-Berechtigungen für bestimmte Objekte. Auch wenn der Datenbank-Platzhalter @*Database_id*= NULL angegeben wird, die Datenbank fehlt.  
  
 Weitere Informationen finden Sie unter [dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Index Related Dynamic Management Views and Functions (Transact-SQL) (Indexbezogene dynamische Verwaltungssichten und -funktionen (Transact-SQL))](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)   
 [sys.dm_os_latch_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)   
 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)   
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  

