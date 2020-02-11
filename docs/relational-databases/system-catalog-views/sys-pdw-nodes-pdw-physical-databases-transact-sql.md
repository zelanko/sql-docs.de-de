---
title: sys. pdw_nodes_pdw_physical_databases (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 03/09/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 70e0939d-4d97-4ae0-ba16-934e0a80e718
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 48f2a2d485f99b91b0f30a6a707a900ccbbeea96
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74399909"
---
# <a name="syspdw_nodes_pdw_physical_databases-transact-sql"></a>sys. pdw_nodes_pdw_physical_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält eine Zeile für jede physische Datenbank auf einem Computeknoten. Aggregieren physischer Datenbankinformationen, um ausführliche Informationen zu Datenbanken zu erhalten. Um Informationen zu kombinieren, `sys.pdw_nodes_pdw_physical_databases` verknüpfen Sie `sys.pdw_database_mappings` den `sys.databases` mit den Tabellen und.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Die Objekt-ID für die Datenbank. Beachten Sie, dass dieser Wert nicht mit einem database_id in der [&#41;Sicht sys. Datenbanken &#40;Transact-SQL](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) übereinstimmt.|  
|physical_name|**sysname**|Der physische Name der Datenbank auf der Shell/den Computeknoten. Dieser Wert ist identisch mit einem Wert in der Spalte physical_name in der [&#41;Ansicht sys. pdw_database_mappings &#40;Transact-SQL](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md) .|  
|pdw_node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-returning"></a>A. Rückreise  
 Die folgende Abfrage gibt den Namen und die ID der einzelnen Datenbanken in der Master-Datenbank sowie den entsprechenden Datenbanknamen auf jedem Computeknoten zurück.  
  
```  
SELECT D.database_id AS DBID_in_master, D.name AS UserDatabaseName,   
PD.pdw_node_id AS NodeID, DM.physical_name AS PhysDBName   
FROM sys.databases AS D  
JOIN sys.pdw_database_mappings AS DM  
    ON D.database_id = DM.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON DM.physical_name = PD.physical_name  
ORDER BY D.database_id, PD.pdw_node_ID;  
```  
  
### <a name="b-using-syspdw_nodes_pdw_physical_databases-to-gather-detailed-object-information"></a>B. Sammeln von detaillierten Objektinformationen mithilfe von sys. pdw_nodes_pdw_physical_databases  
 Die folgende Abfrage zeigt Informationen zu Indizes an und enthält nützliche Informationen über die Datenbank, zu denen die Objekte zu Objekten in der Datenbank gehören.  
  
```  
SELECT D.name AS UserDatabaseName, D.database_id AS DBIDinMaster,  
DM.physical_name AS PhysDBName, PD.pdw_node_id AS NodeID,   
IU.object_id, IU.index_id, IU.user_seeks, IU.user_scans, IU.user_lookups, IU.user_updates  
FROM sys.databases AS D  
JOIN sys.pdw_database_mappings AS DM  
    ON D.database_id = DM.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON DM.physical_name = PD.physical_name  
JOIN sys.dm_pdw_nodes_db_index_usage_stats AS IU  
    ON PD.database_id = IU.database_id  
ORDER BY D.database_id, IU.object_id, IU.index_id, PD.pdw_node_ID;  
```  
  
### <a name="c-using-syspdw_nodes_pdw_physical_databases-to-determine-the-encryption-state"></a>C. Ermitteln des Verschlüsselungs Zustands mithilfe von sys. pdw_nodes_pdw_physical_databases  
 Die folgende Abfrage stellt den Verschlüsselungs Status der AdventureWorksPDW2012-Datenbank bereit.  
  
```  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
            ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM  dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. pdw_database_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  

