---
title: MSSQL_ENG021076 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 900c20dcbfe14e3e9dae40defb66f5441b3fa6b9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010140"
---
# <a name="mssql_eng021076"></a>MSSQL_ENG021076
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|21076|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die Anfangsmomentaufnahme für den %1!s!-Artikel ist noch nicht verfügbar.|  
  
## <a name="explanation"></a>Erklärung  
 Der Fehler MSSQL_ENG021076 wird ausgelöst, wenn der Verteilungs-Agent gestartet wird, bevor der Momentaufnahme-Agent mit dem Generieren der Momentaufnahmen fertig ist. Dieser Fehler wird nur ausgelöst, wenn die Veröffentlichung einen einzigen Artikel enthält. Wenn die Veröffentlichung mehr als einen Artikel enthält, wird stattdessen der Fehler MSSQL_ENG021075 ausgelöst. Weitere Informationen finden Sie unter [MSSQL_ENG021075](mssql-eng021075.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn der Momentaufnahme-Agent für die Veröffentlichung seit der Erstellung des Abonnements oder seit dem letzten erneuten Initialisieren des Abonnements nicht mehr gestartet wurde, starten Sie den Momentaufnahme-Agent, und lassen Sie ihn die Momentaufnahme fertig generieren, bevor Sie den Verteilungs-Agent starten. Weitere Informationen finden Sie unter [Erstellen und Anwenden der Momentaufnahme](create-and-apply-the-snapshot.md).  
  
 Wenn der Momentaufnahme-Agent die Momentaufnahme nicht fertig generiert, überprüfen Sie den Verlauf des Momentaufnahme-Agents auf Fehler, und sorgen Sie für deren Behebung. Informationen zum Anzeigen des Agent-Status und der Fehlerinformationen im Replikationsmonitor finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 Wenn der Fehler weiterhin auftritt, erhöhen Sie die Protokollierungsstufe des Agents, und geben Sie eine Ausgabedatei für das Protokoll an. Je nach Zusammenhang, in dem der Fehler auftritt, finden Sie hier möglicherweise die Schritte, die zum Fehler führen, und/oder weitere Fehlermeldungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
