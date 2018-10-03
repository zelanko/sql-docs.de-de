---
title: Vorlagen und Berechtigungen in SQL Server Profiler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0871006afc74e7295646db928ec5ace0030170cc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175750"
---
# <a name="sql-server-profiler-templates-and-permissions"></a>Vorlagen und Berechtigungen in SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt an, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abfragen intern auflöst. Auf diese Weise können Administratoren genau erfassen, welche [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen oder MDX-Ausdrücke (Multidimensional Expressions) an den Server übermittelt werden und wie der Server auf die Datenbank oder den Cube zugreift, um Resultsets zurückzugeben.  
  
 Mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]können Sie folgende Aktionen ausführen:  
  
-   Erstellen einer Ablaufverfolgung, die auf einer wiederverwendbaren Vorlage basiert.  
  
-   Beobachten der Ablaufverfolgungsergebnisse, während die Ablaufverfolgung ausgeführt wird.  
  
-   Speichern der Ablaufverfolgungsergebnisse in einer Tabelle.  
  
-   Starten, Beenden, Anhalten und Ändern der Ablaufverfolgungsergebnisse nach Bedarf.  
  
-   Wiedergeben der Ablaufverfolgungsergebnisse.  
  
 Überwachen Sie mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ausschließlich die für Sie interessanten Ereignisse. Wenn Ablaufverfolgungen zu umfangreich werden, können Sie diese anhand der gewünschten Informationen filtern, damit nur eine Teilmenge der Ereignisdaten gesammelt wird. Wenn zu viele Ereignisse überwacht werden, nimmt der Verwaltungsaufwand für den Server und den Überwachungsvorgang zu, und die Ablaufverfolgungsdatei oder -tabelle kann sehr groß werden, vor allem, wenn über längere Zeit überwacht wird.  
  
> [!NOTE]  
>  Nachverfolgungsspaltenwerte über 1 GB geben einen Fehler zurück und werden in der Nachverfolgungsausgabe abgeschnitten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[SQL Server Profiler-Vorlagen](sql-server-profiler-templates.md)|Enthält Informationen zu den vordefinierten Ablaufverfolgungsvorlagen, die im Lieferumfang von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]enthalten sind.|  
|[Erforderliche Berechtigungen zum Ausführen von SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md)|Enthält Informationen zu den Berechtigungen, die zum Ausführen von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]erforderlich sind.|  
|[Speichern von Ablaufverfolgungen und Ablaufverfolgungsvorlagen](save-traces-and-trace-templates.md)|Enthält Informationen zum Speichern von Ablaufverfolgungsausgaben und zum Speichern von Ablaufverfolgungsdefinitionen in einer Vorlage.|  
|[Ändern von Ablaufverfolgungsvorlagen](modify-trace-templates.md)|Enthält Informationen zum Ändern von Ablaufverfolgungsvorlagen mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] oder mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|[Starten einer Ablaufverfolgung](start-a-trace.md)|Enthält Informationen zu den Vorgängen beim Starten, Anhalten oder Beenden einer Ablaufverfolgung.|  
|[Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten](correlate-a-trace-with-windows-performance-log-data.md)|Enthält Informationen zur Korrelation von Windows-Leistungsprotokolldaten mit einer Ablaufverfolgung mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.|  
|[Anzeigen und Analysieren von Ablaufverfolgungen mit SQL Server Profiler](view-and-analyze-traces-with-sql-server-profiler.md)|Enthält Informationen zum Verwenden von Ablaufverfolgungen zur Problembehandlung bei Daten, zum Anzeigen von Objektnamen in einer Ablaufverfolgung und zum Finden von Ereignissen in einer Ablaufverfolgung.|  
|[Analysieren von Deadlocks mit SQL Server Profiler](analyze-deadlocks-with-sql-server-profiler.md)|Enthält Informationen zum Verwenden von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zum Identifizieren der Ursache eines Deadlocks.|  
|[Analysieren von Abfragen mit SHOWPLAN-Ergebnissen in SQL Server Profiler](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|Enthält Informationen zum Verwenden von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zum Sammeln und Anzeigen von Ergebnissen für Showplan und Showplanstatistiken.|  
|[Filtern von Ablaufverfolgungen mit SQL Server Profiler](filter-traces-with-sql-server-profiler.md)|Enthält Informationen zum Festlegen von Filtern für Datenspalten zum Filtern von Ablaufverfolgungsausgaben mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Wiedergeben von Ablaufverfolgungen](replay-traces.md)|Erklärt, was das Wiedergeben einer Ablaufverfolgung bedeutet und was erforderlich ist, um eine Ablaufverfolgung wiederzugeben.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Profiler](sql-server-profiler.md)   
 [Starten des SQL Server Profilers](start-sql-server-profiler.md)  
  
  
