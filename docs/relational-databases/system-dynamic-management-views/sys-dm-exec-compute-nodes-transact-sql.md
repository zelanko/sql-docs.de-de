---
title: sys. dm_exec_compute_nodes (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 44664805dc9b728ecbd48acbf38c4565601c631a
ms.sourcegitcommit: 4c7151f9f3f341f8eae70cb2945f3732ddba54af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71326149"
---
# <a name="sysdm_exec_compute_nodes-transact-sql"></a>sys. dm_exec_compute_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu Knoten, die mit der polybase-Datenverwaltung verwendet werden. Sie listet eine Zeile pro Knoten auf.  
  
 Verwenden Sie diese DMV, um die Liste aller Knoten im Cluster mit horizontaler Skalierung mit ihrer Rolle, dem Namen und der IP-Adresse anzuzeigen.  
  
|Column Name|Datentyp|und Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist. Der Schlüssel für diese Ansicht.|Eindeutig in einem Cluster mit horizontaler Skalierung (unabhängig vom Typ).|  
|type|**nvarchar(32)**|Der Typ des Knotens.|"Compute", "Head"|  
|name|**nvarchar(32)**|Logischer Name des Knotens.|Eine beliebige Zeichenfolge mit entsprechender Länge.|  
|address|**nvarchar(32)**|Die IP-Adresse dieses Knotens.|IP-Adressbereich|  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten &#40;in Verbindung mit der Datenbank Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
