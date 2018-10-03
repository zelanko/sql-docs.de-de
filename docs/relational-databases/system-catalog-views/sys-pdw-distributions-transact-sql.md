---
title: Sys.pdw_distributions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1d2d35873a4950f6a3d7a5c4b911f9b72f67f9ba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841858"
---
# <a name="syspdwdistributions-transact-sql"></a>Sys.pdw_distributions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über die Verteilungen auf dem Gerät. Sie enthält eine Zeile pro Appliance-Verteilung.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Eindeutige numerische Id, die die Verteilung.<br /><br /> Der Schlüssel für diese Sicht.|1, um die Anzahl von Computeknoten in Appliance multipliziert die Anzahl von Verteilungen pro Computeknoten.|  
|pdw_node_id|**int**|Die ID des Knotens, die auf diesem Verteilungspunkt befindet.|Finden Sie unter Pdw_node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|NAME|**nvarchar(32)**|Die Zeichenfolgen Sie-ID, die die Verteilung, als Suffix für verteilte Tabellen verwendet.|Zeichenfolge, die aus der "A – Z", "a – Z", "0-9', '_','-'.|  
|position|**int**|Die Position der Verteilung innerhalb eines Knotens, der je nach anderen Verteilungen auf diesem Knoten.|1, um die Anzahl von Verteilungen pro Knoten.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
