---
title: Anzeigen des Veröffentlichungs- und Abonnementstatus (Replikationsmonitor)
description: In diesem Artikel erfahren Sie, wie Sie in SQL Server Management Studio (SSMS) mithilfe des Replikationsmonitors Angaben zum Veröffentlichungs- und Abonnementstatus abrufen können.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 71dc0b6a274b6545169cfcd20487c935086c7764
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159588"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a>Anzeigen des Veröffentlichungs- und Abonnementstatus im Replikationsmonitor
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Im Replikationsmonitor von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] werden Statusinformationen für Veröffentlichungen und Abonnements angezeigt.  
  
-   Der Status einer Veröffentlichung wird durch den Status mit höchster Priorität der zugehörigen Abonnements bestimmt. Wenn beispielsweise ein Abonnement einer Veröffentlichung einen Fehler aufweist und bei einem anderen Abonnement ein leistungsbezogenes Problem vorliegt, wird für die Veröffentlichung ein Statusfehler gemeldet.  
  
-   Der Status eines Abonnements wird durch den Status der Agents bestimmt, die das Abonnement bedienen. Bei einer Mergereplikation handelt es sich hierbei um den Merge-Agent. Bei einer Transaktionsreplikation handelt es sich um den Protokolllese-Agent oder den Verteilungs-Agent (der Status mit höchster Priorität wird angezeigt; der Status kann auch durch den Warteschlangenlese-Agent ermittelt werden, wenn Abonnements mit verzögertem Update über eine Warteschlange verwendet werden). Bei einer Momentaufnahmereplikation handelt es sich hierbei um den Momentaufnahme-Agent oder den Verteilungs-Agent (der Status mit höchster Priorität wird angezeigt).  
  
 In den Tabellen in den nachfolgenden Abschnitten werden mögliche Statuswerte für Veröffentlichungen und Abonnements aufgeführt. Drei der Statuswerte werden nur angezeigt, wenn ein Schwellenwert erreicht oder überschritten wird.  
  
-   Läuft demnächst ab  
  
     Dieser Statuswert gilt für alle Arten der Replikation. Weitere Informationen finden Sie unter [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
-   Leistung ist kritisch  
  
     Dieser Statuswert gilt für die Transaktionsreplikation und die Mergereplikation. Weitere Informationen finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
-   Langer Mergevorgang  
  
     Dieser Statuswert gilt für die Mergereplikation. Weitere Informationen finden Sie unter [Überwachen der Leistung mit dem Replikationsmonitor](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md).  
  
 Zusätzlich zum Veröffentlichungs- und Abonnementstatus stellt die Mergereplikation Statistiken auf Artikelebene bereit, wodurch Sie z. B. wesentlich ausführlichere Informationen zu folgenden wichtigen Fragen erhalten: Wie lange dauert es bis zum Abschluss einer Mergephase? Wie viel Zeit wurde für die Verarbeitung eines bestimmten Artikels aufgewendet? Welchen Verbindungstyp verwendet ein Abonnent? Die Statistiken werden im Replikationsmonitor im Fenster des Merge-Agents angezeigt. Bei der Momentaufnahme- und Transaktionsreplikation werden ausführliche Informationen zur Verteilungs-Agent-Verarbeitung bereitgestellt.  
  
 **So zeigen Sie den Veröffentlichungs- und Abonnementstatus an**  
  
-   Replikationsmonitor: [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md) 
  
 **So zeigen Sie ausführliche Informationen zu Agents an:**  
  
-   Replikationsmonitor: [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)
  
## <a name="publication-status-values"></a>Veröffentlichungsstatuswerte  
 In der nachfolgenden Tabelle werden Veröffentlichungsstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt.  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Leistung ist kritisch|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|OK|none|  
  
## <a name="subscription-status-values"></a>Abonnementstatuswerte  
 In den nachfolgenden Tabellen werden Abonnementstatuswerte und ihre entsprechenden Symbole nach Priorität geordnet aufgeführt. Ein Abonnement kann zwei Statusangaben gleichzeitig aufweisen, beispielsweise **Läuft demnächst ab/Abgelaufen** und **fehlerhafter Befehl wird wiederholt**. Der Status mit der höchsten Priorität wird angezeigt.  
  
 Die Statuswerte **Leistung ist kritisch**, **Läuft demnächst ab/Abgelaufen**und **Nicht initialisiert** sind Warnungen. Wenn eine Warnung eingeblendet wird, geht aus dem Replikationsmonitor ebenfalls hervor, ob derzeit ein Agent ausgeführt wird. Der Status kann also beispielsweise **Wird ausgeführt, Leistungskritisch**sein.  
  
### <a name="transactional-subscriptions"></a>Transaktionsabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Leistung ist kritisch|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Läuft demnächst ab/Abgelaufen|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Nicht initialisiertes Abonnement|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird nicht ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent beendet](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "Benutzeroberflächensymbol: Replikations-Agent beendet")|  
|Wird ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt")|  
  
### <a name="merge-subscriptions"></a>Mergeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Leistung ist kritisch|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Langer Mergevorgang|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Läuft demnächst ab/Abgelaufen|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Nicht initialisiertes Abonnement|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird synchronisiert|![Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt")|  
|Synchronisierung wird nicht ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent beendet](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "Benutzeroberflächensymbol: Replikations-Agent beendet")|  
  
### <a name="snapshot-subscriptions"></a>Momentaufnahmeabonnements  
  
|Status|Symbol|  
|------------|----------|  
|Fehler|![Benutzeroberflächensymbol: Fehler](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "Benutzeroberflächensymbol: Fehler")|  
|Läuft demnächst ab/Abgelaufen|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|Nicht initialisiertes Abonnement|![Benutzeroberflächensymbol: Warnung](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "Benutzeroberflächensymbol: Warnung")|  
|fehlerhafter Befehl wird wiederholt|![Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "Benutzeroberflächensymbol: Wiederholungsversuch des Replikations-Agents")|  
|Wird synchronisiert|![Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "Benutzeroberflächensymbol: Replikations-Agent wird ausgeführt")|  
|Synchronisierung wird nicht ausgeführt|![Benutzeroberflächensymbol: Replikations-Agent beendet](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "Benutzeroberflächensymbol: Replikations-Agent beendet")|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
