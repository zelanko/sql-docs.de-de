---
title: Starten und Beenden eines Replikations-Agents (SSMS)
description: Hier erfahren Sie, wie Sie einen Replikations-Agent in SQL Server Management Studio und im Replikationsmonitor beenden und starten.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: f578311d9daa9e54830ad5aa8330fc8bc2c7ac71
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76288087"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a>Starten und Beenden eines Replikations-Agents (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Starten oder beenden Sie Agents in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder im Replikationsmonitor über den Ordner **Aufträge** oder den Ordner **Replikation**. Starten oder beenden Sie die folgenden Agents und Aufträge:  
  
-   Momentaufnahme-Agent, der von allen Veröffentlichungen verwendet wird.  
  
-   Protokolllese-Agent, der von allen Transaktionsveröffentlichungen verwendet wird.  
  
-   Warteschlangenlese-Agent, der von Transaktionsveröffentlichungen verwendet wird, die für Abonnements mit verzögertem Update über eine Warteschlange aktiviert wurden.  
  
-   Verteilungs-Agent, der Abonnements für Transaktions- und Momentaufnahmeveröffentlichungen synchronisiert.  
  
-   Merge-Agent, der Abonnements für Mergeveröffentlichungen synchronisiert.  
  
-   Aufträge zur Replikationswartung.  
  
 Weitere Informationen zum Starten des Merge-Agents und des Verteilungs-Agents finden Sie unter [Synchronisieren eines Pushabonnements](../../../relational-databases/replication/synchronize-a-push-subscription.md) und [Synchronisieren eines Pullabonnements](../../../relational-databases/replication/synchronize-a-pull-subscription.md). Weitere Informationen zu Wartungsaufträgen finden Sie unter [Ausführen von Aufträgen zur Replikationswartung &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a>So starten oder beenden Sie einen Momentaufnahme-Agent oder Protokolllese-Agent in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten und den Ordner **Replikation** .  
  
2.  Erweitern Sie den Ordner **Lokale Veröffentlichungen** , und klicken Sie mit der rechten Maustaste auf eine Veröffentlichung.  
  
3.  Klicken Sie auf **Status des Momentaufnahme-Agents anzeigen** oder **Status des Protokolllese-Agents anzeigen**.  
  
4.  Klicken Sie auf **Starten** oder **Beenden**.  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a>So starten oder beenden Sie einen Warteschlangenlese-Agent in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verteiler her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **SQL Server-Agent** und anschließend den Ordner **Aufträge** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Auftrag für den Agent, und klicken Sie dann auf **Auftrag starten** oder **Auftrag beenden**. Der Name des Auftrags für den Warteschlangenlese-Agent hat das Format **[\<Distributor>].\<<integer>** .  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a>So starten oder beenden Sie einen Momentaufnahme-Agent, Protokolllese-Agent oder Warteschlangenlese-Agent im Replikations-Monitor  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.  
  
2.  Klicken Sie auf die Registerkarte **Agents** .  
  
3.  Klicken Sie mit der rechten Maustaste auf einen Agent, und klicken Sie dann auf **Agent starten** oder **Agent beenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Ausführbare Konzepte für den Replikations-Agent](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Übersicht über Replikations-Agents](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
