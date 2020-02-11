---
title: Anzeigen des Veröffentlichungs- und Abonnementstatus im Replikationsmonitor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9dad3a2c5f7073ea63608ba5234061a3ffa2102c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62666940"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a>Anzeigen des Veröffentlichungs- und Abonnementstatus im Replikationsmonitor
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Im Replikations Monitor werden Statusinformationen für Veröffentlichungen und Abonnements angezeigt:  
  
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
  
 **So zeigen Sie den Veröffentlichungs-und Abonnement Status an**  
  
-   Replikations Monitor: [Anzeigen von Informationen und Ausführen von Tasks mithilfe des Replikations Monitors](view-information-and-perform-tasks-replication-monitor.md)
  
  
## <a name="publication-status-values"></a>Veröffentlichungsstatuswerte  
 In der nachfolgenden Tabelle werden Veröffentlichungsstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt.  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "UI-Symbol: Fehler")|  
|Leistung ist kritisch|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "UI-Symbol: Wiederholungsversuch des Replikations-Agents")|  
|OK|(Keine)|  
  
## <a name="subscription-status-values"></a>Abonnementstatuswerte  
 In den nachfolgenden Tabellen werden Abonnementstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt. Ein Abonnement kann zwei Statusangaben gleichzeitig aufweisen, beispielsweise **Läuft demnächst ab/Abgelaufen** und **fehlerhafter Befehl wird wiederholt**. Der Status mit der höchsten Priorität wird angezeigt.  
  
 Die Statuswerte **Leistung ist kritisch**, **Läuft demnächst ab/Abgelaufen**und **Nicht initialisiert** sind Warnungen. Wenn eine Warnung eingeblendet wird, geht aus dem Replikationsmonitor ebenfalls hervor, ob derzeit ein Agent ausgeführt wird. Der Status kann also beispielsweise **Wird ausgeführt, Leistungskritisch**sein.  
  
### <a name="transactional-subscriptions"></a>Transaktionsabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Leistung ist kritisch|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Läuft demnächst ab/Abgelaufen|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|Nicht initialisiertes Abonnement|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "UI-Symbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird nicht ausgeführt|![UI-Symbol: Replikations-Agent wird beendet](../media/repl-icon-stopped.gif "UI-Symbol: Replikations-Agent wird beendet")|  
|Wird ausgeführt|![UI-Symbol: Replikations-Agent wird ausgeführt](../media/repl-icon-running.gif "UI-Symbol: Replikations-Agent wird ausgeführt")|  
  
### <a name="merge-subscriptions"></a>Mergeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "UI-Symbol: Fehler")|  
|Leistung ist kritisch|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|Langer Mergevorgang|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|Läuft demnächst ab/Abgelaufen|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|Nicht initialisiertes Abonnement|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "UI-Symbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird synchronisiert|![UI-Symbol: Replikations-Agent wird ausgeführt](../media/repl-icon-running.gif "UI-Symbol: Replikations-Agent wird ausgeführt")|  
|Synchronisierung wird nicht ausgeführt|![UI-Symbol: Replikations-Agent wird beendet](../media/repl-icon-stopped.gif "UI-Symbol: Replikations-Agent wird beendet")|  
  
### <a name="snapshot-subscriptions"></a>Momentaufnahmeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![UI-Symbol: Fehler](../media/repl-icon-error.gif "UI-Symbol: Fehler")|  
|Läuft demnächst ab/Abgelaufen|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|Nicht initialisiertes Abonnement|![UI-Symbol: Warnung](../media/repl-icon-warn.gif "UI-Symbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![UI-Symbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "UI-Symbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird synchronisiert|![UI-Symbol: Replikations-Agent wird ausgeführt](../media/repl-icon-running.gif "UI-Symbol: Replikations-Agent wird ausgeführt")|  
|Synchronisierung wird nicht ausgeführt|![UI-Symbol: Replikations-Agent wird beendet](../media/repl-icon-stopped.gif "UI-Symbol: Replikations-Agent wird beendet")|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../monitoring-replication.md)  
  
  
