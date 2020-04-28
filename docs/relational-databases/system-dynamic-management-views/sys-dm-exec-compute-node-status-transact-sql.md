---
title: sys. dm_exec_compute_node_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 11883f7744aad3f8d483e808922a7170c8fe5391
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73532745"
---
# <a name="sysdm_exec_compute_node_status-transact-sql"></a>sys. dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält zusätzliche Informationen zur Leistung und zum Status aller polybase-Knoten. Listet eine Zeile pro Knoten auf.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|`int`|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|Eindeutig in einem Cluster mit horizontaler Skalierung (unabhängig vom Typ).|  
|process_id|`int`|||  
|process_name|`nvarchar(255)`|Logischer Name des Knotens.|Eine beliebige Zeichenfolge mit entsprechender Länge.|  
|allocated_memory|`bigint`|Insgesamt zugeordneter Arbeitsspeicher auf diesem Knoten.||  
|available_memory|`bigint`|Gesamter verfügbarer Arbeitsspeicher auf diesem Knoten.||  
|process_cpu_usage|`bigint`|Gesamte Prozess-CPU-Auslastung in Ticks.||  
|total_cpu_usage|`bigint`|Gesamte CPU-Auslastung in Ticks.||  
|thread_count|`bigint`|Die Gesamtanzahl der Threads, die auf diesem Knoten verwendet werden.||  
|handle_count|`bigint`|Die Gesamtanzahl von Handles, die auf diesem Knoten verwendet werden.||  
|total_elapsed_time|`bigint`|Gesamtzeit seit dem Start oder Neustart des Systems.|Gesamtzeit seit dem Start oder Neustart des Systems. Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl (24,8 Tage in Millisekunden) überschreitet, führt dies zu einem Materialisierungs Fehler aufgrund eines Überlaufs. Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
|is_available|`bit`|Flag zum angeben, ob dieser Knoten verfügbar ist.||  
|sent_time|`datetime`|Der letzte Zeitpunkt, zu dem ein Netzwerk Paket von diesem gesendet wurde.||  
|received_time|`datetime`|Der letzte Zeitpunkt, zu dem ein Netzwerk Paket von diesem Knoten gesendet wurde.||  
|error_id|`nvarchar(36)`|Eindeutiger Bezeichner des letzten Fehlers, der auf diesem Knoten aufgetreten ist.||
|compute_pool_id|`int`|Eindeutiger Bezeichner für den Pool.|

## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
