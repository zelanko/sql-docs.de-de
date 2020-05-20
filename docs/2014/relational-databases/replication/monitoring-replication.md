---
title: Übersicht über den Replikationsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 615582b2d961f87a2d3df151175d7bd5d06e305f
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000390"
---
# <a name="monitoring-replication"></a>Überwachen (Replikation)
  Die Überwachung einer Replikationstopologie ist ein wichtiger Aspekt bei der Bereitstellung der Replikation. Da die Replikationsaktivität verteilt ist, ist es außerordentlich wichtig, die Aktivität und den Status auf allen an der Replikation beteiligten Computern nachzuverfolgen. Zum Überwachen der Replikation stehen die folgenden Tools zur Verfügung:  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)][!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]Replikations Monitor  
  
     Der Replikationsmonitor ist das wichtigste Tool für die Überwachung der Replikation. Es bietet eine verlegerfokussierte Sicht auf die gesamte Replikationsaktivität. Weitere Informationen finden Sie unter [Überwachen der Leistung mit dem Replikations Monitor](monitor/monitor-performance-with-replication-monitor.md).  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] bietet Zugriff auf den Replikationsmonitor. Darüber hinaus können Sie sich hier den aktuellen Status und die letzte Meldung anzeigen lassen, die vom Protokolllese-Agent, Momentaufnahme-Agent, Merge-Agent bzw. Verteilungs-Agent protokolliert wurde. Außerdem können Sie hier auch alle diese Agents starten und beenden. Weitere Informationen finden Sie unter [Monitor Replication Agents](monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] und Replikationsverwaltungsobjekte (RMO)  
  
     Dank beider Schnittstellen können Sie alle Replikationstypen vom Verteiler aus überwachen. Bei Mergereplikationen haben Sie außerdem die Möglichkeit, die Replikation vom Abonnenten aus zu überwachen.  
  
-   Warnungen für Replikations-Agentereignisse  
  
     Die Replikation bietet eine Reihe vordefinierter Warnungen für Replikations-Agentereignisse. Darüber hinaus können Sie bei Bedarf auch zusätzliche Warnungen erstellen. Warnungen können verwendet werden, um eine automatische Antwort auf ein Ereignis auszulösen und/oder einen Administrator zu benachrichtigen. Weitere Informationen finden Sie unter [Verwenden von Warnungen für Replikations-Agentereignisse](agents/use-alerts-for-replication-agent-events.md).  
  
-   Systemmonitor  
  
     Mit dem Systemmonitor kann die Leistung überwacht werden. Er stellt eine Reihe von Zählern für die Replikation bereit. Weitere Informationen finden Sie unter [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [FAQ zur Replikation](administration/frequently-asked-questions-for-replication-administrators.md)   
 [Bewährte Methoden für die Replikations Verwaltung](administration/best-practices-for-replication-administration.md)   

  
  
