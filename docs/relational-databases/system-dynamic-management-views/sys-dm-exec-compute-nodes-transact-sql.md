---
description: sys. dm_exec_compute_nodes (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 62591df1ce4a2a048c544b219f7efcc3fe18aa61
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283657"
---
# <a name="sysdm_exec_compute_nodes-transact-sql"></a>sys. dm_exec_compute_nodes (Transact-SQL)

[!INCLUDE [sqlserver2016-asa-pdw](../../includes/applies-to-version/sqlserver2016-asa-pdw.md)]

  Enthält Informationen zu Knoten, die mit der polybase-Datenverwaltung verwendet werden. Sie listet eine Zeile pro Knoten auf.  
  
 Verwenden Sie diese DMV, um die Liste aller Knoten im Cluster mit horizontaler Skalierung mit ihrer Rolle, dem Namen und der IP-Adresse anzuzeigen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist. Der Schlüssel für diese Ansicht.|Eindeutig in einem Cluster mit horizontaler Skalierung (unabhängig vom Typ).|  
|type|**nvarchar(32)**|Der Typ des Knotens.|"Compute", "Head"|  
|name|**nvarchar(32)**|Logischer Name des Knotens.|Eine beliebige Zeichenfolge mit entsprechender Länge.|  
|address|**nvarchar(32)**|Die IP-Adresse dieses Knotens.|IP-Adressbereich|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
