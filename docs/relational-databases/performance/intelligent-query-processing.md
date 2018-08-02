---
title: Intelligente Abfrageverarbeitung in SQL-Datenbanken von Microsoft | Microsoft-Dokumentation
description: Features zur intelligenten Abfrageverarbeitung, die die Abfrageleistung in SQL Server und in Azure SQL-Datenbank verbessern
ms.custom: ''
ms.date: 07/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6f1b215e95b7cc911cd2815493eabbbd53a47424
ms.sourcegitcommit: a162a8f02d66c13b32d0b6255b0b52fc80e2187e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "39250448"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Intelligente Abfrageverarbeitung in SQL-Datenbanken
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Die Featurefamilie **Intelligente Abfrageverarbeitung** umfasst Features mit weitreichenden Auswirkungen, die die Leistung vorhandener Workloads mit minimalem Implementierungsaufwand verbessern.

![Features der intelligenten Abfrageverarbeitung](./media/1_IQPFeatureFamily.png)

## <a name="adaptive-query-processing"></a>Adaptive Abfrageverarbeitung
Die Featurefamilie „Adaptive Abfrageverarbeitung“ umfasst Verbesserungen bei der Abfrageverarbeitung, die Optimierungsstrategien auf die Laufzeitbedingungen Ihrer Anwendungsarbeitsauslastung anwenden. Diese Verbesserungen umfassen: Adaptive Joins im Batchmodus, Feedback zur Speicherzuweisung und die verschachtelte Ausführung für Tabellenwertfunktionen mit mehreren Anweisungen.

### <a name="batch-mode-adaptive-joins"></a>Adaptive Joins im Batchmodus
Dieses Feature ermöglicht Ihrem Plan, während der Ausführung mithilfe eines einzelnen zwischengespeicherten Plans dynamisch zu einer besseren Joinstrategie zu wechseln.

### <a name="row-and-batch-mode-memory-grant-feedback"></a>Feedback zur Speicherzuweisung im Zeilen- und Batchmodus
Dieses Feature berechnet den tatsächlich benötigten Speicherplatz für eine Abfrage und aktualisiert anschließend den Zuweisungswert für den zwischengespeicherten Plan. Hierdurch werden exzessive Speicherzuweisungen reduziert, die die Parallelität beeinflussen, und zu gering geschätzte Speicherzuweisungen behoben, die zu teuren Überläufen auf den Datenträger führen.

### <a name="interleaved-execution-for-multi-statement-table-valued-functions-mstvfs"></a>Verschachtelte Ausführung mit Tabellenwertfunktionen mit mehreren Anweisungen (MSTVFs)
Bei der verschachtelten Ausführung verwenden Sie die tatsächliche Zeilenanzahl aus der Funktion, um besser informierte Entscheidungen zum Downstream-Abfrageplan zu treffen. 

Weitere Informationen finden Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="table-variable-deferred-compilation"></a>Verzögerte Kompilierung von Tabellenvariablen
Die verzögerte Kompilierung von Tabellenvariablen verbessert die Qualität des Abfrageplans und die Gesamtleistung für Abfragen mit Verweisen auf Tabellenvariablen. Während der Optimierung und der ersten Kompilierung propagiert diese Funktion Kardinalitätsschätzungen, die auf tatsächlichen Tabellenvariablen-Zeilenzahlen basieren.  Diese genauen Zeilenzahlinformationen werden für die Optimierung der nachgelagerten Planvorgänge verwendet.

Bei der verzögerten Kompilierung von Tabellenvariablen wird die Kompilierung einer Anweisung, die auf eine Tabellenvariable verweist, bis zur ersten tatsächlichen Ausführung der Anweisung verzögert. Dieses verzögerte Kompilierungsverhalten ist identisch mit dem Verhalten von temporären Tabellen, und diese Änderung führt zur Verwendung der tatsächlichen Kardinalität anstelle der ursprünglichen einzeiligen Schätzung. Um die öffentliche Vorschau der verzögerten Kompilierung von Tabellenvariablen in der Azure SQL-Datenbank zu aktivieren, aktivieren Sie Datenbank-Kompatibilitätsgrad 150 für die Datenbank, mit der Sie beim Ausführen der Abfrage verbunden sind.

Weitere Informationen finden Sie unter [Verzögerte Kompilierung von Tabellenvariablen](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation ).

## <a name="approximate-query-processing"></a>Geschätzte Abfrageverarbeitung
Die geschätzte Abfrageverarbeitung ist eine neue Featurefamilie, die konzipiert wurde, um Aggregationen über große Datasets hinweg bereitzustellen, bei denen die Reaktionsfähigkeit wichtiger ist als die absolute Präzision.  Ein Beispiel könnte die Berechnung eines COUNT(DISTINCT()) über 10 Milliarden Zeilen für die Anzeige auf einem Dashboard sein.  In diesem Fall ist absolute Genauigkeit nicht wichtig, aber die Reaktionsfähigkeit ist es jedoch. Diese neue APPROX_COUNT_DISTINCT-Aggregatfunktion gibt die ungefähre Anzahl von eindeutigen Ungleich-Null-Werten in einer Gruppe zurück.

Weitere Informationen finden Sie unter [APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md).

## <a name="see-also"></a>Siehe auch
[Leistungscenter für SQL Server-Datenbankmodul und Azure SQL-Datenbank](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Leitfaden zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md)    
[Referenz zu logischen und physischen Showplanoperatoren](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Joins](../../relational-databases/performance/joins.md)    
[Veranschaulichung der adaptiven Abfrageverarbeitung](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)        
