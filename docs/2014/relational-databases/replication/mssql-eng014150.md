---
title: MSSQL_ENG014150 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07fcbe83f92a523eea000a9a63b4a72a991228fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233050"
---
# <a name="mssqleng014150"></a>MSSQL_ENG014150
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14150|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Replikations-%1!: %2! (Agent) erfolgreich. %s|  
  
## <a name="explanation"></a>Erklärung  
 Mit dieser Meldung wird angegeben, dass ein Replikations-Agent erfolgreich zu Ende ausgeführt wurde. Für die Replikation werden die folgenden Agents verwendet:  
  
-   Der Momentaufnahme-Agent. Dieser Agent wird von allen Veröffentlichungen verwendet.  
  
-   Der Protokolllese-Agent. Dieser Agent wird von allen Transaktionsveröffentlichungen verwendet.  
  
-   Der Warteschlangenlese-Agent. Dieser Agent wird von Transaktionsveröffentlichungen verwendet, die für Abonnements mit verzögertem Update über eine Warteschlange aktiviert sind.  
  
-   Der Verteilungs-Agent. Mit diesem Agent werden Abonnements für Transaktions- und Momentaufnahmeveröffentlichungen synchronisiert.  
  
-   Der Merge-Agent. Mit diesem Agent werden Abonnements für Mergeveröffentlichungen synchronisiert.  
  
-   Aufträge zur Replikationswartung.  
  
## <a name="user-action"></a>Benutzeraktion  
 Der Protokolllese-Agent, der Warteschlangenlese-Agent und der Verteilungs-Agent werden normalerweise kontinuierlich ausgeführt. Die anderen Agents werden hingegen bei Bedarf oder nach einem Zeitplan ausgeführt. Wenn Sie nicht erwarten, dass ein Agent zu Ende ausgeführt wurde, überprüfen Sie den Status des Agents. Weitere Informationen finden Sie unter [Monitor Replication Agents](agents/replication-agents.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Replikations-Agentverwaltung](agents/replication-agent-administration.md)   
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [Replikationsverteilungs Agent](agents/replication-distribution-agent.md)   
 [Replikationsprotokolllese-Agent](agents/replication-log-reader-agent.md)   
 [Replikationsmerge-Agent](agents/replication-merge-agent.md)   
 [Warteschlangenlese-Agent](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  
