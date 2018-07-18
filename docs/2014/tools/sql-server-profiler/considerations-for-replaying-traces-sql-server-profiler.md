---
title: Überlegungen zum Wiedergeben von Ablaufverfolgungen (SQL Server Profiler) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3abe4aaf030ff27be19cc081f8b2d6d87029055e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232563"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>Überlegungen zum Wiedergeben von Ablaufverfolgungen (SQL Server Profiler)
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] können die folgenden Arten von Ablaufverfolgungen nicht wiedergegeben werden:  
  
-   Ablaufverfolgungen, die die Transaktionsreplikation und andere Transaktionsprotokollaktivität enthalten. Diese Ereignisse werden ausgelassen. Andere Replikationsarten markieren nicht das Transaktionsprotokoll und sind nicht betroffen.  
  
-   Ablaufverfolgungen, die Vorgänge mit global eindeutigen Bezeichnern (Globally Unique Identifier, GUID) enthalten. Diese Ereignisse werden ausgelassen.  
  
-   Ablaufverfolgungen, die Vorgänge mit den Spalten **text**, **ntext**und **image** mit dem Hilfsprogramm **bcp** , den Anweisungen BULK INSERT, READTEXT, WRITETEXT und UPDATETEXT und Volltextvorgängen enthalten. Diese Ereignisse werden ausgelassen.  
  
-   Ablaufverfolgungen, die eine Sitzungsbindung enthalten: gespeicherte Systemprozeduren **sp_getbindtoken** und **sp_bindsession** . Diese Ereignisse werden ausgelassen.  
  
> [!NOTE]  
>  Wenn Sie nicht die vorkonfigurierte Wiedergabevorlage (**TSQL_Replay**) verwenden und nicht alle erforderlichen Daten erfassen, wird die Ablaufverfolgung von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] nicht wiedergegeben. Weitere Informationen finden Sie unter [Replay Requirements](replay-requirements.md).  
  
 Informationen zu den Berechtigungen, die zum Wiedergeben einer Ablaufverfolgung erforderlich sind, finden Sie unter [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).  
  
## <a name="see-also"></a>Siehe auch  
 [bcp (Hilfsprogramm)](../bcp-utility.md)   
 [Ereignisklassen in SQL Server: Referenz](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)   
 [sp_bindsession (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql)   
 [WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql)   
 [UPDATETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/updatetext-transact-sql)  
  
  
