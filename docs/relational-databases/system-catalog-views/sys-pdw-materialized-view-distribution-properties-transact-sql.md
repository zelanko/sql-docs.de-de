---
description: sys.pdw_materialized_view_distribution_properties (Transact-SQL) (Vorschau)
title: sys.pdw_materialized_view_distribution_properties (Transact-SQL)
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
monikerRange: = azure-sqldw-latest
ms.openlocfilehash: 4c90a8f745b0e67997ad64ad8434d9fe4fa0a27d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472971"
---
# <a name="syspdw_materialized_view_distribution_properties-transact-sql-preview"></a>sys.pdw_materialized_view_distribution_properties (Transact-SQL) (Vorschau)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Zeigt die materialisierten Sichten der Verteilungs Informationen an.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------| 
|object_id|**int**|ID der materialisierten Sicht, für die die Eigenschaften angegeben wurden.| 
|distribution_policy |**tinyint**|2 = Hash</br>4 = ROUND_ROBIN|  
|distribution_policy_desc |**nvarchar(60)**|Hash, ROUND_ROBIN|  
 
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW DATABASE STATE-Berechtigung.
 
## <a name="see-also"></a>Weitere Informationen

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-materialized-view-as-select-transact-sql.md?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/alter-materialized-view-transact-sql.md?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](../../t-sql/queries/explain-transact-sql.md?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](./sys-pdw-materialized-view-mappings-transact-sql.md?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql.md?view=azure-sqldw-latest)   
[Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[In Azure Synapse Analytics unterstützte Systemsichten](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[In Azure Synapse Analytics unterstützte T-SQL-Anweisungen](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)