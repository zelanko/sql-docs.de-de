---
title: Statistiken für speicheroptimierte Tabellen | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e644766d-1d1c-43d7-83ff-8ccfe4f3af9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ae09d76c2642e23c56afcdd5ae4e1e468ef5883
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025769"
---
# <a name="statistics-for-memory-optimized-tables"></a>Statistiken für speicheroptimierte Tabellen
  Der Abfrageoptimierer verwendet Statistiken zu Spalten zum Erstellen von Abfrageplänen, die die Abfrageleistung verbessern. Die Statistiken werden aus den Tabellen in der Datenbank gesammelt und in den Datenbankmetadaten gespeichert.  
  
 Statistiken werden automatisch erstellt, sie können jedoch auch manuell erstellt werden. Beispielsweise werden Statistiken automatisch für Indexschlüsselspalten erstellt, wenn der Index erstellt wird. Weitere Informationen zum Erstellen von Statistiken finden Sie unter [Statistics](../statistics/statistics.md).  
  
 Tabellendaten ändern sich normalerweise mit der Zeit, wenn Zeilen eingefügt, aktualisiert und gelöscht werden. Dies bedeutet, dass Statistiken regelmäßig aktualisiert werden müssen. Standardmäßig werden Statistiken zu datenträgerbasierten Tabellen automatisch aktualisiert, wenn sie vom Abfrageoptimierer als möglicherweise veraltet eingestuft werden.  
  
 Statistiken für speicheroptimierte Tabellen werden nicht standardmäßig aktualisiert. Stattdessen müssen Sie diese manuell aktualisieren. Verwenden Sie [Update Statistics &#40;Transact-SQL-&#41;](/sql/t-sql/statements/update-statistics-transact-sql) für einzelne Spalten, Indizes oder Tabellen. Verwenden Sie [sp_updatestats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) , um die Statistiken für alle Benutzer-und internen Tabellen in der Datenbank zu aktualisieren.  
  
 Bei Verwendung von [CREATE STATISTICS &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-statistics-transact-sql) oder [Update Statistics &#40;Transact-SQL-&#41;](/sql/t-sql/statements/update-statistics-transact-sql)müssen Sie angeben, `NORECOMPUTE` dass die automatische Aktualisierung von Statistiken für Speicher optimierte Tabellen deaktiviert werden soll. Bei Datenträger basierten Tabellen werden [sp_updatestats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) nur Statistiken aktualisiert, wenn die Tabelle seit der letzten [sp_updatestats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)geändert wurde. Für Speicher optimierte Tabellen generiert [sp_updatestats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) immer aktualisierte Statistiken. [sp_updatestats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) ist eine gute Option für Speicher optimierte Tabellen. Andernfalls müssen Sie wissen, welche Tabellen bedeutende Änderungen aufweisen, damit Sie Statistiken einzeln aktualisieren können.  
  
 Statistiken können entweder generiert werden, indem Datenstichproben entnommen werden oder ein vollständiger Scan ausgeführt wird. Bei Statistiken aus Stichproben wird die Datenverteilung nur anhand einer Stichprobe der Tabellendaten geschätzt. Bei Statistiken auf Grundlage eines vollständigen Scans wird die gesamte Tabelle überprüft, um die Datenverteilung zu bestimmen. Während Statistiken, die auf einem vollständigen Scan basieren, normalerweise genauer sind, dauert die Berechnung länger. Aus Stichproben gewonnene Statistiken können schneller gesammelt werden.  
  
 Für datenträgerbasierte Tabellen werden standardmäßig auf Stichproben beruhende Statistiken verwendet. Speicheroptimierte Tabellen unterstützen nur Statistiken auf Grundlage vollständiger Scans. Bei Verwendung von [CREATE STATISTICS &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-statistics-transact-sql) oder [Update Statistics &#40;Transact-SQL-&#41;](/sql/t-sql/statements/update-statistics-transact-sql)müssen Sie die `FULLSCAN` Option für Speicher optimierte Tabellen angeben.  
  
 Zusätzliche Überlegungen zu Statistiken für speicheroptimierte Tabellen:  
  
-   Indizes für speicheroptimierten Tabellen werden mit der Tabelle erstellt. Die Statistiken zu den Indexschlüsselspalten werden erstellt, wenn die Tabelle leer ist. Daher müssen diese Statistiken aktualisiert werden, nachdem Daten in die Tabelle geladen wurden.  
  
-   Für systemintern kompilierte gespeicherte Prozeduren werden Ausführungspläne für Abfragen in der Prozedur optimiert, wenn die Prozedur kompiliert wird. Dies geschieht nur beim Erstellen der Prozedur und beim Neustart des Servers, nicht beim Aktualisieren der Statistiken. Daher müssen die Tabellen eine repräsentative Menge von Daten enthalten, und die Statistiken müssen auf dem aktuellen Stand sein, bevor die Prozeduren erstellt werden. (Systemintern kompilierte gespeicherte Prozeduren werden neu kompiliert, wenn die Datenbank offline und anschließend wieder online geschaltet oder der Server neu gestartet wird.)  
  
## <a name="guidelines-for-statistics-when-deploying-memory-optimized-tables"></a>Richtlinien für Statistiken beim Bereitstellen speicheroptimierter Tabellen  
 Um sicherzustellen, dass der Abfrageoptimierer beim Erstellen von Abfrageplänen über aktuelle Statistiken verfügt, führen Sie die folgenden fünf Schritte aus, um speicheroptimierte Tabellen bereitzustellen:  
  
1.  Erstellen Sie Tabellen und Indizes. Indizes werden inline in den `CREATE TABLE`-Anweisungen angegeben.  
  
2.  Laden Sie Daten in die Tabellen.  
  
3.  Aktualisieren Sie die Statistik zu den Tabellen.  
  
4.  Erstellen Sie gespeicherte Prozeduren, die auf die Tabellen zugreifen.  
  
5.  Führen Sie die Arbeitsauslastung aus, die eine Kombination aus systemintern kompilierten und interpretierten gespeicherten [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Prozeduren sowie Ad-hoc-Batches enthalten kann.  
  
 Indem Sie systemintern kompilierte gespeicherten Prozeduren erstellen, nachdem die Daten geladen und Statistiken aktualisiert wurden, wird sichergestellt, dass der Abfrageoptimierer über die für die speicheroptimierten Tabellen erforderlichen Statistiken verfügt. Damit liegen effiziente Abfragepläne vor, wenn die Prozedur kompiliert wird.  
  
## <a name="guidelines-for-maintaining-statistics-on-memory-optimized-tables"></a>Richtlinien zum Pflegen von Statistiken für speicheroptimierte Tabellen  
 Um die Statistiken auf dem aktuellen Stand zu halten, aktualisieren Sie die Statistiken für speicheroptimierte Tabellen regelmäßig.  
  
 Wenn sich Daten häufig ändern, sollten Sie auch die Statistik häufig aktualisieren. Aktualisieren Sie die Tabellenstatistik beispielsweise nach einem Batchupdate. Löschen Sie nach dem Aktualisieren der Statistiken systemintern kompilierte gespeicherte Prozeduren, und erstellen Sie sie neu, sodass sie von den aktualisierten Statistiken profitieren.  
  
 .  
  
 Aktualisieren Sie Statistiken nicht während der maximalen Arbeitsauslastung.  
  
 So aktualisieren Sie Statistiken:  
  
-   Verwenden [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zum [Erstellen eines Wartungsplans](../maintenance-plans/create-a-maintenance-plan.md) mit einem [Task "Statistiken aktualisieren](../maintenance-plans/update-statistics-task-maintenance-plan.md) "  
  
-   Sie können Statistiken auch über ein [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Skript aktualisieren, wie im Folgenden erläutert.  
  
 Zum Aktualisieren der Statistiken für eine einzelne Speicher optimierte Tabelle (*MySchema*. *MyTable*), führen Sie das folgende Skript aus:  
  
```  
UPDATE STATISTICS myschema.Mytable WITH FULLSCAN, NORECOMPUTE  
```  
  
 Führen Sie zum Aktualisieren der Statistiken für alle speicheroptimierten Tabellen in der aktuellen Datenbank das folgende Skript aus:  
  
```sql  
DECLARE @sql NVARCHAR(MAX) = N''  
  
SELECT @sql += N'  
   UPDATE STATISTICS ' + quotename(schema_name(schema_id)) + N'.' + quotename(name) + N' WITH FULLSCAN, NORECOMPUTE'  
FROM sys.tables WHERE is_memory_optimized=1  
  
EXEC sp_executesql @sql  
```  
  
 Um die Statistiken für alle Tabellen in der Datenbank zu aktualisieren, führen Sie [sp_updatestats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)aus.  
  
 Im folgenden Beispiel wird ausgegeben, wann die Statistiken für speicheroptimierte Tabellen zuletzt aktualisiert wurden. Anhand dieser Informationen können Sie entscheiden, ob die Statistiken aktualisiert werden müssen.  
  
```sql  
select t.object_id, t.name, sp.last_updated as 'stats_last_updated'  
from sys.tables t join sys.stats s on t.object_id=s.object_id cross apply sys.dm_db_stats_properties(t.object_id, s.stats_id) sp  
where t.is_memory_optimized=1  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speicheroptimierte Tabellen](memory-optimized-tables.md)  
  
  
