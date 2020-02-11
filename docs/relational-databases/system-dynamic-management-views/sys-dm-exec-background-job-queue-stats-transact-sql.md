---
title: sys. dm_exec_background_job_queue_stats (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4707c652b8d47505cceba0be76c53eff2824b728
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68263947"
---
# <a name="sysdm_exec_background_job_queue_stats-transact-sql"></a>sys.dm_exec_background_job_queue_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile zurück, die Gesamtstatistiken zu jedem Abfrageprozessorauftrag bereitstellt, der für die asynchrone Ausführung (im Hintergrund) übermittelt wird.  
  
> [!NOTE]  
>  Um dies von oder [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]aus aufzurufen, verwenden Sie den Namen **sys. dm_pdw_nodes_exec_background_job_queue_stats**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
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
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Sicht gibt nur Informationen für Aufträge zum asynchronen Aktualisieren von Statistiken zurück. Weitere Informationen zu asynchronen Update Statistiken finden Sie unter [Statistics](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist die `VIEW SERVER STATE` -Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE` -Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   

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
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten und-Funktionen im Zusammenhang mit der Ausführung &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


