---
title: Versetzen einer Replikationstopologie in einen inaktiven Status (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 59c179c81c1b6b60787603f5953b85e583668c80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63161717"
---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a>Versetzen einer Replikationstopologie in einen inaktiven Status (Replikationsprogrammierung mit Transact-SQL)
  Um das System*in einen inaktiven Status zu versetzen* , beenden Sie alle Aktivitäten in veröffentlichten Tabellen an allen Knoten, und stellen Sie sicher, dass jeder Knoten alle Änderungen aller anderen Knoten erhalten hat. In diesem Thema wird erläutert, wie eine Replikationstopologie in einen inaktiven Status versetzt wird. Dies ist für eine Reihe von Verwaltungsaufgaben erforderlich. Zudem finden Sie hier Informationen dazu, wie Sie überprüfen können, ob ein Knoten alle Änderungen anderer Knoten erhalten hat.  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a>So versetzen Sie eine Transaktionsreplikationstopologie mit schreibgeschützten Abonnements in einen inaktiven Status  
  
1.  Beenden Sie die Aktivitäten an allen veröffentlichten Tabellen auf dem Verleger.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql) aus.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)aus.  
  
4.  Stellen Sie sicher, dass jeder Abonnent das Überwachungstoken erhalten hat.  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a>So versetzen Sie eine Transaktionsreplikationstopologie mit aktualisierbaren Abonnements in einen inaktiven Status  
  
1.  Beenden Sie die Aktivitäten an allen veröffentlichten Tabellen auf dem Verleger und auf allen Abonnenten.  
  
2.  Wenn Abonnenten Abonnements mit verzögertem Update über eine Warteschlange verwenden:  
  
    1.  Wenn der Warteschlangenlese-Agent nicht im fortlaufenden Modus ausgeführt wird, führen Sie den Agent aus. Weitere Informationen zum Ausführen von Agents finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../concepts/replication-agent-executables-concepts.md) oder [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    2.  Führen Sie auf jedem Abonnenten [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) aus, um zu überprüfen, ob die Warteschlange leer ist.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)aus.  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)aus.  
  
5.  Stellen Sie sicher, dass jeder Abonnent das Überwachungstoken erhalten hat.  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a>So versetzen Sie eine Peer-zu-Peer-Transaktionsreplikationstopologie in einen inaktiven Status  
  
1.  Beenden Sie die Aktivitäten an allen veröffentlichten Tabellen in allen Knoten.  
  
2.  Führen Sie für jede Veröffentlichungsdatenbank in der Topologie [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) aus.  
  
3.  Wenn der Protokolllese-Agent oder der Verteilungs-Agent nicht im fortlaufenden Modus ausgeführt wird, führen Sie den Agent aus. Der Protokolllese-Agent muss vor dem Verteilungs-Agent gestartet werden. Weitere Informationen zum Ausführen von Agents finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../concepts/replication-agent-executables-concepts.md) oder [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
4.  Führen Sie für jede Veröffentlichungsdatenbank in der Topologie [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) aus. Stellen Sie sicher, dass das Resultset Antworten von allen anderen Knoten enthält.  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a>So stellen Sie sicher, dass ein Peer-zu-Peer-Knoten alle vorherigen Änderungen erhalten hat  
  
1.  Führen Sie für die Veröffentlichungsdatenbank an dem überprüften Knoten [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) aus.  
  
2.  Wenn der Protokolllese-Agent oder der Verteilungs-Agent nicht im fortlaufenden Modus ausgeführt wird, führen Sie den Agent aus. Der Protokolllese-Agent muss vor dem Verteilungs-Agent gestartet werden. Weitere Informationen zum Ausführen von Agents finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../concepts/replication-agent-executables-concepts.md) oder [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
3.  Führen Sie für die Veröffentlichungsdatenbank an dem überprüften Knoten [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) aus. Stellen Sie sicher, dass das Resultset Antworten von allen anderen Knoten enthält.  
  
### <a name="to-quiesce-a-merge-replication-topology"></a>So versetzen Sie eine Mergereplikationstopologie in einen inaktiven Status  
  
1.  Beenden Sie die Aktivitäten an allen veröffentlichten Tabellen auf dem Verleger und auf allen Abonnenten.  
  
2.  Führen Sie den Merge-Agent für jedes Abonnement zweimal aus: Synchronisieren Sie alle Abonnements einmal, und synchronisieren Sie dann jedes Abonnement ein zweites Mal. So kann sichergestellt werden, dass alle Änderungen auf allen Knoten repliziert werden. Weitere Informationen zum Ausführen von Agents finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../concepts/replication-agent-executables-concepts.md) oder [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
    > [!NOTE]  
    >  Wenn während der Synchronisierung Konflikte auftreten, werden durch die Konfliktlösung angeforderte Änderungen möglicherweise nicht an alle Knoten weitergegeben, nachdem der Merge-Agent zweimal ausgeführt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten einer Peer-zu-Peer-Topologie &#40;Replikationsprogrammierung mit Transact-SQL&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
