---
title: Sys.dm_exec_compute_node_errors (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d0d43906eb78399fae10e0e6db2f8e9db7cc3d4e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085192"
---
# <a name="sysdmexeccomputenodeerrors-transact-sql"></a>Sys.dm_exec_compute_node_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Gibt Fehler für PolyBase-Computeknoten.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar(36)**|Eindeutige numerische Id des Fehlers.|Eindeutig für alle Abfragefehler im system|  
|Quelle|**nvarchar(255)**|Source-Prozess oder Thread-Beschreibung||  
|Typ|**nvarchar(255)**|Fehlertyp.||  
|create_time|**datetime**|Zeitpunkt der der Fehler aufgetreten||  
|compute_node_id|**int**|Bezeichner für den spezifischen Compute-Knoten|Finden Sie unter Compute_node_id von [dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)|  
|rexecution_id|**nvarchar(36)**|Der Bezeichner der PolyBase-Abfrage, sofern vorhanden.||  
|spid|**int**|ID der SQL Server-Sitzung||  
|thread_id|**int**|Numerischer Bezeichner des Threads auf dem der Fehler aufgetreten ist.||  
|Details|nvarchar(4000)|Vollständige Beschreibung der Details des Fehlers.||  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
