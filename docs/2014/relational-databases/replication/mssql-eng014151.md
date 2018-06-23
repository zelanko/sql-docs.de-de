---
title: MSSQL_ENG014151 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 73e1586367cb9ecaec10f8bdefeec776143990a6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061362"
---
# <a name="mssqleng014151"></a>MSSQL_ENG014151
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14151|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Replikations-%1!s!: Fehler beim %2!s!-Agent. %3!|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler wird bei allen Replikations-Agentfehlern ausgelöst. Der Text am Ende der Fehlermeldung ist kontextbedingt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Dieser Fehler kann in verschiedenen Situationen auftreten. Verwenden Sie zu seiner Behebung ggf. folgende Methoden:  
  
-   Starten Sie den Agent neu, um zu ermitteln, ob er nun fehlerfrei ausgeführt wird. Weitere Informationen finden Sie unter [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) oder [Ausführbare Konzepte für die Programmierung von Replikations-Agents](concepts/replication-agent-executables-concepts.md).  
  
-   Überprüfen Sie Agent- und Auftragsverlauf auf andere Fehler, die eventuell um dieselbe Zeit aufgetreten sind. Informationen zum Anzeigen des Agentstatus und der Fehlerdetails im Replikationsmonitor finden Sie in den folgenden Themen:  
  
    -   Informationen zum Momentaufnahme-Agent, Protokolllese-Agent und Warteschlangenlese-Agent finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben für die einer Veröffentlichung zugeordneten Agents &#40;Replikationsmonitor&#41;](monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
    -   Informationen zum Verteilungs-Agent und zum Merge-Agent finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben für die einem Abonnement zugeordneten Agents &#40;Replikationsmonitor&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
-   Überprüfen Sie, dass die Konnektivität zwischen den Computern, auf die der Agent zugreift, funktioniert, und stellen Sie dann mithilfe eines Hilfsprogramms eine Verbindung mit den einzelnen Computern her, z. B. mit dem [sqlcmd Utility](../../tools/sqlcmd-utility.md). Benutzen Sie zum Herstellen der Verbindungen dasselbe Konto wie der Agent. Weitere Informationen zu den erforderlichen Berechtigungen für die einzelnen Agentkonten finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
-   Wenn der Fehler auftritt, während eine Momentaufnahme erstellt oder angewendet wird, überprüfen Sie die Dateien im Momentaufnahmeverzeichnis auf Fehler.  
  
-   Wenn der Fehler weiterhin auftritt, erhöhen Sie die Protokollierungsstufe des Agents, und geben Sie eine Ausgabedatei für das Protokoll an. Je nach Zusammenhang, in dem der Fehler auftritt, finden Sie hier möglicherweise die Schritte, die zum Fehler führen, und/oder weitere Fehlermeldungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Replikations-Agentverwaltung](agents/replication-agent-administration.md)   
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [Replikationsverteilungs Agent](agents/replication-distribution-agent.md)   
 [Replikationsprotokolllese-Agent](agents/replication-log-reader-agent.md)   
 [Replikationsmerge-Agent](agents/replication-merge-agent.md)   
 [Warteschlangenlese-Agent](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  