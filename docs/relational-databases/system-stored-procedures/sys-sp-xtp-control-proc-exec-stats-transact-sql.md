---
description: sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
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
ms.openlocfilehash: e189cd4e7a5ec9f488cce78ee6cc159c8700a463
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473399"
---
# <a name="syssp_xtp_control_proc_exec_stats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Aktiviert die Statistiksammlung für systemintern kompilierte gespeicherte Prozeduren für die Instanz.  
  
 Informationen zum Aktivieren der Statistik Sammlung auf Abfrage Ebene für System intern kompilierte gespeicherte Prozeduren finden Sie unter [sys. sp_xtp_control_query_exec_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>Argumente  
 @new_collection_value = *Wert*  
 Bestimmt, ob die Statistiksammlung auf Prozedurebene aktiviert (1) oder deaktiviert (0) ist.  
  
 @new_collection_value wird auf NULL festgelegt, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder die Datenbank gestartet wird.  
  
 @old_collection_value = *Wert*  
 Gibt den aktuellen Status zurück.  
  
## <a name="return-code"></a>Rückgabe Code  
 0 für Erfolg. Ungleich 0 für Fehler.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen sysadmin-Rolle.  
  
## <a name="code-samples"></a>Codebeispiele  
 So legen Sie @new_collection_value den Wert von fest und Fragen ihn ab @new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
