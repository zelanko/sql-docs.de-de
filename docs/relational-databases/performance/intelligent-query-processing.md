---
title: Intelligente Abfrageverarbeitung in SQL-Datenbanken von Microsoft | Microsoft-Dokumentation
description: Features zur intelligenten Abfrageverarbeitung, die die Abfrageleistung in SQL Server und in Azure SQL-Datenbank verbessern
ms.custom: ''
ms.date: 02/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dc47ad30edc0eb4092aa1f92fef703c95cb34593
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56291658"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Intelligente Abfrageverarbeitung in SQL-Datenbanken

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Die Featurefamilie für die intelligente Abfrageverarbeitung (QP) umfasst Funktionen mit breiter Wirkung. Sie verbessern die Leistung bestehender Workloads mit minimalem Implementierungsaufwand. Um automatisch von dieser Featurefamilie zu profitieren, wechseln Sie zum entsprechenden Datenbank-Kompatibilitätsgrad.

| **IQP-Feature** | **Unterstützt in Azure SQL-Datenbank** | **Unterstützt in SQL Server** |
| --- | --- | --- |
| [Adaptive Joins (Batchmodus)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#batch-mode-adaptive-joins) | Ja, unter Kompatibilitätsgrad 140| Ja,ab SQL Server 2017 unter Kompatibilitätsgrad 140|
| [Verschachtelte Ausführung](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#interleaved-execution-for-multi-statement-table-valued-functions) | Ja, unter Kompatibilitätsgrad 140| Ja,ab SQL Server 2017 unter Kompatibilitätsgrad 140|
| [Feedback zur Speicherzuweisung (Batchmodus)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#batch-mode-memory-grant-feedback) | Ja, unter Kompatibilitätsgrad 140| Ja,ab SQL Server 2017 unter Kompatibilitätsgrad 140|
| [Feedback zur Speicherzuweisung (Zeilenmodus)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#row-mode-memory-grant-feedback) | Ja, unter Kompatibilitätsgrad 150, öffentliche Vorschauversion| Ja,ab SQL Server 2019 CTP 2.0 unter Kompatibilitätsgrad 150, öffentliche Vorschauversion|
| [Approximate Count Distinct](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#approximate-query-processing) | Ja, öffentliche Vorschauversion| Ja, ab SQL Server 2019 CTP 2.0, öffentliche Vorschauversion|
| [Verzögerte Kompilierung von Tabellenvariablen](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#table-variable-deferred-compilation) | Ja, unter Kompatibilitätsgrad 150, öffentliche Vorschauversion| Ja,ab SQL Server 2019 CTP 2.0 unter Kompatibilitätsgrad 150, öffentliche Vorschauversion|
| [Batchmodus bei Rowstore](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#batch-mode-on-rowstore) | Ja, unter Kompatibilitätsgrad 150, öffentliche Vorschauversion| Ja,ab SQL Server 2019 CTP 2.0 unter Kompatibilitätsgrad 150, öffentliche Vorschauversion|
| [Inlining benutzerdefinierter Skalarfunktionen](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#scalar-udf-inlining) | Nein, aber für ein zukünftiges Update geplant | Ja,ab SQL Server 2019 CTP 2.1 unter Kompatibilitätsgrad 150, öffentliche Vorschauversion|


## <a name="adaptive-query-processing"></a>Adaptive Abfrageverarbeitung

Die Featurefamilie der adaptiven Abfrageverarbeitung umfasst die folgenden Verbesserungen bei der Abfrageverarbeitung. Diese passen die Optimierungsstrategien auf die Runtimebedingungen Ihrer Anwendungsworkload an: 
- Adaptive Joins im Batchmodus
- Feedback zur Speicherzuweisung
- Verschachtelte Ausführung mit Tabellenwertfunktionen mit mehreren Anweisungen (MSTVFs)

### <a name="batch-mode-adaptive-joins"></a>Adaptive Joins im Batchmodus

Dieses Feature ermöglicht Ihrem Plan, während der Ausführung mithilfe eines einzelnen zwischengespeicherten Plans dynamisch zu einer besseren Joinstrategie zu wechseln.

Weitere Informationen zu adaptiven Joins im Batchmodus finden Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="row-and-batch-mode-memory-grant-feedback"></a>Feedback zur Speicherzuweisung im Zeilen- und Batchmodus

> [!NOTE]
> Feedback zur Speicherzuweisung im Zeilenmodus ist eine öffentliche Previewfunktion.  

Dieses Feature berechnet den tatsächlichen Speicherbedarf für eine Abfrage neu. Anschließend wird der Zuweisungswert für den zwischengespeicherten Plan aktualisiert. Übermäßige Speicherzuweisungen, die die Parallelität beeinträchtigen, werden reduziert. Dieses Feature behebt auch unterschätzte Speicherzuweisungen, die zu teueren Überläufen auf dem Datenträger führen.

Weitere Informationen zum Feedback zur Speicherzuweisung finden Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="interleaved-execution-for-mstvfs"></a>Verschachtelte Ausführung für MSTVFs

Bei der verschachtelten Ausführung verwenden Sie die tatsächliche Zeilenanzahl aus der Funktion, um besser informierte Entscheidungen zum Downstream-Abfrageplan zu treffen. Weitere Informationen zu Tabellenwertfunktionen mit mehreren Anweisungen (MSTVFs) finden Sie unter [Tabellenwertfunktionen](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF).

Weitere Informationen finden zur verschachtelten Ausführung Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="table-variable-deferred-compilation"></a>Verzögerte Kompilierung von Tabellenvariablen

> [!NOTE]
> Die verzögerte Kompilierung von Tabellenvariablen ist ein Feature in der öffentlichen Preview.  

Die verzögerte Kompilierung von Tabellenvariablen verbessert die Qualität des Abfrageplans und die Gesamtleistung für Abfragen mit Verweisen auf Tabellenvariablen. Während der Optimierung und der ersten Kompilierung propagiert diese Funktion Kardinalitätsschätzungen, die auf tatsächlichen Tabellenvariablen-Zeilenzahlen basieren. Diese genauen Zeilenzahlinformationen werden für die Optimierung der nachgelagerten Planvorgänge verwendet.

Bei der verzögerten Kompilierung von Tabellenvariablen wird die Kompilierung einer Anweisung, die auf eine Tabellenvariable verweist, bis zur ersten tatsächlichen Ausführung der Anweisung verzögert. Dieses Verhalten der verzögerten Kompilierung ist identisch mit dem von temporären Tabellen. Diese Änderung führt dazu, dass anstelle des ursprünglichen einreihigen Schätzwertes die tatsächliche Kardinalität verwendet wird. 

Sie können die öffentliche Vorschau der verzögerten Kompilierung von Tabellenvariablen in der Azure SQL-Datenbank aktivieren. Aktivieren Sie dazu den Kompatibilitätsgrad 150 für die Datenbank, mit der Sie bei der Ausführung der Abfrage verbunden sind.

Weitere Informationen finden Sie unter [Verzögerte Kompilierung von Tabellenvariablen](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation).

## <a name="scalar-udf-inlining"></a>Inlining benutzerdefinierter Skalarfunktionen

> [!NOTE]
> Das Inlining benutzerdefinierter Skalarfunktion ist eine Previewfunktion.  

Das skalare UDF-Inlining wandelt [skalare UDFs](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#Scalar) automatisch in relationale Ausdrücke um. Diese werden in die aufrufende SQL-Abfrage eingebettet. Diese Transformation verbessert die Leistung von Workloads, die skalare UDFs nutzen. Skalares UDF-Inlining ermöglicht eine kostenbasierte Optimierung der Vorgänge innerhalb von UDFs. Die Ergebnisse sind effiziente, mengenorientierte und parallele statt ineffiziente, iterative, serielle Ausführungspläne. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

Weitere Informationen finden Sie unter [Inlining benutzerdefinierter Skalarfunktionen](../user-defined-functions/scalar-udf-inlining.md).

## <a name="approximate-query-processing"></a>Geschätzte Abfrageverarbeitung

> [!NOTE]
> **APPROX_COUNT_DISTINCT** ist eine öffentliche Previewfunktion.  

Die geschätzte Abfrageverarbeitung ist eine neue Featurefamilie. Sie stellt Aggregationen über große Datasets hinweg bereit, bei denen die Reaktionsfähigkeit wichtiger ist als die absolute Präzision. Ein Beispiel ist die Berechnung eines **COUNT(DISTINCT())** über 10 Milliarden Zeilen für die Anzeige auf einem Dashboard. In diesem Fall ist absolute Genauigkeit nicht wichtig, aber die Reaktionsfähigkeit ist es jedoch. Diese neue **APPROX_COUNT_DISTINCT**-Aggregatfunktion gibt die ungefähre Anzahl von eindeutigen Ungleich-Null-Werten in einer Gruppe zurück.

Weitere Informationen finden Sie unter [APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md).

## <a name="batch-mode-on-rowstore"></a>Batchmodus bei Rowstore 

> [!NOTE]
> Batchmodus bei Rowstore ist eine öffentliche Previewfunktion.  

### <a name="background"></a>Hintergrund

Mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wurde ein neues Feature zur Beschleunigung analytischer Workloads eingeführt: Columnstore-Indizes. Wir haben die Anwendungsfälle erweitert und die Leistung von Columnstore-Indizes in allen nachfolgenden Releases verbessert. Bisher wurden diese Funktionen so dargestellt und dokumentiert, als ob es sich um genau ein Feature handeln würde. Sie erstellen die Columnstore-Indizes in Ihren Tabellen. Und Ihre analytische Workload wird schneller ausgeführt. Es gibt jedoch zwei miteinander zusammenhängende, aber unterschiedliche Gruppen von Technologien:
- **Columnstore**-Indizes erlauben Analyseabfragen nur den Zugriff auf die Daten in den Spalten, die sie benötigen. Die Seitenkomprimierung im Spaltenspeicherformat ist ebenfalls effektiver als die Komprimierung in traditionellen **Rowstore**-Indizes. 
- Mit der Verarbeitung im **Batchmodus** verarbeiten Abfrageoperatoren Daten effizienter. Die Verarbeitung erfolgt für ein Batch an Zeilen und nicht für jede Zeile einzeln. Zahlreiche weitere Verbesserungen der Skalierbarkeit sind an die Batchmodusverarbeitung gebunden. Weitere Informationen zum Batchmodus finden Sie unter [Ausführungsmodi](../../relational-databases/query-processing-architecture-guide.md#execution-modes).

Die zwei Gruppen von Funktionen verbessern zusammen die E/A- und CPU-Auslastung:
- Durch Columnstore-Indizes passen mehr Daten in den Speicher. Dadurch sind weniger E/A-Vorgänge erforderlich.
- Die Batchmodusverarbeitung nutzt die CPU effizienter.

Wann immer möglich, machen sich die beiden Technologien gegenseitig zu Nutze. So können Batchmodusaggregate z.B. als Teil eines Columnstore-Indexes ausgewertet werden. Wir verarbeiten auch mit der Lauflängencodierung komprimierte Columnstore-Daten wesentlich effizienter mit Joins im Batchmodus und Batchmodusaggregaten. 
 
Die beiden Funktionen können unabhängig voneinander verwendet werden:
* Sie erhalten die Zeilemoduspläne, die Columnstore-Indizes verwenden.
* Sie erhalten die Batchmoduspläne, die nur Rowstore-Indizes verwenden. 

Sie erhalten in der Regel die besten Ergebnisse, wenn Sie die beiden Features zusammen verwenden. Bisher betrachtete der SQL Server-Abfrageoptimierer die Verarbeitung im Batchmodus nur für Abfragen, die mindestens eine Tabelle mit einem Columnstore-Index betreffen.

Columnstore-Indizes sind keine gute Option für einige Anwendungen. Eine Anwendung kann ein anderes Feature verwenden, das nicht von Columnstore-Indizes unterstützt wird. Direkte Änderungen sind beispielsweise nicht mit der Columnstore-Komprimierung kompatibel. Daher werden Auslöser in Tabellen mit gruppierten Columnstore-Indizes nicht unterstützt. Noch wichtiger ist, dass **DELETE**- und **UPDATE**-Anweisungen durch Columnstore-Indizes aufwändiger werden. 

Für einige hybride Transaktions-/Analyseworkloads wird der Vorteil von Columnstore-Indizes für Analyseabfragen durch den Mehraufwand bei den Transaktionsaspekten einer Workload zunichte gemacht. Solche Szenarien können die CPU-Auslastung allein durch die Batchverarbeitung verbessern. Aus diesem Grund berücksichtigt der Batchmodus des Rowstore-Features den Batchmodus für alle Abfragen. Es spielt keine Rolle, welche Indizes beteiligt sind.

### <a name="workloads-that-might-benefit-from-batch-mode-on-rowstore"></a>Workloads, die vom Batchmodus auf Rowstore profitieren können

Die folgenden Workloads können vom Batchmodus auf Rowstore profitieren:
* Ein signifikanten Teil der Workload besteht aus analytischen Abfragen. Normalerweise haben diese Abfragen Operatoren wie Joins oder Aggregate, die Hunderttausende von Zeilen oder mehr verarbeiten.
* Die Workload ist CPU-gebunden. Wenn der Engpass E/A ist, empfehlen wir weiterhin, dass Sie einen Columnstore-Index nach Möglichkeit in Betracht ziehen.
* Das Erstellen eines Columnstore-Index fügt dem transaktionalen Teil Ihrer Workload zu viel Mehraufwand hinzu. Oder es kann kein Columnstore-Index erstellt werden, da Ihre Anwendung von einem Feature abhängt, das noch nicht bei Columnstore-Indizes unterstützt wird.

> [!NOTE]
> Batchmodus bei Rowstore kann nur bei der Verringerung des CPU-Verbrauchs helfen. Wenn Ihr Engpass E/A-bezogen ist und Daten nicht bereits zwischengespeichert werden („kalter“ Cache), verbessert Batchmodus bei Rowstore die verstrichene Zeit nicht. Ähnlich gilt, dass, wenn auf dem Computer nicht genügend Arbeitsspeicher zum Zwischenspeichern aller Daten vorhanden ist, eine Leistungsverbesserung unwahrscheinlich ist.

### <a name="what-changes-with-batch-mode-on-rowstore"></a>Welche Änderungen mit dem Batchmodus auf Rowstore verbunden sind

Vom Wechsel zum Kompatibilitätsgrad 150 abgesehen, müssen Sie auf Ihrer Seite nichts ändern, um den Batchmodus auf Rowstore für mögliche Workloads zu aktivieren.

Auch wenn eine Abfrage keine Tabelle mit einem Columnstore-Index beinhaltet, verwendet der Abfrageprozessor jetzt Heuristik, um zu entscheiden, ob der Batchmodus berücksichtigt wird. Die Heuristik umfasst diese Überprüfungen:
1. Ein erstes Überprüfen der Tabellengrößen, verwendeten Operatoren und geschätzten Kardinalitäten in der Eingabeabfrage.
2. Weitere Prüfpunkte kommen hinzu, wenn der Abfrageoptimierer neue, kostengünstigere Pläne für die Abfrage entdeckt. Wenn diese alternativen Pläne keine signifikante Verwendung des Batchmodus aufweisen, beendet der Optimierer die Untersuchung von Batchmodusalternativen.

Wenn der Batch-modus bei Rowstow verwendet wird, sehen Sie den tatsächlichen Ausführungsmodus als **Batchmodus** im Abfrageplan. Der Scan-Operator verwendet den Batchmodus für On-Disk-Heaps und B-Struktur-Indizes. Diese Überprüfung im Batchmodus kann Batchmodus-Bitmapfilter auswerten. Vielleicht finden Sie auch andere Batchmodusoperatoren im Plan. Beispielsweise Hashjoins, hashbasierte Aggregate, Sortierungen, Fensteraggregate, Filter, Verkettung und Skalarwertberechnungs-Operatoren.

### <a name="remarks"></a>Remarks

* Abfragepläne verwenden nicht immer den Batchmodus. Der Abfrageoptimierer entscheidet möglicherweise, dass der Batchmodus für die Abfrage nicht sinnvoll ist. 
* Der Suchbereich des Abfrageoptimierers ändert sich. Wenn Sie also einen Zeilenmodusplan erhalten, ist er möglicherweise nicht derselbe wie der Plan, den Sie in einem niedrigeren Kompatibilitätsgrad erhalten. Und wenn Sie einen Batchmodusplan erhalten, ist er möglicherweise nicht derselbe wie der Plan, den Sie mit einem Columnstore-Index erhalten. 
* Aufgrund des neuen Batchmodus-Rowstore-Scans können Pläne sich auch für Abfragen ändern, die Columnstore- und Rowstore-Indizes mischen.
* Aktuell bestehen folgende Einschränkungen für den neuen Batchmodus bei Rowstorescans: 
    * Er funktioniert nicht bei In-Memory-OLTP-Tabellen und kann ausschließlich für Indizes verwendet werden, die sich auf Datenträgerheaps oder in B-Strukturen befinden. 
    * Er funktioniert auch nicht, wenn eine LOB-Spalte abgerufen oder gefiltert wird. Diese Einschränkung betrifft Spaltensätze mit geringer Dichte und XML-Spalten.
* Es gibt Abfragen, für die der Batchmodus auch bei Columnstore-Indizes nicht verwendet wird. Beispiele sind Abfragen, die Cursor enthalten. Dieselben Ausschlüsse gelten auch für den Batchmodus bei Rowstore.

### <a name="configure-batch-mode-on-rowstore"></a>Konfigurieren des Batchmodus bei Rowstore

Die datenbankweite **BATCH_MODE_ON_ROWSTORE**-Konfiguration ist standardmäßig aktiviert. Sie deaktiviert den Batchmodus bei Rowstore, ohne dass eine Änderung des Datenbank-Kompatibilitätgrads erforderlich ist:

```sql
-- Disabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = OFF;

-- Enabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = ON;
```

Sie können den Batchmodus bei Rowstore über die datenbankweite Konfiguration deaktivieren. Sie können die Einstellung auf Abfrageebene jedoch immer noch überschreiben, indem Sie den Abfragehinweis **ALLOW_BATCH_MODE** verwenden. Im folgenden Beispiel wird der Batchmodus bei Rowstore aktiviert, auch wenn die Funktion über die datenbankweite Konfiguration deaktiviert ist:

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('ALLOW_BATCH_MODE'));
```

Sie können den Batchmodus bei Rowstore auch mit dem Abfragehinweis **DISALLOW_BATCH_MODE** für eine bestimmte Abfrage deaktivieren. Sehen Sie sich folgendes Beispiel an:

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('DISALLOW_BATCH_MODE'));
```

## <a name="see-also"></a>Siehe auch

[Leistungscenter für SQL Server-Datenbankmodul und Azure SQL-Datenbank](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Leitfaden zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md)    
[Referenz zu logischen und physischen Showplanoperatoren](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Joins](../../relational-databases/performance/joins.md)    
[Veranschaulichung der adaptiven Abfrageverarbeitung](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)       
[Veranschaulichung intelligenter Abfrageverarbeitung](https://github.com/joesackmsft/Conferences/blob/master/IQPDemos/IQP_Demo_ReadMe.md)   
