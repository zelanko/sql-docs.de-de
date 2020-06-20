---
title: Speicherplatzanforderungen für Index-DDL-Vorgänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- temporary disk space [SQL Server]
ms.assetid: 35930826-c870-44c1-a966-a6a4638f62ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4ac25fc1555d6b6cfd8ee97b50d261cf5788f587
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025412"
---
# <a name="disk-space-requirements-for-index-ddl-operations"></a>Speicherplatzanforderungen für Index-DDL-Vorgänge
  Der Speicherplatz ist beim Erstellen, Neuerstellen oder Löschen von Indizes ein wichtiger Aspekt, der berücksichtigt werden muss. Unzureichender Speicherplatz kann die Leistung verringern oder sogar bewirken, dass der Indexvorgang einen Fehler erzeugt. Dieses Thema stellt allgemeine Informationen bereit, die Sie beim Ermitteln des Speicherplatzes unterstützen können, der für DDL-Vorgänge (Data Definition Language) des Indexes erforderlich ist.  
  
## <a name="index-operations-that-require-no-additional-disk-space"></a>Indexvorgänge, für die kein zusätzlicher Speicherplatz erforderlich ist  
 Für die folgenden Indexvorgänge ist kein zusätzlicher Speicherplatz erforderlich:  
  
-   ALTER INDEX REORGANIZE; jedoch ist Speicherplatz im Protokoll erforderlich.  
  
-   DROP INDEX, wenn Sie einen nicht gruppierten Index löschen.  
  
-   DROP INDEX, wenn Sie einen gruppierten Index offline löschen, ohne die MOVE TO-Klausel anzugeben, und es sind keine nicht gruppierten Indizes vorhanden.  
  
-   CREATE TABLE (PRIMARY KEY- oder UNIQUE-Einschränkung)  
  
## <a name="index-operations-that-require-additional-disk-space"></a>Indexvorgänge, für die zusätzlicher Speicherplatz erforderlich ist  
 Für alle anderen Index-DDL-Vorgänge ist zusätzlicher temporärer Speicherplatz erforderlich, der während des Vorgangs verwendet werden soll, sowie dauerhafter Speicherplatz, der für das Speichern der neuen Indexstruktur(en) benötigt wird.  
  
 Beim Erstellen einer neuen Indexstruktur wird Speicherplatz sowohl für die alte Struktur (Quelle) als auch für die neue Struktur (Ziel) in den jeweiligen Dateien und Dateigruppen benötigt. Die Zuordnung der alten Struktur wird erst aufgehoben, nachdem die Indexerstellungstransaktion den Commitvorgang ausgeführt hat.  
  
 Die folgenden Index-DDL-Vorgänge erstellen neue Indexstrukturen und erfordern zusätzlichen Speicherplatz:  
  
-   CREATE INDEX  
  
-   CREATE INDEX WITH DROP_EXISTING  
  
-   ALTER INDEX REBUILD  
  
-   ALTER TABLE ADD CONSTRAINT (PRIMARY KEY oder UNIQUE)  
  
-   ALTER TABLE DROP CONSTRAINT (PRIMARY KEY oder UNIQUE), wenn die Einschränkung auf einem gruppierten Index basiert  
  
-   DROP INDEX MOVE TO (Gilt nur für gruppierte Indizes.)  
  
## <a name="temporary-disk-space-for-sorting"></a>Temporärer Speicherplatz für Sortiervorgänge  
 Neben dem für die Quell- und Zielstrukturen benötigten Speicherplatz ist temporärer Speicherplatz für Sortiervorgänge erforderlich, es sei denn, der Abfrageoptimierer ermittelt einen Ausführungsplan, für den keine Sortierung erforderlich ist.  
  
 Wenn Sortierung erforderlich ist, findet die Sortierung für die neuen Indizes nacheinander statt. Wenn Sie z. B. einen gruppierten Index und die zugehörigen nicht gruppierten Indizes mit einer einzigen Anweisung neu erstellen, werden die Indizes nacheinander sortiert. Daher muss der zusätzliche temporäre Speicherplatz, der für die Sortierung erforderlich ist, nur so umfangreich wie der größte Index im Vorgang sein. Dies ist fast immer der gruppierte Index.  
  
 Wenn die Option SORT_IN_TEMPDB auf ON festgelegt wurde, muss der größte Index in **tempdb**passen. Obwohl durch diese Option die Menge des temporären Speicherplatzes erhöht wird, die zur Indexerstellung verwendet wird, kann sich die Zeitspanne verringern, die zum Erstellen eines Indexes erforderlich ist, wenn **tempdb** auf einem anderen Satz von Datenträgern gespeichert ist als die Benutzerdatenbank.  
  
 Wenn SORT_IN_TEMPDB auf OFF festgelegt wurde (die Standardeinstellung), wird jeder Index einschließlich partitionierter Indizes an seinem Zielspeicherplatz sortiert; in diesem Fall ist nur der Speicherplatz für die neuen Indexstrukturen erforderlich.  
  
 Ein Beispiel zum Berechnen des Speicherplatzes finden Sie unter [Index Disk Space Example](index-disk-space-example.md).  
  
## <a name="temporary-disk-space-for-online-index-operations"></a>Temporärer Speicherplatz für Onlineindexvorgänge  
 Wenn Sie Indexvorgänge online ausführen, ist zusätzlicher temporärer Speicherplatz erforderlich.  
  
 Wenn ein gruppierter Index online erstellt, neu erstellt oder gelöscht wird, wird ein temporärer nicht gruppierter Index erstellt, um alte Lesezeichen neuen Lesezeichen zuzuordnen. Wenn die Option SORT_IN_TEMPDB auf ON festgelegt wurde, wird dieser temporäre Index in **tempdb**erstellt. Wurde SORT_IN_TEMPDB auf OFF festgelegt, wird die gleiche Dateigruppe oder das gleiche Partitionsschema wie für den Zielindex verwendet. Der temporäre Zuordnungsindex enthält einen Datensatz für jede Zeile in der Tabelle. Sein Inhalt ist die Vereinigung der alten und der neuen Lesezeichenspalten, einschließlich uniqueifiers und Datensatzbezeichnern sowie einer einzigen Kopie jeder Spalte, die in beiden Lesezeichen verwendet wird. Weitere Informationen zu Onlineindexvorgängen finden Sie unter [Ausführen von Onlineindexvorgängen](perform-index-operations-online.md).  
  
> [!NOTE]  
>  Die SORT_IN_TEMPDB-Option kann nicht für DROP INDEX-Anweisungen festgelegt werden. Der temporäre Zuordnungsindex wird immer in der gleichen Dateigruppe oder dem gleichen Partitionsschema wie der Zielindex erstellt.  
  
 Onlineindexvorgänge verwenden die Zeilenversionsverwaltung, um den Indexvorgang von den Auswirkungen der Änderungen zu isolieren, die von anderen Transaktionen vorgenommen wurden. Auf diese Weise ist es nicht erforderlich, freigegebene Sperren für Zeilen anzufordern, die gelesen wurden. Gleichzeitige Update- und Löschvorgänge durch Benutzer während Onlineindexvorgänge erfordern Speicherplatz für Versionsdatensätze in **tempdb**. Weitere Informationen finden Sie unter [Ausführen von Onlineindexvorgängen](perform-index-operations-online.md) .  
  
## <a name="related-tasks"></a>Related Tasks  
 [Beispiel für den zum Speichern eines Indexes belegten Speicherplatz](index-disk-space-example.md)  
  
 [Transaktionsprotokollspeicherplatz für Indexvorgänge](transaction-log-disk-space-for-index-operations.md)  
  
 [Schätzen der Größe einer Tabelle](../databases/estimate-the-size-of-a-table.md)  
  
 [Schätzen der Größe eines gruppierten Indexes](../databases/estimate-the-size-of-a-clustered-index.md)  
  
 [Schätzen der Größe eines nicht gruppierten Index](../databases/estimate-the-size-of-a-nonclustered-index.md)  
  
 [Schätzen der Größe eines Heaps](../databases/estimate-the-size-of-a-heap.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)  
  
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [Angeben des Füllfaktors für einen Index](specify-fill-factor-for-an-index.md)  
  
 [Neuorganisieren und Neuerstellen von Indizes](indexes.md)  
  
  
