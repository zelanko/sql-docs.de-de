---
title: dm_pdw_request_steps (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 5a6fbf843d3a9aca9172a5ab6ea828a0c0b0a40a
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926841"
---
# <a name="sysdmpdwrequeststeps-transact-sql"></a>sys.dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über alle Schritte, die eine bestimmte Anforderung erstellen, oder -Abfrage im [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Sie enthält eine Zeile pro abfrageschritt.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Anforderungs-ID und Step_index stellen Sie den Schlüssel für diese Sicht.<br /><br /> Eindeutige numerische Id der Anforderung zugeordnet ist.|Finden Sie im Anforderungs-ID [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Anforderungs-ID und Step_index stellen Sie den Schlüssel für diese Sicht.<br /><br /> Die Position dieses Schritts in der Reihenfolge der Schritte, aus denen die Anforderung besteht.|0, um (n-1) für eine Anforderung mit n Schritten.|  
|operation_type|**nvarchar(35)**|Typ des Vorgangs, der durch diesen Schritt dargestellt.|**DMS Abfragevorgänge Plan:** "ReturnOperation", 'PartitionMoveOperation', "MoveOperation", "BroadcastMoveOperation", "ShuffleMoveOperation", "TrimMoveOperation", "CopyOperation", "DistributeReplicatedTableMoveOperation"<br /><br /> **SQL-Abfrage-Plan-Vorgänge:** 'OnOperation', "RemoteOperation"<br /><br /> **Weitere Abfragevorgänge für den Plan:** 'MetaDataCreateOperation', "RandomIDOperation"<br /><br /> **Externe Vorgänge für Lesevorgänge:** 'HadoopShuffleOperation', 'HadoopRoundRobinOperation', "HadoopBroadcastOperation"<br /><br /> **Externe Vorgänge für MapReduce:** 'HadoopJobOperation', "HdfsDeleteOperation"<br /><br /> **Externe Vorgänge für Schreibvorgänge:** 'ExternalExportDistributedOperation', 'ExternalExportReplicatedOperation', "ExternalExportControlOperation"<br /><br /> Weitere Informationen finden Sie unter "Grundlegendes zu Abfragepläne" in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].|  
|distribution_type|**nvarchar(32)**|Die Art der Verteilung, die ausgeführt wird, dass Sie diesen Schritt.|"AllNodes", "AllDistributions", "AllComputeNodes", "ComputeNode", 'Distribution', "SubsetNodes", "SubsetDistributions", "Nicht angegeben"|  
|location_type|**nvarchar(32)**|Gibt an, in dem der Schritt ausgeführt wird.|'Berechnen', 'Control', "DMS"|  
|status|**nvarchar(32)**|Der Status dieses Schritts.|Ausstehend "," wird ausgeführt, abgeschlossen, Fehler, UndoFailed, PendingCancel abgebrochen, rückgängig gemacht werden, wurde abgebrochen|  
|error_id|**nvarchar(36)**|Eindeutige Id des Fehlers mit diesem Schritt verknüpft ist, sofern vorhanden.|Finden Sie unter Fehler-ID des [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). NULL, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Zeitpunkt, zu dem der Schritt Ausführung begonnen hat.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich End_compile_time der Abfrage zu der dieser Schritt gehört. Weitere Informationen zu Abfragen finden Sie unter [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Zeitpunkt, an dem dieser Schritt ausgeführt wurden, wurde abgebrochen oder fehlerhaft.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich Start_time. Schritte, die derzeit in der Ausführung auf NULL festgelegt oder in die Warteschlange eingereiht.|  
|total_elapsed_time|**int**|Die Gesamtmenge der Mal, wenn der abfrageschritt, in Millisekunden ausgeführt wurde.|Zwischen 0 und der Unterschied zwischen End_time und Start_time. 0 für die Schritte in Warteschlange.<br /><br /> Wenn Total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, weiterhin Total_elapsed_time der maximale Wert sein. Diese Bedingung generiert die Warnung "der maximale Wert überschritten wurde."<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|row_count|**bigint**|Gesamtanzahl der Zeilen geändert oder von dieser Anforderung zurückgegeben.|0 für Schritte, die nicht ändern oder Daten zurückgegeben haben. Andernfalls, Anzahl der betroffenen Zeilen.|  
|Befehl|**nvarchar(4000)**|Enthält den vollständigen Text des Befehls dieses Schritts an.|Eine beliebige gültige Anforderungs-Zeichenfolge für einen Schritt. NULL, wenn der Vorgang des Typs MetaDataCreateOperation ist. Bei mehr als 4000 Zeichen abgeschnitten.|  
  
 Informationen, die maximale Anzahl Zeilen, die von dieser Sicht beibehalten können, finden Sie im Abschnitt Maximalwerte System anzeigen, die "minimale und maximale Werte" in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
