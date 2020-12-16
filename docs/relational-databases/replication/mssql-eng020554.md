---
description: MSSQL_ENG020554
title: MSSQL_ENG020554 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: d5c7366692799398fb6397110b0d179431594779
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477801"
---
# <a name="mssql_eng020554"></a>MSSQL_ENG020554
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20554|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Vom Replikations-Agent wurde in %ld Minuten keine Statusmeldung protokolliert. Möglicherweise reagiert der Agent nicht mehr, oder das System ist stark ausgelastet. Überprüfen Sie, ob Datensätze an das Ziel repliziert werden und ob die Verbindungen mit dem Abonnenten, Verleger und Verteiler noch aktiv sind.|  
  
## <a name="explanation"></a>Erklärung  
 Der **Überprüfung des Replikations-Agents** -Auftrag wird nach Ablauf einer angegebenen Zeitspanne (standardmäßig alle 10 Minuten) ausgeführt, um den Status der einzelnen Replikations-Agents zu überprüfen. Wenn ein Agent keine Statusmeldungen protokolliert hat, seitdem der Agentüberprüfungsauftrag zum letzten Mal ausgeführt wurde, wird der Fehler MSSQL_ENG020554 ausgelöst. Vom Agent wird erwartet, dass er zumindest Verlaufsmeldungen protokolliert, auch wenn keinerlei Replikationsaktivität stattgefunden hat. Dass der Replikations-Agent nicht wie erwartet reagiert, heißt nicht unbedingt, dass er beendet wurde oder ausgefallen ist (bei Ausfall eines Agents wird der Fehler MSSQL_ENG020536 ausgelöst).  
  
 Für das Auslösen des Fehlers MSSQL_ENG020554 kann es folgende Gründe geben:  
  
-   Der Agent ist ausgelastet.  
  
     Wenn der Agent so ausgelastet ist, dass er auf den Abruf durch den Agentüberprüfungsauftrag nicht reagieren kann, kann der Agentüberprüfungsauftrag auch nicht berichten, ob der Replikations-Agent ordnungsgemäß funktioniert. Für die Auslastung des Replikations-Agents kann es mehrere Gründe geben. So ist es z. B. möglich, dass viele Daten repliziert werden müssen, oder es gibt Probleme im Anwendungsentwurf bzw. in der Konfiguration, die dazu führen, dass bestimmte Prozesse sehr lange brauchen.  
  
-   Der Agent kann sich auf einem der Computer in der Topologie nicht anmelden.  
  
     Alle Agents besitzen einen **-LoginTimeOut** -Parameter (Standardwert: 15 Sekunden), der bestimmt, wie lange ein Agent versucht, sich bei einem Replikationsknoten anzumelden. Dies gilt auch für Merge-Agents, die sich beim Verleger anmelden. Wenn der Wert für den **-LoginTimeOut** -Parameter höher ist als das Zeitintervall, in dem der Replikations-Agent den Überprüfungsauftrag ausführt, kann das eigentliche Problem für die Ausgabe dieses Fehlers ein Anmeldungsproblem sein: Der MSSQL_ENG020554-Fehler wird ausgelöst, bevor der Agent in der Lage ist, einen spezifischeren Fehler auszulösen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Die notwendige Aktion hängt von der Ursache des Fehlers ab:  
  
-   Für alle Fälle, in denen dieser Fehler ausgegeben wird, gilt Folgendes:  
  
     Überprüfen Sie die Fehlerdetails im Replikationsmonitor, und starten Sie den Replikationsmonitor neu, falls er beendet wurde. Den Fehlerdetails ist vielleicht genauer zu entnehmen, warum der Agent nicht ordnungsgemäß ausgeführt wurde. Wenn der Agent ausgeführt wird, sollten Sie ihn auch nicht beenden und wieder starten, weil sich dadurch das Problem verschlimmern kann. Informationen zum Anzeigen des Agent-Status und der Fehlerinformationen im Replikationsmonitor finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).    
  
-   Wenn der Fehler häufig ausgelöst wird, weil der Agent ausgelastet ist, haben Sie folgende Möglichkeiten:  
  
     Ändern Sie Ihre Anwendung so, dass der Agent weniger Zeit für die Verarbeitung benötigt.  
  
     Erhöhen Sie im Dialogfeld **Auftragseigenschaften** das Zeitintervall, in dem der Agentstatus geprüft wird. Informationen zum Zugreifen auf dieses Dialogfeld für Replikationsaufträge finden Sie unter [View Information and Perform Tasks with Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
-   Wenn ein Agent sich nicht bei einem der Computer in der Topologie anmelden kann, haben Sie folgende Möglichkeiten:  
  
     Es wird empfohlen, den Wert für den **-LoginTimeOut** -Parameter auf einen niedrigeren Wert festzulegen als das Intervall, in dem der Auftrag zur Überprüfung des Replikations-Agents ausgeführt wird. Mitunter wird der Wert für **-LoginTimeOut** aufgrund von Netzwerkproblemen, die zu einem Timeout bei Anmeldungen führen können, relativ hoch angesetzt. Wenn der Wert für **-LoginTimeOut** niedriger festgelegt wird, kann die Replikation spezifischere Informationen zu Fehlern melden, sodass Sie Anmeldeprobleme diagnostizieren können, die durch Probleme bei den Berechtigungen, durch Netzwerkprobleme oder durch andere Probleme hervorgerufen werden. Agentparameter können in den Agentprofilen und in der Befehlszeile angegeben werden. Weitere Informationen finden Sie unter  
  
    -   [Arbeiten mit Replikations-Agent-Profilen](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Anzeigen und Ändern von Befehlszeilenparametern des Replikations-Agents &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)zugeordnet ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwaltung des Replikations-Agents](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Warteschlangenlese-Agent der Microsoft SQL Server-Replikation](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
