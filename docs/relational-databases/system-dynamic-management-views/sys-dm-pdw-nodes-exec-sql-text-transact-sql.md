---
title: sys.dm_pdw_nodes_exec_sql_text (Transact-SQL) | Microsoft Docs
description: Dynamic management view that returns the text of the SQL batch that is identified by the specified sql_handle.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: fd886217b2fb2caf0fe3f32e88b7bf0215ece1a9
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145675"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>sys.pdw_nodes_dm_exec_sql_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Returns the text of the SQL batch that is identified by the specified *sql_handle*. This table-valued function replaces the system function **fn_get_sql**.  
   
## <a name="table-returned"></a>Table returned  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Unique numeric ID associated with the node.|
|**dbid**|**smallint**|ID der Datenbank.<br /><br /> For unplanned and prepared SQL statements, the ID of the database where the statements were compiled.|  
|**objectid**|**int**|ID of object.<br /><br /> Dieser Wert ist für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen NULL.|  
|**number**|**smallint**|Für eine nummerierte gespeicherte Prozedur gibt diese Spalte die Nummer der gespeicherten Prozedur zurück. For more information, see [sys.numbered_procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Dieser Wert ist für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen NULL.|  
|**encrypted**|**bit**|1: SQL text is encrypted.<br /><br /> 0: SQL text is not encrypted.|  
|**text**|**nvarchar(max)**|Text der SQL-Abfrage.<br /><br /> Der Wert ist für verschlüsselte Objekte NULL.|  

## <a name="remarks"></a>Bemerkungen  
The same remarks in [sys.dm_exec_sql_text](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql?view=sql-server-ver15) apply.  
  
## <a name="permissions"></a>Berechtigungen  
 Require **sysadmin** server role or `VIEW SERVER STATE` permission on the server.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Data Warehouse and Parallel Data Warehouse Dynamic Management Views &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Nächste Schritte
 For more development tips, see [SQL Data Warehouse development overview](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).