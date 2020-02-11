---
title: sys. dm_exec_query_plan_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2019
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
ms.openlocfilehash: 279f1a8fbe3ec78dc0cae30d9879615b169075bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75656992"
---
# <a name="sysdm_exec_query_plan_stats-transact-sql"></a>sys. dm_exec_query_plan_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Gibt den-Wert des letzten bekannten tatsächlichen Ausführungs Plans für einen zuvor zwischengespeicherten Abfrageplan zurück.

## <a name="syntax"></a>Syntax

```
sys.dm_exec_query_plan_stats(plan_handle)  
``` 

## <a name="arguments"></a>Argumente 
*plan_handle*  
Ein Token, das einen Abfrage Ausführungsplan für einen Batch eindeutig identifiziert, der ausgeführt wurde und dessen Plan sich im Plancache befindet oder gerade ausgeführt wird. *plan_handle* ist vom Datentyp **varbinary (64)**.   


  *plan_handle* kann aus den folgenden dynamischen Verwaltungsobjekten abgerufen werden:  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys. dm_exec_procedure_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys. dm_exec_trigger_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  

## <a name="table-returned"></a>Zurückgegebene Tabelle

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|
|**DBID**|**smallint**|ID der Kontextdatenbank, die gültig war, als die diesem Plan entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung kompiliert wurde. Für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen, die ID der Datenbank, in der die Anweisungen kompiliert wurden.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**ObjectID**|**int**|ID des Objekts (z. B. gespeicherte Prozedur oder benutzerdefinierte Funktion) für diesen Abfrageplan. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**Zahl**|**smallint**|Gespeicherte Prozedur mit ganzer Zahl. Eine Gruppe von Prozeduren für die **orders**-Anwendung kann z. B. die Namen **orderproc;1**, **orderproc;2** usw. haben. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**.**|**bit**|Zeigt an, ob die entsprechende Prozedur verschlüsselt ist.<br /><br /> 0 = nicht verschlüsselt<br /><br /> 1 = verschlüsselt<br /><br /> NULL-Werte sind in der Spalte nicht zulässig.|  
|**query_plan**|**basi**|Enthält die letzte bekannte Runtime-Showplan-Darstellung des tatsächlichen Abfrage Ausführungs Plans, der mit *plan_handle*angegeben wird. Der Showplan liegt im XML-Format vor. Für jeden Batch, der z. B. Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, Aufrufe von gespeicherten Prozeduren und benutzerdefinierten Funktionen enthält, wird jeweils ein Plan generiert.<br /><br /> Die Spalte lässt NULL-Werte zu.| 

## <a name="remarks"></a>Bemerkungen
Diese Systemfunktion ist ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2,4 verfügbar.

Hierbei handelt es sich um ein optionales Feature, für das das [Ablaufverfolgungsflag](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 aktiviert sein muss. Informationen dazu, wie Sie dies ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.5 auf der Datenbankebene erreichen, finden Sie in der LAST_QUERY_PLAN_STATS-Option unter [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Diese Systemfunktion funktioniert unter der **Lightweight** -Infrastruktur für die Abfrage Ausführungs Statistik-Profilerstellung. Weitere Informationen finden Sie unter [Infrastruktur für die Abfrage Profilerstellung](../../relational-databases/performance/query-profiling-infrastructure.md).  

Die Showplan-Ausgabe von sys. dm_exec_query_plan_stats enthält die folgenden Informationen:
-  Alle im zwischengespeicherten Plan gefundenen Kompilierzeit Informationen
-  Laufzeitinformationen, z. b. die tatsächliche Anzahl von Zeilen pro Operator, die gesamte Abfrage-CPU-Zeit und die Ausführungszeit, Überlauf Warnungen, tatsächlicher DOP, maximal verwendeter Arbeitsspeicher und zugewiesener Arbeitsspeicher

Unter den folgenden Bedingungen wird eine Showplan-Ausgabe **, die einem tatsächlichen Ausführungsplan entspricht** , in der **query_plan** -Spalte der zurückgegebenen Tabelle für **sys. dm_exec_query_plan_stats**zurückgegeben:  

-   Der Plan kann in [sys. dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)gefunden werden.     
    **AND**    
-   Die ausgeführte Abfrage ist komplex oder Ressourcen aufwendig.

Unter den folgenden Bedingungen wird eine **vereinfachte <sup>1</sup> ** Showplan-Ausgabe in der **query_plan** -Spalte der zurückgegebenen Tabelle für **sys. dm_exec_query_plan_stats**zurückgegeben:  

-   Der Plan kann in [sys. dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)gefunden werden.     
    **AND**    
-   Die Abfrage ist einfach genug und wird normalerweise als Teil einer OLTP-Arbeitsauslastung kategorisiert.

<sup>1</sup> ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2,5 bezieht sich dies auf einen Showplan, der nur den Stamm Knoten Operator (Select) enthält. Für [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2,4 bezieht sich dies auf den zwischengespeicherten Plan, `sys.dm_exec_cached_plans`der über verfügbar ist.

Unter den folgenden Bedingungen **wird keine Ausgabe** aus **sys. dm_exec_query_plan_stats**zurückgegeben:

-   Der mit *plan_handle* angegebene Abfrageplan wurde aus dem Plancache entfernt.     
    **oder**    
-   Der Abfrageplan konnte nicht an erster Stelle zwischengespeichert werden. Weitere Informationen finden Sie unter zwischen [Speichern und wieder verwenden von Ausführungsplänen ](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse).
  
> [!NOTE] 
> Aufgrund einer Beschränkung der im **xml** -Datentyp zulässigen Anzahl geschachtelter Ebenen kann **sys.dm_exec_query_plan** keine Abfragepläne zurückgeben, die 128 oder mehr Ebenen geschachtelter Elemente aufweisen. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verhinderte diese Bedingung, dass der Abfrageplan nicht zurückgegeben wurde, und generiert den [Fehler 6335](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-6000-to-6999). In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 und höheren Versionen gibt die **query_plan** -Spalte NULL zurück.  

## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  

## <a name="examples"></a>Beispiele  
  
### <a name="a-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan"></a>A. Betrachten des letzten bekannten Abfrage Ausführungs Plans für einen bestimmten zwischengespeicherten Plan  
 Im folgenden Beispiel wird **sys. dm_exec_cached_plans** abgefragt, um den interessanten Plan zu `plan_handle` suchen und dessen aus der Ausgabe zu kopieren.  
  
```sql  
SELECT * FROM sys.dm_exec_cached_plans;  
GO  
```  
  
Verwenden Sie dann zum Abrufen des letzten bekannten Abfrage Ausführungs Plans den, der mit `plan_handle` der Systemfunktion **sys. dm_exec_query_plan_stats**kopiert wurde.  
  
```sql  
SELECT * FROM sys.dm_exec_query_plan_stats(< copied plan_handle >);  
GO  
```   

### <a name="b-looking-at-last-known-actual-query-execution-plan-for-all-cached-plans"></a>B. Betrachten des letzten bekannten Abfrage Ausführungs Plans für alle zwischengespeicherten Pläne
  
```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps;  
GO  
```   

### <a name="c-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan-and-query-text"></a>C. Betrachten des letzten bekannten Abfrage Ausführungs Plans für einen bestimmten zwischengespeicherten Plan und Abfragetext

```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps
WHERE st.text LIKE 'SELECT * FROM Person.Person%';  
GO  
```   

### <a name="d-look-at-cached-events-for-trigger"></a>D: Suchen nach zwischengespeicherten Ereignissen für den Triggertyp

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

## <a name="see-also"></a>Weitere Informationen
  [Laufverfolgungsflags](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Ausführung &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  

