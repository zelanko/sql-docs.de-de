---
title: sys. pdw_database_mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 46474439474f8a38ba016b16e323b0cb92afe39e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139942"
---
# <a name="syspdw_database_mappings-transact-sql"></a>sys. pdw_database_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Ordnet die **database_id**s der Datenbanken dem physischen Namen zu, der auf Computeknoten verwendet wird, und stellt die **Prinzipal-ID** des Daten Bank Besitzers im System bereit. Verknüpfen Sie **sys. pdw_database_mappings** mit **sys.-Datenbanken** und **sys. pdw_nodes_pdw_physical_databases**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar (36)**|Der physische Name der Datenbank auf den Computeknoten.<br /><br /> **physical_name** und **database_id** den Schlüssel für diese Ansicht bilden.||  
|database_id|**int**|Die Objekt-ID für die Datenbank. Weitere Informationen finden Sie unter [sys. Datenbanken &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).<br /><br /> **physical_name** und **database_id** den Schlüssel für diese Ansicht bilden.||  
  
## <a name="examples-sspdw"></a>Beispiele: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird sys. pdw_database_mappings mit anderen Systemtabellen verknüpft, um anzuzeigen, wie Datenbanken zugeordnet werden.  
  
```  
SELECT DB.database_id, DB.name, Map.*, Phys.*   
FROM sys.databases AS DB  
JOIN sys.pdw_database_mappings AS Map  
    ON DB.database_id = Map.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS Phys  
    ON Map.physical_name = Phys.physical_name  
ORDER BY DB.database_id, Phys.pdw_node_id;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys. pdw_index_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys. pdw_table_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys. pdw_nodes_pdw_physical_databases &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  

