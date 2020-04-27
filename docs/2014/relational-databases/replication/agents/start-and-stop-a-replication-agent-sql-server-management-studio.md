---
title: Starten und Beenden eines Replikations-Agents (SQL Server Management Studio) | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66be53c7b4c145f361c49c0e1611fa2942005ae5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63192464"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a>Starten und Beenden eines Replikations-Agents (SQL Server Management Studio)
  Starten oder beenden Sie Agents in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder im Replikationsmonitor über den Ordner **Aufträge** oder den Ordner **Replikation**. Starten oder beenden Sie die folgenden Agents und Aufträge:  
  
-   Momentaufnahme-Agent, der von allen Veröffentlichungen verwendet wird.  
  
-   Protokolllese-Agent, der von allen Transaktionsveröffentlichungen verwendet wird.  
  
-   Warteschlangenlese-Agent, der von Transaktionsveröffentlichungen verwendet wird, die für Abonnements mit verzögertem Update über eine Warteschlange aktiviert wurden.  
  
-   Verteilungs-Agent, der Abonnements für Transaktions- und Momentaufnahmeveröffentlichungen synchronisiert.  
  
-   Merge-Agent, der Abonnements für Mergeveröffentlichungen synchronisiert.  
  
-   Aufträge zur Replikationswartung.  
  
 Weitere Informationen zum Starten des Merge-Agents und des Verteilungs-Agents finden Sie unter [Synchronisieren eines Pushabonnements](../synchronize-a-push-subscription.md) und [Synchronisieren eines Pullabonnements](../synchronize-a-pull-subscription.md). Weitere Informationen zu Wartungsaufträgen finden Sie unter [Ausführen von Aufträgen zur Replikationswartung &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md).  
  
 Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../monitor/start-the-replication-monitor.md).  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a>So starten oder beenden Sie einen Momentaufnahme-Agent oder Protokolllese-Agent in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten und den Ordner **Replikation** .  
  
2.  Erweitern Sie den Ordner **Lokale Veröffentlichungen** , und klicken Sie mit der rechten Maustaste auf eine Veröffentlichung.  
  
3.  Klicken Sie auf **Status des Momentaufnahme-Agents anzeigen** oder **Status des Protokolllese-Agents anzeigen**.  
  
4.  Klicken Sie auf **Starten** oder **Beenden**.  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a>So starten oder beenden Sie einen Warteschlangenlese-Agent in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Auftrag für den Agent, und klicken Sie dann auf **Auftrag starten** oder **Auftrag beenden**. Der Name des Auftrags für den Warteschlangenlese-Agent hat das Format **[\<Distributor>].\< ganzzahlige>**.  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a>So starten oder beenden Sie einen Momentaufnahme-Agent, Protokolllese-Agent oder Warteschlangenlese-Agent im Replikations-Monitor  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Agents** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Agent, und klicken Sie dann auf **Agent starten** oder **Agent beenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachung der Replikation](../monitoring-replication.md)   
 [Ausführbare Konzepte für den Replikations-Agent](../concepts/replication-agent-executables-concepts.md)   
 [Replikations-Agents (Übersicht)](replication-agents-overview.md)  
  
  
