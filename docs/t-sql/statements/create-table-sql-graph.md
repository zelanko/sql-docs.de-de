---
title: CREATE TABLE (SQL-Graph) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/09/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SQL_GRAPH_TSQL
- TABLE
- CREATE_TABLE_TSQL
- NODE
- NODE_TSQL
- AS_NODE
- AS_NODE_TSQL
- EDGE
- EDGE_TSQL
- AS_EDGE
- AS_EDGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- graph
- SQL graph
- CREATE TABLE SQL graph
- NODE
- EDGE
- SQL graph, CREATE TABLE statement
ms.assetid: ''
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 053e3f5b7d800a2113165de6bb873a19ecd63906
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632904"
---
# <a name="create-table-sql-graph"></a>CREATE TABLE (SQL-Graph)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Erstellt entweder als `NODE`- oder `EDGE`-Tabelle eine neue SQL-Graph-Tabelle. 
  
> [!NOTE]   
>  Standardanweisungen für Transact-SQL finden Sie unter [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
CREATE TABLE   
    { database_name.schema_name.table_name | schema_name.table_name | table_name }
    ( { <column_definition> } 
       | <computed_column_definition>
       | <column_set_definition>
       | [ <table_constraint> ] [ ,... n ]
       | [ <table_index> ] }
          [ ,...n ]
    )   
    AS [ NODE | EDGE ]
    [ ON { partition_scheme_name ( partition_column_name )
           | filegroup
           | "default" } ]
[ ; ] 

< table_constraint > ::=
[ CONSTRAINT constraint_name ]
{
    { PRIMARY KEY | UNIQUE }
        [ CLUSTERED | NONCLUSTERED ]
        (column [ ASC | DESC ] [ ,...n ] )
        [
            WITH FILLFACTOR = fillfactor
           |WITH ( <index_option> [ , ...n ] )
        ]
        [ ON { partition_scheme_name (partition_column_name)
            | filegroup | "default" } ]
    | FOREIGN KEY
        ( column [ ,...n ] )
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]
        [ NOT FOR REPLICATION ]
    | CONNECTION
        ( { node_table TO node_table } 
          [ , {node_table TO node_table }]
          [ , ...n ]
        )
        [ ON DELETE { NO ACTION | CASCADE } ]
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )
```  
  
  
## <a name="arguments"></a>Argumente  
In diesem Dokument werden nur Argumente für SQL-Graph aufgelistet. Eine vollständige Liste und Beschreibung der unterstützten Argumente finden Sie unter [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).

 *database_name*    
 Der Name der Datenbank, in der die Tabelle erstellt wird. *database_name* muss dem Namen einer vorhandenen Datenbank entsprechen. Wird *database_name* nicht angegeben, wird standardmäßig die aktuelle Datenbank verwendet. Der Anmeldename für die aktuelle Verbindung muss einer vorhandenen Benutzer-ID in der durch *database_name* angegebenen Datenbank zugeordnet sein. Diese Benutzer-ID muss über CREATE TABLE-Berechtigungen verfügen.  
  
 *schema_name*    
 Der Name des Schemas, zu dem die neue Tabelle gehört.  
  
 *table_name*      
 Der Name der Knoten- oder Edgetabelle. Tabellennamen müssen die Regeln für [Bezeichner](../../relational-databases/databases/database-identifiers.md) erfüllen. *table_name* kann höchstens 128 Zeichen aufweisen, ausgenommen lokale temporäre Tabellennamen (Namen mit einem Nummernzeichen (#) als Präfix), bei denen maximal 116 Zeichen zulässig sind.  
  
 NODE   
 Erstellt eine Knotentabelle

 EDGE  
 Erstellt eine Edgetabelle  
 
 *table_constraint*   
 Gibt die Eigenschaften einer PRIMARY KEY-, UNIQUE-, FOREIGN KEY-, CONNECTION- oder CHECK-Einschränkung bzw. eine DEFAULT-Definition an, die einer Tabelle hinzugefügt wurde.
 
 ON { partition_scheme | filegroup | "default" }    
 Gibt das Partitionsschema oder die Dateigruppe an, in der die Tabelle gespeichert wird. Wenn „partition_scheme“ angegeben wird, muss die Tabelle eine partitionierte Tabelle sein, deren Partitionen in einem oder mehreren in „partition_scheme“ angegebenen Dateigruppen gespeichert werden. Wenn „filegroup“ angegeben ist, wird die Tabelle in der genannten Dateigruppe gespeichert. Die Dateigruppe muss in der Datenbank vorhanden sein. Wenn "default" angegeben oder ON überhaupt nicht angegeben ist, wird die Tabelle in der Standarddateigruppe gespeichert. Der in CREATE TABLE angegebene Speichermechanismus einer Tabelle kann nachfolgend nicht mehr geändert werden.

 ON {partition_scheme | filegroup | "default"}    
 Kann auch in einer PRIMARY KEY- oder UNIQUE-Einschränkung angegeben werden. Diese Einschränkungen erstellen Indizes. Wenn „filegroup“ angegeben ist, wird der Index in der genannten Dateigruppe gespeichert. Wenn "default" angegeben oder ON überhaupt nicht angegeben ist, wird der Index in derselben Dateigruppe wie die Tabelle gespeichert. Wenn die PRIMARY KEY- oder die UNIQUE-Einschränkung einen gruppierten Index erstellt, werden die Datenseiten für die Tabelle in derselben Dateigruppe wie der Index gespeichert. Wenn CLUSTERED angegeben wird oder ein gruppierter Index anderweitig durch die Einschränkung erstellt wird, und ein Wert für „partition_scheme“ angegeben wird, der von der Angabe für „partition_scheme“ oder „filegroup“ der Tabellendefinition abweicht (oder umgekehrt), wird nur die Einschränkungsdefinition berücksichtigt. Der andere Wert wird ignoriert.
  
## <a name="remarks"></a>Bemerkungen  
Das Erstellen einer temporären Tabelle als Knoten- oder Edgetabelle wird nicht unterstützt.  

Das Erstellen einer Knoten- oder Edgetabelle als temporale Tabelle wird nicht unterstützt.

Stretch Database wird für Knoten- oder Edgetabellen nicht unterstützt.

Knoten- oder Edgetabellen können keine externen Tabellen sein (es besteht keine Unterstützung von PolyBase für Graphtabellen). 

Eine nicht partitionierte Graphknoten-/Edgetabelle kann nicht in eine partitionierte Graphknoten-/Edgetabelle geändert werden. 
  
 
## <a name="examples"></a>Beispiele  
  
### <a name="a-create-a-node-table"></a>A. Erstellen einer `NODE`-Tabelle
 Im folgenden Beispiel wird das Erstellen einer `NODE`-Tabelle veranschaulicht.

```
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>B. Erstellen einer `EDGE`-Tabelle
Im folgenden Beispiel wird das Erstellen von `EDGE`-Tabellen veranschaulicht.

```
 CREATE TABLE friends (
    id integer PRIMARY KEY,
    start_date date
 ) AS EDGE;

```

```
 -- Create a likes edge table, this table does not have any user defined attributes   
 CREATE TABLE likes AS EDGE;

```


## <a name="see-also"></a>Weitere Informationen 
 [ALTER TABLE table_constraint](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [INSERT (SQL-Graph)](../../t-sql/statements/insert-sql-graph.md)]  
 [Graph Processing with SQL Server 2017 (Graph-Verarbeitung mit SQL Server-2017)](../../relational-databases/graphs/sql-graph-overview.md)

