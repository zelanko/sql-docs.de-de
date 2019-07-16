---
title: Erstellen von Profiler-Ablaufverfolgungen für Replay (Analysis Services) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 36ae9263a6ce5f92e144b34c232dd1c096a6609d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181876"
---
# <a name="create-profiler-traces-for-replay-analysis-services"></a>Erstellen von Profilerablaufverfolgungen für Replay (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

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
 [Einführung in die Überwachung von Analysis Services mit SQL Server Profiler](../../analysis-services/instances/introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)  
  
  
