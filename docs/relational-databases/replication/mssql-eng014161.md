---
title: MSSQL_ENG014161 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014161 error
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 36d7a9fc5511069d06e4efc7479e43dfb2514977
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85721812"
---
# <a name="mssql_eng014161"></a>MSSQL_ENG014161
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14161|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Schwellenwert [%s:%s] für die [%s]-Veröffentlichung wurde festgelegt. Stellen Sie sicher, dass der Protokolllese-Agent und der Verteilungs-Agent ausgeführt werden und die Latenzzeitanforderung erfüllen können.|  
  
## <a name="explanation"></a>Erklärung  
 Mit Replikationen können Sie Warnungen für verschiedene Bedingungen aktivieren. Dies schließt das Überschreiten einer angegebenen Latenzzeit für Transaktionsabonnements ein. Bei der Latenzzeit handelt es sich um die Zeitspanne zwischen dem Ausführen des Commit für eine Datenänderung auf dem Verleger und dem Ausführen des Commit für die entsprechende Änderung auf dem Abonnenten.  
  
 Wenn Sie mithilfe des Replikationsmonitors oder mit [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md)eine Warnung aktivieren, geben Sie einen Schwellenwert an, mit dem bestimmt wird, wann eine Warnung ausgelöst wird. Wenn dieser Schwellenwert erreicht oder überschritten wird, wird im Replikationsmonitor eine Warnung angezeigt, und es wird ein Ereignis in das Windows-Ereignisprotokoll geschrieben. Durch das Erreichen eines Schwellenwerts kann zudem eine SQL Server-Agent-Warnung ausgelöst werden. Weitere Informationen finden Sie unter [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) und [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn für ein Abonnement der Schwellenwert einer Latenzzeit überschritten wird, müssen Sie ermitteln, ob im System ein Leistungsproblem vorliegt oder ob der Schwellenwert angepasst werden muss. Entwickeln Sie nach dem Konfigurieren der Replikation Grundwerte für die Leistung, mit denen Sie bestimmen können, wie die Replikation sich mit einer Arbeitsauslastung verhält, die typisch für Ihre Anwendungen und Topologie ist. Nehmen Sie die Latenzzeit in diese Grundwerte auf, damit Sie einen entsprechenden Schwellenwert festlegen können.  
  
 Wenn der Schwellenwert angemessen ist, jedoch überschritten wird, müssen Sie ermitteln, wo sich der Leistungsengpass im System befindet. Weitere Informationen zum Überwachen der Replikationsleistung und zur entsprechenden Problembehandlung finden Sie in den folgenden Themen:  
  
-   [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [Überwachen der Leistung mit dem Replikationsmonitor](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
