---
description: sys.dm_pdw_node_status (Transact-SQL)
title: sys.dm_pdw_node_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: ae7d516d143adb54427146a1675433575d5a2529
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461581"
---
# <a name="sysdm_pdw_node_status-transact-sql"></a>sys.dm_pdw_node_status (Transact-SQL)

[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Enthält zusätzliche Informationen zur Leistung und zum Status aller Geräteknoten (über [sys.dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)). Es wird eine Zeile pro Knoten in der Appliance aufgelistet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.<br /><br /> Der Schlüssel für diese Ansicht.|In der gesamten Appliance eindeutig, unabhängig vom Typ.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|process_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Insgesamt zugeordneter Arbeitsspeicher auf diesem Knoten.||  
|available_memory|**bigint**|Gesamter verfügbarer Arbeitsspeicher auf diesem Knoten.||  
|process_cpu_usage|**bigint**|Gesamte Prozess-CPU-Auslastung in Ticks.||  
|total_cpu_usage|**bigint**|Gesamte CPU-Auslastung in Ticks.||  
|thread_count|**bigint**|Die Gesamtanzahl der Threads, die auf diesem Knoten verwendet werden.||  
|handle_count|**bigint**|Die Gesamtanzahl von Handles, die auf diesem Knoten verwendet werden.||  
|total_elapsed_time|**bigint**|Gesamtzeit seit dem Start oder Neustart des Systems.|Gesamtzeit seit dem Start oder Neustart des Systems. Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl (24,8 Tage in Millisekunden) überschreitet, führt dies zu einem Materialisierungs Fehler aufgrund eines Überlaufs.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
|is_available|**bit**|Flag zum angeben, ob dieser Knoten verfügbar ist.||  
|sent_time|**datetime**|Der letzte Zeitpunkt, zu dem ein Netzwerk Paket von diesem Knoten gesendet wurde.||  
|received_time|**datetime**|Der letzte Zeitpunkt, zu dem ein Netzwerk Paket von diesem Knoten empfangen wurde.||  
|error_id|**nvarchar (36)**|Eindeutiger Bezeichner des letzten Fehlers, der auf diesem Knoten aufgetreten ist.||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure Synapse Analytics und parallele Data Warehouse dynamische Verwaltungs Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
