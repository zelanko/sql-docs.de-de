---
title: Festlegen eines Ablaufverfolgungsfilters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6e3ecc4b125d226fc2cdf6dbe241e0ce017eae6
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126690"
---
# <a name="set-a-trace-filter-transact-sql"></a>Festlegen eines Ablaufverfolgungsfilters (Transact-SQL)
  In diesem Thema wird die Vorgehensweise zum Verwenden gespeicherter Prozeduren zum Erstellen eines Filters beschrieben, von dem nur die von Ihnen benötigten Informationen zum Nachverfolgen eines Ereignisses abgerufen werden.  
  
### <a name="to-set-a-trace-filter"></a>So legen Sie einen Ablaufverfolgungsfilter fest  
  
1.  Wenn die Ablaufverfolgung bereits ausgeführt wird, führen Sie **sp_trace_setstatus** mit **@status = 0** aus, um die Ablaufverfolgung zu beenden.  
  
2.  Führen Sie **sp_trace_setfilter** aus, um den Informationstyp zu konfigurieren, der für das nachzuverfolgende Ereignis abgerufen werden soll.  
  
> [!IMPORTANT]
>  Im Gegensatz zu regulären gespeicherten Prozeduren werden die Parameter aller [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] gespeicherte Prozeduren (<strong>Sp_trace_*Xx*</strong>) genau eingegeben und unterstützen die automatische datentypkonvertierung nicht. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Filtern einer Ablaufverfolgung](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Gespeicherte Prozeduren von SQL Server Profiler &#40;SQL Server Profiler&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
