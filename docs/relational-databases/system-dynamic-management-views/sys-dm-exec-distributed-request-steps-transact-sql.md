---
title: dm_exec_distributed_request_steps (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS_TSQL
- DM_EXEC_DISTRIBUTED_REQUEST_STEPS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_distributed_request_steps
- sys.dm_exec_distributed_request_steps management view
ms.assetid: 1954541d-b716-4e03-8fcc-7022f428e01d
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 61f4133ca4fd29bd03d657f2caa0714e99195c88
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43059431"
---
# <a name="sysdmexecdistributedrequeststeps-transact-sql"></a>dm_exec_distributed_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über alle Schritte, die eine bestimmte Anforderung von PolyBase oder Abfrage bilden. Sie enthält eine Zeile pro abfrageschritt.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|Execution_id und Step_index stellen Sie den Schlüssel für diese Sicht. Eindeutige numerische Id der Anforderung zugeordnet ist.|Finden Sie unter-ID in [Sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Die Position dieses Schritts in der Reihenfolge der Schritte, aus denen die Anforderung besteht.|0, um (n-1) für eine Anforderung mit n Schritten.|  
|operation_type|**nvarchar(128)**|Der Typ des Vorgangs durch diesen Schritt dargestellt.|'MoveOperation', "OnOperation", "RandomIDOperation", "RemoteOperation", "ReturnOperation", "ShuffleMoveOperation", "TempTablePropertiesOperation", "DropDiagnosticsNotifyOperation", "HadoopShuffleOperation", "HadoopBroadCastOperation", "HadoopRoundRobinOperation"|  
|distribution_type|**nvarchar(32)**|Gibt an, in der Schritt ausgeführt wird.|"AllComputeNodes","AllDistributions,"ComputeNode", 'Distribution',"AllNodes","SubsetNodes","SubsetDistributions,"Unspecified".|  
|location_type|**nvarchar(32)**|Gibt an, in der Schritt ausgeführt wird.|"Compute", "Head" oder "DMS". Alle Schritte zum Verschieben von Daten anzeigen "DMS".|  
|status|**nvarchar(32)**|Status dieses Schritts|"Ausstehend" "abgebrochen"Running","Abgeschlossen","Fehlgeschlagen", 'UndoFailed', 'PendingCancel',',"Rückgängig gemacht werden","Abgebrochen"|  
|error_id|**nvarchar(36)**|Eindeutige Id des Fehlers mit diesem Schritt verknüpft ist, falls vorhanden|Finden Sie die Id des [sys.dm_exec_compute_node_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), NULL, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Zeitpunkt, an dem der Schritt die Ausführung gestartet|Kleiner oder gleich der aktuellen Zeit und größer oder gleich End_compile_time der Abfrage zu der dieser Schritt gehört.|  
|end_time|**datetime**|Zeitpunkt, an dem dieser Schritt ausgeführt wurden, wurde abgebrochen oder fehlerhaft.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich Start_time, für die Schritte, die derzeit in der Ausführung auf NULL festgelegt oder in die Warteschlange eingereiht.|  
|total_elapsed_time|**int**|Gesamtmenge der Mal, wenn der abfrageschritt, in Millisekunden ausgeführt wurde|Zwischen 0 und der Unterschied zwischen End_time und Start_time. 0 für die Schritte in Warteschlange.|  
|row_count|**bigint**|Gesamtanzahl der Zeilen, die geändert oder von dieser Anforderung zurückgegebene|0 für Schritte, die nicht ändern oder Rückgabedaten, Anzahl der Zeilen, die andernfalls betroffen. Zur DMS-Schritte auf-1 festgelegt.|  
|Befehl|nvarchar(4000)|Enthält den vollständigen Text des Befehls dieses Schritts an.|Eine beliebige gültige Anforderungs-Zeichenfolge für einen Schritt. Bei mehr als 4000 Zeichen abgeschnitten.|  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
