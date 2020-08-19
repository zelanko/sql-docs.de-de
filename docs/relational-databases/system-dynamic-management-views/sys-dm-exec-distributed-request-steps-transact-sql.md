---
description: sys. dm_exec_distributed_request_steps (Transact-SQL)
title: sys. dm_exec_distributed_request_steps (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 64e2e63c3b2bd7696ec9915b21e726a82bce7b07
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447537"
---
# <a name="sysdm_exec_distributed_request_steps-transact-sql"></a>sys. dm_exec_distributed_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Schritten, die eine bestimmte polybase-Anforderung oder-Abfrage bilden. Es wird eine Zeile pro Abfrage Schritt aufgelistet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**int**|execution_id und step_index bilden den Schlüssel für diese Ansicht. Eindeutige numerische ID, die der Anforderung zugeordnet ist.|Weitere Informationen finden Sie unter ID in [sys. dm_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Die Position dieses Schritts in der Abfolge der Schritte, die die Anforderung bilden.|0 bis (n-1) für eine Anforderung mit n Schritten.|  
|operation_type|**nvarchar(128)**|Der Typ des Vorgangs, der durch diesen Schritt dargestellt wird.|"Muveoperation", "onoperation", "randomidoperation", "Remoteoperation", "returnoperation", "shufflemuveoperation", "temptablepropertiesoperation", "dropdiagnosticsnotifyoperation", "hadoopshuffleoperation", "hadoopbroadcastoperation", "hadooproundrobinoperation"|  
|distribution_type|**nvarchar(32)**|Gibt an, wo der Schritt ausgeführt wird.|"Allcomputenodes", "allverteilungen", "computenode", "Distribution", "allnodes", "subsetnodes", "subsetverteilungen", "nicht angegeben".|  
|location_type|**nvarchar(32)**|Gibt an, wo der Schritt ausgeführt wird.|' Compute ', ' Head ' oder ' DMS '. Alle Daten Verschiebungs Schritte zeigen "DMS" an.|  
|status|**nvarchar(32)**|Status dieses Schritts|"Pending", "Running", "Complete", "failed", "undofailed", "stodingcancel", "abgebrochen", "Undone", "abgebrochen", "abgebrochen"|  
|error_id|**nvarchar (36)**|Eindeutige ID des Fehlers, der diesem Schritt zugeordnet ist, sofern vorhanden.|Siehe ID von [sys. dm_exec_compute_node_errors &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), NULL, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Zeitpunkt, zu dem die Ausführung des Schritts gestartet wurde|Kleiner oder gleich der aktuellen Zeit und größer oder gleich end_compile_time der Abfrage, zu der dieser Schritt gehört.|  
|end_time|**datetime**|Der Zeitpunkt, zu dem dieser Schritt die Ausführung abgeschlossen hat, abgebrochen wurde oder fehlgeschlagen ist.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich start_time, auf NULL für Schritte festgelegt, die gerade ausgeführt werden oder in die Warteschlange eingereiht werden.|  
|total_elapsed_time|**int**|Gesamtzeit Spanne, für die der Abfrage Schritt ausgeführt wurde (in Millisekunden)|Zwischen 0 und dem Unterschied zwischen end_time und start_time. 0 für Schritte in der Warteschlange.|  
|row_count|**bigint**|Gesamtanzahl der von dieser Anforderung geänderten oder zurückgegebenen Zeilen|0 für Schritte, bei denen keine Daten geändert oder zurückgegeben wurden, die Anzahl der betroffenen Zeilen. Legen Sie für DMS-Schritte den Wert-1 fest.|  
|command|nvarchar(4000)|Enthält den vollständigen Text des Befehls dieses Schritts.|Eine beliebige gültige Anforderungs Zeichenfolge für einen Schritt. Wird abgeschnitten, wenn mehr als 4000 Zeichen enthalten sind.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
