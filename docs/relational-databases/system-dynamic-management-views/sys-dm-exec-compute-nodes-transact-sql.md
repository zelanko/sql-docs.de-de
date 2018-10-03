---
title: dm_exec_compute_nodes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODES_TSQL
- DM_EXEC_COMPUTE_NODES
- SYS.DM_EXEC_COMPUTE_NODES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_nodes management view
- PolyBase, views
- PolyBase management views
- dm_exec_compute_nodes management view
ms.assetid: 0de4b7a4-401f-4e2d-9ab0-c54587e05154
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e09741600a63596d9b486ebf2d36a808e7981a87
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753118"
---
# <a name="sysdmexeccomputenodes-transact-sql"></a>dm_exec_compute_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über Knoten mit PolyBase die datenverwaltung verwendet. Sie enthält eine Zeile pro Knoten.  
  
 Verwenden Sie diese dynamische Verwaltungssicht, um die Liste aller Knoten im Cluster Horizontales Skalieren mit ihrer Rolle, die Namen und die IP-Adresse anzuzeigen.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Eindeutige numerische Id, die dem Knoten zugeordnet. Der Schlüssel für diese Sicht.|Eindeutig erweiterungscluster unabhängig von der Art.|  
|Typ|**nvarchar(32)**|Der Typ des Knotens.|"COMPUTE", "HEAD"|  
|NAME|**nvarchar(32)**|Logischer Name des Knotens.|Jede Zeichenfolge der Länge der entsprechenden.|  
|address|**nvarchar(32)**|P-Adresse dieses Knotens.|IP-Adressbereich|  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
