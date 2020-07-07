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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8b8cfc9116440bfba43f16fd1c05bd004fcca0cb
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012662"
---
# <a name="sp_query_store_force_plan-transact-sql"></a>sp_query_store_force_plan (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Ermöglicht das Erzwingen eines bestimmten Plans für eine bestimmte Abfrage.  
  
 Wenn ein Plan für eine bestimmte Abfrage erzwungen wird, wird jedes Mal, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Abfrage gefunden wird, versucht, den Plan im Abfrageoptimierer zu erzwingen. Wenn die Plan Erzwingung fehlschlägt, wird ein erweitertes Ereignis ausgelöst, und der Abfrageoptimierer wird angewiesen, auf die normale Weise zu optimieren.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_query_store_force_plan [ @query_id = ] query_id , [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @query_id = ] query_id`Die ID der Abfrage. *query_id* ist vom Datentyp **bigint**und hat keinen Standardwert.  
  
`[ @plan_id = ] plan_id`Die ID des Abfrage Plans, der erzwungen werden soll. *plan_id* ist vom Datentyp **bigint**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_query_store_remove_plan &#40;TransT-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [Abfragespeicher Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Überwachen der Leistung mithilfe des Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)       
 [Bewährte Methoden für den Abfragespeicher](../../relational-databases/performance/best-practice-with-the-query-store.md#CheckForced)    
  
  
