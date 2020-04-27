---
title: sys. dm_pdw_os_performance_counters (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8f275d48131ef7011307f39f38d37a8bfff4ea18
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899313"
---
# <a name="sysdm_pdw_os_performance_counters-transact-sql"></a>sys. dm_pdw_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu den Windows-Leistungsindikatoren für die [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Knoten in.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Die ID des Knotens, der den Zählers enthält.<br /><br /> pdw_node_id und counter_name den Schlüssel für diese Ansicht bilden.|Weitere Informationen finden Sie unter node_id in [sys. dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Der Name des Windows-Leistungs Zählers.||  
|counter_category|**nvarchar(255)**|Der Name der Windows-Leistungs Leistungswert Kategorie.||  
|instance_name|**nvarchar(255)**|Name der spezifischen Instanz des Leistungsindikators.||  
|counter_value|**Decimal (38, 10)**|Aktueller Wert des Leistungsindikators.||  
|last_update_time|**Datetime2 (3)**|Zeitstempel des letzten Updates des Werts.||  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
