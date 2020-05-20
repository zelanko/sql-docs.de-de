---
title: sys. sp_xtp_control_proc_exec_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_proc_exec_stats
- sys.sp_xtp_control_proc_exec_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_proc_exec_stats
ms.assetid: f5119808-76a1-4522-8529-9e02ee39adcb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 940caad59adf191e0ed1fe550707788de820c6b7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82814505"
---
# <a name="syssp_xtp_control_proc_exec_stats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Aktiviert die Statistiksammlung für systemintern kompilierte gespeicherte Prozeduren für die Instanz.  
  
 Informationen zum Aktivieren der Statistik Sammlung auf Abfrage Ebene für System intern kompilierte gespeicherte Prozeduren finden Sie unter [sys. sp_xtp_control_query_exec_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>Argumente  
 @new_collection_value= *Wert*  
 Bestimmt, ob die Statistiksammlung auf Prozedurebene aktiviert (1) oder deaktiviert (0) ist.  
  
 @new_collection_valuewird auf NULL festgelegt, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder die Datenbank gestartet wird.  
  
 @old_collection_value= *Wert*  
 Gibt den aktuellen Status zurück.  
  
## <a name="return-code"></a>Rückgabe Code  
 0 für Erfolg. Ungleich 0 für Fehler.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen sysadmin-Rolle.  
  
## <a name="code-samples"></a>Codebeispiele  
 So legen Sie @new_collection_value den Wert von fest und Fragen ihn ab@new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
