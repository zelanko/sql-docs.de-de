---
title: INSERT (SQL-Graph) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Syntax, die Berechtigungen und die Argumente für die INSERT-Anweisung, die eine oder mehrere Zeilen zu einem SQL Graph-Knoten oder einer Edgetabelle in SQL Server hinzufügt.
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.custom: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], SQL graph
- SQL graph, INSERT statement
ms.assetid: ''
author: shkale-msft
ms.author: shkale
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7ffd99a9291e35024d1c8a209569e399b71b53de
ms.sourcegitcommit: a4ee6957708089f7d0dda15668804e325b8a240c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87899805"
---
# <a name="insert-sql-graph"></a>INSERT (SQL-Graph)
[!INCLUDE[sqlserver2017-asdb](../../includes/applies-to-version/sqlserver2017-asdb.md)]

Fügt einer `node`- oder `edge`-Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mindestens eine Zeile hinzu. 

> [!NOTE]   
>  Standard Transact-SQL-Anweisungen finden Sie unter [INSERT TABLE (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).
  
![Artikellinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Artikellinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="insert-into-node-table-syntax"></a>INSERT INTO – Syntax für Knotentabellen 
Die Syntax für das Einfügen in eine Knotentabelle entspricht der einer regulären Tabelle. 

```syntaxsql
[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ (column_list) ] | [(<edge_table_column_list>)]  
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
    node_table_name  | edge_table_name
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <on_or_where_search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  

<on_or_where_search_condition> ::=
    {  <search_condition_with_match> | <search_condition> }

<search_condition_with_match> ::=
    { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) }
    [ AND { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<search_condition> ::=
    { [ NOT ] <predicate> | ( <search_condition> ) }
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<graph_predicate> ::=
    MATCH( <graph_search_pattern> [ AND <graph_search_pattern> ] [ , ...n] )

<graph_search_pattern>::=
    <node_alias> { { <-( <edge_alias> )- | -( <edge_alias> )-> } <node_alias> }

<edge_table_column_list> ::=
    ($from_id, $to_id, [column_list])

```  
  
 
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
In diesem Artikel werden Argumente für SQL-Graph beschrieben. Eine vollständige Liste und Beschreibung der unterstützten Argumente in der INSERT-Anweisung finden Sie unter [INSERT TABLE (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).

INTO  
Ein optionales Schlüsselwort, das zwischen `INSERT` und der Zieltabelle verwendet werden kann.  
  
*search_condition_with_match*   
Die `MATCH`-Klausel kann während des Einfügens in eine Knoten- oder Edgetabelle in einer geschachtelten Abfrage verwendet werden. Die `MATCH`-Abfragesyntax finden Sie unter [GRAPH MATCH (Transact-SQL)](../../t-sql/queries/match-sql-graph.md).

*graph_search_pattern*   
Suchmuster, das der `MATCH`-Klausel als Teil des Graph-Prädikats bereitgestellt wird.

*edge_table_column_list*   
Benutzer müssen Werte für `$from_id` und `$to_id` angeben, wenn sie etwas in eine Edgetabelle einfügen. Wenn kein Wert angegeben oder NULL in eine dieser Spalten eingefügt wird, wird ein Fehler zurückgegeben. 
  

## <a name="remarks"></a>Bemerkungen  
Das Einfügen in eine Knotentabelle entspricht dem Einfügen in eine relationale Tabelle. Werte für die $node_id-Spalte werden automatisch generiert.

Beim Einfügen in eine Edgetabelle müssen Benutzer Werte für die Spalten `$from_id` und `$to_id` angeben.   

Masseneinfügung in Knotentabellen entspricht der Masseneinfügung in eine relationale Tabelle.

Vor der Masseneinfügung in eine Edgetabelle müssen die Knotentabellen importiert werden. Anschließend können Werte für `$from_id` und `$to_id` aus der `$node_id`-Spalte der Knotentabelle extrahiert werden und als Edges eingefügt werden. 

  
### <a name="permissions"></a>Berechtigungen  
Die INSERT-Berechtigung ist für die Zieltabelle erforderlich.  
  
Mitglieder der festen Serverrolle **sysadmin**, der festen Datenbankrollen **db_owner** und **db_datawriter** und der Tabellenbesitzer erhalten standardmäßig INSERT-Berechtigungen. Mitglieder der Rollen **sysadmin**, **db_owner** und **db_securityadmin** sowie der Tabellenbesitzer können Berechtigungen an andere Benutzer übertragen.  
  
Zum Ausführen von INSERT mit der Option BULK der OPENROWSET-Funktion müssen Sie Mitglied der festen Serverrolle **sysadmin** oder der festen Serverrolle **bulkadmin** sein.  
  

## <a name="examples"></a>Beispiele  
  
#### <a name="a--insert-into-node-table"></a>A.  Einfügen in Knotentabellen  
Im folgenden Beispiel wird eine Knotentabelle für Personen erstellt, und es werden zwei Reihen in diese Tabelle eingefügt.

```sql
-- Create person node table
CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 
-- Insert records for Alice and John
INSERT INTO dbo.Person VALUES (1, 'Alice');
INSERT INTO dbo.Person VALUES (2,'John');
```
  
#### <a name="b--insert-into-edge-table"></a>B.  Einfügen in Edgetabellen  
Im folgenden Beispiel wird eine Edgetabelle für Freunde erstellt und ein Edge in diese Tabelle eingefügt.

```sql
-- Create friend edge table
CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

-- Create a friend edge, that connect Alice and John
INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');
```

  
## <a name="see-also"></a>Weitere Informationen  
[INSERT TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
[Graph Processing with SQL Server 2017 (Graph-Verarbeitung mit SQL Server-2017)](../../relational-databases/graphs/sql-graph-overview.md)  


