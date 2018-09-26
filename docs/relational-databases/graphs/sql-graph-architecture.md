---
title: SQL-Graph-Architektur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: graphs
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, architecture
ms.assetid: ''
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ebf687fb162b1c5c2ec17c0a0a5ec096dcfdd69d
ms.sourcegitcommit: 07d4ebb8438f7c348880c39046e2b452b2152fd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2018
ms.locfileid: "47158071"
---
# <a name="sql-graph-architecture"></a>SQL-Graph-Architektur  
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Erfahren Sie, wie SQL-Graph entworfen wird. Das Grundwissen wird anderen SQL-Graph-Artikeln zu erleichtern.
 
## <a name="sql-graph-database"></a>SQL-Graph-Datenbank
Benutzer können einem Diagramm pro Datenbank erstellen. Ein Diagramm ist eine Auflistung von Knoten und Edge-Tabellen. Knoten-oder edgetabellen können unter jedem Schema in der Datenbank erstellt werden, aber sie alle zu einem logischen Diagramm gehören. Eine Knotentabelle handelt es sich um Auflistung von ähnlichen Typ von Knoten. So enthält z. B. eine Knotentabelle alle Knoten der Person, die zu einem Diagramm gehören. Auf ähnliche Weise wird eine edgetabelle eine Auflistung von ähnlichen Typ mit Ränder. So enthält z. B. eine edgetabelle für Freunde alle Ränder, die eine Person mit einer anderen Person zu verbinden. Da Knoten und Kanten in Tabellen gespeichert werden, werden die meisten Vorgänge für reguläre Tabellen unterstützt auf Knoten-oder edgetabellen unterstützt. 
 
 
![SQL-Graph-Architektur](../../relational-databases/graphs/media/sql-graph-architecture.png "Sql-Graph-Datenbankarchitektur")   

Abbildung 1: SQL-Graph-Datenbankarchitektur
 
## <a name="node-table"></a>Knotentabelle
Eine Knotentabelle stellt eine Entität in einem Graph-Schema dar. Jedes Mal eine Knotentabelle zusammen mit den benutzerdefinierten Spalten, eine implizite erstellt wird, `$node_id` Spalte erstellt, die einen bestimmten Knoten in der Datenbank eindeutig identifiziert. Die Werte in `$node_id` werden automatisch generiert und sind eine Kombination von `object_id` dieser Knotentabelle und einen intern generierten Bigint-Wert. Aber wenn die `$node_id` Spalte ausgewählt ist, wird ein berechneter Wert in Form einer JSON-Zeichenfolge angezeigt. Darüber hinaus `$node_id` eine Pseudospalte, die einen internen Namen mit einer hexadezimalen Zeichenfolge in der sie zugeordnet ist. Bei der Auswahl `$node_id` aus der Tabelle den Namen der Spalte hostnamensadresse `$node_id_<hex_string>`. Verwenden von Pseudo-Spaltennamen in Abfragen ist die empfohlene Methode der internen Abfrage `$node_id` Spalten- und hex-Zeichenfolge mit interner Name sollte vermieden werden.

Es wird empfohlen, dass Benutzer eine unique-Einschränkung oder einen index erstellen auf der `$node_id` Spalte zum Zeitpunkt der Erstellung der Knotentabelle, aber wenn eine nicht ist erstellt, den Standardwert eindeutigen nicht gruppierten Index wird automatisch erstellt. Allerdings wird ein Index für eine Graph-Pseudo-Spalte für die zugrunde liegende interne Spalten erstellt. D. h. Indizes für die `$node_id` Spalte erscheint im internen `graph_id_<hex_string>` Spalte.   


## <a name="edge-table"></a>Edge-Tabelle
Eine edgetabelle stellt eine Beziehung in einem Diagramm dar. Ränder werden immer weitergeleitet, und verbinden zwei Knoten. Eine edgetabelle ermöglicht Benutzern, die zum Modellieren von m: n Beziehungen im Diagramm. Eine edgetabelle kann nicht haben oder keine benutzerdefinierten Attribute darin. Jedes Mal eine edgetabelle, zusammen mit den benutzerdefinierten Attributen erstellt wird, werden drei implizite Spalten in der Rahmentabelle erstellt:

|Spaltenname    |Description  |
|---   |---  |
|`$edge_id`   |Zur eindeutigen Identifizierung ein angegebenes Randes in der Datenbank. Es ist eine generierte Spalte und der Wert ist eine Kombination von Object_id einen intern generierten Bigint-Wert und der edgetabelle. Aber wenn die `$edge_id` Spalte ausgewählt ist, wird ein berechneter Wert in Form einer JSON-Zeichenfolge angezeigt. `$edge_id` ist eine Pseudo-Spalte, die einen internen Namen mit einer hexadezimalen Zeichenfolge in der sie zugeordnet ist. Bei der Auswahl `$edge_id` aus der Tabelle den Namen der Spalte hostnamensadresse `$edge_id_\<hex_string>`. Verwenden von Pseudo-Spaltennamen in Abfragen ist die empfohlene Methode der internen Abfrage `$edge_id` Spalten- und hex-Zeichenfolge mit interner Name sollte vermieden werden. |
|`$from_id`   |Speichert die `$node_id` des Knotens aus der Rand, stammen.  |
|`$to_id`   |Speichert die `$node_id` des Knotens, an dem die Edge beendet wird. |

Die Knoten, die eine bestimmte Kante eine Verbindung herstellen, kann im eingefügten Daten unterliegen der `$from_id` und `$to_id` Spalten. In der ersten Version ist es nicht möglich, zum Definieren von Einschränkungen für die edgetabelle, um zu verhindern, dass er alle zwei Arten von Knoten verbinden. Eine Kante kann, also zwei beliebigen Knoten im Diagramm, unabhängig von deren Typen eine Verbindung herstellen.

Ähnlich wie die `$node_id` Spalte, es wird empfohlen, dass Benutzer auf einen eindeutigen Index oder die Einschränkung erstellen die `$edge_id` Spalte zum Zeitpunkt der Erstellung der Rahmentabelle zurück, aber wenn eine nicht ist erstellt, den Standardwert eindeutigen nicht gruppierten Index wird automatisch erstellt, auf Diese Spalte. Allerdings wird ein Index für eine Graph-Pseudo-Spalte für die zugrunde liegende interne Spalten erstellt. D. h. Indizes für die `$edge_id` Spalte erscheint im internen `graph_id_<hex_string>` Spalte. Es wird außerdem empfohlen, für OLTP-Szenarien, die Benutzer über einen Index zu erstellen (`$from_id`, `$to_id`) Spalten, die für schnellere Suchvorgänge in die Richtung des Rands.  

Abbildung 2 zeigt, wie Knoten und Edge-Tabellen in der Datenbank gespeichert werden. 

![Person-Freunde-Tables](../../relational-databases/graphs/media/person-friends-tables.png "Person-Knoten und Freunde edge-Tabellen")   

Abbildung 2: Und Rahmentabellen tabellendarstellung



## <a name="metadata"></a>Metadaten
Verwenden Sie diese Metadatenansichten, um die Attribute einer Knoten- oder edgetabelle Tabelle finden Sie unter.
 
### <a name="systables"></a>sys.tables
Die folgenden neuen, bit-Datentyp, werden SYS Spalten hinzugefügt. TABELLEN. Wenn `is_node` ist auf 1 festgelegt, der angibt, dass die Tabelle eine Knotentabelle handelt und wenn `is_edge` ist auf 1 festgelegt, der angibt, dass die Tabelle eine edgetabelle handelt.
 
|Spaltenname |Datentyp |Description |
|--- |---|--- |
|is_node |bit |1 = Dies ist eine Knotentabelle |
|is_edge |bit |1 = Dies ist eine edgetabelle |
 
### <a name="syscolumns"></a>sys.columns
Die `sys.columns` -Ansicht enthält zusätzliche Spalten `graph_type` und `graph_type_desc`, anzugeben, dass den Typ der Spalte im und Rahmentabellen.
 
|Spaltenname |Datentyp |Description |
|--- |---|--- |
|graph_type |ssNoversion |Interne Spalte mit einem Satz von Werten. Die Werte liegen zwischen 1 bis 8 für Graph-Spalten und NULL für andere Benutzer.  |
|graph_type_desc |nvarchar(60)  |interne Spalte mit einem Satz von Werten |
 
Die folgende Tabelle enthält die gültigen Werte für `graph_type` Spalte

|Spaltenwert  |Description  |
|---   |---   |
|1  |GRAPH_ID  |
|2  |GRAPH_ID_COMPUTED  |
|3  |GRAPH_FROM_ID  |
|4  |GRAPH_FROM_OBJ_ID  |
|5  |GRAPH_FROM_ID_COMPUTED  |
|6  |GRAPH_TO_ID  |
|7  |GRAPH_TO_OBJ_ID  |
|8  |GRAPH_TO_ID_COMPUTED  |


`sys.columns` speichert auch Informationen zu impliziten Spalten in der Knoten-oder edgetabellen erstellt. Folgende Informationen kann von sys.columns abgerufen werden, allerdings können keine Benutzer diese Spalten auswählen, aus einer Tabelle Knoten- oder edgetabelle. 

Impliziten Spalten in eine Knotentabelle  
|Spaltenname    |Datentyp  |is_hidden  |Anmerkung  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |interne `graph_id` Spalte  |
|$node_id_\<hex_string> |NVARCHAR   |0  |Externe Knoten `node_id` Spalte  |

Impliziten Spalten in eine edgetabelle  
|Spaltenname    |Datentyp  |is_hidden  |Anmerkung  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |interne `graph_id` Spalte  |
|$edge_id_\<hex_string> |NVARCHAR   |0  |externe `edge_id` Spalte  |
|from_obj_id_\<hex_string>  |INT    |1  |interne von Knoten `object_id`  |
|from_id_\<hex_string>  |bigint |1  |Intern von Knoten `graph_id`  |
|$from_id_\<hex_string> |NVARCHAR   |0  |externe von Knoten `node_id`  |
|To_obj_id_\<Hex_string >    |INT    |1  |interne Knoten `object_id`  |
|to_id_\<hex_string>    |bigint |1  |Intern auf Knoten `graph_id`  |
|$to_id_\<hex_string>   |NVARCHAR   |0  |außerhalb von Knoten `node_id`  |
 
### <a name="system-functions"></a>Systemfunktionen
Die folgenden integrierten Funktionen werden hinzugefügt. Dies hilft Benutzern, die Informationen aus die generierten Spalten zu extrahieren. Beachten Sie, dass diese Methoden nicht die Eingabe des Benutzers überprüft werden. Wenn der Benutzer ein ungültiges angibt `sys.node_id` die-Methode den entsprechenden Teil zu extrahieren und zurückzugeben. Z. B. OBJECT_ID_FROM_NODE_ID dauert eine `$node_id` als Eingabe und gibt die Object_id der Tabelle dieser Knoten gehört. 
 
|Integrierte   |Description  |
|---  |---  |
|OBJECT_ID_FROM_NODE_ID |Extrahieren Sie die Object_id von einem `node_id`  |
|GRAPH_ID_FROM_NODE_ID  |Extrahieren Sie die Graph_id aus einem `node_id`  |
|NODE_ID_FROM_PARTS |Erstellen Sie eine Node_id aus einem `object_id` und ein `graph_id`  |
|OBJECT_ID_FROM_EDGE_ID |Extrahieren Sie `object_id` aus `edge_id`  |
|GRAPH_ID_FROM_EDGE_ID  |Extrahieren Sie die Identität aus `edge_id`  |
|EDGE_ID_FROM_PARTS |Erstellen Sie `edge_id` aus `object_id` und Identität  |



## <a name="transact-sql-reference"></a>Transact-SQL-Referenz 
Erfahren Sie, den [!INCLUDE[tsql-md](../../includes/tsql-md.md)] -Erweiterungen in SQL Server und Azure SQL-Datenbank eingeführt, mit denen erstellen und Abfragen von Graph-Objekte. Die Abfrage-spracherweiterungen helfen Abfrage und durchlaufen Sie das Diagramm mit ASCII-Grafik-Syntax.
 
### <a name="data-definition-language-ddl-statements"></a>Anweisungen der Data Definition Language (DDL)
|Task   |Verwandte Artikel  |Hinweise
|---  |---  |---  |
|CREATE TABLE |[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)|`CREATE TABLE ` ist nun erweitert, um Unterstützung für das Erstellen einer Tabelle, die AS-Knoten- oder EDGETABELLE von AS. Beachten Sie, dass eine edgetabelle kann möglicherweise keine benutzerdefinierten Attribute.  |
|ALTER TABLE    |[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|Und Rahmentabellen können geändert werden, die gleiche Weise wie eine relationale Tabelle ist, verwendet der `ALTER TABLE`. Benutzer können hinzufügen oder Ändern von benutzerdefinierten Spalten, Indizes oder Einschränkungen. Allerdings wie ändern die interne Diagrammspalten, `$node_id` oder `$edge_id`, führt zu einem Fehler.  |
|CREATE INDEX   |[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  |Benutzer können Indizes auf Pseudo-Spalten und benutzerdefinierte Spalten und Rahmentabellen erstellen. Alle Typen von Indizes werden unterstützt, einschließlich gruppierten und nicht gruppierten columnstore-Indizes.  |
|ERSTELLEN VON EDGEEINSCHRÄNKUNGEN    |[EDGEEINSCHRÄNKUNGEN &#40;Transact-SQL&#41;](../../relational-databases/tables/graph-edge-constraints.md)  |Benutzer können jetzt erstellen edgeeinschränkungen auf Edge-Tabellen, um bestimmte Semantik zu erzwingen und Datenintegrität zu gewährleisten  |
|DROP TABLE |[TABELLENLÖSCHUNG &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)  |Und Rahmentabellen können gelöscht werden, die gleiche Weise wie eine relationale Tabelle ist, verwendet der `DROP TABLE`. In dieser Version gibt jedoch keine Einschränkungen, um sicherzustellen, dass keine Ränder zeigen Sie auf ein gelöschter Knoten und kaskadierten Löschung Ränder, nach dem Löschen eines Knotens oder einer Knotentabelle wird nicht unterstützt. Es wird empfohlen, wenn eine Knotentabelle gelöscht wird, Benutzer keinem Rand verbunden, auf die Knoten in dieser Knotentabelle manuell, um die Integrität des Diagramms gewährleisten ablegen.  |


### <a name="data-manipulation-language-dml-statements"></a>Anweisungen der Data Manipulation Language (DML)
|Task   |Verwandte Artikel  |Hinweise
|---  |---  |---  |
|INSERT |[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)|Einfügen in eine Knotentabelle ist unterscheidet sich nicht in eine relationale Tabelle einzufügen. Die Werte für `$node_id` Spalte wird automatisch generiert. Versuch zum Einfügen eines Werts in `$node_id` oder `$edge_id` Spalte führt zu einem Fehler. Benutzer müssen Geben Sie Werte für `$from_id` und `$to_id` Spalten während des Einfügens in eine edgetabelle. `$from_id` und `$to_id` sind die `$node_id` Werte der Knoten, die eine bestimmte Kante verbindet.  |
|Delete | [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|Daten aus einer Knoten-oder edgetabellen können auf gleiche Weise gelöscht werden, wie sie vom relationalen Tabellen gelöscht werden. In dieser Version gibt jedoch keine Einschränkungen, um sicherzustellen, dass keine Ränder zeigen Sie auf ein gelöschter Knoten und kaskadierten Löschung Ränder, nach dem Löschen eines Knotens wird nicht unterstützt. Es wird empfohlen, dass wenn ein Knoten gelöscht wurde, die verbindenden Rändern auf diesen Knoten ebenfalls gelöscht werden, um die Integrität des Diagramms zu gewährleisten.  |
|UPDATE |[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  |Werte in den benutzerdefinierten Spalten können mithilfe der UPDATE-Anweisung aktualisiert werden. Aktualisieren die interne Diagrammspalten `$node_id`, `$edge_id`, `$from_id` und `$to_id` ist nicht zulässig.  |
|MERGE |[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  |`MERGE` Anweisung wird für eine Knoten- oder edgetabelle Tabelle unterstützt.  |


### <a name="query-statements"></a>Abfrageanweisungen
|Task   |Verwandte Artikel  |Hinweise
|---  |---  |---  |
|SELECT |[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)|Knoten und Kanten werden als Tabellen intern gespeichert, daher werden die meisten Vorgänge unterstützt, die für eine Tabelle in SQL Server oder Azure SQL-Datenbank unterstützt, für die Tabellen und Rahmentabellen  |
|MATCH  | [MATCH &#40;Transact-SQL&#41;](../../t-sql/queries/match-sql-graph.md)|Übereinstimmung integrierte wird zur Unterstützung von Musterabgleich und durchlaufen Sie das Diagramm eingeführt.  |



## <a name="limitations-and-known-issues"></a>Einschränkungen und bekannte Probleme  
Es gibt bestimmte Einschränkungen für Knoten und Edge-Tabellen in dieser Version:
* Lokale oder globale temporäre Tabellen Knoten-oder edgetabellen nicht möglich.
* Tabellentypen und Tabellenvariablen können nicht als Knoten- oder edgetabelle Tabelle deklariert werden. 
* Und Rahmentabellen können nicht als temporale Tabellen mit systemversionsverwaltung erstellt werden.   
* Und Rahmentabellen darf nicht auf Speicheroptimierte Tabellen sein.  
* Benutzer können nicht aktualisiert werden. die `$from_id` und `$to_id` Spalten von einer Kante, die mithilfe der UPDATE-Anweisung. Um die Knoten zu aktualisieren, die ein Rand verbindet, müssen Benutzer fügen Sie den neuen Rand auf neue Knoten, und löschen das vorherige Beispiel.
* Datenbankübergreifende werden Abfragen von Graph-Objekte nicht unterstützt. 


## <a name="next-steps"></a>Nächste Schritte
Um den ersten Schritten mit der neuen Syntax finden Sie unter [SQL-Graph-Datenbank – Beispiel](./sql-graph-sample.md)
 

