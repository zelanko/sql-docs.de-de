---
title: CREATE MATERIALIZED VIEW AS SELECT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: data-warehouse
ms.topic: language-reference
f1_keywords:
- CREATE VIEW
- VIEW_TSQL
- VIEW
- CREATE_VIEW_TSQL
- SCHEMABINDING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- table creation [SQL Server], CREATE VIEW
- views [SQL Server], creating
- CREATE VIEW statement
- updatable partitioned views
- tables [SQL Server], virtual
- updatable views
- modifying partitioned views
- virtual tables [SQL Server]
- number of columns per view
- partitioned views [SQL Server], creating
- WITH ENCRYPTION clause
- WITH CHECK OPTION clause
- partitioned views [SQL Server], modifying
- partitioned views [SQL Server], replication
- distributed partitioned views [SQL Server]
- views [SQL Server], indexed views
- maximum number of columns per view
ms.assetid: aecc2f73-2ab5-4db9-b1e6-2f9e3c601fb9
author: XiaoyuL-Preview
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 076bf71586baa61e8bb77c093cd274eca898bf00
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912621"
---
# <a name="create-materialized-view-as-select-transact-sql-preview"></a>CREATE MATERIALIZED VIEW AS SELECT (Transact-SQL) (Vorschau)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Dieser Artikel beschreibt die T-SQL-Anweisung CREATE MATERIALIZED VIEW AS SELECT in Azure SQL Data Warehouse für die Entwicklung von Lösungen. Der Artikel enthält auch Codebeispiele.

Eine materialisierte Sicht behält die von der Sichtdefinitionsabfrage zurückgegebenen Daten bei und wird automatisch aktualisiert, wenn sich Daten in den zugrunde liegenden Tabellen ändern.   Auf diese Weise wird die Leistung komplexer Abfragen (typischerweise Abfragen mit Joins und Aggregationen) verbessert, während gleichzeitig einfache Wartungsvorgänge bereitgestellt werden.   Dank der Funktion zum automatischen Abgleich ihres Ausführungsplans muss eine materialisierte Sicht nicht in der Abfrage referenziert werden, damit der Optimierer die Sicht für Ersetzungen berücksichtigt.  Dadurch können Dateningenieure materialisierte Ansichten als Mechanismus zur Verbesserung der Antwortzeit von Abfragen implementieren, ohne die Abfragen ändern zu müssen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
CREATE MATERIALIZED VIEW [ schema_name. ] materialized_view_name
    WITH (  
      <distribution_option>
    )
    AS <select_statement>
[;]

<distribution_option> ::=
    {  
        DISTRIBUTION = HASH ( distribution_column_name )  
      | DISTRIBUTION = ROUND_ROBIN  
    }

<select_statement> ::=
    SELECT select_criteria
```  
  
## <a name="arguments"></a>Argumente

*schema_name*     
 Ist der Name des Schemas, zu dem die Sicht gehört.  
  
*materialized_view_name*   
Der Name der Sicht. Sichtnamen müssen den Regeln für Bezeichner entsprechen. Das Angeben des Sichtbesitzernamens ist optional.  

*distribution_option*     
Es werden nur HASH- und ROUND_ROBIN-Distributionen unterstützt.

*select_statement*   
Die SELECT-Liste in der Definition der materialisierten Sicht muss mindestens eines von diesen zwei Kriterien erfüllen:
- Die SELECT-Liste enthält eine Aggregatfunktion.
- GROUP BY wird in der Definition der materialisierten Sicht verwendet, und alle Spalten in GROUP BY sind in der SELECT-Liste enthalten.  

Aggregatfunktionen sind in der SELECT-Liste der Definition der materialisierten Sicht erforderlich.  Zu den unterstützten Aggregationen gehören MAX, MIN, AVG, COUNT, COUNT_BIG, SUM, VAR, STDEV.

Wenn MIN/MAX-Aggregate in der SELECT-Liste der Definition der materialisierten Sicht verwendet werden, gelten die folgenden Anforderungen:
 
- FOR_APPEND ist erforderlich.  Beispiel:
  ```sql 
  CREATE MATRIALIZED VIEW mv_test2  
  WITH (distribution = hash(i_category_id), FOR_APPEND)  
  AS
  SELECT MAX(i.i_rec_start_date) as max_i_rec_start_date, MIN(i.i_rec_end_date) as min_i_rec_end_date, i.i_item_sk, i.i_item_id, i.i_category_id
  FROM syntheticworkload.item i  
  GROUP BY i.i_item_sk, i.i_item_id, i.i_category_id
  ```

- Die materialisierte Sicht wird bei einem UPDATE oder DELETE in den referenzierten Basistabellen deaktiviert.  Diese Einschränkung gilt nicht für INSERT-Vorgänge.  Um die materialisierte Sicht erneut zu aktivieren, führen Sie ALTER MATERIALIZED INDEX mit REBUILD aus.
  
## <a name="remarks"></a>Remarks

Eine materialisierte Sicht in Azure Data Warehouse ähnelt in vielerlei Punkten einer indizierten Sicht in SQL Server.  Es gelten fast die gleichen Einschränkungen wie für eine indizierte Sicht (Details siehe [Erstellen indizierter Sichten](/sql/relational-databases/views/create-indexed-views)) – abgesehen davon, dass eine materialisierte Sicht Aggregatfunktionen unterstützt.   Nachfolgend werden einige weitere Überlegungen zu materialisierten Sichten aufgeführt.  
 
Eine materialisierte Sicht unterstützt nur CLUSTERED COLUMNSTORE INDEX. 
 
Eine materialisierte Sicht kann über DROP VIEW gelöscht werden.  Sie können eine materialisierte Sicht mit ALTER MATERIALIZED VIEW deaktivieren oder neu erstellen.   
 
Materialisierte Sichten können für partitionierte Tabellen erstellt werden.  SPLIT/MERGE-Vorgänge werden für Tabellen unterstützt, die in materialisierten Sichten referenziert werden.  SWITCH wird nicht für Tabellen unterstützt, die in materialisierten Sichten referenziert werden. Bei einem Versuch der Verwendung wird dem Benutzer dieser Fehler angezeigt: `Msg 106104, Level 16, State 1, Line 9`
 
ALTER TABLE SWITCH wird nicht für Tabellen unterstützt, die in materialisierten Sichten referenziert werden. Deaktivieren oder löschen Sie die materialisierte Sicht, bevor Sie ALTER TABLE SWITCH verwenden. In den folgenden Szenarien erfordert das Erstellen der materialisierten Sicht das Hinzufügen neuer Spalten zur materialisierten Sicht:

|Szenario|Der materialisierten Sicht neu hinzuzufügende Spalten|Anmerkung|  
|-----------------|---------------|-----------------|
|COUNT_BIG() | Fehlt in der SELECT-List der Definition einer materialisierten Sicht. |COUNT_BIG (*) |Wird beim Erstellen der materialisierten Sicht automatisch hinzugefügt.  Es ist keine Benutzeraktion erforderlich.|
|SUM(a) wird von Benutzern in der SELECT-Liste der Definition einer materialisierten Sicht angegeben, und „a“ ist ein Ausdruck, der NULL-Werte zulässt. |COUNT_BIG (a) |Benutzer müssen der Definition der materialisierten Sicht den Ausdruck „a“ manuell hinzufügen.|
|AVG(a) wird von Benutzern in der SELECT-Liste der Definition einer materialisierten Sicht angegeben, „a“ ist hierbei ein Ausdruck, der NULL-Werte zulässt.|SUM(a), COUNT_BIG(a)|Wird beim Erstellen der materialisierten Sicht automatisch hinzugefügt.  Es ist keine Benutzeraktion erforderlich.|
|STDEV(a) wird von Benutzern in der SELECT-Liste der Definition einer materialisierten Sicht angegeben, „a“ ist hierbei ein Ausdruck.|SUM(a),  
COUNT_BIG(a) SUM(square(a))|Wird beim Erstellen der materialisierten Sicht automatisch hinzugefügt.  Es ist keine Benutzeraktion erforderlich. |
| | | |

Nach ihrer Erstellung werden materialisierte Sichten in SQL Server Management Studio unterhalb des Ordners mit Sichten der Azure SQL Data Warehouse-Instanz angezeigt.

Benutzer können [SP_SPACEUSED](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql?view=azure-sqldw-latest) und [DBCC PDW_SHOWSPACEUSED](/sql/t-sql/database-console-commands/dbcc-pdw-showspaceused-transact-sql?view=azure-sqldw-latest) ausführen, um den von einer materialisierten Sicht verbrauchten Speicherplatz zu bestimmen.  

Der EXPLAIN-Plan und der grafische Plan zur geschätzten Ausführung in SQL Server Management Studio können zeigen, ob eine materialisierte Sicht vom Abfrageoptimierer bei der Abfrageausführung berücksichtigt wird.

Um herauszufinden, ob eine SQL-Anweisung von einer neuen materialisierten Sicht profitieren kann, führen Sie den `EXPLAIN`-Befehl mit `WITH_RECOMMENDATIONS` aus.  Ausführliche Informationen finden Sie unter [EXPLAIN (Transact-SQL)](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest).

## <a name="permissions"></a>Berechtigungen

Erfordert die CREATE VIEW-Berechtigung in der Datenbank und die ALTER-Berechtigung für das Schema, in dem die Sicht erstellt wird. 
  
## <a name="see-also"></a>Siehe auch

[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[In Azure SQL Data Warehouse unterstützte Systemsichten](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[In Azure SQL Data Warehouse unterstützte T-SQL-Anweisungen](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
