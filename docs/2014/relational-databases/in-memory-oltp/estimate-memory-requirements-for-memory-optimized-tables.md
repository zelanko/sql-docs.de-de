---
title: Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: b0d22fd13abf68cd9eea1c21b135427161fbf8be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151368"
---
# <a name="estimate-memory-requirements-for-memory-optimized-tables"></a>Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen
  Unabhängig davon, ob Sie eine neue speicheroptimierte [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Tabelle erstellen oder eine vorhandene datenträgerbasierte Tabelle migrieren, ist es wichtig, den Arbeitsspeicherbedarf der einzelnen Tabellen realistisch einzuschätzen, damit Sie ausreichenden Arbeitsspeicher für den Server bereitstellen können. In diesem Abschnitt wird beschrieben, wie die Speichermenge geschätzt wird, die für die Daten einer speicheroptimierten Tabelle benötigt wird.  
  
 Wenn Sie die Migration von datenträgerbasierten zu speicheroptimierten Tabellen in Erwägung ziehen, finden Sie im Thema [Bestimmen, ob eine Tabelle oder eine gespeicherte Prozedur zu In-Memory OLTP portiert werden soll](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) Informationen dazu, welche Tabellen sich am besten migrieren lassen. Anschließend können Sie mit diesem Thema fortfahren. Alle Themen unter [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md) bieten eine Anleitung zum Migrieren von datenträgerbasierten zu speicheroptimierten Tabellen.  
  
## <a name="sections-in-this-topic"></a>Abschnitte in diesem Thema  
  
-   [Beispiel für eine speicheroptimierte Tabelle](#bkmk_ExampleTable)  
  
-   [Arbeitsspeicher für die Tabelle](#bkmk_MemoryForTable)  
  
-   [Arbeitsspeicher für Indizes](#bkmk_IndexMeemory)  
  
-   [Arbeitsspeicher für die Zeilenversionsverwaltung](#bkmk_MemoryForRowVersions)  
  
-   [Arbeitsspeicher für Tabellenvariablen](#bkmk_TableVariables)  
  
-   [Arbeitsspeicher für zukünftiges Wachstum](#bkmk_MemoryForGrowth)  
  
##  <a name="bkmk_ExampleTable"></a> Beispiel für eine speicheroptimierte Tabelle  
 Betrachten Sie das folgende speicheroptimierte Tabellenschema:  
  
```tsql  
  
CREATE TABLE t_hk (  
col1 int NOT NULL PRIMARY KEY NONCLUSTERED,  
col2 int NOT NULL INDEX t1c2_index   
     HASH WITH (bucket_count = 5000000),  
col3 int NOT NULL INDEX t1c3_index   
     HASH WITH (bucket_count = 5000000),  
col4 int NOT NULL INDEX t1c4_index   
     HASH WITH (bucket_count = 5000000),  
col5 int NOT NULL INDEX t1c5_index NONCLUSTERED,  
col6 char (50) NOT NULL,  
col7 char (50) NOT NULL,   
col8 char (30) NOT NULL,   
col9 char (50) NOT NULL  
     WITH (memory_optimized = on)  
GO  
  
```  
  
 Mithilfe dieses Schemas wird der minimale Arbeitsspeicherbedarf dieser speicheroptimierten Tabelle bestimmt.  
  
##  <a name="bkmk_MemoryForTable"></a> Arbeitsspeicher für die Tabelle  
 Eine Zeile einer speicheroptimierten Tabelle umfasst drei Teile:  
  
-   **Zeitstempel**   
    Zeilenkopf/Zeitstempel = 24 Bytes.  
  
-   **Indexzeiger**   
    Für jeden Hashindex in der Tabelle weist jede Zeile einen 8-Byte-Adresszeiger auf die nächste Zeile im Index auf.  Da es vier Indizes gibt, belegt jede Zeile 32 Bytes für Indexzeiger (einen 8-Byte-Zeiger für jeden Index).  
  
-   **Daten**   
    Die Größe des Datenanteils der Zeile wird bestimmt, indem die Typgröße für jede Datenspalte summiert wird.  Die Tabelle enthält fünf ganze 4-Byte-Zahlen, drei 50-Byte-Zeichenspalten und eine 30-Byte-Zeichenspalte.  Daher beträgt der Datenanteil jeder Zeile 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 oder 200 Bytes.  
  
 Im Folgenden eine Größenberechnung für 5.000.000 (5 Millionen) Zeilen in einer speicheroptimierten Tabelle. Der von den Datenzeilen belegte Gesamtspeicher wird wie folgt geschätzt:  
  
 **Arbeitsspeicher für die Tabellenzeilen**  
  
 Aus den vorherigen Berechnungen ergibt sich für jede Zeile in der speicheroptimierten Tabelle eine Größe von 24 + 32 + 200 oder 256 Bytes.  Da sie 5 Million Zeilen enthält, belegt die Tabelle 5.000.000 * 256 Bytes oder 1.280.000.000 Bytes, also ungefähr 1,28 GB.  
  
##  <a name="bkmk_IndexMeemory"></a> Arbeitsspeicher für Indizes  
 **Arbeitsspeicher für jeden Hashindex**  
  
 Jeder Hashindex ist ein Hasharray aus 8-Byte-Adresszeigern.  Die Größe des Arrays wird am besten anhand der Anzahl eindeutiger Indexwerte für diesen Index bestimmt. Beispielsweise ist die Anzahl eindeutiger Col2-Werte ein guter Ausgangspunkt für die Arraygröße von "t1c2_index". Durch ein übergroßes Hasharray wird Arbeitsspeicher vergeudet.  Ein zu kleines Hasharray verlangsamt die Leistung, da zu viele Konflikte durch Indexwerte entstehen, die demselben Hashindex zugeordnet sind.  
  
 Mit Hashindizes erzielen Sie sehr schnelle Übereinstimmungssuchen wie:  
  
```tsql  
  
SELECT * FROM t_hk  
   WHERE Col2 = 3  
  
```  
  
 Nicht gruppierte Indizes liefern schneller Ergebnisse bei Bereichssuchen wie:  
  
```tsql  
  
SELECT * FROM t_hk  
   WHERE Col2 >= 3  
  
```  
  
 Beim Migrieren einer datenträgerbasierten Tabelle können Sie die Anzahl der eindeutigen Werte für den Index "t1c2_index" wie folgt bestimmen.  
  
```tsql  
  
SELECT COUNT(DISTINCT [Col2])  
  FROM t_hk  
  
```  
  
 Wenn Sie eine neue Tabelle erstellen, müssen Sie vor der Bereitstellung die Arraygröße schätzen oder mithilfe von Tests ermitteln.  
  
 Informationen zur Funktionsweise von Hashindizes in speicheroptimierten [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Tabellen finden Sie unter [Hashindizes](../../database-engine/hash-indexes.md).  
  
 **Hinweis:** können die Arraygröße des Hash-Index bei laufendem Betrieb nicht ändern. Um die Arraygröße des Hashindexes zu ändern, müssen Sie die Tabelle löschen, den bucket_count-Wert ändern und die Tabelle erneut erstellen.  
  
 **Festlegen der Arraygröße der Hash-index**  
  
 Die hasharraygröße wird festgelegt, indem `(bucket_count= <value>)` , in dem \<Wert > ist ein ganzzahliger Wert größer als 0 (null). Wenn \<Wert > ist keine Potenz von 2, der tatsächliche bucket_count-Wert wird aufgerundet auf die nächste nächste Potenz von 2.  In der Beispieltabelle (Bucket_count = 5000000), weil 5.000.000 keine Potenz von 2 ist, die tatsächliche Bucketanzahl auf 8.388.608 (2<sup>23</sup>).  Wenn Sie den vom Hasharray benötigten Arbeitsspeicher berechnen, müssen Sie diesen Wert und nicht 5.000.000 verwenden.  
  
 Daher beträgt der für jedes Hasharray erforderliche Arbeitsspeicher im Beispiel:  
  
 8.388.608 * 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67.108.864 oder ungefähr 64 MB.  
  
 Da wir über drei Hashindizes verfügen, ist der für die Hashindizes erforderliche Arbeitsspeicher 3 * 64 MB = 192 MB.  
  
 **Arbeitsspeicher für nicht gruppierte Indizes**  
  
 Nicht gruppierte Indizes werden als BTrees implementiert, deren innere Knoten den Indexwert und Zeiger auf nachfolgende Knoten enthalten.  Blattknoten enthalten den Indexwert und einen Zeiger auf die Tabellenzeile im Arbeitsspeicher.  
  
 Nicht gruppierte Indizes verfügen im Gegensatz Hashindizes nicht über eine feste Bucketgröße. Der Index vergrößert bzw. verkleinert sich dynamisch mit den Daten.  
  
 Der von nicht gruppierten Indizes belegte Arbeitsspeicher kann wie folgt berechnet werden:  
  
-   **Arbeitsspeicher, der Nichtblattknoten zugeordnet ist**   
    Bei einer typischen Konfiguration hat der Arbeitsspeicher, der Nichtblattknotenden zugeordnet wird, einen geringen prozentualen Anteil am gesamten vom Index belegten Arbeitsspeicher, der so klein ist, dass er problemlos ignoriert werden kann.  
  
-   **Arbeitsspeicher für Blattknoten**   
    Die Blattknoten weisen eine Zeile für jeden eindeutigen Schlüssel in der Tabelle auf, die auf die Datenzeilen mit dem eindeutigen Schlüssel verweist.  Wenn Sie über mehrere Zeilen mit demselben Schlüssel (also über einen nicht eindeutigen nicht gruppierten Index) verfügen, enthält der Indexblattknoten nur eine Zeile, die auf eine der Zeilen verweist, während die anderen Zeilen miteinander verknüpft sind.  Folglich kann für den insgesamt erforderlichen Arbeitsspeicher wie folgt ein Näherungswert ermittelt werden:   
    memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) * rowsWithUniqueKeys  
  
 Nicht gruppierte Indizes eignen sich am besten für Bereichssuchen, wie in der folgenden Abfrage veranschaulicht:  
  
```tsql  
  
SELECT * FROM t_hk  
   WHERE c2 > 5  
```  
  
##  <a name="bkmk_MemoryForRowVersions"></a> Arbeitsspeicher für die Zeilenversionsverwaltung  
 Um Sperren zu vermeiden, nutzt In-Memory OLTP beim Aktualisieren oder Löschen von Zeilen optimistische Nebenläufigkeit. Dies bedeutet, dass bei jedem Zeilenupdate eine zusätzliche Version der Zeile erstellt wird. Die vorherigen Versionen bleiben im System verfügbar, bis alle Transaktionen, von denen die Version möglicherweise verwendet werden könnte, abgeschlossen sind. Wenn eine Zeile gelöscht wird, verhält sich das System auf ähnliche Weise wie bei einem Update und behält die Version bei, bis sie nicht mehr erforderlich ist. Durch Lese- und Einfügevorgänge werden keine zusätzlichen Zeilenversionen erstellt.  
  
 Da der Arbeitsspeicher jederzeit einige zusätzliche Zeilen enthalten kann, während darauf gewartet wird, dass der von den Zeilen belegte Speicher im nächsten Zyklus der Garbage Collection freigegeben wird, benötigen Sie genügend Arbeitsspeicher für diese zusätzlichen Zeilen.  
  
 Die Anzahl der zusätzlichen Zeilen kann geschätzt werden, indem Sie die Höchstanzahl von Zeilenupdates und -löschungen pro Sekunde berechnen und den Wert mit der Anzahl von Sekunden multiplizieren, die die längste Transaktion dauert (mindestens eine Sekunde).  
  
 Anschließend wird dieser Wert mit der Zeilengröße multipliziert, um die Anzahl der Bytes zu erhalten, die für die Zeilenversionsverwaltung benötigt werden.  
  
 `rowVersions = durationOfLongestTransactionInSeconds * peakNumberOfRowUpdatesOrDeletesPerSecond`  
  
 Wird durch die Anzahl veralteter Zeilen mit der Größe einer Zeile einer speicheroptimierten Tabelle multipliziert Arbeitsspeicherbedarf für veraltete Zeilen geschätzt (finden Sie unter [Arbeitsspeicher für die Tabelle](#bkmk_MemoryForTable) oben).  
  
 `memoryForRowVersions = rowVersions * rowSize`  
  
##  <a name="bkmk_TableVariables"></a> Arbeitsspeicher für Tabellenvariablen  
 Der für eine Tabellenvariable verwendete Arbeitsspeicher wird erst freigegeben, wenn die Tabellenvariable den Gültigkeitsbereich verlässt. Gelöschte Zeilen, einschließlich der während eines Updates gelöschten Zeilen, aus einer Tabellenvariablen unterliegen nicht der Garbage Collection. Es wird erst Arbeitsspeicher freigegeben, wenn die Tabellenvariable den Bereich verlässt.  
  
 Tabellenvariablen, die in einem umfangreichen SQL-Batch und nicht in einem Prozedurbereich definiert und in zahlreichen Transaktionen verwendet werden, können viel Arbeitsspeicher beanspruchen. Da sie nicht von der Garbage Collection bereinigt werden, können gelöschte Zeilen in einer Tabellenvariablen viel Arbeitsspeicher beanspruchen und die Leistung beeinträchtigen, da Lesevorgänge auch die gelöschten Zeilen durchlaufen müssen.  
  
##  <a name="bkmk_MemoryForGrowth"></a> Arbeitsspeicher für zukünftiges Wachstum  
 Mit den oben aufgeführten Berechnungen wird der Arbeitsspeicherbedarf für die derzeit bestehende Tabelle geschätzt. Zusätzlich zu diesem Arbeitsspeicher müssen Sie einplanen, dass die Tabelle anwächst, und ausreichend Arbeitsspeicher für zukünftiges Wachstum vorsehen.  Wenn Sie beispielsweise ein zehnprozentiges Wachstum erwarten, müssen Sie die oben ermittelten Ergebnisse mit 1,1 multiplizieren, um den insgesamt erforderlichen Arbeitsspeicher für die Tabelle zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  