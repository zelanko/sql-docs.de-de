---
title: SQL Server Profiler - Beschränken der Leistungsindikatoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4d2265147cf660430e1995030354013a518e76a7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237220"
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
  
  
