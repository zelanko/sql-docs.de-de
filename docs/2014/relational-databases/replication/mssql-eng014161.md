---
title: MSSQL_ENG014161 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014161 error
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 19414c81a8f09250a80d38ac1b065afd14f51ac1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137170"
---
# <a name="mssqleng014161"></a>MSSQL_ENG014161
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14161|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Schwellenwert [%s:%s] für die [%s]-Veröffentlichung wurde festgelegt. Stellen Sie sicher, dass der Protokolllese-Agent und der Verteilungs-Agent ausgeführt werden und die Latenzzeitanforderung erfüllen können.|  
  
## <a name="explanation"></a>Erklärung  
 Mit Replikationen können Sie Warnungen für verschiedene Bedingungen aktivieren. Dies schließt das Überschreiten einer angegebenen Latenzzeit für Transaktionsabonnements ein. Bei der Latenzzeit handelt es sich um die Zeitspanne zwischen dem Ausführen des Commit für eine Datenänderung auf dem Verleger und dem Ausführen des Commit für die entsprechende Änderung auf dem Abonnenten.  
  
 Wenn Sie mithilfe des Replikationsmonitors oder mit [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)eine Warnung aktivieren, geben Sie einen Schwellenwert an, mit dem bestimmt wird, wann eine Warnung ausgelöst wird. Wenn dieser Schwellenwert erreicht oder überschritten wird, wird im Replikationsmonitor eine Warnung angezeigt, und es wird ein Ereignis in das Windows-Ereignisprotokoll geschrieben. Durch das Erreichen eines Schwellenwerts kann zudem eine SQL Server-Agent-Warnung ausgelöst werden. Weitere Informationen finden Sie unter [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) und [Programmgesteuertes Überwachen der Replikation](monitor/monitoring-replication-overview.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn für ein Abonnement der Schwellenwert einer Latenzzeit überschritten wird, müssen Sie ermitteln, ob im System ein Leistungsproblem vorliegt oder ob der Schwellenwert angepasst werden muss. Entwickeln Sie nach dem Konfigurieren der Replikation Grundwerte für die Leistung, mit denen Sie bestimmen können, wie die Replikation sich mit einer Arbeitsauslastung verhält, die typisch für Ihre Anwendungen und Topologie ist. Nehmen Sie die Latenzzeit in diese Grundwerte auf, damit Sie einen entsprechenden Schwellenwert festlegen können.  
  
 Wenn der Schwellenwert angemessen ist, jedoch überschritten wird, müssen Sie ermitteln, wo sich der Leistungsengpass im System befindet. Weitere Informationen zum Überwachen der Replikationsleistung und zur entsprechenden Problembehandlung finden Sie in den folgenden Themen:  
  
-   [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
