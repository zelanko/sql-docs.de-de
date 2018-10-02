---
title: Überwachen (Replikation) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d3e1b64c1c03a1e81fa83983427efbb60a399418
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810938"
---
# <a name="monitoring-replication"></a>Überwachen (Replikation)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Überwachung einer Replikationstopologie ist ein wichtiger Aspekt bei der Bereitstellung der Replikation. Da die Replikationsaktivität verteilt ist, ist es außerordentlich wichtig, die Aktivität und den Status auf allen an der Replikation beteiligten Computern nachzuverfolgen. Zum Überwachen der Replikation stehen die folgenden Tools zur Verfügung:  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Replikationsmonitor  
  
     Der Replikationsmonitor ist das wichtigste Tool für die Überwachung der Replikation. Es bietet eine verlegerfokussierte Sicht auf die gesamte Replikationsaktivität. Weitere Informationen finden Sie unter [Monitoring Replication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] bietet Zugriff auf den Replikationsmonitor. Darüber hinaus können Sie sich hier den aktuellen Status und die letzte Meldung anzeigen lassen, die vom Protokolllese-Agent, Momentaufnahme-Agent, Merge-Agent bzw. Verteilungs-Agent protokolliert wurde. Außerdem können Sie hier auch alle diese Agents starten und beenden. Weitere Informationen finden Sie unter [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] und Replikationsverwaltungsobjekte (RMO)  
  
     Dank beider Schnittstellen können Sie alle Replikationstypen vom Verteiler aus überwachen. Bei Mergereplikationen haben Sie außerdem die Möglichkeit, die Replikation vom Abonnenten aus zu überwachen.  
  
-   Warnungen für Replikations-Agentereignisse  
  
     Die Replikation bietet eine Reihe vordefinierter Warnungen für Replikations-Agentereignisse. Darüber hinaus können Sie bei Bedarf auch zusätzliche Warnungen erstellen. Warnungen können verwendet werden, um eine automatische Antwort auf ein Ereignis auszulösen und/oder einen Administrator zu benachrichtigen. Weitere Informationen finden Sie unter [Verwenden von Warnungen für Replikations-Agentereignisse](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md).  
  
-   Systemmonitor  
  
     Mit dem Systemmonitor kann die Leistung überwacht werden. Er stellt eine Reihe von Zählern für die Replikation bereit. Weitere Informationen finden Sie unter [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwaltung &#40;Replikation&#41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Best Practices for Replication Administration](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Überwachen der Replikation](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
