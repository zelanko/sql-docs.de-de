---
title: Beschriebene columnstore-Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 80a29b8e8cc5b53c09369156a5cf5f717e9447a0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050027"
---
# <a name="columnstore-indexes-described"></a>Columnstore Indexes Described
  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *in-Memory-columnstore--Index* speichert und verwaltet Daten mithilfe von Spalten basiertem Datenspeicher und Spalten basierter Abfrage Verarbeitung. Columnstore-Indizes sind optimal für Data Warehousing-Arbeitsauslastungen geeignet, die hauptsächlich Massenladevorgänge und schreibgeschützte Abfragen ausführen. Verwenden Sie den Columnstore-Index, um eine bis zu **zehnfache Abfrageleistung** gegenüber der herkömmlichen zeilenorientierten Speicherung und eine bis zu **siebenfache Datenkomprimierung** im Vergleich zur unkomprimierten Datengröße zu erzielen.

> [!NOTE]
>  Wir sehen den gruppierten Columnstore-Index als Standard für das Speichern von großen Data Warehousing-Faktentabellen an und erwarten, dass er in den meisten Data Warehousing-Szenarien verwendet wird. Da der gruppierte Columnstore-Index aktualisierbar ist, kann die Arbeitsauslastung eine große Anzahl von Einfüge-, Update- und Löschvorgängen ausführen.

## <a name="contents"></a>Inhalte

-   [Grundlagen](#basics)

-   [Laden von Daten](#dataload)

-   [Tipps zur Leistungssteigerung](#performance)

-   [Verwandte Aufgaben und Themen](#related)

##  <a name="basics"></a><a name="basics"></a>Kenntnisse
 Ein *columnstore index* ist eine Technologie zum Speichern, Abrufen und Verwalten von Daten mithilfe eines spaltenbasierten Datenformats, das als Columnstore bezeichnet wird. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt gruppierte und nicht gruppierte Columnstore-Indizes. Beide verwenden die gleiche In-Memory-Columnstore-Technologie, sie unterscheiden sich jedoch hinsichtlich ihres Verwendungszwecks und Funktionsumfangs.

###  <a name="benefits"></a><a name="benefits"></a> Vorteile
 Columnstore-Indizes sind für die meisten schreibgeschützten Abfragen geeignet, die Analysen für große Datasets ausführen. Dabei handelt es sich häufig um Abfragen für Data Warehousing-Arbeitsauslastungen. Columnstore-Indizes bieten bei Abfragen, die vollständige Tabellenscans verwenden, große Leistungsvorteile und sind nicht für Abfragen geeignet, die Suchvorgänge in Daten ausführen, um einen bestimmten Wert suchen.

 Vorteile von Columnstore-Indizes:

-   Spalten weisen häufig ähnliche Daten auf, wodurch eine hohe Komprimierungsraten erzielt wird.

-   Hohe Komprimierungsraten verbessern die Abfrageleistung, da der Arbeitsspeicherbedarf geringer ist. Auch die Abfrageleistung kann verbessert werden, da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine größere Zahl von speicherinternen Abfrage- und Datenvorgängen ausführen kann.

-   SQL Server besitzt jetzt einen neuen Abfrageausführungsmechanismus, der als Batchmodusausführung bezeichnet wird und durch den die CPU-Nutzung beträchtlich reduziert wird. Die Batchmodusausführung ist eng in das Columnstore-Speicherformat integriert und für dieses optimiert. Die Batchmodusausführung wird auch als vektorbasierte oder vektorisierte Ausführung bezeichnet.

-   Bei Abfragen werden häufig nur wenige Spalten aus einer Tabelle ausgewählt, wodurch das Gesamtaufkommen der E/A-Vorgänge für das physische Medium reduziert wird.

### <a name="columnstore-versions"></a>Columnstore-Versionen
 SQL Server 2012, SQL Server 2012 Parallel Data Warehouse und SQL Server 2014 verwenden Columnstore-Indizes, um häufig verwendete Data Warehouse-Abfragen zu beschleunigen. SQL Server 2012 weist zwei neue Funktionen auf: einen nicht gruppierten Columnstore-Index und eine vektorbasierte Abfrageausführungsfunktion, die Daten in Einheiten verarbeitet, die als "Batches" bezeichnet werden. SQL Server 2014 besitzt die Funktionen von SQL Server 2012 sowie aktualisierbare gruppierte Columnstore-Indizes.

### <a name="key-characteristics"></a>Hauptmerkmale

||
|-|
|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|

 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]weist ein gruppierter Columnstore-Index folgende Merkmale auf:

-   Er ist in Enterprise-, Developer- und Evaluation-Editionen verfügbar.

-   Er kann aktualisiert werden.

-   Er stellt die Hauptspeichermethode für die gesamte Tabelle dar.

-   Er besitzt keine Schlüsselspalten. Alle Spalten sind eingeschlossene Spalten.

-   Er stellt den einzigen Index für die Tabelle dar. Er kann nicht mit anderen Indizes kombiniert werden.

-   Er kann für die Verwendung von Columnstore- oder Columnstore-Archivierungskomprimierung konfiguriert werden.

-   Spalten werden nicht physisch in einer sortierten Reihenfolge gespeichert. Stattdessen werden Daten so gespeichert, dass Komprimierung und Leistung verbessert werden.

||
|-|
|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].|

 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]weist ein nicht gruppierter Columnstore-Index folgende Merkmale auf:

-   Er kann einen Index einer Teilmenge von Spalten im gruppierten Index oder Heap erstellen. Beispielsweise kann ein Index der häufig verwendeten Spalten erstellt werden.

-   Er benötigt zusätzlichen Speicherplatz, um eine Kopie der Spalten im Index zu speichern.

-   Wird aktualisiert, indem der Index neu erstellt oder Partitionen ein-und ausgeschaltet wird. Sie kann nicht mit DML-Vorgängen wie INSERT, Update und DELETE aktualisiert werden.

-   Er kann mit anderen Indizes der Tabelle kombiniert werden.

-   Er kann für die Verwendung von Columnstore- oder Columnstore-Archivierungskomprimierung konfiguriert werden.

-   Spalten werden nicht physisch in einer sortierten Reihenfolge gespeichert. Stattdessen werden Daten so gespeichert, dass Komprimierung und Leistung verbessert werden. Eine Vorsortierung der Daten vor der Erstellung des Columnstore-Indexes ist nicht erforderlich, kann die Columnstore-Komprimierung jedoch verbessern.

###  <a name="key-concepts-and-terms"></a><a name="Concepts"></a>Wichtige Konzepte und Begriffe
 Die folgenden Hauptbegriffe und -konzepte werden im Zusammenhang mit Columnstore-Indizes verwendet.

 columnstore--Index ein *columnstore--Index* ist eine Technologie zum Speichern, abrufen und Verwalten von Daten mithilfe eines Spalten basierten Datenformats, das als columnstore-bezeichnet wird. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt gruppierte und nicht gruppierte Columnstore-Indizes. Beide verwenden die gleiche In-Memory-Columnstore-Technologie, sie unterscheiden sich jedoch hinsichtlich ihres Verwendungszwecks und Funktionsumfangs.

 columnstore-ein *columnstore-* ist Daten, die logisch als Tabelle mit Zeilen und Spalten organisiert und physisch in einem Spalten bezogenen Datenformat gespeichert werden.

 rowstore bei einem *rowstore* handelt es sich um Daten, die logisch als Tabelle mit Zeilen und Spalten organisiert und anschließend physisch in einem Zeilen bezogenen Datenformat gespeichert werden. Dies war die traditionelle Vorgehensweise beim Speichern von Daten aus relationalen Tabellen.

 Zeilen Gruppen und Spalten Segmente für hohe Leistung und hohe Komprimierungs Raten: der columnstore--Index schneidet die Tabelle in Gruppen von Zeilen ab, die als Zeilen Gruppen bezeichnet werden, und komprimiert dann jede Zeilen Gruppe auf spaltenweise. Die Anzahl der Zeilen in der Zeilengruppe muss groß genug sein, um die Komprimierungsraten zu verbessern, und klein genug, um von In-Memory-Vorgängen profitieren zu können.

 Zeilen Gruppe eine Zeilen *Gruppe* ist eine Gruppe von Zeilen, die gleichzeitig in das columnstore--Format komprimiert werden.

 Spalten Segment ein *Spalten Segment* ist eine Spalte mit Daten aus der Zeilen Gruppe.

-   Eine Zeilengruppe enthält normalerweise die maximale Anzahl von Zeilen pro Zeilengruppe, die 1.048.576 Zeilen beträgt.

-   Jede Zeilengruppe enthält ein Spaltensegment für jede Spalte in der Tabelle.

-   Jedes Spaltensegment wird zusammenhängend komprimiert und auf physischen Medien gespeichert.

 ![Spaltensegment](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "Spaltensegment")

 nicht gruppierten columnstore-Index ein *nicht gruppierter columnstore-* -Index ist ein Schreib geschützter Index, der für einen vorhandenen gruppierten Index oder eine Heap Tabelle erstellt wird. Er enthält eine Kopie einer Teilmenge von Spalten, die maximal alle Spalten in der Tabelle umfassen kann. Die Tabelle ist schreibgeschützt, während Sie einen nicht gruppierten columnstore--Index enthält.

 Ein nicht gruppierter Columnstore-Index bietet eine Möglichkeit, über einen Columnstore-Index zum Ausführen von Analyseabfragen zu verfügen, während gleichzeitig schreibgeschützte Vorgänge für die ursprüngliche Tabelle ausgeführt werden.

 ![Nicht gruppierter Columnstore-Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "Nicht gruppierter Columnstore-Index")

 gruppierter columnstore--Index ein *gruppierter columnstore--Index* ist der physische Speicher für die gesamte Tabelle und der einzige Index für die Tabelle. Der gruppierte Index kann aktualisiert werden. Sie können Einfüge-, Lösch- und Updatevorgänge für den Index ausführen und per Massenladen Daten in den Index laden.

 ![Gruppierter Columnstore-Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "Gruppierter Columnstore-Index")

 Um die Fragmentierung der Spaltensegmente zu verringern und die Leistung zu verbessern, können einige Daten im Columnstore-Index vorübergehend in einer Zeilenspeichertabelle, die als Deltastore bezeichnet wird, sowie eine B-Struktur der IDs für gelöschte Zeilen gespeichert werden. Die Deltastore-Vorgänge werden im Hintergrund verarbeitet. Damit die richtigen Abfrageergebnisse zurückgegeben werden, kombiniert der gruppierte Columnstore-Index Abfrageergebnisse aus dem Columnstore und dem Deltastore.

 Delta Store wird nur mit gruppierten columnstore--Indizes verwendet. ein *Delta Store* ist eine rowstore-Tabelle, in der Zeilen gespeichert werden, bis die Anzahl der Zeilen groß genug ist, um in den columnstore-verschoben zu werden. Ein Deltastore wird mit gruppierten Columnstore-Indizes verwendet, um die Leistung bei Lade- und anderen DML-Vorgängen zu verbessern.

 Während eines umfassenden Massenladevorgangs werden die meisten Zeilen ohne Umweg über den Deltastore direkt in den Columnstore verschoben. Einige Zeilen am Ende des Massenladevorgangs erreichen möglicherweise nicht die notwendige Anzahl für die minimale Größe einer Zeilengruppe von 102.400 Zeilen. Wenn dieser Fall auftritt, werden die letzten Zeilen in den Deltastore und nicht in den Columnstore aufgenommen. Bei kleinen Massenladevorgängen mit weniger als 102.400 Zeilen werden alle Zeilen direkt in den Deltastore verschoben.

 Wenn der Deltastore die maximale Zeilenanzahl erreicht, wird er geschlossen. Ein Tupelverschiebungsvorgang überprüft auf geschlossene Zeilengruppen. Wenn die geschlossene Zeilengruppe gefunden wird, wird sie komprimiert und im Columnstore-Index gespeichert.

##  <a name="loading-data"></a><a name="dataload"></a>Laden von Daten

###  <a name="loading-data-into-a-nonclustered-columnstore-index"></a><a name="dataload_nci"></a>Laden von Daten in einen nicht gruppierten columnstore-Index
 Zum Laden von Daten in einen nicht gruppierten columnstore--Index laden Sie zuerst Daten in eine herkömmliche rowstore-Tabelle, die als Heap oder gruppierter Index gespeichert ist, und erstellen Sie dann den nicht gruppierten columnstore--Index mit [Create columnstore-Index &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).

 ![Laden von Daten in einen columnstore-Index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Laden von Daten in einen columnstore-Index")

 Eine Tabelle mit einem nicht gruppierten Columnstore-Index ist so lange schreibgeschützt, bis der Index gelöscht oder deaktiviert wird. Um die Tabelle und den nicht gruppierten columnstore--Index zu aktualisieren, können Sie Partitionen ein-und ausschalten. Sie können den Index auch deaktivieren, die Tabelle aktualisieren und den Index dann neu erstellen.

 Weitere Informationen finden Sie unter [Using Nonclustered Columnstore Indexes](indexes.md).

###  <a name="loading-data-into-a-clustered-columnstore-index"></a><a name="dataload_cci"></a>Laden von Daten in einen gruppierten columnstore-Index
 ![Laden in einen gruppierten Columnstore-Index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "Laden in einen gruppierten Columnstore-Index")

 Wie das Diagramm nahe legt, führt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zum Laden von Daten in einen gruppierten Columnstore-Index Folgendes aus:

1.  Zeilengruppen mit maximal zulässiger Größe werden direkt in den Columnstore eingefügt. Sobald die Daten geladen sind, weist [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Datenzeilen nach der Reihenfolge ihres Eingangs einer OPEN-Zeilengruppe zu.

2.  Für jede Zeilengruppe führt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]nach Erreichen der maximal zulässigen Größe Folgendes aus:

    1.  Die Zeilengruppe wird als CLOSED markiert.

    2.  Der Deltastore wird umgangen.

    3.  Jedes Spaltensegment für die Zeilengruppe wird mit der Columnstore-Komprimierung komprimiert.

    4.  Jedes komprimierte Spaltensegment wird physisch im Columnstore-Index gespeichert.

3.  Die übrigen Zeilen werden wie folgt in den Columnstore oder den Deltastore eingefügt:

    1.  Wenn die Zeilenanzahl die Anforderung bzgl. der minimalen Anzahl von Zeilen pro Zeilengruppe erfüllt, werden die Zeilen dem Columnstore hinzugefügt.

    2.  Wenn die Zeilenanzahl unter der minimalen Anzahl von Zeilen pro Zeilengruppe liegt, werden die Zeilen dem Deltastore hinzugefügt.

 Weitere Informationen zu Deltastore-Aufgaben und -Vorgängen finden Sie unter [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).

##  <a name="performance-tips"></a><a name="performance"></a>Leistungs Tipps

### <a name="plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a>Planen Sie ausreichend Arbeitsspeicher für eine parallele Erstellung von Columnstore-Indizes ein
 Bei der Erstellung eines Columnstore-Indexes handelt es sich standardmäßig um einen parallel ausgeführten Vorgang, sofern der verfügbare Arbeitsspeicher nicht eingeschränkt ist. Die parallele Indexerstellung erfordert mehr Arbeitsspeicher als die serielle Erstellung des Index. Wenn ausreichend Arbeitsspeicher verfügbar ist, dauert das Erstellen eines Columnstore-Indexes 1,5-mal so lange wie das Erstellen einer B-Struktur für die gleichen Spalten.

 Der Speicherplatz, der für das Erstellen eines Columnstore-Indexes erforderlich ist, hängt von der Anzahl von Spalten, der Anzahl der Zeichenfolgenspalten, dem Grad der Parallelität (Degree of Parallelism, DOP) und von den Eigenschaften der Daten ab. Wenn die Tabelle beispielsweise weniger als eine Million Zeilen aufweist, verwendet SQL Server nur einen Thread, um den Columnstore-Index zu erstellen.

 Wenn die Tabelle mehr als eine Million Zeilen aufweist, SQL Server aber keine ausreichend dimensionierte Arbeitsspeicherzuweisung abrufen kann, um den Index mit MAXDOP zu erstellen, verringert SQL Server MAXDOP automatisch nach Bedarf, um es auf den verfügbaren Arbeitsspeicher zu beschränken.  In bestimmten Fällen muss DOP auf eins verringert werden, um den Index mit eingeschränktem Arbeitsspeicher zu erstellen.

##  <a name="related-tasks-and-topics"></a><a name="related"></a>Verwandte Aufgaben und Themen

### <a name="nonclustered-columnstore-indexes"></a>Nicht gruppierte Columnstore-Indizes
 Informationen für häufige Aufgaben finden Sie unter [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md).

-   [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   [Alter Index &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-index-transact-sql) mit Rebuild.

-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)

### <a name="clustered-columnstore-indexes"></a>Gruppierte Columnstore-Indizes
 Informationen für häufige Aufgaben finden Sie unter [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).

-   [Erstellen eines gruppierten columnstore-Indexes &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   [Alter Index &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-index-transact-sql) mit neu erstellen oder neu organisieren.

-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)

-   [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)

-   [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)

-   [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql)

### <a name="metadata"></a>Metadaten
 Alle Spalten in einem Columnstore-Index werden in den Metadaten als eingeschlossene Spalten gespeichert. Der Columnstore-Index weist keine Schlüsselspalten auf.

-   [sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)

-   [sys.index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)

-   [sys.partitions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)

-   [sys.column_store_segments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-segments-transact-sql)

-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql)

-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)


