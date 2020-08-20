---
description: sys.sp_xtp_control_query_exec_stats (Transact-SQL)
title: sys. sp_xtp_control_query_exec_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_query_exec_stats_TSQL
- sys.sp_xtp_control_query_exec_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_query_exec_stats
ms.assetid: 4838125d-ad1e-479e-b7d2-42655e8f4f02
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0963985b2f6f83d9be8c19be35fd16b0451dda8a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473416"
---
# <a name="syssp_xtp_control_query_exec_stats-transact-sql"></a>sys.sp_xtp_control_query_exec_stats (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Aktiviert die Statistiksammlung pro Abfrage für alle systemintern kompilierten gespeicherten Prozeduren der Instanz oder für bestimmte systemintern kompilierte gespeicherte Prozeduren.  
  
 Die Leistung nimmt ab, wenn Sie die Statistiksammlung aktivieren. Wenn Sie eine Problembehandlung nur für eine bzw. einige wenige systemintern kompilierte gespeicherte Prozeduren durchführen möchten, können Sie die Statistiksammlung nur für diese bestimmten systemintern kompilierten gespeicherten Prozeduren aktivieren.  
  
 Informationen zum Aktivieren der Statistik Sammlung auf der Prozedur Ebene für alle System intern kompilierten gespeicherten Prozeduren finden Sie unter [sys. sp_xtp_control_proc_exec_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_xtp_control_query_exec_stats [ [ @new_collection_value = ] collection_value ],  
[ [ @database_id = ] database_id   
[ , [ @xtp_object_id = ] procedure_id ] ,   
[ @old_collection_value] ]  
```  
  
## <a name="arguments"></a>Argumente  
 @new_collection_value = *Wert*  
 Bestimmt, ob die Statistiksammlung auf Prozedurebene aktiviert (1) oder deaktiviert (0) ist.  
  
 @new_collection_value wird auf NULL festgelegt, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestartet wird.  
  
 @database_id = = *database_id*, @xtp_object_id = *procedure_id*  
 Die Datenbank-ID und Objekt-ID der systemintern kompilierten gespeicherten Prozedur. Wenn die Statistik Sammlung für die-Instanz aktiviert ist ([sys. sp_xtp_control_proc_exec_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md)), werden Statistiken für eine System intern kompilierte gespeicherte Prozedur gesammelt. Wenn Sie die Statistiksammlung auf der Instanz deaktivieren, wird die Statistiksammlung für die einzelnen systemintern kompilierten gespeicherten Prozeduren nicht deaktiviert.  
  
 Verwenden Sie [sys. Database &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md), [sys. Procedures &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md), [DB_ID &#40;Transact-SQL&#41;](../../t-sql/functions/db-id-transact-sql.md)oder [object_id &#40;Transact-SQL-&#41;](../../t-sql/functions/object-id-transact-sql.md) , um IDs für eine Datenbank und eine gespeicherte Prozedur abzurufen.  
  
 @old_collection_value = *Wert*  
 Gibt den aktuellen Status zurück.  
  
## <a name="return-code"></a>Rückgabe Code  
 0 für Erfolg. Ungleich 0 für Fehler.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen sysadmin-Rolle.  
  
## <a name="code-sample"></a>Codebeispiel  
 Im folgenden Codebeispiel wird gezeigt, wie die Statistiksammlung für alle systemintern kompilierten gespeicherten Prozeduren für die Instanz und dann für eine bestimmte systemintern kompilierte gespeicherte Prozedur aktiviert wird.  
  
```sql   
DECLARE @c bit  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1;  
  
EXEC sp_xtp_control_query_exec_stats @old_collection_value=@c output;  
SELECT @c AS 'collection status';  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1,   
@database_id = 5, @xtp_object_id = 341576255;  
  
EXEC sp_xtp_control_query_exec_stats @database_id = 5,   
@xtp_object_id = 341576255, @old_collection_value=@c output;  
  
SELECT @c AS 'collection status';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
