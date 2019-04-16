---
title: Sys.dm_exec_query_plan_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_plan_stats
- sys.dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats
helpviewer_keywords:
- sys.dm_exec_query_plan_stats management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfacb
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 62ddfda48429b99558b987cd06c95e96d62702fa
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582097"
---
# <a name="sysdmexecqueryplanstats-transact-sql"></a>sys.dm_exec_query_plan_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Gibt die Darstellung der letzten bekannten tatsächlicher Ausführungsplan für einen zuvor zwischengespeicherten Abfrageplan zurück. 

## <a name="syntax"></a>Syntax

```
sys.dm_exec_query_plan_stats(plan_handle)  
``` 

## <a name="arguments"></a>Argumente 
*plan_handle*  
Ist ein Token, die eindeutig einen Abfrageplan für die Ausführung für einen Batch, die ausgeführt wurde und der Plan im Plancache befindet, oder wird gerade ausgeführt. *plan_handle* ist **varbinary(64)**   

*plan_handle* kann aus den folgenden dynamischen Verwaltungsobjekten abgerufen werden:  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  

## <a name="table-returned"></a>Zurückgegebene Tabelle

|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|
|**dbid**|**smallint**|ID der Kontextdatenbank, die gültig war, als die diesem Plan entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung kompiliert wurde. Für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen, die ID der Datenbank, in der die Anweisungen kompiliert wurden.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**objectid**|**int**|ID des Objekts (z. B. gespeicherte Prozedur oder benutzerdefinierte Funktion) für diesen Abfrageplan. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**number**|**smallint**|Gespeicherte Prozedur mit ganzer Zahl. Eine Gruppe von Prozeduren für die **orders** -Anwendung kann z. B. die Namen **orderproc;1**, **orderproc;2**usw. haben. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**encrypted**|**bit**|Zeigt an, ob die entsprechende Prozedur verschlüsselt ist.<br /><br /> 0 = nicht verschlüsselt<br /><br /> 1 = verschlüsselt<br /><br /> NULL-Werte sind in der Spalte nicht zulässig.|  
|**query_plan**|**xml**|Enthält die letzten bekannten Laufzeit showplandarstellung des den tatsächlichen Abfrageausführungsplan an, die mit angegeben wird *Plan_handle*. Der Showplan liegt im XML-Format vor. Für jeden Batch, der z. B. Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, Aufrufe von gespeicherten Prozeduren und benutzerdefinierten Funktionen enthält, wird jeweils ein Plan generiert.<br /><br /> Die Spalte lässt NULL-Werte zu.| 

## <a name="remarks"></a>Hinweise
Dieser Systemfunktion steht ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4.

Hierbei handelt es sich um ein optionales Feature, für das das [Ablaufverfolgungsflag](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 aktiviert sein muss.   

Dieser Systemfunktion funktioniert die **einfache** abfrageausführungsstatistik profilerstellungsinfrastruktur. Weitere Informationen finden Sie unter [Profilerstellungsinfrastruktur für Abfragen](../../relational-databases/performance/query-profiling-infrastructure.md).  

Unter den folgenden Bedingungen wird eine Showplanausgabe **entspricht eines tatsächlichen Ausführungsplans** wird zurückgegeben, der **Query_plan** Spalte der zurückgegebenen Tabelle für **sys.dm_exec_query_plan_ Statistiken**:  

-   Der Plan finden Sie im [dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   Die auszuführende Abfrage ist komplex ' oder ' Ressourcenverbrauch.

Unter den folgenden Bedingungen wird eine **vereinfachte <sup>1</sup>**  Showplan-Ausgabe wird zurückgegeben, der **Query_plan** Spalte der zurückgegebenen Tabelle für **sys.dm_exec_ Query_plan_stats**:  

-   Der Plan finden Sie im [dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   Die Abfrage ist recht einfach und in der Regel als Teil einer OLTP-Workload kategorisiert.

<sup>1</sup> Dies bezieht sich auf einen Showplan erstellen, die nur den Stamm-Knoten-Operator (auswählen) enthält. Für [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4 nur Dies bezieht sich auf den zwischengespeicherten Plan als dm_exec_cached_plans erhältlich.

Unter den folgenden Bedingungen **wird keine Ausgabe zurückgegeben** aus **sys.dm_exec_query_plan_stats**:

-   Der Abfrageplan, der mithilfe des Parameters *Plan_handle* aus dem Plancache entfernt wurde.     
    **OR**    
-   Der Abfrageplan konnte nicht im vornherein zwischengespeichert werden können. Weitere Informationen finden Sie unter [Ausführung planen Zwischenspeichern und Wiederverwenden von ](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse).
  
> [!NOTE] 
> Aufgrund einer Beschränkung der im **xml** -Datentyp zulässigen Anzahl geschachtelter Ebenen kann **sys.dm_exec_query_plan** keine Abfragepläne zurückgeben, die 128 oder mehr Ebenen geschachtelter Elemente aufweisen. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese Bedingung verhindert, dass den Abfrageplan zurückgeben und generiert [Fehler 6335 wurde](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-6000-to-6999). In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 und höheren Versionen gibt die **query_plan** -Spalte NULL zurück.  

## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  

## <a name="examples"></a>Beispiele  
  
### <a name="a-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan"></a>A. Zu guter Letzt suchen bekannte tatsächlichen Abfrageausführungsplan für einen bestimmten zwischengespeicherten plan  
 Das folgende Beispiel fragt **dm_exec_cached_plans** finden Sie die interessanten Plan, und kopieren die `plan_handle` aus der Ausgabe.  
  
```sql  
SELECT * FROM sys.dm_exec_cached_plans;  
GO  
```  
  
Klicken Sie dann, um den letzten bekannten der eigentlichen Abfrageausführungsplan zu erhalten, verwenden den kopierten `plan_handle` mit der Systemfunktion **sys.dm_exec_query_plan_stats**.  
  
```sql  
SELECT * FROM sys.dm_exec_query_plan_stats(< copied plan_handle >);  
GO  
```   

### <a name="b-looking-at-last-known-actual-query-execution-plan-for-all-cached-plans"></a>B. Zu guter Letzt suchen bekannte tatsächlichen Abfrageausführungsplan für alle zwischengespeicherten Pläne
  
```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps;  
GO  
```   

### <a name="c-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan-and-query-text"></a>C. Zu guter Letzt suchen bekannte tatsächlichen Abfrageausführungsplan für einen bestimmten zwischengespeicherten Plan und dem Abfragetext

```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps
WHERE st.text LIKE 'SELECT * FROM Person.Person%';  
GO  
```   

## <a name="see-also"></a>Siehe auch
  [Ablaufverfolgungsflags](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Ausführung &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  

