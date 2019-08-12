---
title: DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD  (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: ddbb104690c4ded69b1c15628e2f509644c11cb3
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68809871"
---
# <a name="dbcc-pdw_showmaterializedviewoverhead-transact-sql-preview"></a>DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD (Transact-SQL) (Vorschau)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Zeigt die Anzahl inkrementeller Änderungen in den Basistabellen an, die für die materialisierten Sichten in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] gespeichert werden. Das Overheadverhältnis wird als TOTAL_ROWS / MAX (1, BASE_VIEW_ROWS) berechnet.

![Symbol zum Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol zum Themenlink") [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41; (Transact-SQL-Syntaxkonventionen (Transact-SQL))](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax

```
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ( " [ schema_name .] materialized_view_name  " )
[;]
```
  
## <a name="arguments"></a>Argumente

 *schema_name*     
 Ist der Name des Schemas, zu dem die Sicht gehört.

*materialized_view_name*   
Der Name der materialisierten Sicht.

## <a name="remarks"></a>Remarks

Bei einer Änderung der zugrunde liegenden Tabellen in der Definition einer materialisierten Sicht bleiben alle inkrementellen Änderungen in den Basistabellen für die materialisierte Sicht erhalten.  Die Auswahl einer materialisierten Sicht schließt das Überprüfen der gruppierten Columnstore-Struktur für die materialisierte Struktur und das Anwenden dieser inkrementellen Änderungen ein.   Wenn eine große Anzahl von inkrementellen Änderungen beibehalten wurden, setzt dies die Leistung bei Auswahlvorgängen herab.  Benutzer können die materialisierte Sicht neu erstellen, um die gruppierte Columnstore-Struktur neu zu erstellen und alle inkrementellen Änderungen in den Basistabellen zu konsolidieren.
  
## <a name="permissions"></a>Berechtigungen  
  
Erfordert die VIEW DATABASE STATE-Berechtigung.  

## <a name="example"></a>Beispiel  

Dieses Beispiel gibt den verwendeten Deltaspeicher für eine materialisierte Sicht zurück.

```sql
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ( "dbo.MyIndexedView" )
```

Ausgabe:

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|1234|1|3 |3.0 |

</br>

|OBJECT_ID |BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|
|4567|0|0|0.0|

</br>

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|
|789|0|2|2.0|

## <a name="see-also"></a>Siehe auch

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[In Azure SQL Data Warehouse unterstützte Systemsichten](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[In Azure SQL Data Warehouse unterstützte T-SQL-Anweisungen](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)