---
title: Ausführungspläne | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server]
- execution plans [SQL Server]
- query execution plans
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753f
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 9bf75c2d176c4ea2c596f29f1ddda910e794ae12
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68232017"
---
# <a name="execution-plans"></a>Ausführungspläne
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Um Abfragen ausführen zu können, muss die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Anweisung analysieren, um die effizienteste Methode für den Zugriff auf die erforderlichen Daten zu ermitteln. Diese Analyse wird von einer Komponente verarbeitet, die als „Abfrageoptimierer“ bezeichnet wird. Die Eingaben für den Abfrageoptimierer bestehen aus der Abfrage, dem Datenbankschema (Tabellen- und Indexdefinitionen) und den Datenbankstatistiken. Die Ausgabe des Abfrageoptimierers ist ein Abfrageausführungsplan, der manchmal auch als Abfrageplan oder einfach nur als Ausführungsplan bezeichnet wird.   

In einem Abfrageausführungsplan wird Folgendes definiert: 

* Die Reihenfolge des Zugriffs auf die Quelltabellen.  
  In der Regel gibt es viele Abfolgen, in denen der Datenbankserver auf die Basistabellen zugreifen kann, um das Resultset zu erstellen. Wenn eine `SELECT`-Anweisung z.B. auf drei Tabellen verweist, könnte der Datenbankserver zuerst auf `TableA` zugreifen, dann die Daten aus `TableA` verwenden, um die entsprechenden Zeilen aus `TableB` zu extrahieren, und dann die Daten aus `TableB` verwenden, um Daten aus `TableC` zu extrahieren. Die anderen Abfolgen, in denen der Datenbankserver auf die Tabellen zugreifen kann, lauten:  
  `TableC`, `TableB`, `TableA`oder  
  `TableB`, `TableA`, `TableC`oder  
  `TableB`, `TableC`, `TableA`oder  
  `TableC`, `TableA`, `TableB`  

* Die Methoden, die verwendet werden, um Daten aus den einzelnen Tabellen zu extrahieren.  
  Für den Zugriff auf die Daten in den einzelnen Tabellen gibt es in der Regel unterschiedliche Methoden. Wenn nur wenige Zeilen mit bestimmten Schlüsselwerten erforderlich sind, kann der Datenbankserver einen Index verwenden. Wenn alle Zeilen der Tabelle erforderlich sind, kann der Datenbankserver die Indizes übergehen und einen Tabellenscan ausführen. Wenn alle Zeilen einer Tabelle erforderlich sind, die Tabelle jedoch über einen Index verfügt, dessen Schlüsselspalten in einer `ORDER BY`-Klausel verwendet werden, kann durch die Durchführung eines Indexscans anstelle eines Tabellenscans eine andere Sortierung des Resultsets gespeichert werden. Wenn es sich um eine sehr kleine Tabelle handelt, können Tabellenscans die effizienteste Methode für fast alle Zugriffe auf die Tabelle darstellen.

> [!TIP]
> Weitere Informationen zur Abfrageverarbeitung und zu Abfrageausführungsplänen finden Sie im [Handbuch zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md).

## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Profilerstellungsinfrastruktur für Abfragen](../../relational-databases/performance/query-profiling-infrastructure.md)  
  
-   [Anzeigen und Speichern von Ausführungsplänen](../../relational-databases/performance/display-and-save-execution-plans.md)  
  
-   [Vergleichen und Analysieren von Ausführungsplänen](../../relational-databases/performance/compare-and-analyze-execution-plans.md)  

-   [Planhinweislisten](../../relational-databases/performance/plan-guides.md)  

## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Tools für die Leistungsüberwachung und -optimierung](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Leitfaden zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md)    
 [Live-Abfragestatistik](../../relational-databases/performance/live-query-statistics.md)     
 [Aktivitätsmonitor](../../relational-databases/performance-monitor/activity-monitor.md)     
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [Ablaufverfolgungsflags](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [Referenz zu logischen und physischen Showplanoperatoren](../../relational-databases/showplan-logical-and-physical-operators-reference.md)
