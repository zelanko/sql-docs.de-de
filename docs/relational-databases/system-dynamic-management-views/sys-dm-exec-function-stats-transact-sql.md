---
title: dm_exec_function_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d3c4b57cd20addca8091bfef2bf3ecaf6e157817
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844668"
---
# <a name="sysdmexecfunctionstats-transact-sql"></a>dm_exec_function_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Gibt die aggregatleistungsstatistik für zwischengespeicherte Funktionen aus. Gibt die Sicht eine Zeile für jeden Plan der zwischengespeicherten Funktion zurück, und die Lebensdauer der Zeile zwischengespeichert wird, solange die Funktion befindet. Wenn eine Funktion aus dem Cache entfernt wird, wird die entsprechende Zeile aus dieser Sicht gelöscht. Zu diesem Zeitpunkt wird ein Leistungsstatistik-SQL-Ablaufverfolgungsereignis ausgelöst, das **sys.dm_exec_query_stats**entspricht. Informationen zu den skalaren Funktionen, einschließlich der in-Memory-Funktionen und CLR-Skalarfunktionen zurückgegeben. Informationen zu Tabellenwertfunktionen wird nicht zurückgegeben werden.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, dass diese Informationen verfügbar gemacht werden, wird jede Zeile mit Daten, die zum verbundenen Mandanten gehören, herausgefiltert.  
  
> [!NOTE]
> Erste Abfrage von **dm_exec_function_stats** kann zu ungenauen Ergebnissen führen, wenn eine arbeitsauslastung, die gerade ausgeführt wird, auf dem Server vorhanden ist. Erneutes Ausführen der Abfrage liefert unter Umständen genauere Ergebnisse.  
  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Datenbank-ID, die in der die Funktion befindet.|  
|**object_id**|**int**|Objekt-ID der Funktion.|  
|**type**|**char(2)**|Typ des Objekts: FN = Funktionen mit skalaren Werten|  
|**type_desc**|**nvarchar(60)**|Beschreibung des Objekttyps: SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary(64)**|Dies kann verwendet werden, um die Korrelation mit Abfragen in **Sys. dm_exec_query_stats** , die in dieser Funktion aus ausgeführt wurden.|  
|**plan_handle**|**varbinary(64)**|Bezeichner für den speicherinternen Plan. Dieser Bezeichner ist vorübergehend und bleibt nur für die Dauer der Speicherung des Plans im Cache konstant. Dieser Wert kann mit der dynamischen Verwaltungssicht **sys.dm_exec_cached_plans** verwendet werden.<br /><br /> Immer wird 0 x 000, wenn eine systemintern kompilierte Funktion Abfragen, die eine Speicheroptimierte Tabelle sein.|  
|**cached_time**|**datetime**|Zeitpunkt, an dem die Funktion mit dem Cache hinzugefügt wurde.|  
|**last_execution_time**|**datetime**|Letzte Zeitpunkt, an dem die Funktion ausgeführt wurde.|  
|**execution_count**|**bigint**|Anzahl der Fälle, in denen die Funktion seit ausgeführt wurde der letzten Kompilierung.|  
|**total_worker_time**|**bigint**|Gesamtanzahl der Menge an CPU-Zeit Mikrosekunden, wurde diese Funktion Ausführungen seit der Kompilierung.<br /><br /> Bei nativ kompilierten Funktionen **Total_worker_time** möglicherweise nicht genau, wenn zahlreiche Ausführungen weniger als 1 Millisekunde dauern.|  
|**last_worker_time**|**bigint**|CPU-Zeit in Mikrosekunden, die den Zeitpunkt der letzten genutzt wurden, die die Funktion ausgeführt wurde. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Minimale CPU-Zeit in Mikrosekunden, diese Funktion immer eine einzelne Ausführung. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Maximale CPU-Zeit in Mikrosekunden, diese Funktion immer eine einzelne Ausführung. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Die Gesamtanzahl physischer Lesevorgänge für Ausführungen dieser Funktion seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_physical_reads**|**bigint**|Anzahl physischer Lesevorgänge ausgeführt, der letzten Ausführung die Funktion ausgeführt wurde.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**min_physical_reads**|**bigint**|Minimale Anzahl physischer Lesevorgänge, die diese Funktion eine einzelne Ausführung bisherige.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_physical_reads**|**bigint**|Maximale Anzahl physischer Lesevorgänge, die diese Funktion eine einzelne Ausführung bisherige.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_logical_writes**|**bigint**|Die Gesamtanzahl logischer Schreibvorgänge für Ausführungen dieser Funktion seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_logical_writes**|**bigint**|Die Anzahl der Pufferpoolseiten, die seit der letzten Planausführung modifiziert wurden. Wenn eine Seite bereits modifiziert (geändert) wurde, werden keine Schreibvorgänge gezählt.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**min_logical_writes**|**bigint**|Minimale Anzahl logischer Schreibvorgänge, die diese Funktion eine einzelne Ausführung bisherige.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_logical_writes**|**bigint**|Maximale Anzahl logischer Schreibvorgänge, die diese Funktion eine einzelne Ausführung bisherige.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_logical_reads**|**bigint**|Die Gesamtanzahl logischer Lesevorgänge für Ausführungen dieser Funktion seit der Kompilierung.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**last_logical_reads**|**bigint**|Anzahl logischer Lesevorgänge ausgeführt, der letzten Ausführung die Funktion ausgeführt wurde.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**min_logical_reads**|**bigint**|Minimale Anzahl logischer Lesevorgänge, die diese Funktion eine einzelne Ausführung bisherige.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**max_logical_reads**|**bigint**|Maximale Anzahl logischer Lesevorgänge, die diese Funktion eine einzelne Ausführung bisherige.<br /><br /> Ist immer 0, wenn eine speicheroptimierte Tabelle abgefragt wird.|  
|**total_elapsed_time**|**bigint**|Insgesamt verstrichene Zeit in Mikrosekunden, die für abgeschlossene Ausführungen dieser Funktion.|  
|**last_elapsed_time**|**bigint**|Verstrichene Zeit in Mikrosekunden, die für die letzte abgeschlossene Ausführung dieser Funktion.|  
|**min_elapsed_time**|**bigint**|Mindestens verstrichene Zeit, die in Mikrosekunden, die für eine beliebige abgeschlossene Ausführung dieser Funktion.|  
|**max_elapsed_time**|**bigint**|Maximal verstrichene Zeit, die in Mikrosekunden, die für eine beliebige abgeschlossene Ausführung dieser Funktion.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt Informationen zu den Top 10-Funktionen, die durchschnittlich verstrichenen Zeit zurück.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'function name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_function_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung bezogene dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)   
 [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  
  
  
