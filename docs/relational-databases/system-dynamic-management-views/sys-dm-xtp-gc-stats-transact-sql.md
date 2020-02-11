---
title: sys. dm_xtp_gc_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_gc_stats
- dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_gc_stats dynamic management view
ms.assetid: 8287d611-50e3-43e1-ba8d-3e3793d3ba0e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28d98f7f95d9e9c2af967976b875f61388342583
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090174"
---
# <a name="sysdm_xtp_gc_stats-transact-sql"></a>sys.dm_xtp_gc_stats (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Enthält Informationen (Gesamtstatistiken) zum aktuellen Verhalten des Garbage Collection-Prozesses von [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .  
  
 Zeilen werden im Rahmen der regulären Transaktionsverarbeitung von der Garbage Collection oder vom Garbage Collection-Hauptthread bereinigt, der als Leerlaufthread bezeichnet wird. Wenn für eine Benutzertransaktion ein Commit ausgeführt wird, wird ein Arbeits Element aus der Garbage Collection Warteschlange entfernt ([sys. dm_xtp_gc_queue_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md)). Alle Zeilen, die durch die Garbage Collection bereinigt werden konnten, auf die jedoch nicht durch die Hauptbenutzertransaktion zugegriffen wurde, werden im Rahmen des Dusty-Corner-Scans (einem Scan der Indexbereiche, auf die seltener zugegriffen wird) durch den Leerlaufthread bereinigt.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Spaltenname|type|BESCHREIBUNG|  
|-----------------|----------|-----------------|  
|rows_examined|**BIGINT**|Die Anzahl der Zeilen, die vom Subsystem der Garbage Collection überprüft werden, nachdem der Server gestartet wurde.|  
|rows_no_sweep_needed|**BIGINT**|Die Anzahl der Zeilen, die ohne Dusty-Corner-Scan entfernt wurden.|  
|rows_first_in_bucket|**BIGINT**|Die Anzahl der Zeilen, die von der Garbage Collection überprüft wurden und die die erste Zeile im Hashbucket waren.|  
|rows_first_in_bucket_removed|**BIGINT**|Die Anzahl der Zeilen, die von der Garbage Collection überprüft wurden und die als erste Zeile im Hashbucket entfernt wurden.|  
|rows_marked_for_unlink|**BIGINT**|Die Anzahl der Zeilen, die von der Garbage Collection überprüft wurden und in ihren Indizes mit ref count=0 bereits als nicht mehr verknüpft markiert sind.|  
|parallel_assist_count|**BIGINT**|Die Anzahl der Zeilen, die durch Benutzertransaktionen verarbeitet wurden.|  
|idle_worker_count|**BIGINT**|Die Anzahl der Garbage-Zeilen, die durch den Leerlaufthread verarbeitet wurden.|  
|sweep_scans_started|**BIGINT**|Die Anzahl der durch das Garbage Collection-Subsystem ausgeführten Dusty-Corner-Scans.|  
|sweep_scans_retries|**BIGINT**|Die Anzahl der durch das Garbage Collection-Subsystem ausgeführten Dusty-Corner-Scans.|  
|sweep_rows_touched|**BIGINT**|Die durch die Dusty-Corner-Verarbeitung gelesenen Zeilen.|  
|sweep_rows_expiring|**BIGINT**|Die durch die Dusty-Corner-Verarbeitung gelesenen ablaufenden Zeilen.|  
|sweep_rows_expired|**BIGINT**|Die durch die Dusty-Corner-Verarbeitung gelesenen abgelaufenen Zeilen.|  
|sweep_rows_expired_removed|**BIGINT**|Die durch die Dusty-Corner-Verarbeitung entfernten abgelaufenen Zeilen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung für die Instanz.  
  
## <a name="usage-scenario"></a>Verwendungsszenario  
 Im Folgenden eine Beispielausgabe:  
  
```  
rows_examined        rows_no_sweep_needed rows_first_in_bucket rows_first_in_bucket_removed  
280085               209512               69905  
rows_first_in_bucket_removed rows_marked_for_unlink parallel_assist_count idle_worker_count  
69905                        0                      8953  
  
idle_worker_count    sweep_scans_started  sweep_scan_retries   sweep_rows_touched  
10306473             670                  0                    1343  
  
sweep_rows_expiring  sweep_rows_expired   sweep_rows_expired_removed  
               0                 673673  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten für Speicher optimierte Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
