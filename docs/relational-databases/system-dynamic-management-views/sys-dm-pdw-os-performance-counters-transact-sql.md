---
title: Sys.dm_pdw_os_performance_counters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 820027ee5bf893d7df81c51f90b431daa7c0af07
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62704319"
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu Windows-Leistungsindikatoren für die Knoten im [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Die ID des Knotens, der den Indikator enthält.<br /><br /> Pdw_node_id und Counter_name bilden den Schlüssel für diese Ansicht ein.|Finden Sie unter Node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Der Name des Windows-Leistungsindikator.||  
|counter_category|**nvarchar(255)**|Der Name der Leistungsindikatorkategorie für Windows.||  
|instance_name|**nvarchar(255)**|Name der spezifischen Instanz des Leistungsindikators.||  
|counter_value|**Decimal(38,10)**|Aktueller Wert des Leistungsindikators.||  
|last_update_time|**Datetime2(3)**|Zeitstempel der letzten Aktualisierung der Wert geändert wurde.||  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
