---
title: MSSQLSERVER_17300 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6577ec13cc990eb65d66eb2975d61b5f1147201
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62915349"
---
# <a name="mssqlserver17300"></a>MSSQLSERVER_17300
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17300|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|PROC_OUT_OF_SYSTASK_SESSIONS|  
|Meldungstext|Der SQL Server war nicht in der Lage, einen neuen Systemtask auszuführen, entweder aufgrund von unzureichendem Speicher oder weil die Anzahl der konfigurierten Sitzungen die maximale Anzahl der auf dem Server zulässigen Sitzungen übersteigt. Überprüfen Sie, ob der Server über ausreichenden Arbeitsspeicher verfügt. Sie können mithilfe von sp_configure und der Option ‚Benutzerverbindungen’ die maximale Anzahl der zulässigen Benutzerverbindungen überprüfen. Verwenden Sie sys.dm_exec_sessions, um die aktuelle Anzahl von Sitzungen einschließlich der Benutzerprozesse zu überprüfen.|  
  
## <a name="explanation"></a>Erklärung  
 Die Ausführung eines neuen Systemtasks ist aufgrund von unzureichendem Speicher oder weil die Anzahl der konfigurierten Sitzungen auf dem Server überschritten wurde, fehlgeschlagen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie, ob der Server über ausreichenden Arbeitsspeicher verfügt. Überprüfen Sie die aktuelle Anzahl von Systemtasks mit sys.dm_exec_sessions und überprüfen Sie den konfigurierten Wert der maximalen Anzahl von Benutzerverbindungen mit sp_configure.  
  
 Führen Sie die folgenden Tasks entsprechend aus:  
  
-   Fügen Sie dem Server mehr Arbeitsspeicher hinzu.  
  
-   Beenden Sie eine oder mehrere Sitzungen.  
  
-   Erhöhen Sie die maximal zulässige Anzahl von Benutzerverbindungen auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql)   
 [Konfigurieren der Serverkonfigurationsoption-benutzerverbindungen](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)   
 [KILL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/kill-transact-sql)  
  
  
