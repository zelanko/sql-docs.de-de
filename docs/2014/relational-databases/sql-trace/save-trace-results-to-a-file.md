---
title: Speichern von Ablaufverfolgungsergebnissen in einer Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a55662b38fbd69dc45d8f0031856ad4da5929038
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63136436"
---
# <a name="save-trace-results-to-a-file"></a>Speichern von Ablaufverfolgungsergebnissen in einer Datei
  Ablaufverfolgungsergebnisse können in einer Datei gespeichert werden. Die Ablaufverfolgungsergebnisse werden in eine Ablaufverfolgungsdatei geschrieben. Eine Ablaufverfolgungsdatei kann in einem lokalen Verzeichnis (z. B.\\*Ordnername*\\*Dateiname.trc*) oder in einem Netzwerkverzeichnis (z. B. \\\Computername\Freigabename\Dateiname.trc) gespeichert sein.  
  
 Die Ablaufverfolgungsdateien können für die folgenden Aufgaben verwendet werden:  
  
-   Wiedergeben von Ablaufverfolgungen  
  
-   Überwachen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Ausführen einer Leistungsanalyse  
  
-   Korrelation von Ablaufverfolgungsereignissen mit Leistungsindikatoren zur Optimierung der Suche nach Problemen  
  
-   Datenbankoptimierungsratgeber-Analyse  
  
-   Ausführen der Abfrageoptimierung  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert Ablaufverfolgungsergebnisse in einer Datei, wenn ein Pfad und ein Dateiname für das Argument **@tracefile** der gespeicherten Prozedur **sp_trace_create**angegeben sind.  
  
> [!NOTE]  
>  Wenn ein Pfad zur gespeicherten Prozedur **sp_trace_create** zum Speichern der Ablaufverfolgungsdatei angegeben ist, muss der Server Zugriff auf das Verzeichnis haben. Achten Sie auch darauf, dass es sich bei Angabe eines lokalen Verzeichnisses für **sp_trace_create**um ein lokales Verzeichnis auf dem Servercomputer handelt.  
  
 Wenn [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verwendet wird, können Sie Ablaufverfolgungsergebnisse in einer Datei oder Tabelle speichern. Das Speichern von Ablaufverfolgungsergebnissen in einer Tabelle ermöglicht den gleichen Zugriff wie beim Speichern der Ablaufverfolgung in einer Datei. Außerdem können Sie für die Tabelle Abfragen ausführen, um nach bestimmten Ereignissen zu suchen.  
  
 Weitere Informationen zum Speichern von Ablaufverfolgungsergebnissen finden Sie unter [Speichern von Ablaufverfolgungsergebnissen in einer Tabelle &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) und [Speichern von Ablaufverfolgungsergebnissen in einer Datei &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)   
 [Erstellen einer Ablaufverfolgung &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)   
 [Erstellen einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
