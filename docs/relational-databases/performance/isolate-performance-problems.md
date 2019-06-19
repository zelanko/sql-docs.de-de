---
title: Isolieren von Leistungsproblemen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c34186b0e10c66f6729933e5cc8d6b171d053fc1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62645084"
---
# <a name="isolate-performance-problems"></a>Isolieren von Leistungsproblemen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Häufig ist es effektiver, zur Isolierung von Leistungsproblemen bei Datenbanken mehrere [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tools oder Microsoft Windows-Tools gleichzeitig zu verwenden. So können Sie beispielsweise mithilfe der Funktion für den grafischen Ausführungsplan (auch Showplan genannt) Deadlocks in einer einzigen Abfrage erkennen. Einige andere Leistungsprobleme lassen sich wiederum einfacher ermitteln, indem Sie die Überwachungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows zusammen verwenden.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] kann für die Überwachung und Problembehandlung von Transact-SQL-Anweisungen und anwendungsbasierten Problemen verwendet werden. Mit dem Systemmonitor können Sie Hardwareprobleme und andere systembedingte Probleme überwachen.  
  
 Sie können die folgenden Bereiche zur Problembehandlung überwachen:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungsbatches, die von Benutzeranwendungen übermittelt wurden.  
  
-   Benutzeraktivität, z. B. Sperren oder Deadlocks.  
  
-   Hardwareaktivität, z. B. die Datenträgernutzung.  
  
 Mögliche Probleme sind:  
  
-   Fehler bei der Anwendungsentwicklung im Zusammenhang mit fehlerhaft geschriebenen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen.  
  
-   Hardwarefehler, z. B. Fehler im Zusammenhang mit den Datenträgern oder dem Netzwerk.  
  
-   Zu häufiges Blockieren aufgrund einer fehlerhaft entworfenen Datenbank.  
  
## <a name="tools-for-common-performance-problems"></a>Tools für häufig auftretende Leistungsprobleme  
 Genau so wichtig ist die sorgfältige Auswahl der Leistungsprobleme, die durch die einzelnen Tools überwacht oder optimiert werden sollen. Welches Tool und welcher Dienst geeignet sind, hängt von der Art des zu lösenden Leistungsproblems ab.  
  
 Die folgenden Themen enthalten Beschreibungen einer Vielzahl von Tools zur Überwachung und Optimierung sowie der durch sie feststellbaren Probleme.  
  
 [Identifizieren von Engpässen](../../relational-databases/performance/identify-bottlenecks.md)  
  
 [Überwachen der Speicherauslastung](../../relational-databases/performance-monitor/monitor-memory-usage.md)  
  
  
