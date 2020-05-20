---
title: sys. dm_pdw_query_stats_xe (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d551241-db35-4958-b60f-55e996f95c1f
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ba136f705c57fcd5ffbef1433d70ceaefe4e3ae9
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829266"
---
# <a name="sysdm_pdw_query_stats_xe-transact-sql"></a>sys. dm_pdw_query_stats_xe (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Diese DMV ist veraltet und wird in einer zukünftigen Version entfernt. In dieser Version werden 0 Zeilen zurückgegeben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|event|**nvarchar(60)**|Der Schlüssel für diese Ansicht.||  
|event_id|**nvarchar (36)**|||  
|create_time|**datetime**|||  
|session_id|**int**|Die ID für die Sitzung.|Weitere Informationen finden Sie unter session_id in [sys. dm_pdw_exec_sessions &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|cpu|**int**|||  
|Lesevorgänge|**int**|Anzahl logischer Lesevorgänge seit dem Start des Ereignisses.||  
|Schreibvorgänge|**int**|Anzahl logischer Schreibvorgänge seit dem Start des Ereignisses.||  
|sql_text|**nvarchar(4000)**|||  
|client_app_name|**nvarchar(255)**|||  
|tsql_stack|**nvarchar(255)**|||  
|pdw_node_id|**int**|Knoten, auf dem diese XEvent-Instanz ausgeführt wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
