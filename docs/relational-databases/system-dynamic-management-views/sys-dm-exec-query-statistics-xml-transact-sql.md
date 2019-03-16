---
title: sys.dm_exec_query_statistics_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 63e1d22670929448110083c31e9900e462d576bc
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072304"
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Gibt Abfrageplan Ausführung für in-Flight-Anforderungen. Verwenden Sie diese dynamische Verwaltungssicht, um die Showplan XML mit übergangsstatistiken abzurufen. 

## <a name="syntax"></a>Syntax

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Argumente 
*session_id*  
 Führt die Sitzungs-Id den Batch gesucht werden soll. *Sitzungs-ID* ist **Smallint**. *Sitzungs-ID* aus den folgenden dynamischen Verwaltungsobjekten abgerufen werden kann:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Zurückgegebene Tabelle

|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|ID der Sitzung. Lässt keine NULL-Werte zu.|
|request_id|**int**|ID der Anforderung. Lässt keine NULL-Werte zu.|
|sql_handle|**varbinary(64)**|Hashzuordnung des SQL-Text der Anforderung. NULL-Werte sind zulässig.|
|plan_handle|**varbinary(64)**|Hashzuordnung des Abfrageplans. NULL-Werte sind zulässig.|
|query_plan|**xml**|Showplan XML mit partiellen Statistiken. NULL-Werte sind zulässig.|

## <a name="remarks"></a>Hinweise
Dieser Systemfunktion steht ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1. Finden Sie im KB [3190871](https://support.microsoft.com/en-us/help/3190871)

Dieser Systemfunktion funktioniert sowohl **standard** und **einfache** abfrageausführungsstatistik profilerstellungsinfrastruktur. Weitere Informationen finden Sie unter [Profilerstellungsinfrastruktur für Abfragen](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md).  

## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  

## <a name="examples"></a>Beispiele  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. Planung und Ausführung Statistiken für aktive Abfragen für einen ausgeführten Batch ansehen  
 Das folgende Beispiel fragt **Sys. dm_exec_requests** auf die entsprechende Abfrage kopieren zu suchen und dessen `session_id` aus der Ausgabe.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Klicken Sie dann, um den Abfrageplan und Ausführungskontext Statistiken für aktive Abfragen zu erhalten, verwenden den kopierten `session_id` mit der Systemfunktion **dm_exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 Oder für alle ausgeführten Anforderungen kombiniert.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>Siehe auch
  [Ablaufverfolgungsflags](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

