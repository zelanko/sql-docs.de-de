---
title: Kardinalitätsschätzung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/24/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.openlocfilehash: 5a81849f65e5b71acf233febb61e7725ec1e804e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050523"
---
# <a name="cardinality-estimation-sql-server"></a>Kardinalitätsschätzung (SQL Server)
  Die Logik der kardinalitätsschätzung, ist in überarbeitet [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] zur Verbesserung der Qualität von Abfrageplänen und somit um die abfrageleistung zu verbessern. Die neue Kardinalitätsschätzung umfasst Annahmen und Algorithmen, die sich optimal mit den heutigen OLTP- und Data Warehouse-Arbeitsauslastungen ergänzen. Sie basiert auf intensiven Forschungen zum Verhalten der Kardinalitätsschätzung in heutigen Arbeitsauslastungen sowie auf unseren eigenen Erkenntnissen, die wir in den letzten 15 Jahren bei der Optimierung der SQL Server-Kardinalitätsschätzung gewonnen haben. Das Feedback unserer Kunden zeigt, dass die meisten Abfragen von den Änderungen profitieren oder mindestens mit gleicher Leistung ausgeführt werden. Bei einer geringen Zahl von Abfragen kann jedoch eine Verschlechterung gegenüber der früheren Kardinalitätsschätzung auftreten.  
  
> [!NOTE]  
>  Bei einer Kardinalitätsschätzung wird die Anzahl der Zeilen im Abfrageergebnis vorhergesagt. Der Abfrageoptimierer verwendet diese Schätzungen, um einen Plan für die Abfrageausführung auszuwählen. Die Qualität des Abfrageplans wirkt sich direkt optimierend auf die Abfrageleistung aus.  
  
## <a name="performance-testing-and-tuning-recommendations"></a>Empfehlungen für das Testen und Optimieren der Leistung  
 Die neue Kardinalitätsschätzung kann für alle neuen Datenbanken verwendet werden, die in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] erstellt werden. Allerdings ist es nicht möglich, die neue Kardinalitätsschätzung nach einem Upgrade auf [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] für bestehende Datenbanken zu verwenden.  
  
 Um optimale Abfrageleistung zu gewährleisten, sollten Sie diesen Empfehlungen folgen, um Ihre Arbeitsauslastung mit der neuen Kardinalitätsschätzung zu testen, bevor Sie sie in das produktive System übernehmen.  
  
1.  Führen Sie ein Upgrade für alle bestehenden Datenbanken aus, um die neue Kardinalitätsschätzung zu verwenden. Verwenden Sie zu diesem Zweck [ALTER DATABASE Kompatibilitätsgrad &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) der Datenbank-Kompatibilitätsgrad 120 festgelegt.  
  
2.  Führen Sie die Testarbeitsauslastung mit der neuen Kardinalitätsschätzung aus, und beheben Sie etwaige neu auftretende Leistungsprobleme mithilfe derselben Methoden, die sie üblicherweise bei Leistungsproblemen anwenden.  
  
3.  Nach Ihrer arbeitsauslastung mit der neuen kardinalitätsschätzung (Datenbank-Kompatibilitätsgrad 120 (SQL Server 2014)) ausgeführt wird, und einer bestimmte Abfrage verschlechtert, können Sie die Abfrage ausführen, mit dem Ablaufverfolgungsflag 9481 ausführen, um die Version der kardinalitätsschätzung in verwendetenverwenden[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]und früher. Informationen zum Ausführen einer Abfrage mit einem Ablaufverfolgungsflag finden Sie im KB-Artikel [Aktivieren eines SQL Server-Abfrageoptimiererverhaltens, das Pläne beeinflusst und über verschiedene Ablaufverfolgungsflags auf einer spezifischen Abfrageebene gesteuert werden kann](http://support.microsoft.com/kb/2801413).  
  
4.  Wenn Sie nicht, dass alle Datenbanken sofort auf die neue kardinalitätsschätzung zu verwenden ändern, können Sie die frühere kardinalitätsschätzung für alle Datenbanken verwenden, mithilfe von [ALTER DATABASE Kompatibilitätsgrad &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) an die Datenbank-Kompatibilitätsgrad auf 110 festgelegt.  
  
5.  Wenn die Arbeitsauslastung mit dem Datenbank-Kompatibilitätsgrad 110 ausgeführt wird und Sie eine bestimmte Abfrage mit der neuen Kardinalitätsschätzung testen oder ausführen möchten, können Sie sie mit dem Ablaufverfolgungsflag 2312 ausführen, um die SQL Server 2014-Version der Kardinalitätsschätzung zu verwenden.  Informationen zum Ausführen einer Abfrage mit einem Ablaufverfolgungsflag finden Sie im KB-Artikel [Aktivieren eines SQL Server-Abfrageoptimiererverhaltens, das Pläne beeinflusst und über verschiedene Ablaufverfolgungsflags auf einer spezifischen Abfrageebene gesteuert werden kann](http://support.microsoft.com/kb/2801413).  
  
## <a name="new-xevents"></a>Neue XEvents  
 Es gibt zwei neue query_optimizer_estimate_cardinality-XEvents zur Unterstützung der neuen Abfragepläne.  
  
-   *query_optimizer_estimate_cardinality* wird ausgeführt, wenn der Abfrageoptimierer die Kardinalität für einen relationalen Ausdruck schätzt.  
  
-   *query_optimizer_force_both_cardinality_estimation*_behaviors wird ausgeführt, wenn die beiden Ablaufverfolgungsflags 2312 und 9481 aktiviert sind und versucht wird, sowohl das alte als auch das neue Verhalten der Kardinalitätsschätzung zu erzwingen.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen werden einige Änderungen der neuen Kardinalitätsschätzung veranschaulicht. Der Code für die Kardinalitätsschätzung wurde umgeschrieben. Die Logik ist komplex, sodass nicht alle Änderungen detailliert erläutert werden können.  
  
> [!NOTE]  
>  Diese Beispiele dienen als grundlegende Informationen. Sie müssen nichts ändern und können Ihre Datenbanken und Abfragen wie gewohnt entwickeln.  
  
### <a name="example-a-new-cardinality-estimates-use-an-average-cardinality-for-recently-added-ascending-data"></a>Beispiel A. Die neue Kardinalitätsschätzung gibt für kürzlich hinzugefügte aufsteigende Daten eine durchschnittliche Kardinalität zurück.  
 Dieses Beispiel zeigt, wie die neue Kardinalitätsschätzung dazu beitragen kann, Kardinalitätsschätzungen für aufsteigende Daten zu verbessern, die während des letzten Statistikupdates den Höchstwert der Tabelle überschritten haben.  
  
```  
SELECT item, category, amount FROM dbo.Sales AS s WHERE Date = '2013-12-19';  
```  
  
 In diesem Beispiel werden der Sales-Tabelle jeden Tag neue Zeilen hinzugefügt. Durch die Abfrage werden die Umsätze vom 19.12.2013 abgefragt. Die Statistik wurde zuletzt am 18.12.2013 aktualisiert. Bei der früheren Kardinalitätsschätzung wurde davon ausgegangen, dass keine Werte vom 19.12.2013 vorhanden sind, da das Datum das maximal zulässige Datum überschreitet und die Statistik nicht anhand der Werte vom 19.12.2013 aktualisiert wurde. In dieser Situation sprechen wir von einer aufsteigenden Ordnung, die ein Problem verursacht, wenn im Laufe des Tages Daten geladen und vor der Aktualisierung der Statistik Abfragen ausgeführt werden.  
  
 Dieses Verhalten wurde geändert. Auch wenn die Statistik noch nicht anhand der aktuellen aufsteigenden Daten aktualisiert wurde, die seit dem letzten Statistikupdate hinzugefügt wurden, geht die neue Kardinalitätsschätzung jetzt davon aus, dass die Werte vorhanden sind, und gibt für jeden Spaltenwert die durchschnittliche Kardinalität als Schätzwert zurück.  
  
### <a name="example-b-new-cardinality-estimates-assume-filtered-predicates-on-the-same-table-have-some-correlation"></a>Beispiel B. Bei neuen Kardinalitätsschätzungen wird davon ausgegangen, dass gefilterte Prädikate für dieselbe Tabelle eine gewisse Korrelation aufweisen.  
 Bei diesem Beispiel wird angenommen, dass die Tabelle "Cars" 1.000 Zeilen enthält. Beim Hersteller ("Make") ergeben sich 200 Übereinstimmungen für "Honda" und beim Modell 50 Übereinstimmungen für "Civic". Alle Fahrzeuge des Modells "Civic" sind Fabrikate des Herstellers "Honda". Daher entfallen 20 % der Werte in der Spalte "Make" auf "Honda" und 5 % der Werte in der Spalte "Model" auf "Civic". Das ergibt eine tatsächliche Anzahl von 50 Honda Civics. Bei der früheren Kardinalitätsschätzung wurde angenommen, dass die Werte in den Spalten "Make" und "Model" keinen Bezug zueinander haben. Die vorherigen-Abfrageoptimierer davon ausgeht, es gibt 10 Honda Civics (.05 *.20 \* 1000 Zeilen = 10 Zeilen).  
  
```  
SELECT year, purchase_price FROM dbo.Cars WHERE Make = 'Honda' AND Model = 'Civic';  
```  
  
 Dieses Verhalten wurde geändert. Die neue Kardinalitätsschätzung geht davon aus, dass zwischen den Spalten "Make" und "Model" eine *gewisse* Korrelation besteht. Der Abfrageoptimierer gibt eine höhere Kardinalitätsschätzung zurück, indem er der Schätzungsgleichung eine exponentielle Komponente hinzufügt. Der Abfrageoptimierer schätzt jetzt, dass 22,36 Zeilen (.05 * SQRT(.20) \* 1000 Zeilen = 22,36 Zeilen) mit dem Prädikat übereinstimmen. Bei der spezifischen Datenverteilung in diesem Szenario liegt der Wert von 22,36 Zeilen näher an den tatsächlichen 50 Zeilen, die von der Abfrage zurückgegeben werden.  
  
 Beachten Sie, dass die Prädikatselektivitäten von der Logik der neuen Kardinalitätsschätzung sortiert werden und der Exponent erhöht wird. Z. B. wenn die prädikatselektivitäten.05.20 und.25 wäre, die kardinalitätsschätzung wäre (.05 * SQRT(.20) \* SQRT(SQRT(.25))).  
  
### <a name="example-c-new-cardinality-estimates-assume-filtered-predicates-on-different-tables-are-independent"></a>Beispiel C. Bei der neuen Kardinalitätsschätzung wird davon ausgegangen, dass die gefilterten Prädikate für die verschiedenen Tabellen keinen Bezug zueinander haben.  
 In diesem Beispiel setzt die frühere Kardinalitätsschätzung voraus, dass die Prädikatfilter "s.type" und "r.date" in Wechselbeziehung zueinander stehen. Allerdings belegen Tests mit heutigen Arbeitsauslastungen, dass die Prädikatfilter für Spalten in verschiedenen Tabellen in der Regel nicht korrelieren.  
  
```  
SELECT s.ticket, s.customer, r.store FROM dbo.Sales AS s CROSS JOIN dbo.Returns AS r  
WHERE s.ticket = r.ticket AND s.type = 'toy' AND r.date = '2013-12-19';  
```  
  
 Dieses Verhalten wurde geändert. Die Logik der neuen Kardinalitätsschätzung geht nun davon aus, dass "s.type" nicht mit "r.date" in Wechselbeziehung steht. Praktisch gesehen bedeutet dies, dass "toy" jeden Tag und nicht nur an einem bestimmten Tag zurückgegeben wird. In diesem Fall gibt die neue Kardinalitätsschätzung eine kleinere Zahl zurück als die vorherige Kardinalitätsschätzung.  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Optimieren der Leistung](monitor-and-tune-for-performance.md)  
  
  
