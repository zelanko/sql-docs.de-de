---
title: Wiedergeben eines Transact-SQL-Skripts (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- scripts [SQL Server], traces
- replaying traces
ms.assetid: 9c0eb222-e6e3-4bc1-a25f-a41e962d361b
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f380638bca07e1db034df0c35209e144130b4a6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149762"
---
# <a name="replay-a-transact-sql-script-sql-server-profiler"></a>Wiedergeben eines Transact-SQL-Skripts (SQL Server Profiler)
  Verwenden Sie beim Testen von möglichen Lösungen für ein Leistungsproblem [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts wiederzugeben, und vergleichen Sie die Leistung vor und nach dem Ändern.  
  
### <a name="to-replay-a-transact-sql-script"></a>So geben Sie ein Transact-SQL-Skript wieder  
  
1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie dann auf **Skriptdatei**.  
  
2.  Wählen Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei aus, die Sie öffnen möchten. Stellen Sie sicher, dass das [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript die zum Wiedergeben erforderlichen Ereignisse enthält. Weitere Informationen finden Sie unter [Replay Requirements](replay-requirements.md).  
  
3.  Klicken Sie im Menü **Wiedergeben** auf **Start**, und stellen Sie eine Verbindung mit dem Server her, auf dem das Skript wiedergegeben werden soll.  
  
4.  Überprüfen Sie im Dialogfeld **Wiedergabekonfiguration** die Einstellungen, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiedergeben von Ablaufverfolgungen](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  