---
title: Sys.dm_pdw_node_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6c56d169e8aa55e83b86713e1b9fa476bc213ae3
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014146"
---
# <a name="sysdmpdwnodestatus-transact-sql"></a>sys.dm_pdw_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält zusätzliche Informationen (über [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) über die Leistung und Status von allen applianceknoten. Sie enthält eine Zeile pro Knoten in der Appliance.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Eindeutige numerische Id, die dem Knoten zugeordnet.<br /><br /> Der Schlüssel für diese Sicht.|Auf der gesamten Appliance, unabhängig vom Typ eindeutig.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|process_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Insgesamt zugeordneter Arbeitsspeicher auf diesem Knoten.||  
|available_memory|**bigint**|Gesamten verfügbaren Arbeitsspeichers auf diesem Knoten.||  
|process_cpu_usage|**bigint**|Gesamt-Prozess-CPU-Nutzung in Ticks.||  
|total_cpu_usage|**bigint**|Gesamte CPU-Auslastung in Ticks.||  
|thread_count|**bigint**|Die Gesamtanzahl der Threads auf diesem Knoten.||  
|handle_count|**bigint**|Gesamtanzahl der Handles in Verwendung auf diesem Knoten.||  
|total_elapsed_time|**bigint**|Insgesamt verstrichene Zeit seit System starten oder neu starten.|Insgesamt verstrichene Zeit seit System starten oder neu starten. Überschreitet Total_elapsed_time den maximalen Wert für eine ganze Zahl (rund 24,8 Tage in Millisekunden), wird es Materialisierung Fehler aufgrund einer zu einem Überlauf führen.<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|is_available|**bit**|Flag, der angibt, ob dieser Knoten verfügbar ist.||  
|sent_time|**datetime**|Zeitpunkt der letzten ein das Paket wurde von diesem Knoten gesendet werden.||  
|received_time|**datetime**|Zeitpunkt der letzten ein das Paket wurde von diesem Knoten empfangen werden.||  
|error_id|**nvarchar(36)**|Eindeutiger Bezeichner des letzten Fehlers, der auf diesem Knoten aufgetreten ist.||  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
