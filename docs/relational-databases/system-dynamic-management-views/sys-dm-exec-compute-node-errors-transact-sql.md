---
description: sys. dm_exec_compute_node_errors (Transact-SQL)
title: sys. dm_exec_compute_node_errors (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_COMPUTE_NODE_ERRORS_TSQL
- DM_EXEC_COMPUTE_NODE_ERRORS
- DM_EXEC_COMPUTE_NODE_ERRORS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase
- PolyBase, views
- dm_exec_compute_node_errors
- sys.dm_exec_compute_node_errors management view
ms.assetid: 9a03c039-70e4-4974-95d8-d3fa45984ffb
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3b12f7bc4dc5cf9328d26c0f81a827731d28c234
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283831"
---
# <a name="sysdm_exec_compute_node_errors-transact-sql"></a>sys. dm_exec_compute_node_errors (Transact-SQL)

[!INCLUDE [sqlserver2016-asdbmi-asa-pdw](../../includes/applies-to-version/sqlserver2016-asa-pdw.md)]

  Gibt Fehler zurück, die auf polybase-Computeknoten auftreten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|error_id|`nvarchar(36)`|Eindeutige numerische ID, die dem Fehler zugeordnet ist.|Eindeutig in allen Abfrage Fehlern im System|  
|source|`nvarchar(255)`|Quellthread oder PROZESSBESCHREIBUNG||  
|type|`nvarchar(255)`|Fehlertyp.||  
|create_time|`datetime`|Der Zeitpunkt des Auftretens des Fehlers.||  
|compute_node_id|`int`|Bezeichner des spezifischen computeknotens|Weitere Informationen finden Sie unter compute_node_id von [sys. dm_exec_compute_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)|  
|rexecution_id|`nvarchar(36)`|Der Bezeichner der polybase-Abfrage, falls vorhanden.||  
|spid|`int`|Bezeichner der SQL Server Sitzung||  
|thread_id|`int`|Numerischer Bezeichner des Threads, in dem der Fehler aufgetreten ist.||  
|Details|nvarchar(4000)|Vollständige Beschreibung der Details des Fehlers.||
|compute_pool_id|`int`|Eindeutiger Bezeichner für den Pool.|

  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
