---
title: SET RESULT SET CACHING (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: cd0141a6fbd21c11f7401fa2c45dae0cc75b983d
ms.sourcegitcommit: ccea98fa0768d01076cb6ffef0b4bdb221b2f9d5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2019
ms.locfileid: "65561493"
---
# <a name="set-result-set-caching-transact-sql"></a>SET RESULT SET CACHING (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Bewirkt, dass Azure SQL Data Warehouse Abfrageresultsets zwischenspeichert.
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax

```
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Remarks  
  
Sie müssen während der Ausführung dieses Befehls mit der Masterdatenbank verbunden sein.  Änderungen an dieser Datenbankeinstellung werden sofort wirksam.  Speicherkosten fallen durch das Zwischenspeichern von Abfrageresultsets an. Nachdem das Zwischenspeichern von Ergebnissen für eine Datenbank deaktiviert wurde, werden zuvor dauerhaft zwischengespeicherte Ergebnisse sofort aus dem Azure SQL Data Warehouse-Speicher gelöscht. Eine neue Spalte namens „is_result_set_caching_on“ wurde in [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql?view=azure-sqldw-latest
) eingeführt, um die Einstellung für die Zwischenspeicherung von Ergebnissen für eine Datenbank anzuzeigen.  

**ON** (EIN) Gibt an, dass von dieser Datenbank zurückgegebene Abfrageresultsets im Azure SQL Data Warehouse-Speicher zwischengespeichert werden.

**OFF** (AUS) Gibt an, dass von dieser Datenbank zurückgegebene Abfrageresultsets nicht im Azure SQL Data Warehouse-Speicher zwischengespeichert werden.

Benutzer können feststellen, ob eine Abfrage mit einem Ergebniscachetreffer oder -fehler ausgeführt wurde, indem sie [sys.pdw_request_steps](/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql?view=azure-sqldw-latest) mit einer bestimmten request_id abfragen. Liegt ein Cachetreffer vor, enthält das Abfrageergebnis einen einzigen Schritt mit den folgenden Details:

|**Spaltenname**|**Ist gleich**|**ReplTest1**|
|----|----|----|
|operation_type|=|ReturnOperation|
|step_index|=|0|
|location_type|=|Control|
|Befehl|Wie|%DWResultCacheDb%|
||||
  
## <a name="permissions"></a>Berechtigungen

Folgende Berechtigungen sind erforderlich:

- Der Prinzipalanmeldename auf Serverebene (der während des Bereitstellungsprozesses erstellt wurde) oder
- Mitgliedschaft in der dbmanager-Datenbankrolle.

Der Datenbankbesitzer kann die Datenbank nur ändern, wenn er Mitglied der Rolle „dbmanager“ ist.
  
## <a name="examples"></a>Beispiele

### <a name="enable-result-set-caching-for-a-database"></a>Aktivieren der Zwischenspeicherung von Resultsets für eine Datenbank

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING ON;
```

### <a name="disable-result-set-caching-for-a-database"></a>Deaktivieren der Zwischenspeicherung von Resultsets für eine Datenbank

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING OFF;
```

### <a name="check-result-set-caching-setting-for-a-database"></a>Überprüfen der Einstellung für die Zwischenspeicherung von Resultsets für eine Datenbank

```sql
SELECT name, is_result_set_caching  
FROM sys.databases
```

### <a name="check-for-number-of-queries-with-result-set-cache-hit-and-cache-miss"></a>Überprüfen der Anzahl von Abfragen mit Resultset-Cachetreffern oder -fehlern

```sql
SELECT  
Queries=CacheHits+CacheMisses,
CacheHits,
CacheMisses,
CacheHitPct=CacheHits*1.0/(CacheHits+CacheMisses)
FROM  
(SELECT  
CacheHits=count(distinct case when s.command like '%DWResultCacheDb%' and
r.resource_class IS NULL and s.operation_type = 'ReturnOperation' and  
s.step_index = 0 then s.request_id else null end) ,
CacheMisses=count(distinct case when r.resource_class IS NOT NULL then  
s.request_id else null end)
     FROM sys.dm_pdw_request_steps s  
     JOIN sys.dm_pdw_exec_requests r  
     ON s.request_id = r.request_id) A
```

### <a name="check-for-result-set-cache-hit-or-cache-miss-for-a-query"></a>Überprüfen auf Resultsetcachetreffer oder -fehler für eine Abfrage

```sql
If
(SELECT step_index  
FROM sys.dm_pdw_request_steps  
WHERE request_id = 'QID58286'
      and operation_type = 'ReturnOperation'
      and command like '%DWResultCacheDb%') = 0
SELECT 1 as is_cache_hit  
ELSE
SELECT 0 as is_cache_hit
```

### <a name="check-for-all-queries-with-result-set-cache-hits"></a>Überprüfen auf alle Abfragen mit Resultset-Cachetreffern

```sql
SELECT *  
FROM sys.dm_pdw_request_steps  
WHERE command like '%DWResultCacheDb%' and step_index = 0
```

## <a name="see-also"></a>Weitere Informationen

[SET-Anweisungen &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)