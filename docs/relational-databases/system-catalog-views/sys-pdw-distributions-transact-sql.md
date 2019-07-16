---
title: Sys.pdw_distributions (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7deddb57cdc02410fe161728f45190492ac18a16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127551"
---
# <a name="syspdwdistributions-transact-sql"></a>sys.pdw_distributions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen über die Verteilungen auf dem Gerät. Sie enthält eine Zeile pro Appliance-Verteilung.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|Eindeutige numerische Id, die die Verteilung.<br /><br /> Der Schlüssel für diese Sicht.|1, um die Anzahl von Computeknoten in Appliance multipliziert die Anzahl von Verteilungen pro Computeknoten.|  
|pdw_node_id|**int**|Die ID des Knotens, die auf diesem Verteilungspunkt befindet.|Finden Sie unter Pdw_node_id in [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|NAME|**nvarchar(32)**|Die Zeichenfolgen Sie-ID, die die Verteilung, als Suffix für verteilte Tabellen verwendet.|Zeichenfolge, die aus der "A – Z", "a – Z", "0-9', '_','-'.|  
|position|**int**|Die Position der Verteilung innerhalb eines Knotens, der je nach anderen Verteilungen auf diesem Knoten.|1, um die Anzahl von Verteilungen pro Knoten.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
