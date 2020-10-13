---
description: MSSQL_ENG018752
title: MSSQL_ENG018752 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: ed7d71fb9c4e1306826c281806c66db38285e06d
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868627"
---
# <a name="mssql_eng018752"></a>MSSQL_ENG018752
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|18752|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Nur jeweils ein Protokolllese-Agent oder eine protokollbezogene Prozedur (sp_repldone, sp_replcmds oder sp_replshowcmds) kann eine Verbindung mit einer Datenbank herstellen. Falls Sie eine protokollbezogene Prozedur ausgeführt haben, löschen Sie vor dem Starten des Protokolllese-Agents oder dem Ausführen einer weiteren protokollbezogenen Prozedur die Verbindung, über die sie ausgeführt wurde, oder führen Sie 'sp_replflush' über diese Verbindung aus.|  
  
## <a name="explanation"></a>Erklärung  
 Mehrere aktuelle Verbindungen versuchen, **sp_repldone**, **sp_replcmds**oder **sp_replshowcmds**auszuführen. Die gespeicherten Prozeduren [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md) und [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) werden vom Protokolllese-Agent verwendet, um Informationen zu replizierten Transaktionen in einer veröffentlichten Datenbank zu finden und zu aktualisieren. Die gespeicherte Prozedur [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md) wird für die Behandlung bestimmter Problemtypen einer Transaktionsreplikation verwendet.  
  
 Dieser Fehler wird in folgenden Situationen ausgelöst:  
  
-   Wenn der Protokolllese-Agent für eine veröffentlichte Datenbank ausgeführt und versucht wird, einen zweiten Protokolllese-Agent für dieselbe Datenbank auszuführen, wird der Fehler für den zweiten Agent ausgelöst und im Agentverlauf angezeigt.  
  
     In einer Situation, in der offenbar mehrere Agents vorhanden sind, kann es sein, dass einer dieser Agents das Ergebnis eines verwaisten Prozesses ist.  
  
-   Wenn der Protokolllese-Agent für eine veröffentlichte Datenbank gestartet wird und ein Benutzer **sp_repldone**, **sp_replcmds**oder **sp_replshowcmds** für dieselbe Datenbank ausführt, wird der Fehler in der Anwendung ausgelöst, in der die gespeicherte Prozedur ausgeführt wurde (z. B. **sqlcmd**).  
  
-   Wenn für eine veröffentlichte Datenbank kein Protokolllese-Agent ausgeführt wird und ein Benutzer **sp_repldone**, **sp_replcmds**oder **sp_replshowcmds** ausführt, ohne anschließend die Verbindung zu schließen, über die die Prozedur ausgeführt wurde, wird der Fehler ausgelöst, wenn der Protokolllese-Agent versucht, eine Verbindung mit der Datenbank herzustellen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Folgende Schritte können Ihnen bei der Problembehandlung behilflich sein. Wenn der Protokolllese-Agent in einem beliebigen Schritt ohne Fehler gestartet werden kann, müssen die verbleibenden Schritte nicht mehr ausgeführt werden.  
  
-   Überprüfen Sie den Verlauf des Protokolllese-Agents für alle anderen Fehler, die möglicherweise zu diesem Fehler beitragen. Informationen zum Anzeigen des Agent-Status und der Fehlerinformationen im Replikationsmonitor finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
-   Überprüfen Sie die Ausgabe von [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) für spezielle SPIDs, die mit der veröffentlichten Datenbank verbunden sind. Schließen Sie alle Verbindungen, mit denen **sp_repldone**, **sp_replcmds**oder **sp_replshowcmds**möglicherweise ausgeführt wurden.  
  
-   Starten Sie den Protokolllese-Agent neu. Weitere Informationen finden Sie unter [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Dienst auf dem Verteiler neu (schalten Sie ihn in einem Cluster offline oder online). Wenn die Möglichkeit besteht, dass **sp_repldone**, **sp_replcmds**oder **sp_replshowcmds** durch einen geplanten Auftrag von einer anderen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wurde, starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent für die betreffenden Instanzen ebenfalls neu. Weitere Informationen finden Sie unter [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).  
  
-   Führen Sie auf dem Verleger in der Veröffentlichungsdatenbank [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md) aus, und starten Sie den Protokolllese-Agent anschließend neu.  
  
-   Wenn der Fehler weiterhin auftritt, erhöhen Sie die Protokollierungsstufe des Agents, und geben Sie eine Ausgabedatei für das Protokoll an. Je nach Zusammenhang, in dem der Fehler auftritt, finden Sie hier möglicherweise die Schritte, die zum Fehler führen, und/oder weitere Fehlermeldungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Replikationsprotokolllese-Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
