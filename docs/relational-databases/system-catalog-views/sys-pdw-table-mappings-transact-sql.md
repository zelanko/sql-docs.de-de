---
title: sys. pdw_table_mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/01/2018
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1af14fe0-e562-4f48-a7f0-783f300a88ac
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1e8a4b17ad9f37546697714af9611b7e8dbf20c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068122"
---
# <a name="syspdw_table_mappings-transact-sql"></a>sys. pdw_table_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Verknüpft Benutzer Tabellen mit internen Objektnamen **object_id**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar (36)**|Der physische Name für die Tabelle.<br /><br /> **physical_name** und **object_id** den Schlüssel für diese Ansicht bilden.||  
|object_id|**int**|Die Objekt-ID für die Tabelle. Weitere Informationen finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **physical_name** und **object_id** den Schlüssel für diese Ansicht bilden.||  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys. pdw_index_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys. pdw_database_mappings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
