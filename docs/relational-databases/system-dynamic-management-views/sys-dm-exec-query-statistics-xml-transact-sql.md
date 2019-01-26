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
ms.openlocfilehash: 8bb66c5bb9b4f69b32efd7761ae08677ee243fee
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044626"
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

Dieser Systemfunktion funktioniert sowohl **standard** und **einfache** abfrageausführungsstatistik profilerstellungsinfrastruktur.  
  
**Standard** profilerstellungsinfrastruktur Statistics kann mithilfe von aktiviert werden:
  -  [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)
  -  [SET STATISTICS PROFILE AUF](../../t-sql/statements/set-statistics-profile-transact-sql.md)
  -  die `query_post_execution_showplan` erweiterte Ereignisse.  
  
**Lightweight** profilerstellungsinfrastruktur Statistiken finden Sie im [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 und kann aktiviert werden:
  -  Global mit Trace flag 7412.
  -  Mithilfe der [ *Query_thread_profile* ](https://support.microsoft.com/kb/3170113) erweiterte Ereignisse.
  
> [!NOTE]
> Nach der Aktivierung von Ablaufverfolgungsflags 7412 lightweight-profilerstellung wird aktiviert werden, um alle Consumer von den Statistiken zur abfrageausführung profilerstellungsinfrastruktur anstelle der standard-profilerstellung, z. B. die DMV [dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md).
> Standard-profilerstellung wird jedoch immer noch verwendet für die SET STATISTICS XML *Istplan enthalten* Aktion [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)], und `query_post_execution_showplan` xEvent.

> [!IMPORTANT]
> In TPC-C wie workloadtests Fügt einen 1,5 bis 2 Prozent Mehraufwand hinzu, wenn Sie die einfache profilerstellung statistikinfrastruktur zu aktivieren. Im Gegensatz dazu kann die standardmäßigen profilerstellung statistikinfrastruktur bis zu 90 Prozent Mehraufwand für das gleiche Szenario für die Workload hinzufügen.

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

