---
title: sp_query_store_force_plan (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b34cf94a2ab6cfec601d41b02bf32b00f0eb3b41
ms.sourcegitcommit: 816ff47eeab157c66e0f75f18897a63dc8033502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71207722"
---
# <a name="sp_query_store_force_plan-transact-sql"></a>sp_query_store_force_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Ermöglicht das Erzwingen eines bestimmten Plans für eine bestimmte Abfrage.  
  
 Wenn ein Plan für eine bestimmte Abfrage erzwungen wird, wird jedes Mal, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Abfrage findet, versucht, den Plan im Abfrageoptimierer zu erzwingen. Wenn die Plan Erzwingung fehlschlägt, wird ein erweitertes Ereignis ausgelöst, und der Abfrageoptimierer wird angewiesen, auf die normale Weise zu optimieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_query_store_force_plan [ @query_id = ] query_id , [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @query_id = ] query_id` ist die ID der Abfrage. *query_id* ist vom Datentyp **bigint**und hat keinen Standardwert.  
  
`[ @plan_id = ] plan_id` ist die ID des Abfrage Plans, der erzwungen werden soll. *plan_id* ist vom Datentyp **bigint**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Remarks  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **Alter** -Berechtigung für die Datenbank.
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den Abfragen im Abfrage Speicher zurückgegeben.  
  
```sql  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Nachdem Sie die query_id und plan_id identifiziert haben, die Sie erzwingen möchten, verwenden Sie das folgende Beispiel, um zu erzwingen, dass die Abfrage einen Plan verwendet.  
  
```sql  
EXEC sp_query_store_force_plan 3, 3;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [Katalogsichten des Abfragespeichers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Überwachen der Leistung mithilfe der Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md) -   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)       
 [Bewährte Methoden für den Abfragespeicher](../../relational-databases/performance/best-practice-with-the-query-store.md#CheckForced)    
  
  
