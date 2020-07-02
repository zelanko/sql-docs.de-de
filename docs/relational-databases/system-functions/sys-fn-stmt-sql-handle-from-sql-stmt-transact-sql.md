---
title: sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 6794e073-0895-4507-aba3-c3545acc843f
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7f7111f4e0f67e1102712c140737b68914feada6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85652021"
---
# <a name="sysfn_stmt_sql_handle_from_sql_stmt-transact-sql"></a>sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asdw](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asdw.md)]

  Ruft den **stmt_sql_handle** für eine [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung unter dem angegebenen parameterisierungstyp (einfach oder erzwungen) ab. Dies ermöglicht es Ihnen, auf Abfragen zu verweisen, die in der Abfragespeicher gespeichert sind, indem Sie Ihre **stmt_sql_handle** verwenden, wenn Sie Ihren Text kennen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Der Text der Abfrage im Abfrage Speicher, für den Sie das Handle benötigen. *query_sql_text* ist vom Datentyp **nvarchar (max)** und hat keinen Standardwert.  
  
 *query_param_type*  
 Der Parametertyp der Abfrage. *query_param_type* ist ein **tinyint**-Wert. Mögliche Werte:  
  
-   NULL-der Standardwert ist 0.  
  
-   0 – Keine  
  
-   1-Benutzer  
  
-   2: einfach  
  
-   3-erzwungene  
  
## <a name="columns-returned"></a>Zurückgegebene Spalten  
 In der folgenden Tabelle sind die Spalten aufgelistet, die von sys. fn_stmt_sql_handle_from_sql_stmt zurückgegeben werden.  
  
|Spaltenname|Typ|BESCHREIBUNG|  
|-----------------|----------|-----------------|  
|**statement_sql_handle**|**varbinary(64)**|Das SQL-handle.|  
|**query_sql_text**|**nvarchar(max)**|Der Text der [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung.|  
|**query_parameterization_type**|**tinyint**|Der parameterisierungstyp der Abfrage.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **Execute** -Berechtigung für die Datenbank und die **Delete** -Berechtigung für die Katalog Sichten des Abfrage Speicher.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine-Anweisung ausgeführt, und dann wird verwendet, `sys.fn_stmt_sql_handle_from_sql_stmt` um das SQL-Handle dieser Anweisung zurückzugeben.  
  
```  
SELECT * FROM sys.databases;   
SELECT * FROM sys.fn_stmt_sql_handle_from_sql_stmt('SELECT * FROM sys.databases', NULL);  
```  
  
 Verwenden Sie die-Funktion, um Abfragespeicher Daten mit anderen dynamischen Verwaltungs Sichten zu korrelieren. Im Beispiel unten geschieht Folgendes:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_query_store_force_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;TransT-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [Abfragespeicher Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
