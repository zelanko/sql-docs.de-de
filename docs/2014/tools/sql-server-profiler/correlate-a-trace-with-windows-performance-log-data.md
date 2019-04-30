---
title: Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c8a3d7a9888423d312d578784e1f7e1ff75434d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316308"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten
  Mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]können Sie ein Microsoft Windows-Leistungsprotokoll öffnen, die Leistungsindikatoren auswählen, die Sie mit einer Ablaufverfolgung korrelieren möchten, und die ausgewählten Leistungsindikatoren zusammen mit der Ablaufverfolgung auf der grafischen Benutzeroberfläche von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] anzeigen. Wenn Sie ein Ereignis im Ablaufverfolgungsfenster auswählen, zeigt ein senkrechter roter Strich im Datenfensterbereich des Systemmonitors von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] an, welche Leistungsprotokolldaten mit dem ausgewählten Ablaufverfolgungsereignis korrelieren.  
  
 Um eine Ablaufverfolgung mit Leistungsindikatoren zu korrelieren, öffnen Sie eine Ablaufverfolgungsdatei oder -tabelle, die die Datenspalten **StartTime** und **EndTime** data columns, und then click **Datei** von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Leistungsdaten importieren** . Anschließend können Sie das Leistungsprotokoll öffnen und die Systemmonitor-Objekte und -Leistungsindikatoren auswählen, die Sie mit der Ablaufverfolgung korrelieren möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten &#40;SQL Server Profiler&#41;](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
