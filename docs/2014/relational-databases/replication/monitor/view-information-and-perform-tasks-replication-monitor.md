---
title: Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing publication information
- publications [SQL Server replication], viewing information
- publications [SQL Server replication], Replication Monitor tasks
ms.assetid: 92e28a07-d6a7-461b-a0b3-bd9bc6afcbe5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 400db44d053caf131ef13947adbd0154875995cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62667131"
---
# <a name="view-information-and-perform-tasks-using-replication-monitor"></a>Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor
Im Replikationsmonitor finden Sie mehrere Registerkarten und Optionen, mit denen Sie Informationen anzeigen und verschiedene Aufgaben ausführen können. In diesem Artikel werden unterschiedliche Informationen und Aufgaben beschrieben, die Sie mithilfe des Replikationsmonitor aufrufen bzw. ausführen können.

## <a name="for-a-publication"></a>Veröffentlichungen

### <a name="view-information"></a>Anzeigen von Informationen

  Der Replikationsmonitor stellt die folgenden Registerkarten mit Informationen zur ausgewählten Veröffentlichung bereit:  
  
-   **Alle Abonnements** -auf dieser Registerkarte werden Informationen zu allen Abonnements für die ausgewählte Veröffentlichung angezeigt.  
  
-   **Agents** -auf dieser Registerkarte zeigt Informationen zu allen Agents, die von einer Veröffentlichung verwendet wird:  
  
    -   Momentaufnahme-Agent, der von allen Veröffentlichungen verwendet wird.    
    -   Protokolllese-Agent, der von allen Transaktionsveröffentlichungen verwendet wird.    
    -   Dem Warteschlangenlese-Agent, der von Transaktionsveröffentlichungen verwendet wird, die Abonnements mit verzögertem Update über eine Warteschlange aufweisen.  
  
-   **Warnungen** (bei Verteilern, auf denen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird)   
    -   Auf dieser Registerkarte können Sie Warnungen für Agents angeben.  
  
-   **Überwachungstoken** (nur bei der Transaktionsreplikation für Verteiler, auf denen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird)  
  
     Über diese Registerkarte können Sie die Latenzzeit messen, d. h. die Zeitspanne zwischen dem Ausführen des Commit für eine Transaktion auf dem Verleger und dem Ausführen des Commit für die entsprechende Aktion auf dem Abonnenten.  
  
 Weitere Informationen zu den Optionen der einzelnen Registerkarten finden Sie, wenn Sie auf die Registerkarte im rechten Bereich und dann auf **Hilfe** auf der Menüleiste klicken. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](start-the-replication-monitor.md).  
  
### <a name="perform-tasks"></a>Ausführen von Aufgaben
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.    
2.  Zum Anzeigen und Ändern von Veröffentlichungseigenschaften klicken Sie mit der rechten Maustaste auf die Veröffentlichung, und klicken Sie dann auf **Eigenschaften**.    
3.  Um Informationen zu Abonnements anzuzeigen, klicken Sie auf die Registerkarte **Alle Abonnements** .  
  
     Zum Anzeigen und Ändern von Abonnementeigenschaften klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Eigenschaften**. Sie können auf dieser Registerkarte auch auf detailliertere Informationen zugreifen und Aufgaben ausführen. Weitere Informationen finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](view-information-and-perform-tasks-replication-monitor.md).  
  
4.  Um Informationen zu Agents anzuzeigen, klicken Sie auf die Registerkarte **Agents** . Sie können auf dieser Registerkarte auch auf detailliertere Informationen zugreifen und Aufgaben ausführen. Weitere Informationen finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](view-information-and-perform-tasks-replication-monitor.md).    
5.  Um Informationen zu Agentwarnungen und Schwellenwerten anzuzeigen, klicken Sie auf die Registerkarte **Warnungen** . Weitere Informationen finden Sie unter [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).   
6.  Um Informationen zu Überwachungstoken anzuzeigen, klicken Sie auf die Registerkarte **Überwachungstoken** . Weitere Informationen zu Überwachungstoken finden Sie unter [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## <a name="for-a-publisher"></a>Verleger
  Der Replikationsmonitor bietet folgende Registerkarten, auf denen Informationen zu dem ausgewählten Verleger angezeigt werden:  
  
-   **Veröffentlichungen** -auf dieser Registerkarte werden Informationen zu allen Veröffentlichungen auf dem ausgewählten Verleger angezeigt.  
  
-   **Überwachungsliste für Abonnements** -diese Registerkarte dient zum Anzeigen von Informationen zu Abonnements von allen Veröffentlichungen auf dem ausgewählten Verleger, die Fehler, Warnungen oder die vorhandenen Leistung aufweisen. Bei Verteilern, auf denen Versionen vor [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ausgeführt werden, wird diese Registerkarte nicht angezeigt.  
  
-   **Agents** Registerkarte - auf dieser Registerkarte zeigt ausführliche Informationen zu den Agents und Aufträge, die verwendet wird, werden von allen Typen der Replikation. Über diese Registerkarte können Sie zudem alle Agents und Aufträge starten und beenden.  
  
 Wenn Sie weitere Informationen zu den Optionen auf den einzelnen Registerkarten anzeigen möchten, klicken Sie im rechten Bereich auf die Registerkarte, und klicken Sie anschließend auf der Menüleiste auf **Hilfe** . Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](start-the-replication-monitor.md).  
  
### <a name="view-information-and-perform-tasks"></a>Anzeigen von Informationen und Ausführen von Aufgaben
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, und klicken Sie dann auf einen Verleger.    
2.  Um Informationen zu allen Veröffentlichungen anzuzeigen, klicken Sie auf die Registerkarte **Veröffentlichungen** .    
3.  Um Informationen zu Abonnements anzuzeigen, klicken Sie auf die Registerkarte **Überwachungsliste für Abonnements** . Über diese Registerkarte können Sie auch auf ausführliche Informationen zugreifen und Aufgaben ausführen:    
    -   Wenn Sie detaillierte Informationen zum Agent angezeigt bekommen möchten, der dem jeweiligen Abonnement zugeordnet ist, klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Details anzeigen**.    
    -   Wenn Sie die Eigenschaften eines Abonnements anzeigen möchten, klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie anschließend auf **Eigenschaften**.    
    -   Wenn Sie ein Pushabonnement synchronisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Synchronisierung starten**.    
    -   Wenn Sie ein Abonnement erneut initialisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement erneut initialisieren**.   
4.  Um Informationen zu Agents anzuzeigen, klicken Sie auf die Registerkarte **Agents** . Sie können von dieser Registerkarte aus auch auf detailliertere Informationen zugreifen und Aufgaben ausführen:    
    -   Wenn Sie ausführliche Informationen zu einem Agent (z. B. Informationsmeldungen und Fehlermeldungen) anzeigen möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Details anzeigen**.    
    -   Wenn Sie detaillierte Informationen zu dem Auftrag anzeigen möchten, durch den der Agent ausgeführt wird (z. B. Zeitplan, Details zu den Auftragsschritten usw.), klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie anschließend auf **Eigenschaften**.    
    -   Wenn Sie die Profile für den Agent verwalten möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agentprofil**. Weitere Informationen finden Sie unter [Arbeiten mit Replikations-Agent-Profilen](../agents/replication-agent-profiles.md).    
    -   Um einen Agent zu starten, der nicht ausgeführt wird, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agent starten**.    
    -   Um einen Agent zu beenden, der ausgeführt wird, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agent beenden**.  
  
## <a name="for-a-subscription"></a>Abonnements 

  Der Replikationsmonitor umfasst folgende Registerkarten mit Informationen zu Abonnements:  
  
-   **Alle Abonnements** -auf dieser Registerkarte werden Informationen zu allen Abonnements für die ausgewählte Veröffentlichung angezeigt.  
  
-   **Überwachungsliste für Abonnements** -diese Registerkarte dient zum Anzeigen von Informationen zu Abonnements von allen Veröffentlichungen auf dem ausgewählten Verleger, die Fehler, Warnungen oder die vorhandenen Leistung aufweisen. Bei Verteilern, auf denen Versionen vor [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ausgeführt werden, wird diese Registerkarte nicht angezeigt.  
  
 Weitere Informationen zu den Optionen der einzelnen Registerkarten finden Sie, wenn Sie auf die Registerkarte im rechten Bereich und dann auf **Hilfe** auf der Menüleiste klicken. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](start-the-replication-monitor.md).  
  
### <a name="all-subscriptions-tab"></a>Registerkarte "alle Abonnements"  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.   
2.  Um Informationen zu Abonnements anzuzeigen, klicken Sie auf die Registerkarte **Alle Abonnements** . Um nur die Abonnements anzuzeigen, die sich in einem bestimmten Status befinden, wie z. B. diejenigen, die gerade synchronisiert werden, wählen Sie die entsprechende Option aus der Dropdownliste **Anzeigen** aus.   
3.  Zum Anzeigen und Ändern von Abonnementeigenschaften klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Eigenschaften**. Sie können auf dieser Registerkarte auch auf detailliertere Informationen zugreifen und Aufgaben ausführen. Weitere Informationen finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](view-information-and-perform-tasks-replication-monitor.md).  
  
### <a name="subscription-watch-list-tab"></a>Registerkarte „Überwachungsliste für Abonnements“  
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, und klicken Sie dann auf einen Verleger.   
2.  Um Informationen zu Abonnements anzuzeigen, klicken Sie auf die Registerkarte **Überwachungsliste für Abonnements** .  
3.  Wählen Sie den anzuzeigenden Abonnementtyp aus der Dropdownliste **\<SubscriptionType>-Abonnements anzeigen** aus. Um nur die Abonnements anzuzeigen, die sich in einem bestimmten Status befinden, wie z. B. diejenigen, die gerade synchronisiert werden, wählen Sie die entsprechende Option aus der Dropdownliste **Anzeigen** aus.    
4.  Zum Anzeigen und Ändern von Abonnementeigenschaften klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Eigenschaften**. Sie können auf dieser Registerkarte auch auf detailliertere Informationen zugreifen und Aufgaben ausführen. Weitere Informationen finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](view-information-and-perform-tasks-replication-monitor.md).  

## <a name="for-publication-agents"></a>Veröffentlichungs-Agents

  Der Replikationsmonitor stellt die Registerkarte **Agents** bereit, auf der Informationen zu den Agents enthalten sind, die der ausgewählten Veröffentlichung zugeordnet sind. Der Verteilungs-Agent und Merge-Agent sind Abonnements zugeordnet. Weitere Informationen finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben mithilfe des Replikationsmonitors](view-information-and-perform-tasks-replication-monitor.md).  
  
 Diese Registerkarte enthält Informationen zu folgenden Agents:    
-   Momentaufnahme-Agent, der von allen Veröffentlichungen verwendet wird.    
-   Protokolllese-Agent, der von allen Transaktionsveröffentlichungen verwendet wird.    
-   Warteschlangenlese-Agent, der von Transaktionsveröffentlichungen verwendet wird, die für Abonnements mit verzögertem Update über eine Warteschlange aktiviert wurden.  
  
 Wenn Sie weitere Informationen zu den Optionen dieser Registerkarte erhalten möchten, klicken Sie auf der Menüleiste auf **Hilfe** . Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](start-the-replication-monitor.md).  
  
### <a name="view-information-and-perform-tasks"></a>Anzeigen von Informationen und Ausführen von Aufgaben 
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.    
2.  Klicken Sie auf die Registerkarte **Agents** , um Informationen zu Agents anzuzeigen. Sie können von dieser Registerkarte aus auch auf detailliertere Informationen zugreifen und Aufgaben ausführen:  
  
    -   Wenn Sie ausführliche Informationen zu einem Agent (z. B. Informationsmeldungen und Fehlermeldungen) anzeigen möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Details anzeigen**.    
    -   Wenn Sie detaillierte Informationen zu dem Auftrag anzeigen möchten, durch den der Agent ausgeführt wird (z. B. Zeitplan, Details zu den Auftragsschritten usw.), klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie anschließend auf **Eigenschaften**.    
    -   Wenn Sie die Profile für den Agent verwalten möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agentprofil**. Weitere Informationen finden Sie unter [Arbeiten mit Replikations-Agent-Profilen](../agents/replication-agent-profiles.md).  
    -   Um einen Agent zu starten, der nicht ausgeführt wird, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agent starten**.  
      -   Um einen Agent zu beenden, der ausgeführt wird, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agent beenden**.  

## <a name="for-subscription-agents"></a>Abonnement-Agents

### <a name="view-information-and-perform-tasks"></a>Anzeigen von Informationen und Ausführen von Aufgaben
  Im Replikationsmonitor gibt es zwei Registerkarten, über die Sie auf Informationen zu den Agents zugreifen können, die dem jeweiligen Abonnement zugeordnet sind:  
  
-   **Alle Abonnements** -auf dieser Registerkarte werden Informationen zu allen Abonnements für die ausgewählte Veröffentlichung angezeigt.  
  
-   **Überwachungsliste für Abonnements** -diese Registerkarte dient zum Anzeigen von Informationen zu Abonnements von allen Veröffentlichungen auf dem ausgewählten Verleger, die Fehler, Warnungen oder die vorhandenen Leistung aufweisen. Bei Verteilern, auf denen Versionen vor [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ausgeführt werden, wird diese Registerkarte nicht angezeigt.  
  
 Weitere Informationen zu den Optionen der einzelnen Registerkarten finden Sie, wenn Sie auf die Registerkarte im rechten Bereich und dann auf **Hilfe** auf der Menüleiste klicken. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](start-the-replication-monitor.md).  
  
### <a name="view-information-and-perform-tasks"></a>Anzeigen von Informationen und Ausführen von Aufgaben 
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, erweitern Sie einen Verleger, und klicken Sie dann auf eine Veröffentlichung.   
2.  Klicken Sie auf die Registerkarte **Alle Abonnements** , um sich Informationen zu den Abonnements anzeigen zu lassen. Sie können von dieser Registerkarte aus auch auf detailliertere Informationen zugreifen und Aufgaben ausführen:  
  
    -   Wenn Sie detaillierte Informationen zum Agent angezeigt bekommen möchten, der dem jeweiligen Abonnement zugeordnet ist, klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Details anzeigen**. Zu den Detailinformationen gehören: Agentverlauf und Fehlermeldungen, bei der Transaktionsreplikation eine Leistungsstatistik und bei der Mergereplikation eine Synchronisierungsstatistik auf Artikelebene.    
         Welche Registerkarten das Detailfenster enthält, hängt von der Art des Abonnements ab: Bei Momentaufnahmeabonnements wird die Registerkarte **Verlauf Verteiler zu Abonnent**angezeigt, bei Transaktionsabonnements enthält das Fenster die Registerkarten **Verlauf Verleger zu Verteiler**, **Verlauf Verteiler zu Abonnent**und **Nicht verteilte Befehle**, und bei Mergeabonnements finden Sie hier die Registerkarte **Synchronisierungsverlauf**.    
    -   Wenn Sie ein Pushabonnement synchronisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Synchronisierung starten**.    
    -   Wenn Sie ein Abonnement erneut initialisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement erneut initialisieren**.    
    -   Wenn Sie ein einzelnes Mergeabonnement überprüfen möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement überprüfen**. Wenn Sie alle Abonnements für eine Mergeveröffentlichung überprüfen möchten, klicken Sie mit der rechten Maustaste auf die entsprechende Veröffentlichung, und klicken Sie dann auf **Alle Abonnements überprüfen**. Wenn alle Abonnements für eine Transaktionsveröffentlichung überprüft werden sollen, klicken Sie mit der rechten Maustaste auf die betreffende Veröffentlichung, und klicken Sie dann auf **Abonnements überprüfen**.    
    -   Wenn Sie die Profile für den Agent verwalten möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agentprofil**. Weitere Informationen finden Sie unter [Arbeiten mit Replikations-Agent-Profilen](../agents/replication-agent-profiles.md).  
  
### <a name="view-information-and-perform-tasks"></a>Anzeigen von Informationen und Ausführen von Aufgaben
  
1.  Erweitern Sie im linken Bereich eine Verlegergruppe, und klicken Sie dann auf einen Verleger.   
2.  Klicken Sie auf die Registerkarte **Überwachungsliste für Abonnements** , um sich Informationen zu den Abonnements anzeigen zu lassen. Sie können von dieser Registerkarte aus auch auf detailliertere Informationen zugreifen und Aufgaben ausführen:    
    -   Wenn Sie detaillierte Informationen zum Agent angezeigt bekommen möchten, der dem jeweiligen Abonnement zugeordnet ist, klicken Sie mit der rechten Maustaste auf das Abonnement, und klicken Sie dann auf **Details anzeigen**. Zu den Detailinformationen gehören: Agentverlauf und Fehlermeldungen, bei der Transaktionsreplikation eine Leistungsstatistik und bei der Mergereplikation eine Synchronisierungsstatistik auf Artikelebene.    
         Welche Registerkarten das Detailfenster enthält, hängt von der Art des Abonnements ab: Bei Momentaufnahmeabonnements wird die Registerkarte **Verlauf Verteiler zu Abonnent**angezeigt, bei Transaktionsabonnements enthält das Fenster die Registerkarten **Verlauf Verleger zu Verteiler**, **Verlauf Verteiler zu Abonnent**und **Leistung**, und bei Mergeabonnements finden Sie hier die Registerkarte **Synchronisierungsverlauf**.    
    -   Wenn Sie ein Pushabonnement synchronisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Synchronisierung starten**.    
    -   Wenn Sie ein Abonnement erneut initialisieren möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement erneut initialisieren**.    
    -   Wenn Sie ein einzelnes Mergeabonnement überprüfen möchten, klicken Sie mit der rechten Maustaste auf das betreffende Abonnement, und klicken Sie dann auf **Abonnement überprüfen**. Wenn Sie alle Abonnements für eine Mergeveröffentlichung überprüfen möchten, klicken Sie mit der rechten Maustaste auf die entsprechende Veröffentlichung, und klicken Sie dann auf **Alle Abonnements überprüfen**. Wenn alle Abonnements für eine Transaktionsveröffentlichung überprüft werden sollen, klicken Sie mit der rechten Maustaste auf die betreffende Veröffentlichung, und klicken Sie dann auf **Abonnements überprüfen**.    
    -   Wenn Sie die Profile für den Agent verwalten möchten, klicken Sie mit der rechten Maustaste auf den Agent, und klicken Sie dann auf **Agentprofil**. Weitere Informationen finden Sie unter [Arbeiten mit Replikations-Agent-Profilen](../agents/replication-agent-profiles.md).  
  

## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../publish/view-and-modify-publication-properties.md)   
 [Überwachen der Replikation](../monitoring-replication.md)  
  