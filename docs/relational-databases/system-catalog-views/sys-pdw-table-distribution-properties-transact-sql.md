---
title: sys. pdw_table_distribution_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 43974e2ae8becb5ad24daf0c52246a71c890bce2
ms.sourcegitcommit: f8cf8cc6650a22e0b61779c20ca7428cdb23c850
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2019
ms.locfileid: "74822160"
---
# <a name="syspdw_table_distribution_properties-transact-sql"></a>sys. pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Verteilungs Informationen für Tabellen.  
  
|Spaltenname|Datentyp|Beschreibung|Range|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**wartenden**|ID der Tabelle, für die die Eigenschaften angegeben wurden.||  
|**distribution_policy**|**tinyint**|0 = nicht definiert<br /><br /> 1 = None<br /><br /> 2 = Hash<br /><br /> 3 = replizieren<br /><br /> 4 = ROUND_ROBIN||  
|**distribution_policy_desc**|**nvarchar (60)**|nicht definiert, keine, Hash, replizieren, ROUND_ROBIN|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Gibt entweder Hash, ROUND_ROBIN oder replizieren zurück.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
