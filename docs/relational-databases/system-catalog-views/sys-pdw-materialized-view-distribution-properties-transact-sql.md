---
title: sys. pdw_materialized_view_distribution_properties (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 5dca3564e8e2ccc83f0968d42c636112880f6e56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401685"
---
# <a name="syspdw_materialized_view_distribution_properties-transact-sql-preview"></a>sys. pdw_materialized_view_distribution_properties (Transact-SQL) (Vorschau)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Zeigt die materialisierten Sichten der Verteilungs Informationen an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------| 
|object_id|**int**|ID der materialisierten Sicht, für die die Eigenschaften angegeben wurden.| 
|distribution_policy |**tinyint**|2 = Hash</br>4 = ROUND_ROBIN|  
|distribution_policy_desc |**nvarchar (60)**|Hash, ROUND_ROBIN|  
 
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW DATABASE STATE-Berechtigung.
 
## <a name="see-also"></a>Weitere Informationen

[Erstellen Sie eine materialisierte Sicht, und wählen Sie &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[Erläuterung &#40;Transact-SQL-&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys. pdw_materialized_view_mappings &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL-&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[In Azure SQL Data Warehouse unterstützte System Sichten](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[T-SQL-Anweisungen, die in Azure SQL Data Warehouse unterstützt werden](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
