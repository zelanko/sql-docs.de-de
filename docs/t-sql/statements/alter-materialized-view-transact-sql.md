---
description: ALTER MATERIALIZED VIEW (Transact-SQL)
title: ALTER MATERIALIZED VIEW (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: jrasnick
ms.technology: data-warehouse
ms.topic: language-reference
f1_keywords:
- ALTER_VIEW_TSQL
- ALTER VIEW
dev_langs:
- TSQL
helpviewer_keywords:
- indexed views [SQL Server], modifying
- views [SQL Server], modifying
- modifying views
- ALTER VIEW statement
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 3dd2ed6aab24741144c8c96c1db29079b46b16c5
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379635"
---
# <a name="alter-materialized-view-transact-sql"></a>ALTER MATERIALIZED VIEW (Transact-SQL)  

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Ändert eine zuvor erstellte materialisierte Sicht. ALTER VIEW wirkt sich nicht auf abhängige gespeicherte Prozeduren oder Trigger aus und ändert keine Berechtigungen.  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
ALTER MATERIALIZED VIEW [ schema_name . ] view_name
{
      REBUILD | DISABLE
}
[;]
```  
  
## <a name="arguments"></a>Argumente

 *schema_name*     
 Ist der Name des Schemas, zu dem die Sicht gehört.  
  
 *view_name*     
 Der Name der zu ändernden materialisierten Sicht.  
  
*REBUILD*   
Erstellt die materialisierte Sicht neu.

*DISABLE*   
Hält die Verwaltung der materialisierten Sicht an, aber behält Metadaten und Berechtigungen bei.Alle Abfragen einer materialisierten Sicht im deaktivierten Status werden für die zugrunde liegenden Tabellen aufgelöst.
  
## <a name="permissions"></a>Berechtigungen

Erfordert die ALTER-Berechtigung für die Tabelle oder Sicht.
  
## <a name="examples"></a>Beispiele

Dieses Beispiel deaktiviert eine materialisierte Sicht und versetzt sie in den angehaltenen Modus.
  
```sql
ALTER MATERIALIZED VIEW My_Indexed_View DISABLE;  
```  
  
Dieses Beispiel setzt eine materialisierte Sicht fort, indem sie neu erstellt wird.  
  
```sql
ALTER MATERIALIZED VIEW My_Indexed_View REBUILD;  
```  
  
## <a name="see-also"></a>Weitere Informationen

[Leistungsoptimierung durch materialisierte Sicht](/azure/sql-data-warehouse/performance-tuning-materialized-views)   
[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[[!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)]- und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]-Ansichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[In [!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)] unterstützte Systemansichten](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[In [!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)] unterstützte T-SQL-Anweisungen](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
