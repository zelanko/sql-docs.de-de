---
description: sys. pdw_index_mappings (Transact-SQL)
title: sys. pdw_index_mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e79b15df940c154d20c2bc6a4ab5218717ddabe5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88400966"
---
# <a name="syspdw_index_mappings-transact-sql"></a>sys. pdw_index_mappings (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Ordnet die logischen Indizes dem physischen Namen zu, der auf Computeknoten verwendet wird. Dies wird durch eine eindeutige Kombination aus **object_id** der Tabelle, die den Index enthält, und der **index_id** eines bestimmten Indexes in dieser Tabelle dargestellt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Die Objekt-ID für die logische Tabelle, für die dieser Index vorhanden ist. Weitere Informationen finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **physical_name** und **object_id** den Schlüssel für diese Ansicht bilden.||  
|index_id|**nvarchar(32)**|Die ID für den Index. Weitere Informationen finden Sie unter [sys. Indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).||  
|physical_name|**nvarchar (36)**|Der Name des Indexes in den Datenbanken auf den Computeknoten.<br /><br /> **physical_name** und **object_id** den Schlüssel für diese Ansicht bilden.||  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys. pdw_table_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys. pdw_database_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
