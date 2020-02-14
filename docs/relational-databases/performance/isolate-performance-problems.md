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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 643551201567ae10980c1fe3d5efca95a1bc9ded
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68051967"
---
# <a name="isolate-performance-problems"></a>Isolieren von Leistungsproblemen
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In den meisten Fällen ist es effektiver, mehrere [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]- oder Microsoft Windows-Tools gleichzeitig zu verwenden, um Leistungsprobleme mit der Datenbank zu isolieren, anstatt immer nur ein Tool zu verwenden. So können Sie beispielsweise mithilfe der Funktion für den grafischen Ausführungsplan (auch Showplan genannt) Deadlocks in einer einzigen Abfrage erkennen. Einige andere Leistungsprobleme lassen sich wiederum einfacher ermitteln, indem Sie die Überwachungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows zusammen verwenden.  
  
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
  
  
