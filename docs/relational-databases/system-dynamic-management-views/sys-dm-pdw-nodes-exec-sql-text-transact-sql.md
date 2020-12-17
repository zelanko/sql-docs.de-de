---
title: sys.dm_pdw_nodes_exec_sql_text (Transact-SQL) | Microsoft-Dokumentation
description: Dynamische Verwaltungs Sicht, die den Text des SQL-Batches zurückgibt, der durch die angegebene sql_handle identifiziert wird.
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
monikerRange: =azure-sqldw-latest
ms.openlocfilehash: b4e4c686411d40a2c161c670821e6566460db4a4
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644067"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>sys.pdw_nodes_dm_exec_sql_text (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Gibt den Text des SQL-Batches zurück, der durch die angegebene *sql_handle* identifiziert wird. Diese Tabellenwertfunktion ersetzt die Systemfunktion **fn_get_sql**.  
   
## <a name="table-returned"></a>Zurückgegebene Tabelle  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|
|**DBID**|**smallint**|ID der Datenbank.<br /><br /> Für nicht geplante und vorbereitete SQL-Anweisungen die ID der Datenbank, in der die Anweisungen kompiliert wurden.|  
|**objectid**|**int**|ID des Objekts.<br /><br /> Dieser Wert ist für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen NULL.|  
|**Zahl**|**smallint**|Für eine nummerierte gespeicherte Prozedur gibt diese Spalte die Nummer der gespeicherten Prozedur zurück. Weitere Informationen finden Sie unter [sys.numbered_procedures &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Dieser Wert ist für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen NULL.|  
|**.**|**bit**|1: der SQL-Text ist verschlüsselt.<br /><br /> 0: der SQL-Text ist nicht verschlüsselt.|  
|**text**|**nvarchar(max)**|Text der SQL-Abfrage.<br /><br /> Der Wert ist für verschlüsselte Objekte NULL.|  

## <a name="remarks"></a>Hinweise  
Die gleichen Hinweise in [sys.dm_exec_sql_text](./sys-dm-exec-sql-text-transact-sql.md) gelten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **sysadmin** -Server Rolle oder- `VIEW SERVER STATE` Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure Synapse Analytics und parallele Data Warehouse dynamische Verwaltungs Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Nächste Schritte
 Weitere Tipps zur Entwicklung finden Sie unter [Übersicht über die Entwicklung von Azure Synapse-Analysen](/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).