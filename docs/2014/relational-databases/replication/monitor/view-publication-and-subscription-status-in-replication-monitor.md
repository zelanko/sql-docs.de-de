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
ms.openlocfilehash: 9b8d48b9a21d810f60b071c17dd89ad51c9e489a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049385"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a>Anzeigen des Veröffentlichungs- und Abonnementstatus im Replikationsmonitor
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]Im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replikations Monitor werden Statusinformationen für Veröffentlichungen und Abonnements angezeigt:  
  
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
  
-   Replikations Monitor: [Anzeigen von Informationen und Ausführen von Tasks mithilfe des Replikations Monitors](view-information-and-perform-tasks-replication-monitor.md)
  
  
## <a name="publication-status-values"></a>Veröffentlichungsstatuswerte  
 In der nachfolgenden Tabelle werden Veröffentlichungsstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt.  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Leistung ist kritisch|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|OK|Keine|  
  
## <a name="subscription-status-values"></a>Abonnementstatuswerte  
 In den nachfolgenden Tabellen werden Abonnementstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt. Ein Abonnement kann zwei Statusangaben gleichzeitig aufweisen, beispielsweise **Läuft demnächst ab/Abgelaufen** und **fehlerhafter Befehl wird wiederholt**. Der Status mit der höchsten Priorität wird angezeigt.  
  
 Die Statuswerte **Leistung ist kritisch**, **Läuft demnächst ab/Abgelaufen**und **Nicht initialisiert** sind Warnungen. Wenn eine Warnung eingeblendet wird, geht aus dem Replikationsmonitor ebenfalls hervor, ob derzeit ein Agent ausgeführt wird. Der Status kann also beispielsweise **Wird ausgeführt, Leistungskritisch**sein.  
  
### <a name="transactional-subscriptions"></a>Transaktionsabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Leistung ist kritisch|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Läuft demnächst ab/Abgelaufen|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Nicht initialisiertes Abonnement|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird nicht ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent beendet](../media/repl-icon-stopped.gif "Benutzeroberflächensymbol: Replikations-Agent beendet")|  
|Wird ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt](../media/repl-icon-running.gif "Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt")|  
  
### <a name="merge-subscriptions"></a>Mergeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Leistung ist kritisch|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Langer Mergevorgang|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Läuft demnächst ab/Abgelaufen|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Nicht initialisiertes Abonnement|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird synchronisiert|![Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt](../media/repl-icon-running.gif "Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt")|  
|Synchronisierung wird nicht ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent beendet](../media/repl-icon-stopped.gif "Benutzeroberflächensymbol: Replikations-Agent beendet")|  
  
### <a name="snapshot-subscriptions"></a>Momentaufnahmeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Läuft demnächst ab/Abgelaufen|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Nicht initialisiertes Abonnement|![Benutzeroberflächensymbol: Warnung](../media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird synchronisiert|![Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt](../media/repl-icon-running.gif "Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt")|  
|Synchronisierung wird nicht ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent beendet](../media/repl-icon-stopped.gif "Benutzeroberflächensymbol: Replikations-Agent beendet")|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachung der Replikation](../monitoring-replication.md)  
  
  
