---
description: sys. dm_exec_query_plan_stats (Transact-SQL)
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
ms.openlocfilehash: 0ab11e74205f47d50e927680081e8e13dfee37fb
ms.sourcegitcommit: 9be0047805ff14e26710cfbc6e10d6d6809e8b2c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "89042477"
---
# <a name="sysdm_exec_query_plan_stats-transact-sql"></a>sys. dm_exec_query_plan_stats (Transact-SQL)
[!INCLUDE[SQL Server 2019](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Gibt den-Wert des letzten bekannten tatsächlichen Ausführungs Plans für einen zuvor zwischengespeicherten Abfrageplan zurück.

## <a name="syntax"></a>Syntax

```
sys.dm_exec_query_plan_stats(plan_handle)  
``` 

## <a name="arguments"></a>Argumente 
*plan_handle*  
Ein Token, das einen Abfrage Ausführungsplan für einen Batch eindeutig identifiziert, der ausgeführt wurde und dessen Plan sich im Plancache befindet oder gerade ausgeführt wird. *plan_handle* ist **varbinary(64)**   

*plan_handle* kann aus den folgenden dynamischen Verwaltungsobjekten abgerufen werden:  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys. dm_exec_procedure_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys. dm_exec_trigger_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  

## <a name="table-returned"></a>Zurückgegebene Tabelle

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|
|**DBID**|**smallint**|ID der Kontextdatenbank, die gültig war, als die diesem Plan entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung kompiliert wurde. Für Ad-hoc-Anweisungen und vorbereitete SQL-Anweisungen, die ID der Datenbank, in der die Anweisungen kompiliert wurden.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**objectid**|**int**|ID des Objekts (z. B. gespeicherte Prozedur oder benutzerdefinierte Funktion) für diesen Abfrageplan. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**Zahl**|**smallint**|Gespeicherte Prozedur mit ganzer Zahl. Eine Gruppe von Prozeduren für die **orders**-Anwendung kann z. B. die Namen **orderproc;1**, **orderproc;2** usw. haben. Für Ad-hoc- und vorbereitete Batches entspricht diese Spalte dem Wert **NULL**.<br /><br /> Die Spalte lässt NULL-Werte zu.|  
|**.**|**bit**|Zeigt an, ob die entsprechende Prozedur verschlüsselt ist.<br /><br /> 0 = nicht verschlüsselt<br /><br /> 1 = verschlüsselt<br /><br /> NULL-Werte sind in der Spalte nicht zulässig.|  
|**query_plan**|**xml**|Enthält die letzte bekannte Runtime-Showplan-Darstellung des tatsächlichen Abfrage Ausführungs Plans, der mit *plan_handle*angegeben wird. Der Showplan liegt im XML-Format vor. Für jeden Batch, der z. B. Ad-hoc- [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, Aufrufe von gespeicherten Prozeduren und benutzerdefinierten Funktionen enthält, wird jeweils ein Plan generiert.<br /><br /> Die Spalte lässt NULL-Werte zu.| 

## <a name="remarks"></a>Bemerkungen
Dies ist ein Opt-in-Feature. Verwenden Sie das Ablaufverfolgungsflag [trace flag](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451, um auf Serverebene zu aktivieren. Um auf Datenbankebene zu aktivieren, verwenden Sie die Option LAST_QUERY_PLAN_STATS in [ALTER DATABASE scoped Configuration &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Diese Systemfunktion funktioniert unter der **Lightweight** -Infrastruktur für die Abfrage Ausführungs Statistik-Profilerstellung. Weitere Informationen finden Sie unter [Profilerstellungsinfrastruktur für Abfragen](../../relational-databases/performance/query-profiling-infrastructure.md).  

Die Showplan-Ausgabe von `sys.dm_exec_query_plan_stats` enthält die folgenden Informationen:
-  Alle im zwischengespeicherten Plan gefundenen Kompilierzeit Informationen
-  Laufzeitinformationen, z. b. die tatsächliche Anzahl von Zeilen pro Operator, die gesamte Abfrage-CPU-Zeit und die Ausführungszeit, Überlauf Warnungen, tatsächlicher DOP, maximal verwendeter Arbeitsspeicher und zugewiesener Arbeitsspeicher

Unter den folgenden Bedingungen wird eine Showplan-Ausgabe, die **einem tatsächlichen Ausführungsplan entspricht** , in der **query_plan** -Spalte der zurückgegebenen Tabelle für zurückgegeben `sys.dm_exec_query_plan_stats` :  

-   Der Plan kann in [sys. dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)gefunden werden.     
    **AND**    
-   Die ausgeführte Abfrage ist komplex oder Ressourcen aufwendig.

Unter den folgenden Bedingungen wird eine **vereinfachte <sup>1</sup> ** Showplan-Ausgabe in der **query_plan** -Spalte der zurückgegebenen Tabelle für zurückgegeben `sys.dm_exec_query_plan_stats` :  

-   Der Plan kann in [sys. dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)gefunden werden.     
    **AND**    
-   Die Abfrage ist einfach genug und wird normalerweise als Teil einer OLTP-Arbeitsauslastung kategorisiert.

<sup>1</sup> bezieht sich auf einen Showplan, der nur den Stamm Knoten Operator (Select) enthält.

Unter den folgenden Bedingungen **wird keine Ausgabe von zurückgegeben** `sys.dm_exec_query_plan_stats` :

-   Der mit angegebene Abfrageplan wurde `plan_handle` aus dem Plancache entfernt.     
    **OR**    
-   Der Abfrageplan konnte nicht an erster Stelle zwischengespeichert werden. Weitere Informationen finden Sie unter zwischen [Speichern und wieder verwenden von Ausführungsplänen ](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse).
  
> [!NOTE] 
> Aufgrund einer Einschränkung in der Anzahl der zulässigen, im **XML** -Datentyp zulässigen Werte `sys.dm_exec_query_plan` kann keine Abfrage Pläne zurückgeben, die 128 Ebenen von geschachtelte-Elementen erfüllen oder überschreiten. In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verhinderte diese Bedingung, dass der Abfrageplan nicht zurückgegeben wurde, und generiert den [Fehler 6335](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-6000-to-6999). In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 und höheren Versionen gibt die `query_plan` Spalte NULL zurück.  

## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  

## <a name="examples"></a>Beispiele  
  
### <a name="a-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan"></a>A. Betrachten des letzten bekannten Abfrage Ausführungs Plans für einen bestimmten zwischengespeicherten Plan  
 Im folgenden Beispiel wird **sys. dm_exec_cached_plans** abgefragt, um den interessanten Plan zu suchen und dessen `plan_handle` aus der Ausgabe zu kopieren.  
  
```sql  
SELECT * FROM sys.dm_exec_cached_plans;  
GO  
```  
  
Verwenden Sie dann zum Abrufen des letzten bekannten Abfrage Ausführungs Plans den, der `plan_handle` mit der Systemfunktion **sys. dm_exec_query_plan_stats**kopiert wurde.  
  
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
  [Ablaufverfolgungsflags](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Ausführung &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  

