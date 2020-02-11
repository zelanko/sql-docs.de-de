---
title: sys. dm_pdw_nodes_exec_text_query_plan (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 45f26c9569950c2450318abf546a838632e06f20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73145665"
---
# <a name="sysdm_pdw_nodes_exec_text_query_plan--transact-sql"></a>sys. dm_pdw_nodes_exec_text_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Gibt den Showplan im Textformat für einen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch oder für eine bestimmte Anweisung innerhalb des Batches zurück.

## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**pdw_node_ID**|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|
|**DBID**|**smallint**|ID der Kontextdatenbank, die gültig war, als die diesem Plan entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung kompiliert wurde. Für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen, die ID der Datenbank, in der die Anweisungen kompiliert wurden.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**ObjectID**|**int**|ID des Objekts (z. B. gespeicherte Prozedur oder benutzerdefinierte Funktion) für diesen Abfrageplan. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**Zahl**|**smallint**|Gespeicherte Prozedur mit ganzer Zahl. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.| 
|**.**|**bit**|Zeigt an, ob die entsprechende Prozedur verschlüsselt ist.<br /><br /> 0 = nicht verschlüsselt<br /><br /> 1 = verschlüsselt<br /><br /> NULL-Werte sind in der Spalte nicht zulässig.|  
|**query_plan**|**nvarchar(max)**|Enthält eine zur Kompilierzeit erstellte Showplandarstellung des Abfrageausführungsplans, der mit *plan_handle*angegeben ist. Der Showplan liegt im Textformat vor. Für jeden Batch, der z. B. Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, Aufrufe von gespeicherten Prozeduren und benutzerdefinierten Funktionen enthält, wird jeweils ein Plan generiert.<br /><br /> Die Spalte lässt NULL-Werte zu.|  

## <a name="remarks"></a>Bemerkungen  
Die gleichen Hinweise in [sys. dm_exec_text_query_plan](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql?view=sql-server-ver15) werden angewendet.  

## <a name="permissions"></a>Berechtigungen  
 Erfordert die **sysadmin** -Server `VIEW SERVER STATE` Rolle oder-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Nächste Schritte
 Weitere Hinweise zur Entwicklung finden Sie in der [Entwicklungsübersicht für SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).