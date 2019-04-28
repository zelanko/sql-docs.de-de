---
title: Sys.dm_exec_distributed_sql_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_distributed_requests management view
- dm_exec_distributed_requests management view
ms.assetid: d065dc01-35d4-472f-9554-53ac41e7d104
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2f86941149741caee7849c579e32ad070d7a3dec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013402"
---
# <a name="sysdmexecdistributedsqlrequests-transact-sql"></a>sys.dm_exec_distributed_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über alle Verteilungen von SQL-Abfrage als Teil eines SQL-Schritts in der Abfrage.  In dieser Ansicht wird angezeigt, die Daten für die letzten 1000 Anforderungen. aktive Anforderungen haben immer die Daten in dieser Ansicht vorhanden.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Execution_id und Step_index stellen Sie den Schlüssel für diese Sicht. Eindeutige numerische Id der Anforderung zugeordnet ist.|Finden Sie unter-ID in [Sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)|  
|step_index|**int**|Der Index des abfrageschritts, die diesem Verteilungspunkt gehört.|Finden Sie unter Step_index in [dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|compute_node_id|**int**|Der Typ des Vorgangs durch diesen Schritt dargestellt.|Finden Sie unter Compute_node_id in [dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|Gibt an, in der Schritt ausgeführt wird.|Legen Sie auf-1 für Anforderungen, die im Bereich von Knoten nicht den Verteilungsbereich ausgeführt werden.|  
|status|**nvarchar(32)**|Status dieses Schritts|Aktive, abgebrochen, abgeschlossen, Fehler, in der Warteschlange|  
|error_id|**nvarchar(36)**|Eindeutige Id des Fehlers mit diesem Schritt verknüpft ist, falls vorhanden|Finden Sie die Id des [sys.dm_exec_compute_node_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), NULL, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Zeitpunkt, an dem der Schritt die Ausführung gestartet|Kleiner oder gleich der aktuellen Zeit und größer oder gleich End_compile_time der Abfrage zu der dieser Schritt gehört.|  
|end_time|**datetime**|Zeitpunkt, an dem dieser Schritt ausgeführt wurden, wurde abgebrochen oder fehlerhaft.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich Start_time, für die Schritte, die derzeit in der Ausführung auf NULL festgelegt oder in die Warteschlange eingereiht.|  
|total_elapsed_time|**int**|Gesamtmenge der Mal, wenn der abfrageschritt, in Millisekunden ausgeführt wurde|Zwischen 0 und der Unterschied zwischen End_time und Start_time. 0 für die Schritte in Warteschlange.|  
|row_count|**bigint**|Gesamtanzahl der Zeilen, die geändert oder von dieser Anforderung zurückgegebene|0 für Schritte, die nicht ändern oder Rückgabedaten, Anzahl der Zeilen, die andernfalls betroffen. Zur DMS-Schritte auf-1 festgelegt.|  
|spid|**int**|Sitzungs-Id für die SQL Server-Instanz, die die Verteilung von Abfragen ausführen||  
|Befehl|nvarchar(4000)|Enthält den vollständigen Text des Befehls dieses Schritts an.|Eine beliebige gültige Anforderungs-Zeichenfolge für einen Schritt. Bei mehr als 4000 Zeichen abgeschnitten.|  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
