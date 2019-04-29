---
title: Isolieren von Leistungsproblemen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e700f5178a3520fe83f4d896662a8741aa166b9a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150907"
---
# <a name="isolate-performance-problems"></a>Isolieren von Leistungsproblemen
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
  
 [Identifizieren von Engpässen](identify-bottlenecks.md)  
  
 [Überwachen der Speicherauslastung](../performance-monitor/monitor-memory-usage.md)  
  
  
