---
title: Sp_query_store_force_plan (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SYS.SP_QUERY_STORE_FORCE_PLAN
- SP_QUERY_STORE_FORCE_PLAN
- SYS.SP_QUERY_STORE_FORCE_PLAN_TSQL
- SP_QUERY_STORE_FORCE_PLAN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_force_plan
- sp_query_store_force_plan
ms.assetid: 0068f258-b998-4e4e-b47b-e375157c8213
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 02ccb9f5c9614b10d43c9e886892a9f8d26779c3
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43079799"
---
# <a name="spquerystoreforceplan-transact-sql"></a>Sp_query_store_force_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Ermöglicht das Erzwingen eines bestimmten Plans für eine bestimmte Abfrage.  
  
 Wenn ein Plan erzwungen wird für eine bestimmte Abfrage jedes Mal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] findet die Abfrage, wird versucht, den Plan in der Abfrageoptimierer zu erzwingen. Wenn das Erzwingen eines Plans ein Fehler auftritt, ein XEvent wird ausgelöst, und der Optimierer angewiesen, auf die übliche Weise zu optimieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_query_store_force_plan [ @query_id = ] query_id , [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@query_id =** ] *Query_id*  
 Ist die Id der Abfrage. *Query_id* ist eine **Bigint**, hat keinen Standardwert.  
  
 [  **@plan_id =** ] *' plan_id '*  
 Ist die Id des Abfrageplans erzwungen werden. *Plan_id* ist eine **Bigint**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **EXECUTE** -Berechtigung für die Datenbank und **einfügen**, **UPDATE**, und **löschen** -Berechtigung für den Abfrage-Store-Katalog Ansichten.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt Informationen zu den Abfragen im Abfragespeicher zurück.  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Nachdem Sie identifiziert die Query_id und ' plan_id ', die Sie erzwingen möchten, verwenden Sie das folgende Beispiel, um der Abfrage verwendet einen Plan zu erzwingen.  
  
```  
EXEC sp_query_store_force_plan 3, 3;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [Katalogsichten des Abfragespeichers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)  
  
  
