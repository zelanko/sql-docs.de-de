---
title: Intelligente Abfrageverarbeitung in SQL-Datenbanken von Microsoft | Microsoft-Dokumentation
description: Features zur intelligenten Abfrageverarbeitung, die die Abfrageleistung in SQL Server und in Azure SQL-Datenbank verbessern
ms.custom: ''
ms.date: 01/11/2019
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
ms.openlocfilehash: e07bfa316330a24e9a7b9db5a2486ddd7cad470c
ms.sourcegitcommit: b51edbe07a0a2fdb5f74b5874771042400baf919
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087800"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Intelligente Abfrageverarbeitung in SQL-Datenbanken

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Die Featurefamilie **Intelligente Abfrageverarbeitung** umfasst Features mit weitreichenden Auswirkungen, die die Leistung vorhandener Workloads mit minimalem Implementierungsaufwand verbessern.  Sie können automatisch von dieser Featurefamilie profitieren, wenn Sie zum entsprechenden Datenbank-Kompatibilitätsgrad wechseln.

![Features der intelligenten Abfrageverarbeitung](./media/3_IQPFeatureFamily.png)

## <a name="adaptive-query-processing"></a>Adaptive Abfrageverarbeitung

Die Featurefamilie „Adaptive Abfrageverarbeitung“ umfasst Verbesserungen bei der Abfrageverarbeitung, die Optimierungsstrategien auf die Laufzeitbedingungen Ihrer Anwendungsworkload anwenden. Diese Verbesserungen beinhalten: 
- Adaptive Joins im Batchmodus
- Feedback zur Speicherzuweisung
- Verschachtelte Ausführung mit Tabellenwertfunktionen mit mehreren Anweisungen (MSTVFs)

### <a name="batch-mode-adaptive-joins"></a>Adaptive Joins im Batchmodus

Dieses Feature ermöglicht Ihrem Plan, während der Ausführung mithilfe eines einzelnen zwischengespeicherten Plans dynamisch zu einer besseren Joinstrategie zu wechseln.

Weitere Informationen zu adaptiven Joins im Batchmodus finden Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="row-and-batch-mode-memory-grant-feedback"></a>Feedback zur Speicherzuweisung im Zeilen- und Batchmodus

> [!NOTE]
> Feedback zur Speicherzuweisung im Zeilenmodus ist eine öffentliche Previewfunktion.  

Dieses Feature berechnet den tatsächlich benötigten Speicherplatz für eine Abfrage und aktualisiert anschließend den Zuweisungswert für den zwischengespeicherten Plan. Hierdurch werden exzessive Speicherzuweisungen reduziert, die die Parallelität beeinflussen, und zu gering geschätzte Speicherzuweisungen behoben, die zu teuren Überläufen auf den Datenträger führen.

Weitere Informationen zum Feedback zur Speicherzuweisung finden Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

### <a name="interleaved-execution-for-multi-statement-table-valued-functions-mstvfs"></a>Verschachtelte Ausführung mit Tabellenwertfunktionen mit mehreren Anweisungen (MSTVFs)

Bei der verschachtelten Ausführung verwenden Sie die tatsächliche Zeilenanzahl aus der Funktion, um besser informierte Entscheidungen zum Downstream-Abfrageplan zu treffen. Weitere Informationen zu Tabellenwertfunktionen mit mehreren Anweisungen (MSTVFs) finden Sie unter [Tabellenwertfunktionen](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF).

Weitere Informationen finden zur verschachtelten Ausführung Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="table-variable-deferred-compilation"></a>Verzögerte Kompilierung von Tabellenvariablen

> [!NOTE]
> Die verzögerte Kompilierung von Tabellenvariablen ist ein Feature in der öffentlichen Preview.  

Die verzögerte Kompilierung von Tabellenvariablen verbessert die Qualität des Abfrageplans und die Gesamtleistung für Abfragen mit Verweisen auf Tabellenvariablen. Während der Optimierung und der ersten Kompilierung propagiert diese Funktion Kardinalitätsschätzungen, die auf tatsächlichen Tabellenvariablen-Zeilenzahlen basieren.  Diese genauen Zeilenzahlinformationen werden für die Optimierung der nachgelagerten Planvorgänge verwendet.

Bei der verzögerten Kompilierung von Tabellenvariablen wird die Kompilierung einer Anweisung, die auf eine Tabellenvariable verweist, bis zur ersten tatsächlichen Ausführung der Anweisung verzögert. Dieses verzögerte Kompilierungsverhalten ist identisch mit dem Verhalten von temporären Tabellen, und diese Änderung führt zur Verwendung der tatsächlichen Kardinalität anstelle der ursprünglichen einzeiligen Schätzung. Um die öffentliche Vorschau der verzögerten Kompilierung von Tabellenvariablen in der Azure SQL-Datenbank zu aktivieren, aktivieren Sie Datenbank-Kompatibilitätsgrad 150 für die Datenbank, mit der Sie beim Ausführen der Abfrage verbunden sind.

Weitere Informationen finden Sie unter [Verzögerte Kompilierung von Tabellenvariablen](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation ).

## <a name="scalar-udf-inlining"></a>Inlining benutzerdefinierter Skalarfunktionen

> [!NOTE]
> Das Inlining benutzerdefinierter Skalarfunktion ist ein Previewfeature.  

Das Inlining [benutzerdefinierter Skalarfunktionen](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#Scalar) wandelt die entsprechenden Funktionen automatisch in relationale Ausdrücke um und bettet sie in die aufrufende SQL-Abfrage ein. Dadurch wird die Leistung von Workloads verbessert, die benutzerdefinierte Skalarfunktionen verwenden. Das Inlining benutzerdefinierter Skalarfunktionen ermöglicht eine kostenbasierte Optimierung von Vorgängen in benutzerdefinierten Funktionen und erzielt effiziente Pläne, die konkret und parallel sind – im Gegensatz zu ineffizienten, iterativen, seriellen Ausführungsplänen. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

Weitere Informationen finden Sie unter [Scalar UDF Inlining (Inlining benutzerdefinierter Skalarfunktionen)](../user-defined-functions/scalar-udf-inlining.md).

## <a name="approximate-query-processing"></a>Geschätzte Abfrageverarbeitung

> [!NOTE]
> APPROX_COUNT_DISTINCT ist ein öffentliches Vorschaufeature.  

Die geschätzte Abfrageverarbeitung ist eine neue Featurefamilie, die konzipiert wurde, um Aggregationen über große Datasets hinweg bereitzustellen, bei denen die Reaktionsfähigkeit wichtiger ist als die absolute Präzision.  Ein Beispiel könnte die Berechnung eines COUNT(DISTINCT()) über 10 Milliarden Zeilen für die Anzeige auf einem Dashboard sein.  In diesem Fall ist absolute Genauigkeit nicht wichtig, aber die Reaktionsfähigkeit ist es jedoch. Diese neue APPROX_COUNT_DISTINCT-Aggregatfunktion gibt die ungefähre Anzahl von eindeutigen Ungleich-Null-Werten in einer Gruppe zurück.

Weitere Informationen finden Sie unter [APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md).

## <a name="batch-mode-on-rowstore"></a>Batchmodus bei Rowstore 

> [!NOTE]
> Batchmodus bei Rowstore ist eine öffentliche Previewfunktion.  

### <a name="background"></a>Hintergrund

Mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] wurde ein neues Feature zur Beschleunigung analytischer Workloads eingeführt: Columnstore-Indizes. Wir haben die Anwendungsfälle erweitert und die Leistung von Columnstore-Indizes in allen nachfolgenden Releases verbessert. Bisher wurden diese Funktionen so dargestellt und dokumentiert, als ob es sich um genau ein Feature handeln würde: Durch die Erstellung von Columnstore-Indizes für Tabellen wurden analytische Workloads einfach schneller ausgeführt. Im Hintergrund gibt es jedoch zwei miteinander zusammenhängende, aber unterschiedliche Gruppen von Technologien:
- **Columnstore**-Indizes erlauben Analyseabfragen nur den Zugriff auf die Daten in den Spalten, die sie benötigen. Das Columnstore-Format ermöglicht auch viel effektivere Komprimierung, als Sie mit der Seitenkomprimierung in herkömmlichen „Rowstore“-Indizes erhalten. 
- **Batchmodus**-Verarbeitung ermöglicht Abfrageoperatoren, Daten effizienter zu verarbeiten, indem jeweils ein Batch von Zeilen statt einer einzelnen Zeile verarbeitet wird. Zahlreiche weitere Verbesserungen der Skalierbarkeit sind an die Batchmodusverarbeitung gebunden. Weitere Informationen zum Batchmodus finden Sie unter [Ausführungsmodi](../../relational-databases/query-processing-architecture-guide.md#execution-modes).

Die zwei Gruppen von Funktionen verbessern zusammen die E/A- und CPU-Auslastung:
- Mit Columnstore-Indizes passen mehr Daten in den Arbeitsspeicher, und dies reduziert die E/A-Anforderungen.
- Die Batchmodusverarbeitung nutzt die CPU effizienter.

Wann immer möglich, machen sich die beiden Technologien gegenseitig zu Nutze. So können Batchmodusaggregate z.B. als Teil eines Columnstore-Indexes ausgewertet werden. Wir verarbeiten auch mit der Lauflängenkodierung komprimierte Columnstore-Daten wesentlich effizienter mit Joins im Batchmodus und Batchmodusaggregaten. 
 
Die beiden Features können schon unabhängig verwendet werden: Sie können Zeilenmoduspläne erhalten, die Columnstore-Indizes verwenden, und Batchmoduspläne, die nur Rowstore-Indizes verwenden. Aber da Sie in den meisten Fällen die besten Ergebnisse erhalten, wenn die beiden Features gemeinsam verwendet werden, hat der Abfrageoptimierer von SQL den Batchmodus bis jetzt nur für Abfragen in Erwägung gezogen, die mindestens eine Tabelle mit einem Columnstore-Index enthalten.

Bei einigen Anwendungen sind Columnstore-Indizes nicht realisierbar, da die Anwendung ein anderes Feature benutzt, das mit Columnstore-Indizes nicht unterstützt wird (Trigger werden z.B. nicht für Tabellen mit gruppierten Columnstore-Indizes unterstützt). Noch wichtiger: Columnstore-Indizes bewirken zusätzlichen Aufwand für DELETE- und UPDATE-Anweisungen, da direkte Änderungen nicht mit der Columnstore-Komprimierung kompatibel sind. Für einige hybride Transaktions-/Analyseworkloads wird der Vorteil von Columnstore-Indizes für Analyseabfragen durch den Mehraufwand bei den Transaktionsaspekten einer Workload zunichte gemacht. In solchen Szenarien wird eine verbesserte CPU-Auslastung allein durch die Batchmodusverarbeitung erzielt, weshalb das **Batchmodus bei Rowstore**-Feature den Batchmodus für alle Abfragen favorisiert, unabhängig davon, ob Indizes im Spiel sind.

### <a name="what-workloads-may-benefit-from-batch-mode-on-rowstore"></a>Workloads, die vom Batchmodus auf Rowstore profitieren können

Die folgenden Workloads können vom Batchmodus auf Rowstore profitieren:
1. Ein erheblicher Teil der Workloads besteht aus Analyseabfragen (als Faustregel: Abfragen mit Operatoren wie z.B. Joins oder Aggregaten, die mindestens Hunderte oder Tausende von Zeilen verarbeiten), **UND**
2. Die Workload ist CPU-abhängig (wenn E/A der Engpass ist, sollte nach Möglichkeit dennoch ein Columnstore-Index verwendet werden), **UND**
3. Erstellen eines Columnstore-Indexes steigert den Aufwand für den Transaktionsteil Ihrer Workload zu stark, **ODER** das Erstellen eines Columnstore-Indexes ist nicht möglich, da Ihre Anwendung von einem Feature abhängt, das noch nicht mit Columnstore-Indizes unterstützt wird.

> [!NOTE]
> Batchmodus bei Rowstore kann nur bei der Verringerung des CPU-Verbrauchs helfen. Wenn Ihr Engpass E/A-bezogen ist und Daten nicht bereits zwischengespeichert werden („kalter“ Cache), verbessert Batchmodus bei Rowstore die verstrichene Zeit NICHT. Ähnlich gilt, dass, wenn auf dem Computer nicht genügend Arbeitsspeicher zum Zwischenspeichern aller Daten vorhanden ist, eine Leistungsverbesserung unwahrscheinlich ist.

### <a name="what-changes-with-batch-mode-on-rowstore"></a>Welche Änderungen mit dem Batchmodus auf Rowstore verbunden sind

Vom Wechsel zum Kompatibilitätsgrad 150 abgesehen, müssen Sie auf Ihrer Seite nichts ändern, um den Batchmodus auf Rowstore für mögliche Workloads zu aktivieren.

Auch wenn eine Abfrage keine Tabelle mit einem Columnstore-Index beinhaltet, verwendet der Abfrageprozessor jetzt Heuristik, um zu entscheiden, ob der Batchmodus berücksichtigt wird. Die Heuristik umfasst Folgendes:
1. Ein erstes Überprüfen der Tabellengrößen, verwendeten Operatoren und geschätzten Kardinalitäten in der Eingabeabfrage.
2. Weitere Prüfpunkte kommen hinzu, wenn der Abfrageoptimierer neue, kostengünstigere Pläne für die Abfrage entdeckt. Wenn diese alternativen Pläne keine signifikante Verwendung des Batchmodus aufweisen, beendet der Optimierer die Untersuchung von Batchmodusalternativen.

Wenn der Batchmodus bei Rowstore verwendet wird, sehen Sie im Abfrageausführungsplan als tatsächlichen Ausführungsmodus den „Batchmodus“, der vom Scan-Operator für Heaps auf dem Datenträger und B-Struktur-Indizes verwendet wird.  Diese Überprüfung im Batchmodus kann Batchmodus-Bitmapfilter auswerten.  Vielleicht finden Sie auch andere Batchmodusoperatoren im Plan, z.B. Hashjoins, hashbasierte Aggregate, Sortierungen, Fensteraggregate, Filter, Verkettung und Skalarwertberechnungs-Operatoren.

### <a name="remarks"></a>Remarks

1. Es gibt keine Garantie, dass Abfragepläne den Batchmodus verwenden. Der Abfrageoptimierer entscheidet möglicherweise, dass der Batchmodus für die Abfrage nicht sinnvoll zu sein scheint. 
2. Wenn sich der Suchbereich des Abfrageoptimierers ändert, besteht keine Garantie, dass ein Zeilenmodusplan, den Sie erhalten, mit dem Plan identisch ist, den Sie in einem niedrigeren Kompatibilitätsgrad erhalten. Es gibt auch keine Garantie, dass ein Batchmodusplan, den Sie erhalten, mit dem Plan identisch ist, den Sie mit einem Columnstore-Index erhalten. 
3. Aufgrund des neuen Batchmodus-Rowstore-Scans können Pläne sich auch leicht für Abfragen ändern, die Columnstore- und Rowstore-Indizes mischen.
4. Aktuell bestehen folgende Einschränkungen für den neuen Batchmodus bei Rowstorescans: Er funktioniert nicht bei In-Memory-OLTP-Tabellen und kann ausschließlich für Indizes verwendet werden, die sich auf Datenträgerheaps oder in B-Strukturen befinden. Er funktioniert auch nicht, wenn eine LOB-Spalte abgerufen oder gefiltert wird. Diese Einschränkung betrifft Spaltensätze mit geringer Dichte und XML-Spalten.
5. Es gibt Abfragen, für die der Batchmodus auch mit Columnstore-Indizes nicht verwendet wird (z.B. Abfragen im Zusammenhang mit Cursorn), und die gleichen Ausschlüsse gelten auch für den Batchmodus bei Rowstore.

### <a name="configuring-batch-mode-on-rowstore"></a>Konfigurieren des Batchmodus bei Rowstore

Die datenbankweite Konfiguration BATCH_MODE_ON_ROWSTORE ist standardmäßig aktiviert und kann verwendet werden, um den Batchmodus bei Rowstore zu deaktivieren, ohne dass eine Änderung im Datenbank-Kompatibilitätsgrad erforderlich ist:

```sql
-- Disabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = OFF;

-- Enabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = ON;
```

Sie können den Batchmodus bei Rowstore über die datenbankweite Konfiguration deaktivieren, aber die Einstellung immer noch auf der Abfrageebene mit dem Abfragehinweis ALLOW_BATCH_MODE überschreiben. Im folgenden Beispiel wird der Batchmodus bei Rowstore aktiviert, auch wenn die Funktion über die datenbankweite Konfiguration deaktiviert ist:

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('ALLOW_BATCH_MODE'));
```

Sie können den Batchmodus bei Rowstore auch mit dem Abfragehinweis DISALLOW_BATCH_MODE für eine bestimmte Abfrage deaktivieren. Zum Beispiel:

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
