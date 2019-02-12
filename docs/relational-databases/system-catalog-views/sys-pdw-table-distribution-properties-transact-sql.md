---
title: sys.pdw_table_distribution_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 33d6ad4a8a22186fdf6174a0605eadfe62108dee
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035621"
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>sys.pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Verteilungsinformationen zur für Tabellen.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Die ID der Tabelle, für die drei Eigenschaften angegeben wurden.||  
|**distribution_policy**|**tinyint**|0 = NICHT DEFINIERT<br /><br /> 1 = KEINE<br /><br /> 2 = HASH<br /><br /> 3 = REPLIZIERT<br /><br /> 4 = ROUND_ROBIN|Replikation gilt nur für [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|  
|**distribution_policy_desc**|**nvarchar(60)**|NICHT DEFINIERT IST, NONE, HASH, REPLIZIEREN, SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Gibt den HASH oder REPLICATE zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
