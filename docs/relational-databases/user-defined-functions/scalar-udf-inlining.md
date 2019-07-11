---
title: Inlining benutzerdefinierter Skalarfunktionen in Datenbanken von Microsoft SQL Server | Microsoft-Dokumentation
description: In diesem Artikel wird das Inlining benutzerdefinierter Skalarfunktionen erläutert, um die Leistung von Abfragen zu verbessern, die benutzerdefinierte Skalarfunktionen in SQL Server (2018 und höher) und Azure SQL-Datenbank aufrufen.
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: s-r-k
ms.author: karam
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 8dba65eb4ca0aa97ca747567a6337e68fb7c2f29
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67581425"
---
# <a name="scalar-udf-inlining"></a>Inlining benutzerdefinierter Skalarfunktionen

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Dieser Artikel stellt eine Einführung in das Inlining benutzerdefinierter Skalarfunktionen dar. Dabei handelt es sich um ein Feature für die intelligente Abfrageverarbeitung. Durch dieses Feature wird die Leistung von Abfragen verbessert, die benutzerdefinierte Skalarfunktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab [!INCLUDE[ssSQLv15](../../includes/sssqlv15-md.md)]) und [!INCLUDE[ssSDS](../../includes/sssds-md.md)] aufrufen.

## <a name="t-sql-scalar-user-defined-functions"></a>Benutzerdefinierte Transact-SQL-Skalarfunktionen

Benutzerdefinierte Funktionen (User-defined functions, UDF), die in Transact-SQL implementiert werden und einen einzelnen Datenwert zurückgeben, werden als benutzerdefinierte Transact-SQL-Skalarfunktionen bezeichnet. Benutzerdefinierte Transact-SQL-Funktionen sind gut geeignet, um Code in SQL-Abfragen wiederzuverwenden und Modularität zu erreichen. Einige Berechnungen (z.B. komplexe Geschäftsregeln) können einfacher in imperativer UDF-Form ausgedrückt werden. Mit benutzerdefinierten Funktionen können Sie eine komplexe Logik erstellen, ohne komplexe SQL-Abfragen schreiben zu können.

## <a name="performance-of-scalar-udfs"></a>Leistung von benutzerdefinierten Skalarfunktionen

Die Leistung von benutzerdefinierten Skalarfunktionen ist aus folgenden Gründen häufig niedrig:

- **Iterativer Aufruf:** Benutzerdefinierte Funktionen werden einmal pro qualifiziertem Tupel iterativ aufgerufen. Durch diese Funktionsaufrufe entstehen zusätzliche Kosten für den Kontextwechsel. Dies betrifft besonders benutzerdefinierte Funktionen, die SQL-Abfragen in ihrer Definition ausführen.
- **Keine Kostenberechnung:** Während der Optimierung fallen nur Kosten für relationale Operatoren an, nicht für Skalaroperatoren. Vor der Einführung benutzerdefinierter Skalarfunktionen waren andere Skalaroperatoren in der Regel günstig, sodass keine Kostenberechnung nötig war. Es war ausreichend, geringe CPU-Kosten für einen Skalarvorgang hinzuzufügen. In einigen Szenarios sind die tatsächlichen Kosten jedoch wichtig und werden dennoch nicht ausreichend repräsentiert.
- **Interpretierte Ausführung:** Benutzerdefinierte Funktionen werden als Anweisungsbatch ausgewertet und Anweisung für Anweisung ausgeführt. Jede Anweisung wird kompiliert, und der kompilierte Plan wird zwischengespeichert. Die Zwischenspeicherung spart zwar Zeit, da Neukompilierungen vermieden werden, aber jede Anweisung wird isoliert ausgeführt. Es können keine anweisungsübergreifenden Optimierungen durchgeführt werden.
- **Serielle Ausführung:** SQL Server lässt in Abfragen, die benutzerdefinierte Funktionen aufrufen, keinen abfrageinternen Parallelismus zu. 

## <a name="automatic-inlining-of-scalar-udfs"></a>Automatisches Inlining von benutzerdefinierrten Skalarfunktionen

Mit dem Feature für das Inlining benutzerdefinierter Skalarfunktionen soll die Leistung von Abfragen verbessert werden, die benutzerdefinierte Transact-SQL-Skalarfunktionen ausführen, bei denen die Ausführung der benutzerdefinierten Funktion den entscheidenden Engpass darstellt.

Mit diesem neuen Feature werden benutzerdefinierte Skalarfunktionen automatisch in Skalarausdrücke oder skalare Unterabfragen transformiert, die in der aufrufenden Abfrage den UDF-Operator ersetzen. Diese Ausdrücke und Unterabfragen werden anschließend optimiert. Dadurch enthält der Abfrageplan keinen UDF-Operator mehr. Seine Auswirkungen werden im Plan überwacht, z.B. Ansichten oder Inline-Tabellenwertfunktionen.

### <a name="example-1---single-statement-scalar-udf"></a>1\. Beispiel: Benutzerdefinierte Skalarfunktion mit einer einzelnen Anweisung

Sehen Sie sich die folgende Abfrage an:

```sql
SELECT L_SHIPDATE, O_SHIPPRIORITY, SUM (L_EXTENDEDPRICE *(1 - L_DISCOUNT)) 
FROM LINEITEM
INNER JOIN ORDERS
  ON O_ORDERKEY = L_ORDERKEY 
GROUP BY L_SHIPDATE, O_SHIPPRIORITY ORDER BY L_SHIPDATE;
```

Diese Abfrage berechnet die Summe der reduzierten Preise für Einzelposten und gruppiert die Ergebnisse nach Versanddatum und Versandpriorität. Der Ausdruck `L_EXTENDEDPRICE *(1 - L_DISCOUNT)` enthält die Formel für den reduzierten Preis eines bestimmten Einzelpostens. Solche Formeln können in Funktionen extrahiert werden, um Modularität und Wiederverwendbarkeit zu erreichen.

```sql
CREATE FUNCTION dbo.discount_price(@price DECIMAL(12,2), @discount DECIMAL(12,2)) 
RETURNS DECIMAL (12,2) AS
BEGIN
  RETURN @price * (1 - @discount);
END

```

Die Abfrage kann nun geändert werden, um diese benutzerdefinierte Funktion aufzurufen.

```sql
SELECT L_SHIPDATE, O_SHIPPRIORITY, SUM (dbo.discount_price(L_EXTENDEDPRICE, L_DISCOUNT)) 
FROM LINEITEM
INNER JOIN ORDERS
  ON O_ORDERKEY = L_ORDERKEY 
GROUP BY L_SHIPDATE, O_SHIPPRIORITY ORDER BY L_SHIPDATE
```

Wie zuvor beschrieben ist die Leistung der Abfrage mit der benutzerdefinierten Funktion niedrig. Durch das Inlining der benutzerdefinierten Skalarfunktion wird der Skalarausdruck im Textkörper der benutzerdefinierten Funktion direkt in der Abfrage ersetzt. Die Ergebnisse dieser Abfrage werden in folgender Tabelle aufgeführt:

| Abfrage: | Abfrage ohne benutzerdefinierte Funktion | Abfrage mit benutzerdefinierter Funktion (ohne Inlining) | Abfrage mit Inlining benutzerdefinierter Skalarfunktionen | 
| --- | --- | --- | --- |
| Ausführungszeit: | 1,6 Sekunden | 29 Minuten, 11 Sekunden | 1,6 Sekunden |

Diese Zahlen basieren auf einer CCI-Datenbank mit 10 GB (mit dem TPC-H-Schema), die auf einem Computer mit Dualprozessor (12 Kerne), 96 GB RAM und SSD-Sicherung ausgeführt wird. Dabei wurden die Kompilier- und die Ausführungszeit mit einem kalten Prozedurcache und Pufferpool eingeschlossen. Die Standardkonfiguration wurde verwendet, und es wurden keine weiteren Indizes erstellt.

### <a name="example-2---multi-statement-scalar-udf"></a>2\. Beispiel: Benutzerdefinierte Skalarfunktion mit einer mehreren Anweisungen

Für benutzerdefinierte Skalarfunktionen, die über mehrere T-SQL-Anweisungen implementiert werden, z.B. Variablenzuweisungen und bedingte Verzweigungen, kann ebenfalls ein Inlining durchgeführt werden. Sehen Sie sich folgende benutzerdefinierte Skalarfunktion an, die die Servicekategorie für einen bestimmten Kunden bestimmt, wenn ein benutzerdefinierter Schlüssel vorhanden ist. Die Kategorie wird erreicht, indem zuerst der Gesamtpreis aller Bestellungen des Kunden mithilfe einer SQL-Abfrage berechnet wird. Anschließend wird eine `IF-ELSE`-Logik verwendet, um die Kategorie auf Grundlage des Gesamtpreises zu bestimmen.

```sql
CREATE OR ALTER FUNCTION dbo.customer_category(@ckey INT) 
RETURNS CHAR(10) AS
BEGIN
  DECLARE @total_price DECIMAL(18,2);
  DECLARE @category CHAR(10);

  SELECT @total_price = SUM(O_TOTALPRICE) FROM ORDERS WHERE O_CUSTKEY = @ckey;

  IF @total_price < 500000
    SET @category = 'REGULAR';
  ELSE IF @total_price < 1000000
    SET @category = 'GOLD';
  ELSE 
    SET @category = 'PLATINUM';

  RETURN @category;
END

```

Sehen Sie sich nun eine Abfrage an, die diese benutzerdefinierte Funktion aufruft.

```sql
SELECT C_NAME, dbo.customer_category(C_CUSTKEY) FROM CUSTOMER;
```

Der Ausführungsplan für diese Abfrage in SQL Server 2017 (Kompatibilitätsgrad 140 und früher) sieht folgendermaßen aus:

![Abfrageplan ohne Inlining](./media/query-plan-without-udf-inlining.png)

Der Plan zeigt, dass SQL Server in diesem Fall eine einfache Strategie übernimmt: Für jedes Tupel in der `CUSTOMER`-Tabelle werden die benutzerdefinierte Funktion aufgerufen und die Ergebnisse ausgegeben. Diese Strategie ist nicht effizient. Durch Inlining werden solche benutzerdefinierten Funktionen in gleichwertige skalare Unterabfragen transformiert, die die benutzerdefinierte Funktion in der aufrufenden Abfrage ersetzen.

Der Plan mit Inlining der benutzerdefinierten Funktion sieht für die gleiche Abfrage folgendermaßen aus.

![Abfrageplan mit Inlining](./media/query-plan-with-udf-inlining.png)

Wie zuvor erwähnt enthält der Abfrageplan keinen UDF-Operator mehr. Seine Auswirkungen sind nun im Plan ersichtlich, z.B. Ansichten oder Inline-Tabellenwertfunktionen. Hier sind die wichtigsten Beobachtungen, die aus dem obigen Plan resultieren:

1. SQL Server hat den impliziten Join zwischen `CUSTOMER` und `ORDERS` abgeleitet und diesen über einen Joinoperator in einen expliziten transformiert.
2. SQL Server hat außerdem die implizite `GROUP BY O_CUSTKEY on ORDERS`-Anweisung abgeleitet und „IndexSpool + StreamAggregate“ verwendet, um diese zu implementieren.
3. SQL Server verwendet nun einen Parallelismus für alle Operatoren.

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

Je nach Komplexität der Logik in der benutzerdefinierten Funktion kann der resultierende Abfrageplan größer und komplexer werden. Wie Sie sehen können, handelt es sich bei den Vorgängen innerhalb der benutzerdefinierten Funktion nicht mehr um eine Blackbox. Deshalb kann der Abfrageoptimierer diese Vorgänge optimieren und deren Kosten berücksichtigen. Da die benutzerdefinierte Funktion sich nicht mehr im Plan befindet, wird der iterative Aufruf derselben durch einen Plan ersetzt, der den Aufwand, der durch Funktionsaufrufe entsteht, vollständig vermeidet.

## <a name="inlineable-scalar-udfs-requirements"></a>Anforderungen für inlinefähige benutzerdefinierte Skalarfunktionen

Für eine benutzerdefinierte T-SQL-Skalarfunktion kann ein Inlining durchgeführt werden, wenn alle der folgenden Bedingungen erfüllt sind:

- Die benutzerdefinierte Funktion wurde mit folgenden Konstrukten geschrieben:
    - `DECLARE`, `SET`: Variablendeklaration und -zuweisungen
    - `SELECT`: SQL-Abfrage mit einer bzw. mehreren Variablenzuweisungen<sup>1</sup>
    - `IF`/`ELSE`: Verzweigung mit beliebigen Schachtelungsebenen
    - `RETURN`: eine oder mehrere RETURN-Anweisungen
    - `UDF`: geschachtelte bzw. rekursive Funktionsaufrufe<sup>2</sup>
    - Sonstige: relationale Vorgänge wie `EXISTS`, `ISNULL`
- Die benutzerdefinierte Funktion ruft keine intrinsische Funktion auf, die zeitabhängig ist (wie `GETDATE()`) oder Nebeneffekte<sup>3</sup> hat (wie `NEWSEQUENTIALID()`).
- Die benutzerdefinierte Funktion verwendet die `EXECUTE AS CALLER`-Klausel (Standardverhalten, wenn die `EXECUTE AS`-Klausel nicht angegeben wurde).
- Die benutzerdefinierte Funktion verweist nicht auf Tabellenvariablen oder Tabellenwertparameter.
- Die Abfrage, die eine benutzerdefinierte Skalarfunktion aufruft, verweist in der `GROUP BY`-Klausel nicht auf einen Aufruf einer benutzerdefinierten Skalarfunktion.
- Die Abfrage, die eine benutzerdefinierte Skalarfunktion in der Auswahlliste mit der `DISTINCT`-Klausel aufruft, verweist in der `ORDER BY`-Klausel nicht auf einen Aufruf einer benutzerdefinierten Skalarfunktion.
- Die benutzerdefinierte Funktion wird nicht nativ kompiliert (Interop wird unterstützt).
- Die benutzerdefinierte Funktion wird nicht in einer berechneten Spalte oder in der Definition einer CHECK-Einschränkung verwendet.
- Die benutzerdefinierte Funktion verweist nicht auf benutzerdefinierte Typen.
- Zur benutzerdefinierten Funktion werden keine Signaturen hinzugefügt.
- Bei der benutzerdefinierten Funktion handelt es sich nicht um eine Partitionsfunktion.

<sup>1</sup> Für `SELECT` mit einer Variablenakkumulation bzw. -aggregation (z.B. `SELECT @val += col1 FROM table1`) wird das Inlining nicht unterstützt.

<sup>2</sup> Für rekursive benutzerdefinierte Funktionen wird das Inlining nur bis zu einem bestimmten Grad durchgeführt.

<sup>3</sup> Intrinsische Funktionen, deren Ergebnisse von der aktuellen Systemzeit abhängen, sind zeitabhängig. Ein Beispiel für eine Funktion mit Nebeneffekten ist eine intrinsische Funktion, die einen internen globalen Status aktualisieren kann. Solche Funktionen geben bei jedem Aufruf unterschiedliche Ergebnisse auf Grundlage des internen Status zurück.

### <a name="checking-whether-or-not-a-udf-can-be-inlined"></a>So überprüfen Sie, ob ein Inlining einer benutzerdefinierten Funktion möglich ist

Für jede benutzerdefinierte T-SQL-Skalarfunktion enthält die Katalogansicht [sys.sql_modules](../system-catalog-views/sys-sql-modules-transact-sql.md) eine Eigenschaft namens `is_inlineable`, die angibt, ob für eine benutzerdefinierte Funktion ein Inlining möglich ist. Der Wert 1 gibt an, dass ein Inlining möglich ist, während der Wert 0 angibt, dass kein Inlining möglich ist. Diese Eigenschaft enthält für alle Inline-Tabellenwertfunktionen den Wert 1. Für alle anderen Module ist der Wert 0.

>[!NOTE]
>Wenn ein Inlining für eine benutzerdefinierte Skalarfunktion möglich ist, bedeutet das nicht, dass immer ein Inlining durchgeführt wird. SQL Server entscheidet (pro Abfrage und pro benutzerdefinierter Funktion), ob für eine benutzerdefinierte Funktion ein Inlining durchgeführt wird. Wenn die Definition der benutzerdefinierten Funktion beispielsweise zu Tausenden Codezeilen führt, führt SQL Server für diese möglicherweise kein Inlining durch. Für eine benutzerdefinierte Funktion in einer `GROUP BY`-Klausel wird ebenfalls kein Inlining durchgeführt. Diese Entscheidung erfolgt, wenn die Abfrage, die auf eine benutzerdefinierte Skalarfunktion verweist, kompiliert wird.

### <a name="checking-whether-inlining-has-happened-or-not"></a>So überprüfen Sie, ob ein Inlining durchgeführt wurde

Wenn alle Bedingungen erfüllt sind und SQL Server ein Inlining durchführt, wird die benutzerdefinierte Funktion in einen relationalen Ausdruck transformiert. Über den Abfrageplan können Sie einfach feststellen, ob ein Inlining durchgeführt wurde:

- Die XML des Plans enthält keinen `<UserDefinedFunction>`-XML-Knoten für eine benutzerdefinierte Funktion, für die erfolgreich ein Inlining durchführt wurde. 
- Bestimmte erweiterte Events (XEvents) werden ausgegeben.

## <a name="enabling-scalar-udf-inlining"></a>Aktivieren des Inlinings benutzerdefinierter Skalarfunktionen

Sie können Workloads automatisch für das Inlining benutzerdefinierter Skalarfunktionen zulassen, indem Sie den Kompatibilitätsgrad 150 für die Datenbank aktivieren. Diesen können Sie mit Transact-SQL festlegen. Beispiel:  

```sql
ALTER DATABASE [WideWorldImportersDW] SET COMPATIBILITY_LEVEL = 150;
```

Es müssen keine weiteren Änderungen vorgenommen, damit dieses Feature für benutzerdefinierte Funktionen oder Abfragen verwendet werden kann.

## <a name="disabling-scalar-udf-inlining-without-changing-the-compatibility-level"></a>Deaktivieren des Inlinings von benutzerdefinierten Skalarfunktionen ohne Änderung des Kompatibilitätsgrads

Das Inlining von benutzerdefinierten Skalarfunktionen kann im Datenbank- oder Anweisungs-, oder UDF-Bereich deaktiviert werden, während der Datenbankkompatibilitätsgrad weiterhin bei 150 und höher bleibt. Führen Sie folgende Anweisung im Kontext einer Datenbank aus, um das Inlining für benutzerdefinierte Skalarfunktionen im Datenbankbereich zu deaktivieren: 

```sql
ALTER DATABASE SCOPED CONFIGURATION SET TSQL_SCALAR_UDF_INLINING = OFF;
```

Führen Sie folgende Anweisung im Kontext einer Datenbank aus, um das Inlining für benutzerdefinierte Skalarfunktionen für eine Datenbank wieder zu aktivieren:

```sql
ALTER DATABASE SCOPED CONFIGURATION SET TSQL_SCALAR_UDF_INLINING = ON;
```

Wenn die Option auf ON festgelegt ist, wird die Einstellung in [`sys.database_scoped_configurations`](../system-catalog-views/sys-database-scoped-configurations-transact-sql.md) als „aktiviert“ angezeigt. Sie können das Inlining benutzerdefinierter Skalarfunktionen für eine bestimmte Abfrage auch deaktivieren, indem Sie `DISABLE_TSQL_SCALAR_UDF_INLINING` als `USE HINT`-Abfragehinweis festlegen. Beispiel:

```sql
SELECT L_SHIPDATE, O_SHIPPRIORITY, SUM (dbo.discount_price(L_EXTENDEDPRICE, L_DISCOUNT)) 
FROM LINEITEM
INNER JOIN ORDERS
  ON O_ORDERKEY = L_ORDERKEY 
GROUP BY L_SHIPDATE, O_SHIPPRIORITY ORDER BY L_SHIPDATE
OPTION (USE HINT('DISABLE_TSQL_SCALAR_UDF_INLINING'));
```

Ein `USE HINT`-Abfragehinweis hat Vorrang vor einer datenbankweit gültigen Konfiguration oder einer Einstellung des Kompatibilitätsgrads.

Das Inlining benutzerdefinierter Skalarfunktionen kann auch für eine bestimmte benutzerdefinierte Funktion deaktiviert werden, indem Sie die INLINE-Klausel in der `CREATE FUNCTION`- oder `ALTER FUNCTION`-Anweisung verwenden.
Beispiel:

```sql
CREATE OR ALTER FUNCTION dbo.discount_price(@price DECIMAL(12,2), @discount DECIMAL(12,2))
RETURNS DECIMAL (12,2)
WITH INLINE = OFF
AS
BEGIN
    RETURN @price * (1 - @discount);
END
```

Sobald die oben genannte Anweisung ausgeführt wurde, wird für diese benutzerdefinierte Funktion kein Inlining durchgeführt, wenn sie von einer Abfrage aufgerufen wird. Führen Sie folgende Anweisung aus, um das Inlining für diese benutzerdefinierte Funktion wieder zu aktivieren:

```sql
CREATE OR ALTER FUNCTION dbo.discount_price(@price DECIMAL(12,2), @discount DECIMAL(12,2))
RETURNS DECIMAL (12,2)
WITH INLINE = ON
AS
BEGIN
    RETURN @price * (1 - @discount);
END
```

>[!NOTE]
>Die `INLINE`-Klausel ist nicht verbindlich. Wenn die `INLINE`-Klausel nicht festgelegt ist, wird sie automatisch auf `ON`/`OFF` festgelegt, je nachdem, ob ein Inlining für die benutzerdefinierte Funktion durchgeführt werden kann. Wenn `INLINE=ON` festgelegt ist, aber für die benutzerdefinierte Funktion kein Inlining durchgeführt werden kann, wird ein Fehler ausgegeben.

## <a name="important-notes"></a>Wichtige Hinweise

Wie in diesem Artikel beschrieben wurde, wird beim Inlining einer benutzerdefinierten Skalarfunktion eine Abfrage mit benutzerdefinierten Skalarfunktionen in eine Abfrage mit einer gleichwertigen skalaren Unterabfrage transformiert. Durch diese Transformation kann es in folgenden Szenarios zu Unterschieden bei der Verhaltensweise kommen:

1. Das Inlining führt zu einem anderen Abfragehash für den gleichen Abfragetext.
1. Bestimmte Warnungen in Anweisungen in der benutzerdefinierten Funktion (z.B. die Division durch 0), die zuvor ausgeblendet waren, werden durch das Inlining nun möglicherweise angezeigt.
1. Joinhinweise auf Abfrageebene sind möglicherweise nicht mehr gültig, da durch das Inlining neue Joins hinzugefügt werden. Sie müssen stattdessen lokale Joinhinweise verwenden.
1. Ansichten, die auf benutzerdefinierte Inlineskalarfunktionen verweisen, können nicht indiziert werden. Wenn Sie einen Index in einer entsprechenden Ansicht erstellen müssen, sollten Sie das Inlining für die benutzerdefinierten Funktionen deaktivieren, auf die verwiesen wird.
1. Durch das Inlining benutzerdefinierter Funktionen kann das Verhalten der [dynamischen Datenmaskierung](../security/dynamic-data-masking.md) sich ändern. In bestimmten Situationen (je nach Logik in der benutzerdefinierten Funktion) in Bezug auf das Maskieren von Ausgabespalten einen konservativeren Ansatz dar. In Szenarios, bei denen es sich bei den Spalten, auf die in einer benutzerdefinierten Funktion verwiesen wird, nicht um Ausgabespalten handelt, werden diese nicht maskiert. 
1. Wenn eine benutzerdefinierte Funktion auf integrierte Funktionen wie `SCOPE_IDENTITY()` verweist, ändert sich der Wert, der von der integrierten Funktion zurückgegeben wird, durch das Inlining. Diese Änderung im Verhalten geht darauf zurück, dass das Inlining den Bereich der Anweisungen in der benutzerdefinierten Funktion ändert.

## <a name="see-also"></a>Weitere Informationen

[Leistungscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)

[Handbuch zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md)

[Referenz zu logischen und physischen Showplanoperatoren](../../relational-databases/showplan-logical-and-physical-operators-reference.md)

[Joins](../../relational-databases/performance/joins.md)

[Veranschaulichung der adaptiven Abfrageverarbeitung](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)
