---
title: sys.dm_exec_background_job_queue_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_background_job_queue_stats
- sys.dm_exec_background_job_queue_stats
- dm_exec_background_job_queue_stats_TSQL
- sys.dm_exec_background_job_queue_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_background_job_queue_stats dynamic management view
ms.assetid: 27f62ab5-46c4-417e-814d-8d6437034d1c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fa06da06ae057839a9d0e6433e57edb1f8a603d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013514"
---
# <a name="sysdmexecbackgroundjobqueuestats-transact-sql"></a>sys.dm_exec_background_job_queue_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile zurück, die Gesamtstatistiken zu jedem Abfrageprozessorauftrag bereitstellt, der für die asynchrone Ausführung (im Hintergrund) übermittelt wird.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_exec_background_job_queue_stats**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**queue_max_len**|**int**|Maximale Länge der Warteschlange.|  
|**enqueued_count**|**int**|Anzahl der erfolgreich an die Warteschlange gesendeten Anforderungen.|  
|**started_count**|**int**|Anzahl der Anforderungen, mit deren Ausführung begonnen wurde.|  
|**ended_count**|**int**|Anzahl der Anforderungen, die entweder mit Erfolg oder Fehler abgeschlossen wurden.|  
|**failed_lock_count**|**int**|Anzahl der Anforderungen, die aufgrund von Sperrkonflikten oder Deadlocks Fehler erzeugt haben.|  
|**failed_other_count**|**int**|Anzahl der Anforderungen, die aus anderen Gründen Fehler erzeugt haben.|  
|**failed_giveup_count**|**int**|Anzahl der Anforderungen, die Fehler erzeugt haben, da das Wiederholungslimit erreicht wurde.|  
|**enqueue_failed_full_count**|**int**|Anzahl der gescheiterten Versuche zum Einreihen in eine Warteschlange, da die Warteschlange voll ist.|  
|**enqueue_failed_duplicate_count**|**int**|Anzahl der doppelten Versuche zum Einreihen in eine Warteschlange.|  
|**elapsed_avg_ms**|**int**|Durchschnittliche Dauer von Anforderungen in Millisekunden.|  
|**elapsed_max_ms**|**int**|Dauer der längsten Anforderung in Millisekunden.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Sicht gibt nur Informationen für Aufträge zum asynchronen Aktualisieren von Statistiken zurück. Weitere Informationen zum asynchronen Aktualisieren von Statistiken finden Sie unter [Statistiken](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="examples"></a>Beispiele  
  
### <a name="a-determining-the-percentage-of-failed-background-jobs"></a>A. Bestimmen des Prozentsatzes von Hintergrundaufträgen mit Fehlern  
 Im folgenden Beispiel wird der Prozentsatz der fehlgeschlagenen Hintergrundaufträge für alle ausgeführten Abfragen zurückgegeben.  
  
```  
SELECT   
        CASE ended_count WHEN 0   
                THEN 'No jobs ended'   
                ELSE CAST((failed_lock_count + failed_giveup_count + failed_other_count) / CAST(ended_count AS float) * 100 AS varchar(20))   
        END AS [Percent Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
### <a name="b-determining-the-percentage-of-failed-enqueue-attempts"></a>B. Bestimmen des Prozentsatzes fehlerhafter Versuche, Elemente in die Warteschlange einzureihen  
 Im folgenden Beispiel wird der Prozentsatz der fehlgeschlagenen Versuche zum Einreihen in eine Warteschlange für alle ausgeführten Abfragen zurückgegeben.  
  
```  
SELECT   
        CASE enqueued_count WHEN 0   
                THEN 'No jobs posted'   
                ELSE CAST((enqueue_failed_full_count + enqueue_failed_duplicate_count) / CAST(enqueued_count + enqueue_failed_full_count + enqueue_failed_duplicate_count AS float) * 100 AS varchar(20))   
        END AS [Percent Enqueue Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


