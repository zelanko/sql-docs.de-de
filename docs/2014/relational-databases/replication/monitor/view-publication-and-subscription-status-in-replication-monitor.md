---
title: Anzeigen des Veröffentlichungs- und Abonnementstatus im Replikationsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 191735b8b5be2a7828136abfaf09e95d295a7850
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047620"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a>Anzeigen des Veröffentlichungs- und Abonnementstatus im Replikationsmonitor
  Im Replikationsmonitor von[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] werden Statusinformationen für Veröffentlichungen und Abonnements angezeigt:  
  
-   Der Status einer Veröffentlichung wird durch den Status mit höchster Priorität der zugehörigen Abonnements bestimmt. Wenn beispielsweise ein Abonnement einer Veröffentlichung einen Fehler aufweist und bei einem anderen Abonnement ein leistungsbezogenes Problem vorliegt, wird für die Veröffentlichung ein Statusfehler gemeldet.  
  
-   Der Status eines Abonnements wird durch den Status der Agents bestimmt, die das Abonnement bedienen. Bei einer Mergereplikation handelt es sich hierbei um den Merge-Agent. Bei einer Transaktionsreplikation handelt es sich um den Protokolllese-Agent oder den Verteilungs-Agent (der Status mit höchster Priorität wird angezeigt; der Status kann auch durch den Warteschlangenlese-Agent ermittelt werden, wenn Abonnements mit verzögertem Update über eine Warteschlange verwendet werden). Bei einer Momentaufnahmereplikation handelt es sich hierbei um den Momentaufnahme-Agent oder den Verteilungs-Agent (der Status mit höchster Priorität wird angezeigt).  
  
 In den Tabellen in den nachfolgenden Abschnitten werden mögliche Statuswerte für Veröffentlichungen und Abonnements aufgeführt. Drei der Statuswerte werden nur angezeigt, wenn ein Schwellenwert erreicht oder überschritten wird.  
  
-   Läuft demnächst ab  
  
     Dieser Statuswert gilt für alle Arten der Replikation. Weitere Informationen finden Sie unter [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).  
  
-   Leistung ist kritisch  
  
     Dieser Statuswert gilt für die Transaktionsreplikation und die Mergereplikation. Weitere Informationen finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor-performance-with-replication-monitor.md).  
  
-   Langer Mergevorgang  
  
     Dieser Statuswert gilt für die Mergereplikation. Weitere Informationen finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](monitor-performance-with-replication-monitor.md).  
  
 Zusätzlich zum Veröffentlichungs- und Abonnementstatus stellt die Mergereplikation Statistiken auf Artikelebene bereit, wodurch Sie z. B. wesentlich ausführlichere Informationen zu folgenden wichtigen Fragen erhalten: Wie lange dauert es bis zum Abschluss einer Mergephase? Wie viel Zeit wurde für die Verarbeitung eines bestimmten Artikels aufgewendet? Welchen Verbindungstyp verwendet ein Abonnent? Die Statistiken werden im Replikationsmonitor im Fenster des Merge-Agents angezeigt. Bei der Momentaufnahme- und Transaktionsreplikation werden ausführliche Informationen zur Verteilungs-Agent-Verarbeitung bereitgestellt.  
  
 **So zeigen Sie den Veröffentlichungs- und Abonnementstatus an**  
  
-   Replikationsmonitor: [Anzeigen von Informationen und Ausführen von Aufgaben für eine Veröffentlichung &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-a-publication-replication-monitor.md) und [Anzeigen von Informationen und Ausführen von Aufgaben für ein Abonnement &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
  
 **So zeigen Sie ausführliche Informationen zu Agents an:**  
  
-   Replikationsmonitor: [Anzeigen von Informationen und Ausführen von Aufgaben für die einer Veröffentlichung zugeordneten Agents &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-publication-agents.md) und [Anzeigen von Informationen und Ausführen von Aufgaben für die einem Abonnement zugeordneten Agents &#40;Replikationsmonitor&#41;](view-information-and-perform-tasks-for-subscription-agents.md).  
  
## <a name="publication-status-values"></a>Veröffentlichungsstatuswerte  
 In der nachfolgenden Tabelle werden Veröffentlichungsstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt.  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "UI icon: error")|  
|Leistung ist kritisch|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholung Replikations-Agent](../media/repl-icon-retry.gif "UI icon: replication agent retry")|  
|OK|none|  
  
## <a name="subscription-status-values"></a>Abonnementstatuswerte  
 In den nachfolgenden Tabellen werden Abonnementstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt. Ein Abonnement kann zwei Statusangaben gleichzeitig aufweisen, beispielsweise **Läuft demnächst ab/Abgelaufen** und **fehlerhafter Befehl wird wiederholt**. Der Status mit der höchsten Priorität wird angezeigt.  
  
 Die Statuswerte **Leistung ist kritisch**, **Läuft demnächst ab/Abgelaufen**und **Nicht initialisiert** sind Warnungen. Wenn eine Warnung eingeblendet wird, geht aus dem Replikationsmonitor ebenfalls hervor, ob derzeit ein Agent ausgeführt wird. Der Status kann also beispielsweise **Wird ausgeführt, Leistungskritisch**sein.  
  
### <a name="transactional-subscriptions"></a>Transaktionsabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "UI icon: error")|  
|Leistung ist kritisch|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|Läuft demnächst ab/Abgelaufen|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|Nicht initialisiertes Abonnement|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholung Replikations-Agent](../media/repl-icon-retry.gif "UI icon: replication agent retry")|  
|Wird nicht ausgeführt|![UI-Symbol: Replikations-Agent beendet](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")|  
|Wird ausgeführt|![UI-Symbol: Replikations-Agent Ausführung](../media/repl-icon-running.gif "UI icon: replication agent running")|  
  
### <a name="merge-subscriptions"></a>Mergeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "UI icon: error")|  
|Leistung ist kritisch|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|Langer Mergevorgang|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|Läuft demnächst ab/Abgelaufen|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|Nicht initialisiertes Abonnement|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholung Replikations-Agent](../media/repl-icon-retry.gif "UI icon: replication agent retry")|  
|Wird synchronisiert|![UI-Symbol: Replikations-Agent Ausführung](../media/repl-icon-running.gif "UI icon: replication agent running")|  
|Synchronisierung wird nicht ausgeführt|![UI-Symbol: Replikations-Agent beendet](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")|  
  
### <a name="snapshot-subscriptions"></a>Momentaufnahmeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "UI icon: error")|  
|Läuft demnächst ab/Abgelaufen|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|Nicht initialisiertes Abonnement|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI icon: warning")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholung Replikations-Agent](../media/repl-icon-retry.gif "UI icon: replication agent retry")|  
|Wird synchronisiert|![UI-Symbol: Replikations-Agent Ausführung](../media/repl-icon-running.gif "UI icon: replication agent running")|  
|Synchronisierung wird nicht ausgeführt|![UI-Symbol: Replikations-Agent beendet](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Replikation](../monitoring-replication.md)  
  
  