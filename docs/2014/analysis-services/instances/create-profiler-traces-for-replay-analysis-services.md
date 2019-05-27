---
title: Erstellen von Profiler-Ablaufverfolgungen für Replay (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- replaying queries
- replaying discovers
- events [Analysis Services]
- replaying commands
- Profiler [SQL Server Profiler], Analysis Services
- performance [Analysis Services], replays
- traces [Analysis Services]
ms.assetid: 93b2fc46-7cfb-4ab5-abeb-1475a7d6f0f2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc494fa63064d5c48c94e44cb91db5b1fe0f988d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080135"
---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>Erstellen von Profilerablaufverfolgungen für Replay (Analysis Services)
  Für die Wiedergabe von Abfragen, Ermittlungen und Befehlen, die von Benutzern an [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] die erforderlichen Ereignisse sammeln. Um die Sammlung dieser Ereignisse zu initiieren, müssen auf der Registerkarte **Ereignisauswahl** des Dialogfelds **Ablaufverfolgungseigenschaften** geeignete Ereignisklassen ausgewählt werden. Wenn z. B. die Query Begin-Ereignisklasse ausgewählt ist, werden Ereignisse mit Abfragen gesammelt und für die Wiedergabe verwendet. Die Ablaufverfolgungsdatei enthält außerdem ausreichende Informationen, um die Wiedergabe von Servertransaktionen in einer verteilten Umgebung in der ursprünglichen Abfolge von Transaktionen zu unterstützen.  
  
## <a name="replay-for-queries"></a>Wiedergabe für Abfragen  
 Zur Wiedergabe von Abfragen muss [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] die folgenden Ereignisse erfassen:  
  
-   „Audit Login“-Ereignisklasse mit allen zugehörigen Datenspalten. Diese Ereignisklasse stellt Informationen zu den angemeldeten Benutzern und zu den Sitzungseinstellungen bereit. Die Serverprozess-ID (SPID) verweist auf die betreffende Benutzersitzung. Weitere Informationen finden Sie unter [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).  
  
-   „Query Begin“-Ereignisklasse mit allen zugehörigen Datenspalten. Diese Ereignisklasse stellt Informationen zu der an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]gesendeten Abfrage bereit. Die Event Subclass-Spalte stellt Informationen zum Typ der Abfrage bereit. Der eigentliche Text der Abfrage wird in der TextData-Spalte bereitgestellt. Die RequestParameters-Spalte stellt die Parameter für parametrisierte Abfragen bereit, und die RequestProperties-Spalte stellt die Eigenschaften einer XMLA-Anforderung (XML for Analysis) bereit. Weitere Informationen finden Sie unter [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).  
  
-   „Query End“-Ereignisklasse mit allen zugehörigen Datenspalten. Diese Ereignisklasse überprüft den Status der Abfrageausführung. Weitere Informationen finden Sie unter [Queries Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/queries-events-data-columns).  
  
## <a name="replay-for-discovers"></a>Wiedergabe für Ermittlungen  
 Zur Wiedergabe von Ermittlungen muss [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] die folgenden Ereignisse erfassen:  
  
-   „Audit Login“-Ereignisklasse mit allen zugehörigen Datenspalten. Diese Ereignisklasse stellt Informationen zu den angemeldeten Benutzern und zu den Sitzungseinstellungen bereit. Die SPID (Serverprozess-ID) stellt die betreffende Benutzersitzung bereit. Weitere Informationen finden Sie unter [Security Audit Data Columns](https://docs.microsoft.com/bi-reference/trace-events/security-audit-data-columns).  
  
-   „Discover Begin“-Ereignisklasse mit allen zugehörigen Datenspalten. Die TextData-Spalte stellt die \<RequestType > Teil die Discover-Anforderung, und die RequestProperties-Spalte stellt die \<Eigenschaften >-Teil der ermittlungsanforderung. Der Ermittlungstyp wird in der EventSubclass-Spalte bereitgestellt. Weitere Informationen finden Sie unter [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).  
  
-   „Discover End“-Ereignisklasse mit allen zugehörigen Datenspalten. Diese Ereignisklasse überprüft den Status der Ermittlungsanforderung. Weitere Informationen finden Sie unter [Discover Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/discover-events-data-columns).  
  
## <a name="replay-for-commands"></a>Wiedergabe für Befehle  
 Zur Wiedergabe von Befehlen muss [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] die folgenden Ereignisse erfassen:  
  
-   „Command Begin“-Ereignisklasse mit allen zugehörigen Datenspalten. Die TextData-Spalte stellt die Befehlsdetails bereit, z.B. den Prozesstyp, die Datenbank-ID und die Cube-ID. Die RequestParameters-Spalte stellt die Parameter für parametrisierte Befehle bereit, und die RequestProperties-Spalte stellt die Eigenschaften einer XMLA-Anforderung bereit. Weitere Informationen finden Sie unter [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).  
  
-   „Command End“-Ereignisklasse mit allen zugehörigen Datenspalten. Diese Ereignisklasse überprüft den Status des Befehls. Weitere Informationen finden Sie unter [Command Events Data Columns](https://docs.microsoft.com/bi-reference/trace-events/command-events-data-columns).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Ablaufverfolgungsereignisse](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)   
 [Einführung in die Überwachung von Analysis Services mit SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  
