---
description: sys.pdw_table_distribution_properties (Transact-SQL)
title: sys.pdw_table_distribution_properties (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: e5a4c129ab6224872293e5bd4cfd9a1b87a378f5
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97412018"
---
# <a name="syspdw_table_distribution_properties-transact-sql"></a>sys.pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Verteilungs Informationen für Tabellen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|ID der Tabelle, für die die Eigenschaften angegeben wurden.||  
|**distribution_policy**|**tinyint**|0 = nicht definiert<br /><br /> 1 = None<br /><br /> 2 = Hash<br /><br /> 3 = replizieren<br /><br /> 4 = ROUND_ROBIN||  
|**distribution_policy_desc**|**nvarchar(60)**|nicht definiert, keine, Hash, replizieren, ROUND_ROBIN|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Gibt entweder Hash, ROUND_ROBIN oder replizieren zurück.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
