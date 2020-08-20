---
description: Löschen einer Ablaufverfolgung (Transact-SQL)
title: Löschen einer Ablaufverfolgung (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3264c9fe9622bdddee3aecd002193c245c5b457
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455371"
---
# <a name="delete-a-trace-transact-sql"></a>Löschen einer Ablaufverfolgung (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie Sie mithilfe von gespeicherten Prozeduren eine Ablaufverfolgung löschen.  
  
 Ein Beispiel zum Verwenden gespeicherter Prozeduren der Ablaufverfolgung finden Sie unter [Erstellen einer Ablaufverfolgung &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
### <a name="to-delete-a-trace"></a>So löschen Sie eine Ablaufverfolgung  
  
1.  Führen Sie **sp_trace_setstatus** aus, indem Sie `@status = 0` angeben, um die Ablaufverfolgung zu beenden.  
  
2.  Führen Sie **sp_trace_setstatus** aus, indem Sie `@status = 2` angeben, um die Ablaufverfolgung zu schließen und die zugehörigen Informationen vom Server zu löschen.  
  
> [!NOTE]  
>  Eine Ablaufverfolgung muss beendet werden, bevor sie geschlossen werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren von SQL Server Profiler &#40;SQL Server Profiler&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  
