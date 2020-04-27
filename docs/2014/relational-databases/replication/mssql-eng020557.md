---
title: MSSQL_ENG020557 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6816a0301a03e2c0d01cfe78a5c88213394c445b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63057110"
---
# <a name="mssql_eng020557"></a>MSSQL_ENG020557
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20557|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Agent wird heruntergefahren. Weitere Informationen finden Sie im Auftragsverlauf des SQL Server-Agents für den Auftrag '%s'.|  
  
## <a name="explanation"></a>Erklärung  
 Ein Replikations-Agent wurde beendet, ohne dass ein Grund in die entsprechende Verlaufstabelle geschrieben wurde, oder der Agent wurde während eines Prozesses beendet.  
  
## <a name="user-action"></a>Benutzeraktion  
  
-   Starten Sie den Agent neu, um zu ermitteln, ob er nun fehlerfrei ausgeführt wird. Weitere Informationen finden Sie unter [Starten und Beenden eines Replikations-Agents &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) oder [Ausführbare Konzepte für die Programmierung von Replikations-Agents](concepts/replication-agent-executables-concepts.md).  
  
-   Überprüfen Sie Agent- und Auftragsverlauf auf andere Fehler, die eventuell um dieselbe Zeit aufgetreten sind. Informationen zum Anzeigen des Agent-Status und der Fehlerinformationen im Replikationsmonitor finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md).
-   Stellen Sie sicher, dass die Konnektivität zwischen den Computern, auf die der Agent zugreift, funktioniert, und stellen Sie dann mithilfe eines Hilfsprogramms eine Verbindung mit den einzelnen Computern her, z. B. mithilfe des Hilfsprogramms **sqlcmd** . Benutzen Sie zum Herstellen der Verbindungen dasselbe Konto wie der Agent. Weitere Informationen zu den erforderlichen Berechtigungen für die einzelnen Agentkonten finden Sie unter [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
-   Wenn der Fehler auftritt, während Sie eine Momentaufnahme erstellen oder anwenden, überprüfen Sie die Dateien im Momentaufnahmeverzeichnis auf Fehler.  
  
-   Wenn der Fehler weiterhin auftritt, erhöhen Sie die Protokollierungsstufe des Agents, und geben Sie eine Ausgabedatei für das Protokoll an. Je nach Zusammenhang, in dem der Fehler auftritt, finden Sie hier möglicherweise die Schritte, die zum Fehler führen, und weitere Fehlermeldungen. Weitere Informationen zur Konfiguration der Protokollierung für die Replikation finden Sie im Microsoft Knowledge Base-Artikel [312292](https://support.microsoft.com/kb/312292).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
