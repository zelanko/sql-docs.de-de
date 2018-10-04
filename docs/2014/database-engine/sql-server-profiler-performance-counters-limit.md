---
title: SQL Server Profiler - Beschränken der Leistungsindikatoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 74ac3839567366c429c64e0139f8e86793aa942a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165220"
---
# <a name="sql-server-profiler---performance-counters-limit"></a>SQL Server Profiler - Beschränken der Leistungsindikatoren
  Mithilfe des Dialogfelds zum Beschränken der Leistungsindikatoren, können Sie die Informationen aus einer Leistungsprotokolldatei des Systemmonitors beschränken, wenn er mit einer [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] -Ablaufverfolgung korreliert wird. Mithilfe dieses Dialogfelds können Sie Indikatoren auswählen, die angezeigt und für die Korrelation verwendet werden sollen.  
  
 Das Dialogfeld zum **Beschränken der Leistungsindikatoren** wird mit den Leistungsobjekten und -indikatoren aufgefüllt, die in der Leistungsprotokolldatei enthalten sind.  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a>So wählen Sie Leistungsobjekte und -indikatoren aus, die mit einer Ablaufverfolgung korreliert werden sollen  
  
1.  Erweitern Sie ein Leistungsobjekt, um anzuzeigen, welche Indikatoren in der Leistungsprotokolldatei enthalten sind.  
  
2.  Aktivieren Sie die Indikatoren, die mit der [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] -Ablaufverfolgungsdatei korreliert werden sollen.  
  
     Wenn Sie alle Indikatoren für ein Leistungsobjekt auswählen möchten, setzen Sie in das Feld neben dem Leistungsobjekt ein Häkchen. Wenn Sie den obersten Knoten aktivieren, der für den Computer steht, werden alle Leistungsobjekte und -indikatoren ausgewählt, die in der Leistungsprotokolldatei enthalten sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  
