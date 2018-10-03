---
title: pdw_replicated_table_cache_state (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 41d1cbf37418804ef3a39efc268c818f6966c5f8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835468"
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Gibt den Status des Caches durch eine replizierte Tabelle zugeordneten **Object_id**.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Die Objekt-ID für die Tabelle. Finden Sie unter [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **Object_id** ist der Schlüssel für diese Sicht.||  
|state|**nvarchar(40)**|Der replizierten Tabelle-Cache-Status für diese Tabelle.|"NotReady", "Bereit"|  
  
## <a name="example"></a>Beispiel
In diesem Beispiel verknüpft pdw_replicated_table_cache_state mit ' sys.Tables ', um den Namen der Tabelle und den Status des replizierten tabellencaches abzurufen.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Nächste Schritte  
 Eine Übersicht über die Katalogsichten für SQL Data Warehouse und Parallel Data Warehouse finden Sie unter [SQL Data Warehouse und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
