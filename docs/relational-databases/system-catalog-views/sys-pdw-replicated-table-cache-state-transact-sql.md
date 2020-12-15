---
description: sys.pdw_replicated_table_cache_state (Transact-SQL)
title: sys.pdw_replicated_table_cache_state (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 07/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: = azure-sqldw-latest
ms.openlocfilehash: 76b5f9ec684b4733934a8cdd703942f12cf1b541
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97404461"
---
# <a name="syspdw_replicated_table_cache_state-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  Gibt den Status des Caches zurück, der einer replizierten Tabelle durch **object_id** zugeordnet ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Die Objekt-ID für die Tabelle. Weitere Informationen finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** ist der Schlüssel für diese Sicht.||  
|state|**nvarchar(40)**|Der Cache Zustand der replizierten Tabelle für diese Tabelle.|"Notready", "Ready"|  
  
## <a name="example"></a>Beispiel
In diesem Beispiel wird sys.pdw_replicated_table_cache_state mit sys. Tables verbunden, um den Tabellennamen und den Status des replizierten Tabellen Caches abzurufen.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Nächste Schritte  
 Eine Liste aller Katalog Sichten für Azure Synapse-Analysen und parallele Data Warehouse finden Sie unter [Azure-Synapse-Analysen und parallele Data Warehouse-Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
