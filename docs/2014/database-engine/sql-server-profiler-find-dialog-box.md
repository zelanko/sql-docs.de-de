---
title: SQL Server Profiler - suchen (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 81ed454290a5ca62093fe9bdb619179106ca9985
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088858"
---
# <a name="sql-server-profiler---find-dialog-box"></a>SQL Server Profiler - Suchen (Dialogfeld)
  Mithilfe des Dialogfelds **Suchen** können Sie eine Ablaufverfolgung nach bestimmten Zeichen oder Wörtern durchsuchen. Um einen Suchvorgang abzubrechen, drücken Sie ESC.  
  
 Um das Dialogfeld in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] zu öffnen, klicken Sie im Menü **Bearbeiten** auf **Suchen**.  
  
## <a name="options"></a>Optionen  
 **Suchen nach**  
 Geben Sie den Text ein, nach dem gesucht werden soll. Die Suche entspricht jeder Zeichenfolge, die die angegebene Zeichenfolge enthält. Die Suche nach "Completed" entspricht beispielsweise "SQL:BatchCompleted". Platzhalterzeichen (*, ? usw.) werden nicht unterstützt.  
  
 **Suchen in Spalte**  
 Klicken Sie auf eine zu durchsuchende Datenspalte oder auf **\<Alle Spalten>**, um alle Datenspalten in der Ablaufverfolgung zu durchsuchen.  
  
 **Groß-/Kleinschreibung beachten**  
 Sucht nach Text, der die gleiche Groß-/Kleinschreibung besitzt wie der Text im Feld **Suchen nach** . Deaktivieren Sie dieses Kontrollkästchen, um in der Ablaufverfolgung nach Beispielen zu suchen, die groß oder klein geschrieben werden.  
  
 **Nur ganzes Wort suchen**  
 Schränkt die Suche auf ganze Wörter ein. Deaktivieren Sie das Kontrollkästchen **Nur ganzes Wort** suchen, um nach Zeichen innerhalb eines Worts zu suchen.  
  
 **Weitersuchen**  
 Sucht nach dem nächsten Beispiel der im Feld **Suchen nach** angegebenen Zeichen.  
  
 **Vorheriges suchen**  
 Sucht in der Ablaufverfolgung rückwärts nach dem vorherigen Beispiel der im Feld **Suchen nach** angegebenen Zeichen.  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen eines Wertes oder einer Datenspalte während der Ablaufverfolgung &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [Erstellen einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Vorlagen und Berechtigungen in SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
