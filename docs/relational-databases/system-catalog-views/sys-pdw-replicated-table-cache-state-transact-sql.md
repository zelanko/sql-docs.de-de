---
title: pdw_replicated_table_cache_state (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2017
ms.prod: sql
ms.technology: data-warehousee"
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 02fa0d4efa6c90c2bfc5840971d8de7f50cb9a7c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016585"
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Gibt den Status des Caches durch eine replizierte Tabelle zugeordneten **Object_id**.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Die Objekt-ID für die Tabelle. Finden Sie unter [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **Object_id** ist der Schlüssel für diese Sicht.||  
|state|**nvarchar(40)**|Der replizierten Tabelle-Cache-Status für diese Tabelle.|'NotReady','Ready'|  
  
## <a name="example"></a>Beispiel
In diesem Beispiel verknüpft pdw_replicated_table_cache_state mit ' sys.Tables ', um den Namen der Tabelle und den Status des replizierten tabellencaches abzurufen.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Nächste Schritte  
 Eine Übersicht über die Katalogsichten für SQL Data Warehouse und Parallel Data Warehouse finden Sie unter [SQL Data Warehouse und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
