---
title: Sys.pdw_table_distribution_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: cd815a8c96aef11dc33a33e32bb8119c13c35422
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719310"
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>Sys.pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Verteilungsinformationen zur für Tabellen.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Die ID der Tabelle, für die drei Eigenschaften angegeben wurden.||  
|**distribution_policy**|**tinyint**|0 = NICHT DEFINIERT<br /><br /> 1 = KEINE<br /><br /> 2 = HASH<br /><br /> 3 = REPLIZIERT<br /><br /> 4 = ROUND_ROBIN|Replikation gilt nur für [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|  
|**distribution_policy_desc**|**nvarchar(60)**|NICHT DEFINIERT IST, NONE, HASH, REPLIZIEREN, SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Gibt den HASH oder REPLICATE zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
