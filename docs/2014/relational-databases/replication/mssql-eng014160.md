---
title: MSSQL_ENG014160 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 42f0b6894bac639d287eb62f9870d7bfd6daba3a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62864845"
---
# <a name="mssqleng014160"></a>MSSQL_ENG014160
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14160|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Schwellenwert [%s:%s] für die [%s]-Veröffentlichung wurde festgelegt. Mindestens ein Abonnement für diese Veröffentlichung ist abgelaufen.|  
  
## <a name="explanation"></a>Erklärung  
 Mit Replikationen können Sie Warnungen für verschiedene Bedingungen aktivieren. Dazu zählt das bevorstehende Ablaufdatum des Abonnements. Abonnements können ablaufen, wenn sie nicht innerhalb einer angegebenen *Beibehaltungsdauer*synchronisiert werden. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 Wenn Sie mithilfe des Replikationsmonitors oder mit [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)eine Warnung aktivieren, geben Sie einen Schwellenwert an, mit dem bestimmt wird, wann eine Warnung ausgelöst wird. Wenn dieser Schwellenwert erreicht oder überschritten wird, wird im Replikationsmonitor eine Warnung angezeigt, und es wird ein Ereignis in das Windows-Ereignisprotokoll geschrieben. Durch das Erreichen eines Schwellenwerts kann zudem eine SQL Server-Agent-Warnung ausgelöst werden. Weitere Informationen finden Sie unter [Festlegen von Schwellenwerten und Warnungen im Replikationsmonitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) und [Programmgesteuertes Überwachen der Replikation](monitoring-replication.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Die Lösung für dieses Problem hängt von der Ursache für die Auslösung der Warnung ab:  
  
-   Wenn der Schwellenwert überschritten wurde, das Abonnement jedoch noch nicht abgelaufen ist, synchronisieren Sie das Abonnement. Weitere Informationen finden Sie unter [Synchronisieren von Daten](synchronize-data.md).  
  
-   Wenn der Agent ausgeführt wurde, die Änderungen jedoch nicht ordnungsgemäß repliziert wurden, kann das Abonnement aus diesem Grund ablaufen. Stellen Sie für die Transaktionsreplikation sicher, dass der Verteilungs-Agent sowie der Protokolllese-Agent ausgeführt werden. Stellen Sie für die Mergereplikation sicher, dass der Merge-Agent ausgeführt wird. Weitere Informationen zum Starten dieser Agents finden Sie unter [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) und [Ausführbare Konzepte für die Programmierung von Replikations-Agents](concepts/replication-agent-executables-concepts.md).  
  
-   Wenn das Abonnement abgelaufen ist, muss es erneut initialisiert werden oder verworfen und neu erstellt werden. Dies richtet sich nach der Art des Abonnements und danach, wie lange es schon abgelaufen war. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
