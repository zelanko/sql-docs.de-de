---
description: sys.pdw_distributions (Transact-SQL)
title: sys.pdw_distributions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 054dc5391ce03fc079bae505ec3f8fbe2eca2ea2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461591"
---
# <a name="syspdw_distributions-transact-sql"></a>sys.pdw_distributions (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Informationen zu den Verteilungen auf dem Gerät. Es wird eine Zeile pro Geräte Verteilung aufgelistet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Eindeutige, der Verteilung zugeordnete numerische ID.<br /><br /> Der Schlüssel für diese Ansicht.|1 bis zur Anzahl der Computeknoten in der Appliance multipliziert mit der Anzahl der Verteilungen pro Computeknoten.|  
|pdw_node_id|**int**|ID des Knotens, auf dem sich diese Distribution befindet.|Weitere Informationen finden Sie unter pdw_node_id in [sys.dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|name|**nvarchar(32)**|Der Verteilung zugeordneter Zeichen folgen Bezeichner, der als Suffix für verteilte Tabellen verwendet wird.|Zeichenfolge, die aus "a-z", "a-z", "0-9", "_", "-" besteht.|  
|position|**int**|Die Position der Verteilung innerhalb eines Knotens für andere Verteilungen auf diesem Knoten.|1 bis zur Anzahl der Verteilungen pro Knoten.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
