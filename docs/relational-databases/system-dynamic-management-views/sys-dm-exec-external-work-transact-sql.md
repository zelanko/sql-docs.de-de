---
title: Sys.dm_exec_external_work (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39cf8d2c232487c89d47a67401b27014b57f7f58
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632601"
---
# <a name="sysdmexecexternalwork-transact-sql"></a>Sys.dm_exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Informationen über die arbeitsauslastung pro Worker, auf jedem Computeknoten zurück.  
  
 Für die Kommunikation mit der externen Datenquelle (z. B. Hadoop oder externen SQL Server) hochgefahren sys.dm_exec_external_work Abfrage, um die Arbeit zu identifizieren.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Eindeutiger Bezeichner für den zugeordneten PolyBase-Abfrage.|Finden Sie unter *Request_ID* in [Sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|**int**|Die Anforderung, die dieser Arbeitsthread ausgeführt wird.|Finden Sie unter *Step_index* in [Sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|**int**|Schritt in den DMS-Plan, den dieser Arbeitsthread ausgeführt wird.|Finden Sie unter [sys.dm_exec_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|**int**|Der Knoten der Worker ausgeführt wird.|Finden Sie unter [dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|Typ|**nvarchar(60)**|Der Typ der externen Ressourcen.|"File Split"|  
|work_id|**int**|Die ID der tatsächlichen Teilung.|Größer als oder gleich 0.|  
|input_name|**nvarchar(4000)**|Name der Eingabe gelesen werden|Name der Datei bei Verwendung von Hadoop.|  
|read_location|**bigint**|Offset oder Speicherort gelesen.|Der Offset des zu lesenden Datei.|  
|bytes_processed|**bigint**|Gesamtzahl der Bytes von diesem Arbeitsthread verarbeitet werden.|Größer als oder gleich 0.|  
|length|**bigint**|Länge der knotenspezifischen Teilung bzw. bei Hadoop HDFS-block|Benutzerdefinierbaren. Der Standardwert ist 64M|  
|status|**nvarchar(32)**|Status des Arbeitsthreads|Ausstehende, Verarbeitung, ausgeführt, Fehler, wurde abgebrochen|  
|start_time|**datetime**|Beginn der Arbeit||  
|end_time|**datetime**|Ende der Arbeit||  
|total_elapsed_time|**int**|Gesamtzeit in Millisekunden||  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
