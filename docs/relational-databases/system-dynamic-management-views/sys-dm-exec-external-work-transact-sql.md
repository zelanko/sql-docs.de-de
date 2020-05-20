---
title: sys. dm_exec_external_work (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8348ebacb68f2df122b73d6ad3480cadedd27c1b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821103"
---
# <a name="sysdm_exec_external_work-transact-sql"></a>sys. dm_exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Gibt Informationen über die Arbeitsauslastung pro Worker auf jedem Computeknoten zurück.  
  
 Fragen Sie sys. dm_exec_external_work ab, um die für die Kommunikation mit der externen Datenquelle (z. b. Hadoop oder externe SQL Server) aufgedrehte Arbeit zu identifizieren.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|`nvarchar(32)`|Eindeutiger Bezeichner für zugeordnete polybase-Abfrage.|Weitere Informationen finden Sie unter *request_ID* in [sys. dm_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|`int`|Die Anforderung, die dieser Worker ausführt.|Weitere Informationen finden Sie unter *step_index* in [sys. dm_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|`int`|Schritt in den DMS-Plan, der von diesem Worker ausgeführt wird.|Weitere Informationen finden Sie unter [sys. dm_exec_dms_workers &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|`int`|Der Knoten, auf dem der Worker ausgeführt wird.|Weitere Informationen finden Sie unter [sys. dm_exec_compute_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|Typ|`nvarchar(60)`|Der Typ der externen Arbeit.|' Datei Teilung '|  
|work_id|`int`|ID der tatsächlichen Teilung.|Größer oder gleich 0 (null).|  
|input_name|`nvarchar(4000)`|Name der zu lesenden Eingabe|Dateiname bei Verwendung von Hadoop.|  
|read_location|`bigint`|Offset oder Lese Speicherort.|Der Offset der zu lesenden Datei.|  
|bytes_processed|`bigint`|Gesamtanzahl der für die Verarbeitung von Daten durch diesen Worker zugeordneten Bytes. Dies kann nicht notwendigerweise die Gesamtmenge der Daten darstellen, die von der Abfrage zurückgegeben werden. |Größer oder gleich 0 (null).|  
|length|`bigint`|Länge des Split-oder HDFS-Blocks im Fall von Hadoop|Benutzerdefinierbar. Der Standardwert ist 64M.|  
|status|`nvarchar(32)`|Status des Workers|Ausstehend, verarbeitet, abgeschlossen, fehlgeschlagen, abgebrochen|  
|start_time|`datetime`|Beginn der Arbeit||  
|end_time|`datetime`|Ende der Arbeit||  
|total_elapsed_time|`int`|Gesamtzeit in Millisekunden||
|compute_pool_id|`int`|Eindeutiger Bezeichner für den Pool.|

## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
