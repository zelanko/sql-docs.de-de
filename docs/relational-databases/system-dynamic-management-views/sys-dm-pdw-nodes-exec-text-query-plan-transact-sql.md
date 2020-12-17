---
title: sys.dm_pdw_nodes_exec_text_query_plan (Transact-SQL) | Microsoft-Dokumentation
description: Dynamische Verwaltungs Sicht, die den Showplan im Textformat für einen unql-Batch oder für eine bestimmte Anweisung innerhalb des Batches zurückgibt.
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
ms.openlocfilehash: 5ecfdb5747eee9fc12934f3514b3df4b74cd8d46
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644043"
---
# <a name="sysdm_pdw_nodes_exec_text_query_plan--transact-sql"></a>sys.dm_pdw_nodes_exec_text_query_plan (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Gibt den Showplan im Textformat für einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch oder für eine bestimmte Anweisung innerhalb des Batches zurück.

## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**pdw_node_ID**|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|
|**DBID**|**smallint**|ID der Kontextdatenbank, die gültig war, als die diesem Plan entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung kompiliert wurde. Für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen, die ID der Datenbank, in der die Anweisungen kompiliert wurden.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**objectid**|**int**|ID des Objekts (z. B. gespeicherte Prozedur oder benutzerdefinierte Funktion) für diesen Abfrageplan. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**Zahl**|**smallint**|Gespeicherte Prozedur mit ganzer Zahl. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.| 
|**.**|**bit**|Zeigt an, ob die entsprechende Prozedur verschlüsselt ist.<br /><br /> 0 = nicht verschlüsselt<br /><br /> 1 = verschlüsselt<br /><br /> NULL-Werte sind in der Spalte nicht zulässig.|  
|**query_plan**|**nvarchar(max)**|Enthält eine zur Kompilierzeit erstellte Showplandarstellung des Abfrageausführungsplans, der mit *plan_handle* angegeben ist. Der Showplan liegt im Textformat vor. Für jeden Batch, der z. B. Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, Aufrufe von gespeicherten Prozeduren und benutzerdefinierten Funktionen enthält, wird jeweils ein Plan generiert.<br /><br /> Die Spalte lässt NULL-Werte zu.|  

## <a name="remarks"></a>Hinweise  
Die gleichen Hinweise in [sys.dm_exec_text_query_plan](./sys-dm-exec-text-query-plan-transact-sql.md) gelten.  

## <a name="permissions"></a>Berechtigungen  
 Erfordert die **sysadmin** -Server Rolle oder- `VIEW SERVER STATE` Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure Synapse Analytics und parallele Data Warehouse dynamische Verwaltungs Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Nächste Schritte
 Weitere Tipps zur Entwicklung finden Sie unter [Übersicht über die Entwicklung von Azure Synapse-Analysen](/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).