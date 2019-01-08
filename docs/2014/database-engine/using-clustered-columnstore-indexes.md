---
title: Verwenden von gruppierten columnstore-Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e65c3e277eb9a3e5e3703525b9c1ac06b423c96
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502703"
---
# <a name="using-clustered-columnstore-indexes"></a>Verwenden von gruppierten Columnstore-Indizes
  Tasks für die Verwendung von gruppierten Columnstore-Indizes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Eine Übersicht über Columnstore-Indizes finden Sie unter [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Informationen zum Verwenden von gruppierten Columnstore-Indizes finden Sie unter [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Inhalt  
  
-   [Erstellen Sie einen gruppierten columnstore-Index](#create)  
  
-   [Löschen eines gruppierten columnstore-Indexes](#drop)  
  
-   [Laden von Daten in einen gruppierten columnstore-Index](#load)  
  
-   [Ändern von Daten in einem gruppierten columnstore-Index](#change)  
  
-   [Erstellen Sie einen gruppierten columnstore-Index neu.](#rebuild)  
  
-   [Ein gruppierter columnstore-Index neu zu organisieren](#reorganize)  
  
##  <a name="create"></a> Erstellen Sie einen gruppierten columnstore-Index  
 Um einen gruppierten columnstore-Index zu erstellen, erstellen Sie zuerst eine Rowstore-Tabelle als Heap oder gruppierten Index, und verwenden Sie dann die [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) Anweisung, um die Tabelle in eine gruppierte konvertieren columnstore-Index. Wenn der gruppierte Columnstore-Index denselben Namen erhalten soll wie der gruppierte Index, verwenden Sie die Option DROP_EXISTING.  
  
 In diesem Beispiel wird eine Tabelle als Heap erstellt und anschließend in einen gruppierten Columnstore-Index mit dem Namen cci_Simple konvertiert. Dadurch wird der Speicher für die gesamte Tabelle von rowstore in columnstore geändert.  
  
```  
CREATE TABLE T1(  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;  
GO  
```  
  
 Weitere Beispiele finden Sie im Abschnitt "Beispiele" in [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).  
  
##  <a name="drop"></a> Löschen eines gruppierten columnstore-Indexes  
 Verwenden der [DROP INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/drop-index-transact-sql) Anweisung, um einen gruppierten columnstore-Index zu löschen. Bei diesem Vorgang wird der Index gelöscht, und die Columnstore-Tabelle wird in einen Rowstore-Heap konvertiert.  
  
##  <a name="load"></a> Laden von Daten in einen gruppierten columnstore-Index  
 Sie können einem vorhandenen gruppierten Columnstore-Index Daten hinzufügen, indem Sie eine der Standardladenmethoden verwenden.  Z. B. Bcp massenladetool, Integration Services, und INSERT... Mithilfe von SELECT können alle Daten in einen gruppierten ColumnStore-Index geladen werden.  
  
 Gruppierte Columnstore-Indizes nutzen den Deltastore, um eine Fragmentierung der Spaltensegmente im Columnstore zu verhindern.  
  
### <a name="loading-into-a-partitioned-table"></a>Laden von Daten in eine partitionierte Tabelle  
 Bei partitionierten Daten weist [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zuerst jede Zeile einer Partition zu und führt dann Columnstore-Vorgänge für die Daten innerhalb der Partition aus. Jede Partition verfügt über eigene Zeilengruppen und mindestens einen Deltastore.  
  
### <a name="deltastore-loading-scenarios"></a>Ladeszenarien für Deltastores  
 Zeilen werden im Deltastore gesammelt, bis ihre Anzahl die maximale Anzahl der Zeilen erreicht, die für eine Zeilengruppe zulässig sind. Wenn der Deltastore die maximale Anzahl von Zeilen pro Zeilengruppe enthält [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] markiert die Zeilengruppe als "CLOSED". Ein Hintergrundprozess, der "Tuple Mover" bezeichnet, sucht die CLOSED-Zeilengruppe und verschiebt in den Columnstore zu, in denen die Zeilengruppe in spaltensegmente komprimiert wird und die spaltensegmente im Columnstore gespeichert sind.  
  
 Für jeden gruppierten Columnstore-Index können mehrere Deltastores vorhanden sein.  
  
-   Wenn ein Deltastore gesperrt ist, versucht [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], eine Sperre für einen anderen Deltastore zu erhalten. Wenn keine Deltastores verfügbar sind, erstellt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] einen neuen Deltastore.  
  
-   Für eine partitionierte Tabelle sind für jede Partition ein oder mehrere Deltastores vorhanden.  
  
 Die folgenden Szenarien gelten nur für gruppierte Columnstore-Indizes und veranschaulichen, in welchen Fällen geladene Zeilen direkt in den Columnstore und in welchen Fällen sie in den Deltastore aufgenommen werden.  
  
 In diesem Beispiel kann jede Zeilengruppe 102.400 bis 1.048.576 Zeilen pro Zeilengruppe enthalten.  
  
|Zeilen für Massenladevorgang|Dem Columnstore hinzugefügte Zeilen|Dem Deltastore hinzugefügte Zeilen|  
|-----------------------|-----------------------------------|----------------------------------|  
|102,000|0|102,000|  
|145,000|145,000<br /><br /> Zeilengruppengröße: 145,000|0|  
|1,048,577|1,048,576<br /><br /> Zeilengruppengröße: 1,048,576.|1|  
|2,252,152|2,252,152<br /><br /> Zeilengruppengrößen: 1,048,576, 1,048,576, 155,000.|0|  
  
 Im folgenden Beispiel werden die Ergebnisse des Ladens von 1.048.577 Zeilen in eine Partition angezeigt. Aus den Ergebnissen wird ersichtlich, dass eine COMPRESSED-Zeilengruppe im Columnstore (in Form von komprimierten Spaltensegmenten) und eine Zeile im Deltastore vorhanden sind.  
  
```  
SELECT * FROM sys.column_store_row_groups  
```  
  
 ![Zeilengruppe und Deltastore für einen Batchladevorgang](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup and deltastore for a batch load")  
  

  
##  <a name="change"></a> Ändern von Daten in einem gruppierten columnstore-Index  
 Gruppierte Columnstore-Indizes unterstützen DML-Vorgänge zum Einfügen, Aktualisieren und Löschen.  
  
 Verwendung [einfügen &#40;Transact-SQL&#41; ](/sql/t-sql/statements/insert-transact-sql) um eine Zeile einzufügen. Die Zeile wird dem Deltastore hinzugefügt.  
  
 Verwenden Sie [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) zum Löschen einer Zeile.  
  
-   Wenn die Zeile im Columnstore-Index enthalten ist, markiert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Zeile als logisch gelöscht, der physische Speicherplatz für die Zeile wird jedoch erst freigegeben, nachdem der Index neu erstellt wurde.  
  
-   Wenn sich die Zeile im Deltastore befindet, löscht [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Zeile logisch und physisch.  
  
 Verwenden Sie [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) , um eine Zeile zu aktualisieren.  
  
-   Wenn sich die Zeile im Columnstore befindet, markiert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Zeile als logisch gelöscht und fügt die aktualisierte Zeile anschließend in den Deltastore ein.  
  
-   Wenn sich die Zeile im Deltastore befindet, aktualisiert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Zeile im Deltastore.  
  
##  <a name="rebuild"></a> Erstellen Sie einen gruppierten columnstore-Index neu.  
 Verwendung [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) oder [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) , führen Sie eine vollständige Neuerstellung eines vorhandenen gruppierten columnstore-Indexes. Darüber hinaus können Sie ALTER INDEX... REBUILD zum Neu erstellen einer bestimmten Partition.  
  
### <a name="rebuild-process"></a>Neuerstellungsprozess  
 Die Neuerstellung eines gruppierten columnstore-Indexes verläuft in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wie folgt:  
  
-   Abrufen einer exklusiven Sperre für die Tabelle oder Partition, während die Neuerstellung ausgeführt wird.  Die Daten sind während der Neuerstellung „offline“ und nicht verfügbar.  
  
-   Defragmentieren des Columnstore, indem physisch Zeilen gelöscht werden, die logisch aus der Tabelle gelöscht wurden. Die gelöschten Bytes werden auf dem physischen Medium freigegeben.  
  
-   Führt die Rowstore-Daten im Deltastore mit den Daten im Columnstore zusammen, bevor der Index neu erstellt wird. Nachdem die Neuerstellung abgeschlossen ist, sind alle Daten im Columnstore-Format gespeichert, und der Deltastore ist leer.  
  
-   Neukomprimierung aller Daten im Columnstore. Während die Neuerstellung ausgeführt wird, gibt es zwei Kopien des columnstore-Indexes. Nach Abschluss der Neuerstellung wird der ursprüngliche columnstore-Index in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gelöscht.  
  
### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a>Empfehlungen zum Neuerstellen eines gruppierten Columnstore-Indexes  
 Das Neuerstellen eines gruppierten Columnstore-Index ist sinnvoll, um Fragmentierungen zu beseitigen und um alle Zeilen in den Columnstore zu verschieben. Berücksichtigen Sie die folgenden Empfehlungen:  
  
-   Erstellen Sie nur eine Partition neu und nicht die gesamte Tabelle.  
  
    1.  Wenn der Index groß ist, nimmt das Neuerstellen der gesamten Tabelle viel Zeit in Anspruch, und es muss ausreichend Speicherplatz verfügbar sein, um während der Neuerstellung eine zusätzliche Kopie des Indexes speichern zu können. In der Regel muss nur die zuletzt verwendete Partition neu erstellt werden.  
  
    2.  Bei partitionierten Tabellen müssen Sie nicht den gesamten Columnstore-Index neu erstellen, da die Fragmentierung wahrscheinlich nur in den Partitionen vorliegt, die kürzlich geändert wurden. Faktentabellen und große Dimensionstabellen werden i. d. R. partitioniert, um Sicherungs- und Verwaltungsvorgänge für Segmente der Tabelle auszuführen.  
  
-   Erstellen Sie eine Partition nach intensiven DML-Vorgängen neu.  
  
     Durch das Neuerstellen einer Partition wird die Partition defragmentiert und der benötigte Festplattenspeicherplatz reduziert. Beim Neuerstellen werden alle zum Löschen markierten Zeilen aus dem Columnstore gelöscht und alle Zeilen aus dem Deltastore in den Columnstore verschoben.  
  
-   Erstellen Sie eine Partition neu, nachdem Sie Daten geladen haben.  
  
     Dadurch wird sichergestellt, dass alle Daten im Columnstore gespeichert sind. Wenn mehrere Ladevorgänge zur gleichen Zeit ausgeführt werden, kann dies ggf. dazu führen, dass für jede Partition mehrere Deltastores vorhanden sind. Durch das Neuerstellen werden alle Deltastore-Zeilen in den Columnstore verschoben.  
  
##  <a name="reorganize"></a> Ein gruppierter columnstore-Index neu zu organisieren  
 Beim Neuorganisieren eines gruppierten Columnstore-Indexes werden alle Closed-Zeilengruppen in den Columnstore-Index verschoben. Um eine neuorganisierung durchzuführen, verwenden Sie [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)mit der Option REORGANIZE.  
  
 Die Neuorganisation ist für das Verschieben von CLOSED-Zeilengruppen in den Columnstore nicht zwingend erforderlich. Zuletzt werden alle CLOSED-Zeilengruppen vom TM (Tuple Mover)-Vorgang gesucht und verschoben. Da der Tuple Mover jedoch in einem einzelnen Thread ausgeführt wird, werden die Zeilengruppen für Ihre Arbeitsauslastung u. U. nicht schnell genug verschoben.  
  
### <a name="recommendations-for-reorganizing"></a>Empfehlungen zum Neuorganisieren  
 In folgenden Fällen muss ein gruppierter Columnstore-Index neuorganisiert werden:  
  
-   Neuorganisieren Sie einen gruppierten Columnstore-Index nach einem oder mehreren Datenladevorgängen, um so schnell wie möglich die bessere Abfrageleistung nutzbar zu machen. Beim Neuorganisieren sind zunächst zusätzliche CPU-Ressourcen zum Komprimieren der Daten erforderlich. Dies kann die Gesamtleistung des Systems beeinträchtigen. Sobald die Daten jedoch komprimiert sind, kann sich die Abfrageleistung verbessern.  
  
  
