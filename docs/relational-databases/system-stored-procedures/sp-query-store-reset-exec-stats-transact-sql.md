---
title: sp_query_store_reset_exec_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_query_store_reset_exec_stats_TSQL
- sys.sp_query_store_reset_exec_stats_TSQL
- sys.sp_query_store_reset_exec_stats
- sp_query_store_reset_exec_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_query_store_reset_exec_stats
- sys.sp_query_store_reset_exec_stats
ms.assetid: 899df1ff-e871-44df-9361-f3b87ac3ea31
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8d818d6ebf8c00d788f422c19b0bf32edaff0c24
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012625"
---
# <a name="sp_query_store_reset_exec_stats-transact-sql"></a>sp_query_store_reset_exec_stats (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Löscht die Lauf Zeit Statistiken für einen bestimmten Abfrageplan aus dem Abfrage Speicher.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_query_store_reset_exec_stats [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @plan_id = ] plan_id`Die ID des Abfrage Plans, der gelöscht werden soll. *plan_id* ist vom Datentyp **bigint**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **Alter** -Berechtigung für die Datenbank. 
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den Abfragen im Abfrage Speicher zurückgegeben.  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Nachdem Sie die plan_id identifiziert haben, für die Sie die Statistik löschen möchten, verwenden Sie das folgende Beispiel, um die Ausführungs Statistik für einen bestimmten Abfrageplan zu löschen. In diesem Beispiel werden die Ausführungs Statistiken für die Plan Nummer 3 gelöscht.  
  
```  
EXEC sp_query_store_reset_exec_stats 3;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_query_store_force_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;TransT-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [Abfragespeicher Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
