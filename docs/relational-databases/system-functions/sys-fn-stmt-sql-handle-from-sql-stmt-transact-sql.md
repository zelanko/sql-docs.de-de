---
title: sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 6794e073-0895-4507-aba3-c3545acc843f
caps.latest.revision: 9
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 893a9a89863b8ca1eff9a30e61277f5f779b4f12
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39537760"
---
# <a name="sysfnstmtsqlhandlefromsqlstmt-transact-sql"></a>sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Ruft die **Stmt_sql_handle** für eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung unter Parametrisierung-Typ (einfache oder erzwungene). Dadurch können Sie zum Verweisen auf Abfragen, die in der Abfrage-Store gespeichert sind, mit deren **Stmt_sql_handle** Wenn Sie wissen, dass ihrem Text.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.fn_stmt_sql_handle_from_sql_stmt   
(  
    'query_sql_text',   
    [ query_param_type   
) [;]  
```  
  
## <a name="arguments"></a>Argumente  
 *query_sql_text*  
 Ist der Text der Abfrage im Abfragespeicher, dem das Handle des soll. *Query_sql_text* ist eine **nvarchar(max)**, hat keinen Standardwert.  
  
 *query_param_type*  
 Ist der Parametertyp der Abfrage. *Query_param_type* ist eine **Tinyint**. Folgende Werte sind möglich:  
  
-   NULL-Standardwert ist 0  
  
-   0 – none  
  
-   1 – Benutzer  
  
-   2 – einfach  
  
-   3 – erzwungen  
  
## <a name="columns-returned"></a>Zurückgegebene Spalten  
 Die folgende Tabelle listet die Spalten dieser sys.fn_stmt_sql_handle_from_sql_stmt zurückgibt.  
  
|Spaltenname|Typ|Description|  
|-----------------|----------|-----------------|  
|**statement_sql_handle**|**varbinary(64)**|Die SQL-Handle.|  
|**query_sql_text**|**nvarchar(max)**|Der Text, der die [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**query_parameterization_type**|**tinyint**|Der Typ des Abfrage-Parametrisierung.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **EXECUTE** -Berechtigung für die Datenbank und **löschen** -Berechtigung für der Katalogsichten des Abfragespeichers.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel führt eine Anweisung aus, und verwendet dann `sys.fn_stmt_sql_handle_from_sql_stmt` der SQL-Handle für diese Anweisung zurückgegeben.  
  
```  
SELECT * FROM sys.databases;   
SELECT * FROM sys.fn_stmt_sql_handle_from_sql_stmt('SELECT * FROM sys.databases', NULL);  
```  
  
 Verwenden Sie die Funktion, um die Abfrage von Store-Daten mit anderen dynamischen Verwaltungssichten zu korrelieren. Im folgenden Beispiel:  
  
```  
SELECT qt.query_text_id, q.query_id, qt.query_sql_text, qt.statement_sql_handle,  
q.context_settings_id, qs.statement_context_id   
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_id  
CROSS APPLY sys.fn_stmt_sql_handle_from_sql_stmt (qt.query_sql_text, null) AS fn_handle_from_stmt  
JOIN sys.dm_exec_query_stats AS qs   
    ON fn_handle_from_stmt.statement_sql_handle = qs.statement_sql_handle;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [Sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [Katalogsichten des Abfragespeichers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
