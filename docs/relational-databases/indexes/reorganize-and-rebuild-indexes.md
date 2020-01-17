---
title: Neuorganisieren und Neuerstellen von Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql13.swb.index.rebuild.f1
- sql13.swb.indexproperties.fragmentation.f1
- sql13.swb.index.reorg.f1
helpviewer_keywords:
- large object defragmenting
- indexes [SQL Server], reorganizing
- index reorganization [SQL Server]
- reorganizing indexes
- defragmenting large object data types
- index fragmentation [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- indexes [SQL Server], rebuilding
- defragmenting indexes
- nonclustered indexes [SQL Server], defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
- LOB data [SQL Server], defragmenting
- clustered indexes, defragmenting
ms.assetid: a28c684a-c4e9-4b24-a7ae-e248808b31e9
author: pmasl
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cd844947b93e17684643fe95b5c51335af81b473
ms.sourcegitcommit: c98c6e33d04d4a1888db7dbe89cb0b1bb3a66418
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "74249753"
---
# <a name="reorganize-and-rebuild-indexes"></a>Neuorganisieren und Neuerstellen von Indizes

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

In diesem Artikel wird beschrieben, wie Sie einen fragmentierten Index in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] neu organisieren oder erneut erstellen. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwaltet Indizes automatisch, wenn Einfüge-, Update- oder Löschvorgänge an den zugrunde liegenden Daten vorgenommen werden. Im Lauf der Zeit können diese Änderungen dazu führen, dass die Informationen im Index in der Datenbank verstreut (fragmentiert) werden. Fragmentierung liegt vor, wenn Indizes über Seiten verfügen, in denen die logische Reihenfolge (basierend auf dem Schlüsselwert) nicht der physischen Reihenfolge in der Datendatei entspricht. Hochgradig fragmentierte Indizes können die Abfrageleistung beeinträchtigen und dazu führen, dass Ihre Anwendung nur langsam reagiert.

Sie können die Indexfragmentierung durch Neuorganisieren oder Neuerstellen eines Indexes beheben. Für partitionierte Indizes, die auf Grundlage eines Partitionsschemas erstellt wurden, können beide Methoden für einen vollständigen Index oder für eine einzelne Partition eines Indexes verwendet werden:

- Das **Neuorganisieren eines Indexes** beansprucht minimale Systemressourcen und ist ein Vorgang, der online ausgeführt wird. Dies bedeutet, dass keine blockierende Langzeitsperren für Tabellen aufrechterhalten werden und dass während der `ALTER INDEX REORGANIZE`-Transaktion Abfragen oder Updates der zugrunde liegenden Tabelle fortgesetzt werden können.
  - Für **Rowstore**-Indizes wird die Blattebene von gruppierten und nicht gruppierten Indizes in Tabellen und Sichten defragmentiert, indem die Blattebenenseiten physisch neu geordnet werden, damit sie mit der logischen Reihenfolge der Blattknoten von links nach rechts übereinstimmen. Durch das Neuorganisieren werden die Indexseiten auch komprimiert. Die Komprimierung basiert auf dem vorhandenen Füllfaktorwert. Verwenden Sie zum Anzeigen der Füllfaktoreinstellung [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).
  - Bei der Verwendung von **Columnstore**-Indizes kann der Deltastore nach dem Laden von Daten mehrere kleine Zeilengruppen umfassen. Durch eine Neuorganisation des Columnstore-Index wird der Einschluss aller Zeilengruppen in den Columnstore erzwungen, und anschließend werden die Zeilengruppen kombiniert, sodass weniger Zeilengruppen mit mehr Zeilen entstehen. Der Neuorganisationsvorgang entfernt auch Zeilen, die aus dem Columnstore gelöscht wurden. Beim Neuorganisieren sind zunächst zusätzliche CPU-Ressourcen zum Komprimieren der Daten erforderlich. Dies kann die Gesamtleistung des Systems beeinträchtigen. Sobald die Daten jedoch komprimiert sind, kann sich die Abfrageleistung verbessern.

- Beim **Neuerstellen eines Indexes** wird der Index gelöscht und neu erstellt. Abhängig vom Typ des Indexes und der [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Version kann diese Neuerstellung online oder offline erfolgen.
  - Für **Rowstore**-Indizes wird die Fragmentierung entfernt, Speicherplatz freigegeben, indem die Seiten auf der Grundlage der angegebenen oder vorhandenen Füllfaktoreinstellung komprimiert werden, und die Indexzeilen werden in aufeinanderfolgenden Seiten neu geordnet. Wenn `ALL` angegeben ist, werden alle Indizes der Tabelle in einer einzelnen Transaktion gelöscht und neu erstellt. Fremdschlüsseleinschränkungen müssen nicht im Voraus gelöscht werden. Wenn Indizes mit mindestens 128 Blöcken neu erstellt werden, verzögert das [!INCLUDE[ssDE](../../includes/ssde-md.md)] die tatsächlichen aufgehobenen Seitenzuordnungen sowie deren zugeordnete Sperren, bis für die Transaktion ein Commit ausgeführt wird.
  - Für **Columnstore**-Indizes wird bei der Neuerstellung die Fragmentierung entfernt, alle Zeilen werden in den Columnstore verschoben, und Speicherplatz wird freigegeben, indem die logisch aus der Tabelle gelöschten Zeilen physisch gelöscht werden. Ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ist die Neuerstellung des Columnstore-Indexes in der Regel nicht notwendig, weil `REORGANIZE` die Grundlagen der Neuerstellung im Hintergrund als Onlinevorgang ausführt.

In Vorgängerversionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte in einigen Fällen ein nicht gruppierter Rowstore-Index neu erstellt werden, um durch Hardwarefehler verursachte Inkonsistenzen zu korrigieren.
Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sind Sie u. U. weiterhin in der Lage, solche Inkonsistenzen zwischen dem Index und dem gruppierten Index zu beheben, indem Sie einen nicht gruppierten Index offline erstellen. Sie können die Inkonsistenzen eines nicht gruppierten Indexes jedoch nicht beheben, indem Sie den Index online neu erstellen, da der Onlineneuerstellungsmechanismus den vorhandenen nicht gruppierten Index als Grundlage für die Neuerstellung verwendet und somit die Inkonsistenzen bestehen bleiben. Wird der Index offline neu erstellt, wird in manchen Fällen ein Scan des gruppierten Indexes (oder Heaps) erzwungen. um dadurch Inkonsistenzen zu entfernen. Löschen Sie den nicht gruppierten Index, und erstellen Sie ihn neu, um eine Neuerstellung über den gruppierter Index zu gewährleisten. Wie in früheren Versionen wird zum Entfernen von Inkonsistenzen empfohlenen, die betroffenen Daten aus einer Sicherung wiederherzustellen. Die Inkonsistenzen des Indexes können möglicherweise auch behoben werden, indem der nicht gruppierte Index offline neu erstellt wird. Weitere Informationen finden Sie unter [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).

## <a name="Fragmentation"></a> Erkennen einer Fragmentierung

Der erste Schritt bei der Entscheidung für eine Defragmentierungsmethode besteht im Analysieren des Indexes, um den Fragmentierungsgrad zu ermitteln.

### <a name="detecting-fragmentation-on-rowstore-indexes"></a>Erkennen einer Fragmentierung für Rowstore-Indizes

Mithilfe der Systemfunktion [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) können Sie die Fragmentierung in einem bestimmten Index, allen Indizes in einer Tabelle oder indizierten Sicht, allen Indizes in einer Datenbank oder allen Indizes in allen Datenbanken erkennen. Für partitionierte Indizes stellt **sys.dm_db_index_physical_stats** außerdem Fragmentierungsinformationen für jede Partition bereit.

Das durch die Funktion **sys.dm_db_index_physical_stats** zurückgegebene Resultset umfasst die folgenden Spalten:

|Column|BESCHREIBUNG|
|------------|-----------------|
|**avg_fragmentation_in_percent**|Der Prozentsatz der logischen Fragmentierung (falsche Reihenfolge der Seiten in einem Index).|
|**fragment_count**|Die Anzahl der Fragmente (physisch aufeinanderfolgende Blattseiten) im Index.|
|**avg_fragment_size_in_pages**|Durchschnittliche Anzahl der Seiten in einem Fragment in einem Index.|

Nachdem der Grad der Fragmentierung bekannt ist, verwenden Sie die folgenden Tabelle, um die beste Methode zum Beheben der Fragmentierung zu ermitteln.

|**avg_fragmentation_in_percent** -Wert|Korrigierende Anweisung|
|-----------------------------------------------|--------------------------|
|> 5 % und < = 30 %|ALTER INDEX REORGANIZE|
|> 30%|ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup>|

<sup>1</sup> Das Neuerstellen eines Indexes kann online oder offline erfolgen. Das Neuorganisieren eines Indexes erfolgt immer online. Damit eine Verfügbarkeit ähnlich der Neuorganisierungsoption erreicht wird, sollten Indizes online neu erstellt werden. Weitere Informationen finden Sie unter [Ausführen von Onlineindexvorgängen](../../relational-databases/indexes/perform-index-operations-online.md) .

> [!TIP]
> Diese Werte dienen als grobe Richtlinie, um den Punkt zu bestimmen, an dem Sie zwischen `ALTER INDEX REORGANIZE` und `ALTER INDEX REBUILD` wechseln sollten. Die Istwerte können jedoch von Fall zu Fall unterschiedlich sein. Es ist wichtig, dass Sie experimentieren, um den besten Schwellenwert für Ihre Umgebung zu bestimmen. Wird ein bestimmter Index beispielsweise hauptsächlich für Überprüfungsvorgänge verwendet, kann ein Entfernen der Fragmentierung die Leistung dieser Vorgänge verbessern. Für Indizes, die in erster Linie für Suchvorgänge verwendet werden, fällt der Leistungsvorteil weniger auf. Ähnliches gilt für das Entfernen der Fragmentierung in einem Heap (einer Tabelle ohne gruppierten Index). Auch dies ist besonders nützlich für Überprüfungsvorgänge für nicht gruppierte Indizes, wirkt sich aber kaum auf Suchvorgänge aus.

Bei sehr niedrigen Fragmentierungsniveaus (unter 5 Prozent) sollten diese Befehle normalerweise nicht eingesetzt werden, da die Vorteile des Entfernens einer so geringen Fragmentierung die Kosten für das Neuorganisieren und Neuerstellen des Indexes nicht aufwiegen. Weitere Informationen zu `ALTER INDEX REORGANIZE` und `ALTER INDEX REBUILD` finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).

> [!NOTE]
> Durch das erneute Erstellen oder Organisieren kleiner Rowstore-Indizes lässt sich die Fragmentierung häufig nicht verringern. Die Seiten kleiner Indizes werden manchmal in gemischten Blöcken gespeichert. Da gemischte Blöcke von bis zu acht Objekten gemeinsam genutzt werden, lässt sich die Fragmentierung in einem kleinen Index durch die erneute Erstellung oder Organisation des Indexes möglicherweise nicht verringern.

### <a name="detecting-fragmentation-on-columnstore-indexes"></a>Erkennen einer Fragmentierung für Columnstore-Indizes

Durch Verwendung der DMV [sys.dm_db_column_store_row_group_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md) können Sie den Prozentsatz der gelöschten Zeilen ermitteln, der ein gutes Maß für die Fragmentierung in einer Zeilengruppe darstellt. Verwenden Sie diese Informationen, um die Fragmentierung in einem bestimmten Index, für alle Indizes in einer Tabelle, für alle Indizes in einer Datenbank oder für alle Indizes in sämtlichen Datenbanken zu berechnen.

Das durch die DMV **sys.dm_db_column_store_row_group_physical_stats** zurückgegebene Resultset umfasst die folgenden Spalten:

|Column|BESCHREIBUNG|
|------------|-----------------|
|**total_rows**|Die Anzahl von Zeilen, die in der Zeilengruppe physisch gespeichert sind. Für komprimierte Zeilengruppen schließt dies die Zeilen ein, die als gelöscht markiert sind.|
|**deleted_rows**|Die Anzahl von Zeilen, die in einer komprimierten Zeilengruppe physisch gespeichert und zum Löschen markiert sind. Für Zeilengruppen im Deltastore lautet der Wert 0.|

Hierüber kann die Fragmentierung mithilfe der Formel `100*(ISNULL(deleted_rows,0))/NULLIF(total_rows,0)` berechnet werden. Nachdem der Grad der Fragmentierung bekannt ist, verwenden Sie die folgenden Tabelle, um die beste Methode zum Beheben der Fragmentierung zu ermitteln.

|**Berechnete Fragmentierung als Prozentwert**|Gilt für Version|Korrigierende Anweisung|
|-----------------------------------------------|--------------------------|--------------------------|
|> = 20 %|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|ALTER INDEX REBUILD|
|> = 20 %|Seit [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|ALTER INDEX REORGANIZE|

## <a name="index-defragmentation-considerations"></a>Überlegungen zur Indexdefragmentierung

Bei Zutreffen bestimmter Bedingungen führt eine Neuerstellung eines gruppierten Indexes dazu, dass alle nicht gruppierten Indizes, in denen auf den Gruppierungsschlüssel verwiesen wird, automatisch neu erstellt werden, wenn die physischen oder logischen IDs geändert werden müssen, die sich in den nicht gruppierten Indexdatensätzen befinden.

In diesen Szenarien wird erzwungen, dass alle nicht gruppierten Rowstore-Indizes für eine Tabelle automatisch neu erstellt werden:

- Erstellen eines gruppierten Indexes für eine Tabelle
- Entfernen eines gruppierten Indexes, was zur Folge hat, dass die Tabelle als Heap gespeichert wird
- Ändern des Gruppierungsschlüssels, um Spalten einzubeziehen oder auszuschließen

In diesen Szenarien ist es nicht erforderlich, dass alle nicht gruppierten Rowstore-Indizes für eine Tabelle automatisch neu erstellt werden:

- Neuerstellen eines eindeutigen gruppierten Indexes
- Neuerstellen eines nicht eindeutigen gruppierten Indexes
- Ändern des Indexschemas, beispielsweise Anwenden eines Partitionierungsschemas auf einen gruppierten Index oder Verschieben des gruppierten Indexes in eine andere Dateigruppe

> [!IMPORTANT]
> Ein Index kann nicht neu organisiert oder neu erstellt werden, wenn die Dateigruppe, in der er enthalten ist, eine Offline- oder schreibgeschützte Dateigruppe ist. Wenn das Schlüsselwort ALL angegeben ist und mindestens ein Index in einer Offline- oder schreibgeschützten Dateigruppe enthalten ist, erzeugt die Anweisung einen Fehler.
>
> Während der Neuerstellung eines Indexes muss das physische Medium über genügend Speicherplatz verfügen, um zwei Kopien des Indexes zu speichern. Nach Abschluss der Neuerstellung löscht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den ursprünglichen Index.

Wenn `ALL` mit der `ALTER INDEX`-Anweisung angegeben wird, werden relationale Indizes – sowohl gruppierte als auch nicht gruppierte – und XML-Indizes der Tabelle neu organisiert.

### <a name="considerations-specific-to-rebuilding-a-columnstore-index"></a>Überlegungen zur Neuerstellung eines Columnstore-Indexes

Bei der Neuerstellung eines Columnstore-Indexes liest die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] alle Daten aus dem ursprünglichen Columnstore-Index, einschließlich des Deltastore. Die Daten werden in neuen Zeilengruppen zusammengefasst, und die Zeilengruppen werden in den Columnstore-Index komprimiert. Die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] defragmentiert den Columnstore, indem physisch Zeilen gelöscht werden, die logisch aus der Tabelle gelöscht wurden. Die gelöschten Bytes werden auf dem Datenträger freigegeben.

Erstellen Sie nicht die gesamte Tabelle, sondern nur eine Partition neu:

- Wenn der Index groß ist, nimmt das Neuerstellen der gesamten Tabelle viel Zeit in Anspruch, und es muss ausreichend Speicherplatz verfügbar sein, um während der Neuerstellung eine zusätzliche Kopie des Indexes speichern zu können. In der Regel muss nur die zuletzt verwendete Partition neu erstellt werden.
- Bei partitionierten Tabellen müssen Sie nicht den gesamten Columnstore-Index neu erstellen, da die Fragmentierung wahrscheinlich nur in den Partitionen vorliegt, die kürzlich geändert wurden. Faktentabellen und große Dimensionstabellen werden i. d. R. partitioniert, um Sicherungs- und Verwaltungsvorgänge für Segmente der Tabelle auszuführen.

Erstellen Sie eine Partition nach intensiven DML-Vorgängen neu:

- Durch das Neuerstellen einer Partition wird die Partition defragmentiert und der benötigte Festplattenspeicherplatz reduziert. Beim Neuerstellen werden alle zum Löschen markierten Zeilen aus dem Columnstore gelöscht und alle Zeilengruppen aus dem Deltastore in den Columnstore verschoben. Beachten Sie, dass mehrere Zeilengruppen im Deltastore vorhanden sein können, die weniger als eine Million Zeilen enthalten.

Erstellen Sie eine Partition neu, nachdem Sie Daten geladen haben:

- Dadurch wird sichergestellt, dass alle Daten im Columnstore gespeichert sind. Wenn parallel ausgeführte Prozesse gleichzeitig jeweils weniger als 100.000 Zeilen in dieselbe Partition laden, kann die Partition anschließend mehrere Deltastores aufweisen. Durch das Neuerstellen werden alle Deltastore-Zeilen in den Columnstore verschoben.

### <a name="considerations-specific-to-reorganizing-a-columnstore-index"></a>Überlegungen zur Neuorganisation eines Columnstore-Indexes

Bei der Neuorganisation eines Columnstore-Indizes komprimiert die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] jede CLOSED-Deltazeilengruppe im Columnstore als eine komprimierte Zeilengruppe. Ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] führt der `REORGANIZE`-Befehl die folgenden Optimierungen für eine zusätzliche Defragmentierung online aus:

- Es werden Zeilen physisch aus der Zeilengruppe entfernt, wenn mindestens 10 % der Zeilen logisch gelöscht wurden. Die gelöschten Bytes werden auf den physischen Medien freigegeben. Bei einer komprimierten Zeilengruppe mit 1 Million Zeilen, in der beispielsweise 100.000 Zeilen gelöscht wurden, werden von SQL Server die gelöschten Zeilen entfernt, und die Zeilengruppe wird mit 900.000 Zeilen neu komprimiert. Durch das Entfernen gelöschter Zeilen wird Speicherplatz eingespart.

- Eine oder mehrere komprimierte Zeilengruppen werden kombiniert, um die Anzahl der Zeilen pro Zeilengruppe auf maximal 1.024.576 Zeilen zu erhöhen. Bei einem Massenexport von 5 Batches mit 102.400 Zeilen erhalten Sie beispielsweise 5 komprimierte Zeilengruppen. Wenn Sie REORGANIZE ausführen, werden diese Zeilengruppen in eine komprimierte Zeilengruppe mit 512.000 Zeilen zusammengeführt. Dies setzt voraus, dass keine Wörterbuchumfangsbegrenzungen oder Arbeitsspeichereinschränkungen vorhanden sind.
- Zeilengruppen, in denen mindestens 10 % der Zeilen logisch gelöscht wurden, versucht die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] mit einer oder mehreren Zeilengruppen zu kombinieren. Beispiel: Zeilengruppe 1 ist mit 500.000 Zeilen komprimiert und Zeilengruppe 21 mit dem Maximalwert von 1.048.576 Zeilen. In Zeilengruppe 21 wurden 60 % der Zeilen gelöscht, wodurch noch 409.830 Zeilen vorhanden sind. In [!INCLUDE[ssde_md](../../includes/ssde_md.md)] werden diese beiden Zeilengruppen vorzugsweise kombiniert, um eine neue Zeilengruppe mit 909.830 Zeilen zu komprimieren.

Nach dem Ausführen von Datenladevorgängen weist Ihr Deltastore möglicherweise mehrere kleine Zeilengruppen auf. Sie können `ALTER INDEX REORGANIZE` verwenden, um alle Zeilengruppen in den Columnstore zu zwingen und anschließend zu kombinieren, sodass weniger Zeilengruppen mit mehr Zeilen entstehen. Der Neuorganisationsvorgang entfernt auch Zeilen, die aus dem Columnstore gelöscht wurden.

## <a name="Restrictions"></a> Einschränkungen

Rowstore-Indizes mit mehr als 128 Blöcken werden in zwei getrennten Phasen neu erstellt: der logischen und der physischen Phase. In der logischen Phase werden die vorhandenen Zuordnungseinheiten, die vom Index verwendet werden, für die Aufhebung der Zuordnung markiert, die Datenzeilen werden kopiert und sortiert und dann in neue Zuordnungseinheiten verschoben, die erstellt werden, um den neu erstellten Index zu speichern. In der physischen Phase werden die zuvor für die Aufhebung der Zuordnung markierten Zuordnungseinheiten in kurzen Transaktionen physisch gelöscht, die im Hintergrund ausgeführt werden und nicht viele Sperren benötigen. Weitere Informationen zu Blöcken finden Sie im [Handbuch zur Architektur von Seiten und Blöcken](../../relational-databases/pages-and-extents-architecture-guide.md).

Die `ALTER INDEX REORGANIZE` -Anweisung erfordert, dass die Datendatei mit dem Index über Platz verfügt, da der Vorgang temporäre Arbeitsseiten nur in der gleichen Datei zuordnen kann, nicht in einer anderen Datei der Dateigruppe. Selbst wenn in einer Dateigruppe leere Seiten verfügbar sind, kann für den Benutzer daher trotzdem Fehler 1105 auftreten: `Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`

> [!WARNING]
> Das Erstellen bzw. Neuerstellen von nicht ausgerichteten Indizes für eine Tabelle mit mehr als 1.000 Partitionen ist möglich, wird aber nicht unterstützt. Dies hätte Leistungseinbußen oder eine zu hohe Speicherauslastung während der Vorgänge zur Folge. Microsoft empfiehlt, bei mehr als 1.000 Partitionen nur ausgerichtete Indizes zu verwenden.

Ein Index kann nicht neu organisiert oder neu erstellt werden, wenn die Dateigruppe, in der er enthalten ist, **offline** ist oder als **schreibgeschützt** festgelegt wurde. Wenn das Schlüsselwort `ALL` angegeben ist und mindestens ein Index in einer Offline- oder schreibgeschützten Dateigruppe enthalten ist, erzeugt die Anweisung einen Fehler.

Wenn ein Index in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**erstellt** oder **neu erstellt** wird, werden Statistiken erstellt oder aktualisiert, indem alle Zeilen in der Tabelle gescannt werden. Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden Statistiken aber mehr nicht durch das Scannen aller Zeilen in der Tabelle erstellt oder aktualisiert, wenn ein partitionierter Index erstellt oder neu erstellt wird. Stattdessen verwendet der Abfrageoptimierer den Standardalgorithmus zur Stichprobenentnahme, um diese Statistiken zu generieren. Um Statistiken zu partitionierten Indizes durch das Scannen aller Zeilen in der Tabelle abzurufen, verwenden Sie `CREATE STATISTICS` oder `UPDATE STATISTICS` mit der `FULLSCAN`-Klausel.

Wenn ein Index in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**neu organisiert** wird, werden die Statistiken nicht aktualisiert.

Ein Index kann nicht neu organisiert werden, wenn `ALLOW_PAGE_LOCKS` auf OFF festgelegt ist.

Bis [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] wird die Neuerstellung eines gruppierten Columnstore-Indexes als Offlinevorgang durchgeführt. Die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] muss eine exklusive Sperre für die Tabelle oder Partition abrufen, während die Neuerstellung ausgeführt wird. Die Daten sind während der Neuerstellung offline und nicht verfügbar, selbst bei Verwendung von `NOLOCK`, Read Commited-Momentaufnahmeisolation (RCSI) oder Momentaufnahmeisolation.
Ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] kann ein gruppierter Columnstore-Index mit der Option `ONLINE=ON` neu erstellt werden.

Bei einer Azure SQL Data Warehouse-Tabelle mit einem sortierten gruppierten Columnstore-Index werden mit `ALTER INDEX REBUILD` die Daten mit TempDB neu sortiert. Überwachen Sie TempDB während der Neuerstellungsvorgänge. Wenn Sie mehr TempDB-Speicherplatz benötigen, können Sie die Data Warehouse-Instanz zentral hochskalieren. Skalieren Sie es nach Abschluss der Indexneuerstellung wieder herunter.

Bei einer Azure SQL Data Warehouse-Tabelle mit einem sortierten gruppierten Columnstore-Index werden mit `ALTER INDEX REORGANIZE` die Daten nicht neu sortiert. Verwenden Sie `ALTER INDEX REBUILD` zum Neusortieren der Daten.

## <a name="Security"></a> Sicherheit

### <a name="Permissions"></a> Berechtigungen

Erfordert die `ALTER`-Berechtigung für die Tabelle oder Sicht. Der Benutzer muss ein Mitglied mindestens einer der folgenden Rollen sein:

- Datenbankrolle **db_ddladmin**<sup>1</sup>
- Datenbankrolle **db_owner**
- Serverrolle **sysadmin**

<sup>1</sup>Die Datenbankrolle **db_ddladmin** hat die [niedrigsten Berechtigungen](/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models).

## <a name="SSMSProcedureFrag"></a> Überprüfen der Indexfragmentierung mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]

> [!NOTE]
> [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] kann nicht zum Berechnen der Fragmentierung von Columnstore-Indizes in SQL Server und nicht zum Berechnen der Fragmentierung von Indizes in Azure SQL-Datenbank verwendet werden. Verwenden Sie das [unten angegebene](#TsqlProcedureFrag)[!INCLUDE[tsql](../../includes/tsql-md.md)]-Beispiel.

1. Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, in der Sie die Fragmentierung eines Indexes überprüfen möchten.
2. Erweitern Sie den Ordner **Tabellen** .
3. Erweitern Sie die Tabelle, in der Sie die Fragmentierung eines Indexes überprüfen möchten.
4. Erweitern Sie den Ordner **Indizes** .
5. Klicken Sie mit der rechten Maustaste auf den Index, für den Sie die Fragmentierung überprüfen möchten, und wählen Sie **Eigenschaften**aus.
6. Wählen Sie unter **Seite auswählen**die Option **Fragmentierung**aus.

Die folgenden Informationen sind auf der Seite **Fragmentierung** verfügbar:

|value|BESCHREIBUNG|
|---|---|
|**Seitenfüllgrad**|Gibt den durchschnittlichen Füllgrad der Indexseiten als Prozentwert an. 100 % bedeutet, dass die Indexseiten vollständig gefüllt sind. 50 % heißt, dass jede Indexseite im Durchschnitt zur Hälfte gefüllt ist.|
|**Fragmentierung gesamt**|Prozentwert der logischen Fragmentierung. Dieser Wert gibt die Anzahl der Seiten in einem Index an, die nicht in Reihenfolge gespeichert sind.|
|**Durchschnittliche Zeilengröße**|Die durchschnittliche Größe einer Zeile auf Blattebene.|
|**Tiefe**|Die Anzahl von Ebenen im Index, einschließlich der Blattebene.|
|**Weitergeleitete Datensätze**|Anzahl der Datensätze in einem Heap, die Weiterleitungszeiger auf einen anderen Datenspeicherort besitzen. (Dieser Status tritt während eines Updates auf, wenn nicht genügend Speicherplatz vorhanden ist, um die neue Zeile am ursprünglichen Speicherort zu speichern.)|
|**Inaktive Zeilen**|Anzahl der Zeilen, die als gelöscht markiert sind, aber noch nicht entfernt wurden. Diese Zeilen werden von einem Bereinigungsthread entfernt, wenn der Server nicht ausgelastet ist. Dieser Wert schließt keine Zeilen ein, die aufgrund einer ausstehenden Momentaufnahme-Isolationstransaktion beibehalten werden.|
|**Indextyp**|Der Indextyp. Mögliche Werte sind **Gruppierter Index**, **Nicht gruppierter Index**und **Primär-XML**. Tabellen können auch als Heap gespeichert werden (ohne Indizes). Dann kann aber diese Seite Indexeigenschaften nicht geöffnet werden.|
|**Zeilen auf Blattebene**|Die Anzahl von Zeilen auf Blattebene.|
|**Maximale Zeilengröße**|Maximale Größe von Zeilen auf Blattebene.|
|**Minimale Zeilengröße**|Minimale Größe von Zeilen auf Blattebene.|
|**Seiten**|Gesamtanzahl der Datenseiten.|
|**Partitions-ID**|Partitions-ID der B-Struktur, die den Index enthält.|
|**Inaktive Zeilen (Version)**|Die Anzahl inaktiver Datensätze, die aufgrund einer ausstehenden Momentaufnahme-Isolationstransaktion beibehalten werden.|

## <a name="TsqlProcedureFrag"></a> Überprüfen der Indexfragmentierung mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]

### <a name="to-check-the-fragmentation-of-a-rowstore-index"></a>So überprüfen Sie die Fragmentierung eines Rowstore-Indexes

Das folgende Beispiel ermittelt den durchschnittlichen Prozentsatz der Fragmentierung aller Indizes der Tabelle „`HumanResources.Employee`“ in der `AdventureWorks2016`-Datenbank.

```sql
SELECT a.object_id, object_name(a.object_id) AS TableName,
    a.index_id, name AS IndedxName, avg_fragmentation_in_percent
FROM sys.dm_db_index_physical_stats
    (DB_ID (N'AdventureWorks2016_EXT')
        , OBJECT_ID(N'HumanResources.Employee')
        , NULL
        , NULL
        , NULL) AS a
INNER JOIN sys.indexes AS b
    ON a.object_id = b.object_id
    AND a.index_id = b.index_id;
GO
```

Das von der vorherigen Anweisung zurückgegebene Resultset kann in etwa wie folgt aussehen.

```
object_id   TableName    index_id    IndexName                                             avg_fragmentation_in_percent
----------- ------------ ----------- ----------------------------------------------------- ------------------------------
1557580587  Employee     1           PK_Employee_BusinessEntityID                          0
1557580587  Employee     2           IX_Employee_OrganizationalNode                        0
1557580587  Employee     3           IX_Employee_OrganizationalLevel_OrganizationalNode    0
1557580587  Employee     5           AK_Employee_LoginID                                   66.6666666666667
1557580587  Employee     6           AK_Employee_NationalIDNumber                          50
1557580587  Employee     7           AK_Employee_rowguid                                   0

(6 row(s) affected)
```

Weitere Informationen finden Sie unter [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).

### <a name="to-check-the-fragmentation-of-a-columnstore-index"></a>So überprüfen Sie die Fragmentierung eines Columnstore-Indexes

Das folgende Beispiel ermittelt den durchschnittlichen Prozentsatz der Fragmentierung aller Indizes der Tabelle „`dbo.FactResellerSalesXL_CCI`“ in der `AdventureWorksDW2016`-Datenbank.

```sql
SELECT i.object_id,
    object_name(i.object_id) AS TableName,
    i.index_id,
    i.name AS IndexName,
    100*(ISNULL(SUM(CSRowGroups.deleted_rows),0))/NULLIF(SUM(CSRowGroups.total_rows),0) AS 'Fragmentation'
FROM sys.indexes AS i  
INNER JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups
    ON i.object_id = CSRowGroups.object_id
    AND i.index_id = CSRowGroups.index_id
WHERE object_name(i.object_id) = 'FactResellerSalesXL_CCI'
GROUP BY i.object_id, i.index_id, i.name
ORDER BY object_name(i.object_id), i.name;
```

Das von der vorherigen Anweisung zurückgegebene Resultset kann in etwa wie folgt aussehen.

```
object_id   TableName                   index_id    IndexName                       Fragmentation
----------- --------------------------- ----------- ------------------------------- ---------------
114099447   FactResellerSalesXL_CCI     1           IndFactResellerSalesXL_CCI      0

(1 row(s) affected)
```

## <a name="SSMSProcedureReorg"></a> Entfernen der Indexfragmentierung mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]

### <a name="to-reorganize-or-rebuild-an-index"></a>So organisieren oder erstellen Sie einen Index neu

1. Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, in der Sie einen Index neu organisieren möchten.
2. Erweitern Sie den Ordner **Tabellen** .
3. Erweitern Sie die Tabelle, in der Sie einen Index neu organisieren möchten.
4. Erweitern Sie den Ordner **Indizes** .
5. Klicken Sie mit der rechten Maustaste auf den Index, den Sie neu organisieren möchten, und wählen Sie **Neu organisieren**aus.
6. Vergewissern Sie sich im Dialogfeld **Indizes neu organisieren** , dass der richtige Index im Raster **Neu zu organisierende Indizes** ausgewählt ist, und klicken Sie auf **OK**.
7. Aktivieren Sie das Kontrollkästchen **Spaltendaten großer Objekte komprimieren** , um anzugeben, dass alle Seiten mit umfangreichen Objektdaten (Large Object, LOB) komprimiert werden sollen.
8. Klicken Sie auf **OK**.

> [!NOTE]
> Bei der Neuorganisation eines Columnstore-Indizes mit [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] werden `COMPRESSED`-Zeilengruppen kombiniert, aber es wird keine Komprimierung aller Zeilengruppen im Columnstore erzwungen. CLOSED-Zeilengruppen werden komprimiert, aber OPEN-Zeilengruppen werden nicht im Columnstore komprimiert. Um alle Zeilengruppen zu komprimieren, verwenden Sie das [unten angegebene](#TsqlProcedureReorg)[!INCLUDE[tsql](../../includes/tsql-md.md)]-Beispiel.

### <a name="to-reorganize-all-indexes-in-a-table"></a>So organisieren Sie alle Indizes in einer Tabelle neu

1. Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, in der Sie die Indizes neu organisieren möchten.
2. Erweitern Sie den Ordner **Tabellen** .
3. Erweitern Sie die Tabelle, in der Sie die Indizes neu organisieren möchten.
4. Klicken Sie mit der rechten Maustaste auf den Ordner **Indizes** , und wählen Sie **Alle neu organisieren**aus.
5. Vergewissern Sie sich im Dialogfeld **Index neu organisieren** , dass die richtigen Indizes im Raster **Neu zu organisierende Indizes**ausgewählt sind. Um einen Index aus dem Raster **Neu zu organisierende Indizes** zu entfernen, wählen Sie den Index aus, und drücken Sie die ENTF-Taste.
6. Aktivieren Sie das Kontrollkästchen **Spaltendaten großer Objekte komprimieren** , um anzugeben, dass alle Seiten mit umfangreichen Objektdaten (Large Object, LOB) komprimiert werden sollen.
7. Klicken Sie auf **OK**.

### <a name="to-rebuild-an-index"></a>So erstellen Sie einen Index neu

1. Erweitern Sie im Objekt-Explorer die Datenbank mit der Tabelle, in der Sie einen Index neu organisieren möchten.
2. Erweitern Sie den Ordner **Tabellen** .
3. Erweitern Sie die Tabelle, in der Sie einen Index neu organisieren möchten.
4. Erweitern Sie den Ordner **Indizes** .
5. Klicken Sie mit der rechten Maustaste auf den Index, den Sie neu organisieren möchten, und wählen Sie **Neu erstellen** aus.
6. Vergewissern Sie sich im Dialogfeld **Indizes neu erstellen** , dass der richtige Index im Raster **Erneut zu erstellende Indizes** ausgewählt ist, und klicken Sie auf **OK**.
7. Aktivieren Sie das Kontrollkästchen **Spaltendaten großer Objekte komprimieren** , um anzugeben, dass alle Seiten mit umfangreichen Objektdaten (Large Object, LOB) komprimiert werden sollen.
8. Klicken Sie auf **OK**.

## <a name="TsqlProcedureReorg"></a> Entfernen der Indexfragmentierung mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]

> [!NOTE]
> Weitere Beispiele zum Verwenden von [!INCLUDE[tsql](../../includes/tsql-md.md)] zur Neuerstellung oder Neuorganisation von Indizes finden Sie unter [ALTER INDEX-Beispiele: Columnstore-Indizes](../../t-sql/statements/alter-index-transact-sql.md#examples-columnstore-indexes) und [ALTER INDEX-Beispiele: Rowstore-Indizes](../../t-sql/statements/alter-index-transact-sql.md#examples-rowstore-indexes).

### <a name="to-reorganize-a-fragmented-index"></a>So organisieren Sie einen fragmentierten Index neu

Im folgenden Beispiel wird der `IX_Employee_OrganizationalLevel_OrganizationalNode`-Index für die `HumanResources.Employee`-Tabelle in der `AdventureWorks2016`-Datenbank neu organisiert.

```sql
ALTER INDEX IX_Employee_OrganizationalLevel_OrganizationalNode
    ON HumanResources.Employee
    REORGANIZE;
```

Im folgenden Beispiel wird der `IndFactResellerSalesXL_CCI`-Columnstore-Index für die `dbo.FactResellerSalesXL_CCI`-Tabelle in der `AdventureWorksDW2016`-Datenbank neu organisiert.

```sql
-- This command will force all CLOSED and OPEN rowgroups into the columnstore.
ALTER INDEX IndFactResellerSalesXL_CCI
    ON FactResellerSalesXL_CCI
    REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);
```

### <a name="to-reorganize-all-indexes-in-a-table"></a>So organisieren Sie alle Indizes in einer Tabelle neu

Im folgenden Beispiel werden alle Indizes für die `HumanResources.Employee`-Tabelle in der `AdventureWorks2016`-Datenbank neu organisiert.

```sql
ALTER INDEX ALL ON HumanResources.Employee
   REORGANIZE;
```

### <a name="to-rebuild-a-fragmented-index"></a>So erstellen Sie einen fragmentierten Index neu

Im folgenden Beispiel wird ein einzelner Index für die `Employee`-Tabelle der `AdventureWorks2016`-Datenbank neu erstellt.

[!code-sql[IndexDDL#AlterIndex1](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_1.sql)]

### <a name="to-rebuild-all-indexes-in-a-table"></a>So erstellen Sie alle Indizes in einer Tabelle neu

Im folgende Beispiel werden alle Indizes, die der Tabelle in der `AdventureWorks2016`-Datenbank zugeordnet sind, mithilfe des Schlüsselworts `ALL` neu erstellt. Es werden drei Optionen angegeben.

[!code-sql[IndexDDL#AlterIndex2](../../relational-databases/indexes/codesnippet/tsql/reorganize-and-rebuild-i_2.sql)]

Weitere Informationen finden Sie unter [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).

### <a name="automatic-index-and-statistics-management"></a>Automatische Verwaltung von Index und Statistiken

Nutzen Sie Lösungen wie [Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag), um die Indexdefragmentierung und das Aktualisieren der Statistiken für eine oder mehrere Datenbanken automatisch zu verwalten. Dieser Vorgang entscheidet unter anderem anhand des Fragmentierungsgrads automatisch, ob ein Index neu organisiert oder neu erstellt wird und aktualisiert Statistiken mit einem linearen Schwellenwert.

## <a name="see-also"></a>Weitere Informationen

- [Leitfaden zur Architektur und zum Entwurf von SQL Server-Indizes](../../relational-databases/sql-server-index-design-guide.md)
- [Ausführen von Onlineindexvorgängen](../../relational-databases/indexes/perform-index-operations-online.md)
- [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)
- [Adaptive Indexdefragmentierung](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag)
- [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)
- [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)
- [Abfrageleistung für Columnstore-Indizes](../../relational-databases/indexes/columnstore-indexes-query-performance.md)
- [Erste Schritte mit Columnstore für die operative Echtzeitanalyse](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)
- [Columnstore-Indizes für Data Warehousing](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)
- [Columnstore-Indizes und Zusammenführungsrichtlinien für Zeilengruppen](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)
