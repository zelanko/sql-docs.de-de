---
title: Bestimmen der korrekten Bucketanzahl für Hash Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6d1ac280-87db-4bd8-ad43-54353647d8b5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b1b79c0908f8639df869d01a8ff862afc5be77cb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754242"
---
# <a name="determining-the-correct-bucket-count-for-hash-indexes"></a>Bestimmen der korrekten Bucketanzahl für Hashindizes
  Beim Erstellen der speicheroptimierten Tabelle müssen Sie einen Wert für den `BUCKET_COUNT`-Parameter angeben. Dieses Thema enthält Empfehlungen zum Bestimmen des geeigneten Werts für den `BUCKET_COUNT`-Parameter. Wenn Sie die richtige Bucketanzahl nicht ermitteln können, verwenden Sie einen nicht gruppierten Index.  Ein ungültiger `BUCKET_COUNT`-Wert kann, insbesondere wenn er zu niedrig ist, die Arbeitsauslastungsleistung sowie die Wiederherstellungszeit der Datenbank erheblich beeinträchtigen. Es ist besser, die Bucketanzahl zu überschätzen.  
  
 Doppelte Indexschlüssel können bei Verwendung eines Hashindexes die Leistung beeinträchtigen, da die Schlüssel demselben Hashbucket hinzugefügt werden, wodurch die Kette dieses Buckets anwächst.  
  
 Weitere Informationen zu nicht gruppierten Hashindizes finden Sie unter [Hash Indexes](hash-indexes.md) und [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Für jeden Hashindex in einer speicheroptimierten Tabelle wird eine Hashtabelle zugeordnet. Die Größe der Hash Tabelle, die für einen Index zugeordnet ist, wird `BUCKET_COUNT` durch den-Parameter in [CREATE TABLE &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-table-transact-sql) oder [Create Type &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-type-transact-sql)angegeben. Die Bucketanzahl wird intern bis zur nächsten Zweierpotenz aufgerundet. Wenn als Bucketanzahl beispielsweise 300.000 angegeben wird, führt dies zu einer tatsächlichen Bucketanzahl von 524.288.  
  
 Links zu einem Artikel und Videos zur Bucketanzahl finden Sie unter [Bestimmen der richtigen Bucketanzahl für Hashindizes (In-Memory OLTP)](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/).  
  
## <a name="recommendations"></a>Empfehlungen  
 In den meisten Fällen sollte die Bucketanzahl das Ein- bis Zweifache der Anzahl von unterschiedlichen Werten im Indexschlüssel betragen. Wenn der Indexschlüssel zahlreiche doppelte Werte enthält und durchschnittlich über 10 Zeilen für jeden Indexschlüsselwert vorhanden sind, verwenden Sie einen nicht gruppierten Index.  
  
 Möglicherweise können Sie nicht immer prognostizieren, wie viele Werte ein bestimmter Indexschlüssel enthalten kann oder wird. Die Leistung sollte akzeptabel sein, wenn der `BUCKET_COUNT`-Wert bis zum Fünffachen der tatsächlichen Anzahl von Schlüsselwerten beträgt.  
  
 Verwenden Sie zum Ermitteln der Anzahl von eindeutigen Indexschlüsseln in vorhandenen Daten Abfragen wie in den folgenden Beispielen:  
  
### <a name="primary-key-and-unique-indexes"></a>Primärschlüssel und eindeutige Indizes  
 Da der Primärschlüsselindex eindeutig ist, entspricht die Anzahl unterschiedlicher Werte im Schlüssel der Anzahl der Zeilen in der Tabelle. Geben Sie für einen Beispielprimärschlüssel für (SalesOrderID, SalesOrderDetailID) in der Tabelle "Sales.SalesOrderDetail" in der AdventureWorks-Datenbank die folgende Abfrage aus, um die Anzahl der unterschiedlichen Primärschlüsselwerte zu berechnen. Diese entspricht der Anzahl der Zeilen in der Tabelle.  
  
```sql  
SELECT COUNT(*) AS [row count]   
FROM Sales.SalesOrderDetail  
```  
  
 Diese Abfrage enthält eine Zeilenanzahl von 121.317. Verwenden Sie eine Bucketanzahl von 240.000, wenn sich die Zeilenanzahl nicht signifikant ändert. Verwenden Sie eine Bucketanzahl von 480.000, wenn Sie erwarten, dass sich die Anzahl der Bestellungen vervierfachen wird.  
  
### <a name="non-unique-indexes"></a>Nicht eindeutige Indizes  
 Für andere Indizes, z. B. einen mehrspaltigen Index für (SpecialOfferID, ProductID), geben Sie die folgende Abfrage aus, um die Anzahl von eindeutigen Indexschlüsselwerten zu bestimmen:  
  
```sql  
SELECT COUNT(*) AS [SpecialOfferID_ProductID index key count]  
FROM   
   (SELECT DISTINCT SpecialOfferID, ProductID   
    FROM Sales.SalesOrderDetail) t  
```  
  
 Diese Abfrage gibt für (SpecialOfferID, ProductID) die Indexschlüsselanzahl 484 zurück, was darauf hindeutet, dass ein nicht gruppierter Index anstelle eines nicht gruppierten Hashindexes verwendet werden sollte.  
  
### <a name="determining-the-number-of-duplicates"></a>Bestimmen der Anzahl von Duplikaten  
 Teilen Sie zum Bestimmen der durchschnittlichen Anzahl doppelter Werte für einen Indexschlüsselwert die Gesamtzeilenanzahl durch die Anzahl der eindeutigen Indexschlüssel.  
  
 Beim Beispielindex für (SpecialOfferID, ProductID) ist dies 121317/484 = 251. Dies bedeutet, dass der Durchschnitt von Indexschlüsselwerten 251 beträgt und es sich daher hier um einen nicht gruppierten Index handeln sollte.  
  
## <a name="troubleshooting-the-bucket-count"></a>Problembehandlung für die Bucketanzahl  
 Um Probleme mit der Bucketanzahl in Speicher optimierten Tabellen zu beheben, verwenden Sie [sys. dm_db_xtp_hash_index_stats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql) , um Statistiken über die leeren Bucket und die Länge der Zeilen Ketten abzurufen. Mit der folgenden Abfrage können Statistiken zu allen Hashindizes in der aktuellen Datenbank abgerufen werden. Die Abfrage kann einige Zeit in Anspruch nehmen, wenn die Datenbank große Tabellen enthält.  
  
```sql  
SELECT   
   object_name(hs.object_id) AS 'object name',   
   i.name as 'index name',   
   hs.total_bucket_count,  
   hs.empty_bucket_count,  
   floor((cast(empty_bucket_count as float)/total_bucket_count) * 100) AS 'empty_bucket_percent',  
   hs.avg_chain_length,   
   hs.max_chain_length  
FROM sys.dm_db_xtp_hash_index_stats AS hs   
   JOIN sys.indexes AS i   
   ON hs.object_id=i.object_id AND hs.index_id=i.index_id  
```  
  
 Zwei wichtige Indikatoren für den Zustand von Hashindizes lauten wie folgt:  
  
 *empty_bucket_percent*  
 *empty_bucket_percent* gibt die Anzahl der leeren Bucket im Hashindex an.  
  
 Wenn *empty_bucket_percent* kleiner als 10 Prozent ist, ist die Bucketanzahl wahrscheinlich zu niedrig. Im Idealfall sollte *empty_bucket_percent* mindestens 33 Prozent betragen. Wenn die Bucketanzahl der Anzahl der Indexschlüsselwerte entspricht, ist ca. 1/3 der Buckets aufgrund der Hashverteilung leer.  
  
 *avg_chain_length*  
 *avg_chain_length* die die durchschnittliche Länge der Zeilen Ketten in den hashbuchern angibt.  
  
 Wenn *avg_chain_length* größer als 10 und *empty_bucket_percent* größer als 10 Prozent ist, sind wahrscheinlich zahlreiche doppelte Indexschlüsselwerte vorhanden, und ein nicht gruppierter Index wäre besser geeignet. Eine durchschnittliche Kettenlänge von 1 ist ideal.  
  
 Zwei Faktoren haben Auswirkungen auf die Kettenlänge:  
  
1.  Duplikate: Alle doppelten Zeilen sind Teil derselben Kette im Hashindex.  
  
2.  Mehrere Schlüsselwerte wurden dem gleichen Bucket zugeordnet. Je niedriger die Bucketanzahl, desto mehr Buckets sind mehrere Werte zugeordnet.  
  
 Betrachten Sie als Beispiel die folgende Tabelle und das Skript zum Einfügen von Beispielzeilen in der Tabelle:  
  
```sql  
CREATE TABLE [Sales].[SalesOrderHeader_test]  
(  
   [SalesOrderID] [uniqueidentifier] NOT NULL DEFAULT (newid()),  
   [OrderSequence] int NOT NULL,  
   [OrderDate] [datetime2](7) NOT NULL,  
   [Status] [tinyint] NOT NULL,  
  
PRIMARY KEY NONCLUSTERED HASH ([SalesOrderID]) WITH ( BUCKET_COUNT = 262144 ),  
INDEX IX_OrderSequence HASH (OrderSequence) WITH ( BUCKET_COUNT = 20000),  
INDEX IX_Status HASH ([Status]) WITH ( BUCKET_COUNT = 8),  
INDEX IX_OrderDate NONCLUSTERED ([OrderDate] ASC),  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
DECLARE @i int = 0  
BEGIN TRAN  
WHILE @i < 262144  
BEGIN  
   INSERT Sales.SalesOrderHeader_test (OrderSequence, OrderDate, [Status]) VALUES (@i, sysdatetime(), @i % 8)  
   SET @i += 1  
END  
COMMIT  
GO  
```  
  
 Mit dem Skript werden 262.144 Zeilen in der Tabelle eingefügt. Das Skript fügt eindeutige Werte im Primärschlüsselindex und in "IX_OrderSequence" ein. Es werden zahlreiche doppelte Werte im Index "IX_Status" eingefügt. Das Skript generiert nur 8 unterschiedliche Werte.  
  
 Die Ausgabe der BUCKET_COUNT-Abfrage zur Problembehandlung lautet wie folgt:  
  
|Indexname|total_bucket_count|empty_bucket_count|empty_bucket_percent|avg_chain_length|max_chain_length|  
|----------------|--------------------------|--------------------------|----------------------------|------------------------|------------------------|  
|IX_Status|8|4|50|65536|65536|  
|IX_OrderSequence|32.768|13|0|8|26|  
|PK_SalesOrd_B14003C3F8FB3364|262.144|96319|36|1|8|  
  
 Betrachten Sie die drei Hashindizes für diese Tabelle:  
  
-   IX_Status: 50 Prozent der Buckets sind leer, das ist positiv. Die durchschnittliche Kettenlänge ist jedoch sehr hoch (65.536). Dies weist auf eine große Anzahl doppelter Werte hin. Die Verwendung eines nicht gruppierten Hashindexes ist in diesem Fall daher nicht sinnvoll. Stattdessen sollte ein nicht gruppierter Index verwendet werden.  
  
-   IX_OrderSequence: 0 Prozent der Buckets sind leer. Dieser Wert ist zu niedrig. Darüber hinaus beträgt die durchschnittliche Kettenlänge 8. Da die Werte in diesem Index eindeutig sind, bedeutet dies, dass durchschnittlich jedem Bucket 8 Werte zugeordnet sind. Die Bucketanzahl sollte erhöht werden. Da der Indexschlüssel 262.144 eindeutige Werte enthält, sollte die Bucketanzahl mindestens 262.144 betragen. Wenn zukünftiges Wachstum erwartet wird, sollte die Zahl größer sein.  
  
-   Primärschlüssel Index (PK__SalesOrder...): 36 Prozent der Eimer sind leer, was gut ist. Außerdem beträgt die durchschnittliche Kettenlänge 1, was ebenfalls positiv ist. Es ist keine Änderung erforderlich.  
  
 Weitere Informationen zur Fehlerbehebung bei speicheroptimierten Hashindizes finden Sie unter [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md).  
  
## <a name="detailed-considerations-for-further-optimization"></a>Ausführliche Überlegungen für die weitere Optimierung  
 Dieser Abschnitt enthält zusätzliche Überlegungen zum Optimieren der Bucketanzahl.  
  
 Um die optimale Leistung von Hashindizes zu gewährleisten, müssen Sie ein Gleichgewicht zwischen dem Speicherplatz, der der Hashtabelle im Arbeitsspeicher zugeordnet ist, und der Anzahl der unterschiedlichen Werte im Indexschlüssel finden. Zudem besteht ein Zusammenhang zwischen der Leistung von Punktsuchen und Tabellenscans:  
  
-   Je höher der Wert für die Bucketanzahl ist, desto mehr leere Buckets sind im Index enthalten. Dies hat Auswirkungen auf die Speicherauslastung (8 Bytes pro Bucket) und die Leistung von Tabellenscans, da jeder Bucket als Teil eines Tabellenscans überprüft wird.  
  
-   Je niedriger die Bucketanzahl, desto mehr Werte sind einem einzelnen Bucket zugewiesen. Dadurch wird die Leistung für Punktsuchen und Einfügungen verringert, da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] möglicherweise mehrere Werte in einem einzelnen Bucket durchlaufen muss, um den durch das Suchprädikat angegebenen Wert zu finden.  
  
 Wenn die Bucketanzahl deutlich niedriger als die Anzahl der eindeutigen Indexschlüssel ist, werden jedem Bucket zahlreiche Werte zugeordnet. Dadurch wird die Leistung der meisten DML-Vorgänge beeinträchtigt, insbesondere von Punktsuchen (Suchen nach einzelnen Indexschlüsseln) und Einfügevorgängen. Beispielsweise lässt sich eine Leistungsminderung bei SELECT-Abfragen sowie UPDATE- und DELETE-Vorgängen mit Gleichheitsprädikaten feststellen, durch die die Indexschlüsselspalten in der WHERE-Klausel verglichen werden. Eine niedrige Bucketanzahl hat außerdem Auswirkungen auf die Dauer der Datenbankwiederherstellung, da die Indizes beim Datenbankstart neu erstellt werden.  
  
### <a name="duplicate-index-key-values"></a>Doppelte Indexschlüsselwerte  
 Doppelte Werte können die Auswirkungen auf die Leistung durch Hashkonflikte verstärken. Dies stellt normalerweise kein Problem dar, wenn jeder Indexschlüssel eine geringe Anzahl von Duplikaten aufweist. Es kann jedoch problematisch werden, wenn die Diskrepanz zwischen der Anzahl eindeutiger Indexschlüssel und der Anzahl der Tabellenzeilen erheblich zunimmt.  
  
 Alle Zeilen mit dem gleichen Indexschlüssel werden der gleichen Duplikatkette zugewiesen. Wenn ein Bucket aufgrund eines Hashkonflikts mehrere Indexschlüssel enthält, müssen Indexscanner immer die vollständige Duplikatkette nach dem ersten Wert durchsuchen, bevor die erste Zeile gesucht werden kann, die dem zweiten Wert entspricht. Doppelte Schlüssel erschweren der Garbage Collection zusätzlich die Suche nach der entsprechenden Zeile. Beispiel: Wenn für einen Schlüssel 1.000 Duplikate vorhanden sind und eine der Zeilen gelöscht wird, muss der Garbage Collector die gesamte Kette von 1.000 Duplikaten überprüfen, um die Verknüpfung der Zeile mit dem Index aufzuheben. Dies gilt selbst dann, wenn die Abfrage, durch die die gelöschte Zeile gefunden wurde, einen effizienteren Index (Primärschlüsselindex) zum Suchen der Zeile verwendet hat, weil der Garbage Collector die Verknüpfung mit jedem Index aufheben muss.  
  
 Bei Hashindizes gibt es zwei Möglichkeiten, den durch doppelte Indexschlüsselwerte verursachten Aufwand zu reduzieren:  
  
-   Verwenden Sie stattdessen einen nicht gruppierten Index. Sie können die Duplikate verringern, indem Sie dem Indexschlüssel Spalten hinzufügen, ohne dass Änderungen an der Anwendung erforderlich sind.  
  
-   Geben Sie eine sehr hohe Bucketanzahl für den Index an. Beispielsweise das 20- bis 100-fache der Anzahl der eindeutigen Indexschlüssel. Dadurch werden Hashkonflikte verringert.  
  
### <a name="small-tables"></a>Kleine Tabellen  
 Bei kleineren Tabellen ist die Arbeitsspeicherauslastung normalerweise kein Problem, da die Indexgröße im Vergleich zur Gesamtgröße der Datenbank gering ist.  
  
 Sie müssen nun auf Grundlage der gewünschten Leistung eine Auswahl treffen:  
  
-   Wenn es sich bei den leistungskritischen Vorgängen für den Index vorwiegend um Punktsuchen und/oder Einfügevorgänge handelt, ist eine höhere Bucketanzahl sinnvoll, um die Wahrscheinlichkeit von Hashkonflikten zu reduzieren. Das Dreifache der Zeilenanzahl oder sogar ein höherer Wert ist hier die beste Option.  
  
-   Wenn es sich bei den wichtigsten leistungskritischen Vorgängen um vollständige Indexscans handelt, verwenden Sie eine Bucketanzahl, die nah an der tatsächlichen Anzahl von Indexschlüsselwerten liegt.  
  
### <a name="big-tables"></a>Große Tabellen  
 Bei großen Tabellen kann die Arbeitsspeicherauslastung zu einem Problem werden. Bei einer 250 Millionen-Zeilen Tabelle mit vier Hash Indizes, die jeweils über eine Bucketanzahl von 1 Milliarde verfügen, beträgt der Aufwand für die Hash Tabellen beispielsweise 4 Indizes * \* 1 Milliarde Bucket 8 Bytes = 32 Gigabyte Arbeitsspeicher Auslastung. Wenn eine Bucketanzahl von 250 Millionen für jeden der Indizes ausgewählt wird, beträgt die benötigte Leistung für die Hashtabellen 8 GB. Beachten Sie, dass dies zusätzlich zu den 8 Bytes der Speicherauslastung liegt, die jeder Index jeder einzelnen Zeile hinzufügt, d. h. 8 Gigabyte in diesem Szenario \* (4 \* Indizes 8 Bytes 250 Millionen Zeilen).  
  
 Vollständige Tabellenscans befinden sich normalerweise nicht im leistungskritischen Pfad für OLTP-Arbeitsauslastungen. Daher muss eine Wahl zwischen Arbeitsspeicherauslastung und Leistung von Punktsuchen und Einfügevorgängen getroffen werden:  
  
-   Wenn die Arbeitsspeicherauslastung wichtig ist, wählen Sie eine Bucketanzahl aus, die nahe an der Anzahl der Indexschlüsselwerte liegt. Die Bucketanzahl sollte nicht deutlich niedriger sein als die Anzahl der Indexschlüsselwerte, da dies Auswirkungen auf die meisten DML-Vorgänge sowie die Zeit hat, die zum Wiederherstellen der Datenbank nach einem Neustart des Servers benötigt wird.  
  
-   Beim Optimieren der Leistung für Punktsuchen ist eine höhere Bucketanzahl (das Zwei- oder Dreifache der Anzahl von eindeutigen Indexwerten) angemessen. Eine höhere Bucketanzahl würde eine erhöhte Speicherauslastung bedeuten und die benötigte Zeit für einen vollständigen Indexscan verlängern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Indizes für speicheroptimierte Tabellen](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
