---
title: Wiedergeben von jeweils einem einzelnen Ereignis (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9c36aafe3a01a48f7623fa1d2871428ee3bea390
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63240472"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a>Wiedergeben von jeweils einem einzelnen Ereignis (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Sie mithilfe von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]jeweils ein einzelnes Ereignis einer Ablaufverfolgungsdatei oder -tabelle wiedergeben.  
  
### <a name="to-replay-a-single-event-at-a-time"></a>So geben Sie jeweils ein einzelnes Ereignis wieder  
  
1.  Öffnen Sie die Ablaufverfolgungsdatei oder -tabelle, die Sie wiedergeben möchten. Weitere Informationen finden Sie unter [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) oder den Optimierungsratgeber von [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)die richtigen Ereignisse und Spalten aufgezeichnet werden.  
  
     Stellen Sie sicher, dass die geöffnete Ablaufverfolgungsdatei oder -tabelle die Ereignisklassen enthält, die für die Wiedergabe erforderlich sind. Weitere Informationen finden Sie unter [Replay Requirements](replay-requirements.md).  
  
2.  Klicken Sie im Menü **Wiedergabe** auf **Schritt**, und stellen Sie eine Verbindung mit der Serverinstanz her, auf der die Ablaufverfolgung wiedergegeben werden soll.  
  
3.  Überprüfen Sie im Dialogfeld **Wiedergabekonfiguration** die Einstellungen, und klicken Sie dann auf **OK**. Weitere Informationen zu den Einstellungen im Dialogfeld **Wiedergabekonfiguration** finden Sie unter [Wiedergeben einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) oder [Wiedergeben einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md).  
  
4.  Klicken Sie im Dialogfeld **Wiedergabekonfiguration** auf **OK** , um das erste Ereignis wiederzugeben.  
  
5.  Um die nachfolgenden Ereignisse wiederzugeben, klicken Sie im Menü **Wiedergabe** auf **Schritt**, oder drücken Sie F10. Klicken Sie für jedes Ereignis entweder auf **Schritt** , oder drücken Sie F10.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wiedergeben von Ablaufverfolgungen](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
