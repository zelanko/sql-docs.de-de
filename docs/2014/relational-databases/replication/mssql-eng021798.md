---
title: MSSQL_ENG021798 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 51cf4acc8ed270c8302137fe5050c06cb35e91ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63023533"
---
# <a name="mssqleng021798"></a>MSSQL_ENG021798
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21798|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der '%s'-Agent-Auftrag muss vor dem Fortsetzen des Vorgangs über '%s' hinzugefügt werden. Lesen Sie die Dokumentation zu '%3!s!'.|  
  
## <a name="explanation"></a>Erklärung  
 Um eine Veröffentlichung erstellen zu können, müssen Sie ein Mitglied der festen Serverrolle **sysadmin** auf dem Verleger oder ein Mitglied der festen Datenbankrolle **db_owner** in der Veröffentlichungsdatenbank sein. Wenn Sie ein Mitglied der **db_owner** -Rolle sind, wird dieser Fehler in folgenden Situationen ausgelöst:  
  
-   Sie führen Skripts von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]aus. Das Sicherheitsmodell wurde in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]geändert, daher müssen die Skripts aktualisiert werden.  
  
-   Die gespeicherte Prozedur **sp_addpublication** wird vor [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) ausgeführt. Dies gilt für alle Transaktionsveröffentlichungen.  
  
-   Die gespeicherte Prozedur **sp_addpublication** wird vor [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) ausgeführt. Dies gilt für Transaktionsveröffentlichungen, für die Abonnements mit verzögertem Update über eine Warteschlange aktiviert sind (d. h., für den **@allow_queued_tran** -Parameter von **sp_addpublication**ist der Wert TRUE ausgewählt).  
  
 Die gespeicherten Prozeduren **sp_addlogreader_agent** und **sp_addqreader_agent** erstellen jeweils einen Agentauftrag und ermöglichen Ihnen, das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto anzugeben, unter dem der Agent ausgeführt wird. Für Benutzer, die die Rolle **sysadmin** besitzen, werden Agentaufträge implizit erstellt, wenn **sp_addlogreader_agent** und **sp_addqreader_agent** nicht ausgeführt werden. Die Agents werden im Kontext des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstkontos auf dem Verteiler ausgeführt. Obwohl **sp_addlogreader_agent** und **sp_addqreader_agent** für Benutzer in der **sysadmin** -Rolle nicht erforderlich sind, empfiehlt sich als bewährte Sicherheitsmethode, ein separates Konto für die Agents anzugeben. Weitere Informationen finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie sicher, dass Sie die Prozeduren in der richtigen Reihenfolge ausführen. Weitere Informationen finden Sie unter [erstellen Sie eine Veröffentlichung](publish/create-a-publication.md), aktualisieren Sie diese Skripts, um die gespeicherten Prozeduren und die erforderlichen Parameter enthalten [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen. Weitere Informationen finden Sie unter [Aktualisieren von Replikationsskripts &#40;Replikationsprogrammierung mit Transact-SQL&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
