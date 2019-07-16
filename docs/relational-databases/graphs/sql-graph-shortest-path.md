---
title: KÜRZESTE Pfad (SQL-Graph) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- SHORTEST PATH
- SHORTEST_PATH
dev_langs:
- TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b4e07c8aa0c7911b02f7df5386c03b1860df38c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035880"
---
# <a name="shortestpath-transact-sql"></a>SHORTEST_PATH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver2015-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Gibt eine Suchbedingung für ein Diagramm, d.h. durchsucht rekursiv oder wiederholt. SHORTEST_PATH kann in Übereinstimmung mit der Graph-Knoten und Edge-Tabellen, in der SELECT-Anweisung verwendet werden. 
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="shortest-path"></a>Kürzeste Pfad
Der SHORTEST_PATH-Funktion können Sie die finden:    
* Einen kürzesten Pfad zwischen zwei gegebenen Knoten/Entitäten
* Kürzeste keine(n) für einzelne Quelle.
* Kürzesten Pfad aus mehreren Datenquellen-Knoten auf mehrere Knoten.

Er ein beliebiger Länge Muster als Eingabe akzeptiert und gibt einen kürzesten Pfad, der vorhanden ist, zwischen zwei Knoten. Diese Funktion kann nur in MATCH verwendet werden. Die Funktion gibt nur einen kürzesten Pfad zwischen zwei beliebigen angegebenen Knoten. Wenn es vorhanden ist, zwei oder mehr kürzesten derselben Länge zwischen einem Quell- und Ziel-Knoten, die nur eine Funktion gibt den Pfad, der während des Durchlaufs zuerst gefunden wurde. Beachten Sie, dass eine beliebiger Länge-Muster kann nur innerhalb einer SHORTEST_PATH-Funktion angegeben werden. 

Finden Sie in der [MATCH (SQL-Graph)](../../t-sql/queries/match-sql-graph.md) Syntax. 

## <a name="for-path"></a>FÜR DEN PFAD
FÜR Pfad mit alle Knoten- oder edgetabelle Tabellennamen in der FROM-Klausel verwendet werden muss, in eine beliebige Länge Muster einbezogen werden. FÜR den Pfad weist der Engine an, dass die Knoten- oder edgetabelle-Tabelle eine geordnete Auflistung, die die Liste von Knoten oder Kanten, die entlang des Pfads durchlaufen gefunden zurückgibt. Die Attribute aus diesen Tabellen können nicht direkt in der SELECT-Klausel projiziert werden. Zum projizieren von Attributen aus diesen Tabellen graph-Pfad-Aggregatfunktionen muss verwendet werden.  

## <a name="arbitrary-length-pattern"></a>Beliebiger Länge-Muster
Dieses Muster enthält, die Knoten und Kanten, die wiederholt durchlaufen werden müssen, bis Sie der gewünschte Knoten erreicht wird, oder bis die maximale Anzahl von Iterationen gemäß dem Muster erfüllt ist. Jedes Mal, wenn die Abfrage ausgeführt wird, wird das Ergebnis der Ausführung dieses Muster eine geordnete Auflistung von Knoten und Kanten, die entlang des Pfads vom Startknoten zum Endknoten durchlaufen werden. Dies ist die Syntax-Muster eines regulären Ausdrucks-Stil und die folgenden zwei Muster Quantifizierer werden unterstützt:

* **'+'** : Das Muster 1 oder mehrmals wiederholen. Beenden, sobald ein kürzester Pfad gefunden wird.
* **{1,n}** : Das Muster 1 bis „n“ Male wiederholen. Beenden Sie als einen kürzesten gefunden wird.

## <a name="lastnode"></a>LAST_NODE
LAST_NODE()-Funktion ermöglicht das Verketten von zwei beliebiger Länge Traversal-Muster. Es kann in Szenarien verwendet werden, in denen:    
* Mehr als einen kürzesten pfadmuster werden in einer Abfrage verwendet, und ein Muster, die an den letzten Knoten des vorherigen Musters beginnt.
* Zwei pfadmuster für den kürzesten auf dem gleichen LAST_NODE() zusammengeführt werden.

## <a name="graph-path-order"></a>Reihenfolge der Graph-Pfad
Reihenfolge der Graph-Pfad bezieht sich auf Reihenfolge der Daten in den Ausgabepfad. Die Reihenfolge der Ausgabe-Pfads beginnt immer im nicht rekursiven Teil des Musters, gefolgt von den Knoten und Flanken, die im rekursiven Teil angezeigt werden. Die Reihenfolge, in der das Diagramm, während der Optimierung/abfrageausführung durchlaufen wird, hat nichts mit der Reihenfolge, in der Ausgabe ausgegeben werden. Auf ähnliche Weise beeinflusst die Richtung des Pfeils in der rekursiven Muster auch nicht die Reihenfolge der Graph-Pfad. 

## <a name="graph-path-aggregate-functions"></a>Graph-Pfad-Aggregatfunktionen
Da der Knoten und Edges Einfluss auf die Rückgabe beliebiger Länge-Muster eine Auflistung (von Knoten und durchlaufen in diesem Pfad verankerten), können keine Benutzer die Attribute, die direkt mit der konventionellen tablename.attributename-Syntax projizieren. Für Abfragen, wenn es erforderlich, Projekt-Attributwerte aus der Knoten- oder edgetabelle Zwischentabellen, in dem Pfad durchlaufen, verwenden Sie folgende Aggregatfunktionen für Graph-Pfad ist: STRING_AGG, LAST_VALUE, SUM, AVG, MIN, MAX und COUNT. Diese Aggregatfunktionen in der SELECT-Klausel verwendet die allgemeine Syntax lautet:

```
<GRAPH_PATH_AGGREGATE_FUNCTION>(<expression> , <separator>)  <order_clause>

    <order_clause> ::=
        { WITHIN GROUP (GRAPH PATH) }

    <GRAPH_PATH_AGGREGATE_FUNCTION> ::=
          STRING_AGG
        | LAST_VALUE
        | SUM
        | COUNT
        | AVG
        | MIN
        | MAX

```

### <a name="stringagg"></a>STRING_AGG
Die STRING_AGG-Funktion akzeptiert einen Ausdruck und die Trennzeichen als Eingabe und gibt eine Zeichenfolge zurück. Benutzer können Sie diese Funktion in der SELECT-Klausel für Projektattribute aus dem Zwischenknoten oder Ränder in durchlaufene Pfad verwenden. 

### <a name="lastvalue"></a>LAST_VALUE
Hinzu, die Attribute aus den letzten Knoten des Pfad durchlaufen wurde, aggregierte LAST_VALUE-Funktion verwendet werden können. Es ist ein Fehler Edge Tabellenalias als Eingabe für diese Funktion nur Knoten Tabellennamen angeben, oder Aliase können verwendet werden.

**Knoten der letzten**: Der letzte Knoten bezieht sich auf den Knoten, der letzte in den Pfad durchlaufen werden, unabhängig von der die Richtung des Pfeils in der MATCH-Prädikat angezeigt wird. Beispiel: `MATCH(SHORTEST_PATH(n(-(e)->p)+) )`. Hier werden die letzte Knoten im Pfad den letzten besuchten P-Knoten. 

Während der letzten Knoten der letzte n-ten Knoten im Diagramm Ausgabepfad für dieses Muster ist: `MATCH(SHORTEST_PATH((n<-(e)-)+p))`    

### <a name="sum"></a>SUM
Diese Funktion gibt die Summe der Attributwerte für die angegebenen Knoten/Microsoft Edge oder einen Ausdruck, die angezeigt wurden, in die entsprechende Pfad.

### <a name="count"></a>COUNT
Diese Funktion gibt die Anzahl der Werte ungleich Null des gewünschten Knoten/Edge-Attributs im Pfad. Die COUNT-Funktion unterstützt die '\*'-Operator mit Tabellenalias Knoten- oder edgetabelle. Ohne Knoten- oder edgetabelle Tabellenalias, die Verwendung von \* ist mehrdeutig und führt zu einem Fehler.

    {  COUNT( <expression> | <node_or_edge_alias>.* )  <order_clause>  }


### <a name="avg"></a>AVG
Gibt den Durchschnitt der Attributwerte für die angegebenen Knoten/Microsoft Edge oder einen Ausdruck, die angezeigt wurden in die entsprechende Pfad zurück.

### <a name="min"></a>MIN
Gibt den kleinsten Wert aus der bereitgestellten Knoten/Edge-Attributwerte oder Ausdruck, der in die entsprechende Pfad angezeigt.

### <a name="max"></a>MAX
Gibt den größten Wert aus der bereitgestellten Knoten/Edge-Attributwerte oder Ausdruck, der in die entsprechende Pfad angezeigt.

## <a name="remarks"></a>Hinweise  
Shortest_path-Funktion kann nur in MATCH verwendet werden.     
LAST_NODE wird nur innerhalb einer Shortest_path unterstützt.     
Suchen von gewichteten kürzesten Pfad "," alle Pfade "oder" alle kürzesten Pfad wird nicht unterstützt.         
In einigen Fällen möglicherweise fehlerhafte Pläne für Abfragen mit einer höheren Anzahl von Hops, was zu höheren Ausführungszeiten von Abfragen führt generiert werden. Verwenden von Hash Join-Hinweis kann hilfreich sein.    


## <a name="examples"></a>Beispiele 
Für die hier gezeigten, befassen wir uns zu Beispielabfragen verwenden Sie den Knoten und Edge-Tabellen, in erstellt [SQL-Graph-Beispiel](./sql-graph-sample.md)

### <a name="a--find-shortest-path-between-2-people"></a>A.  Suchen der kürzeste Pfad zwischen 2 Personen
 Im folgenden Beispiel suchen wir kürzesten Pfad zwischen Jacob und Alice. Wir benötigen die Person-Knoten und FriendOf Edge aus Graph-Beispielskript erstellt wurde. 

 ```
SELECT PersonName, Friends
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

 ### <a name="b--find-shortest-path-from-a-given-node-to-all-other-nodes-in-the-graph"></a>B.  Suchen Sie kürzesten Wegs von einem bestimmten Knoten für alle anderen Knoten im Diagramm. 
 Im folgende Beispiel sucht die Leute, die mit Jacob verbunden ist, in das Diagramm und den kürzesten Pfad Jacob beginnend mit allen diesen Personen. 

 ```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
AND Person1.name = 'Jacob'
 ```

### <a name="c--count-the-number-of-hopslevels-traversed-to-go-from-one-person-to-another-in-the-graph"></a>C.  Die Anzahl der Hops/-Stufen durchlaufen, um von einer Person zu einem anderen im Diagramm zu wechseln.
 Im folgenden Beispiel findet den kürzesten Pfad zwischen Jacob und Alice und gibt die Anzahl der Hops dauert um von Jacob zu Alice zu gelangen. 

 ```
 SELECT PersonName, Friends, levels
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

### <a name="d-find-people-1-3-hops-away-from-a-given-person"></a>D. Suchen Sie Personen, 1 bis 3-Hops von einer bestimmten person
Im folgende Beispiel sucht den kürzesten Pfad zwischen Jacob und die Leute, die mit dem er verbunden ist, in die Graph-1 bis 3 Hops, die von ihm. 

```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
AND Person1.name = 'Jacob'
```

### <a name="e-find-people-exactly-2-hops-away-from-a-given-person"></a>E. Suchen nach Personen genau 2 Hops von einer bestimmten person
Im folgende Beispiel findet den kürzesten Pfad zwischen Jacob und Personen, die genau 2 Hops von ihm im Diagramm sind. 

```
SELECT PersonName, Friends
FROM (
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
    AND Person1.name = 'Jacob'
) Q
WHERE Q.levels = 2
```

## <a name="see-also"></a>Siehe auch  
 [Übereinstimmung (SQL-Graph)](../../t-sql/queries/match-sql-graph.md)    
 [CREATE TABLE &#40;SQL-Graph&#41;](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (SQL-Graph)](../../t-sql/statements/insert-sql-graph.md)]  
 [Graph Processing with SQL Server 2017 (Graph-Verarbeitung mit SQL Server-2017)](../../relational-databases/graphs/sql-graph-overview.md)     
 
