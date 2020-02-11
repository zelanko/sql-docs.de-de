---
title: sys. dm_db_tuning_recommendations (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie potenzielle Leistungsprobleme und empfohlene Korrekturen in SQL Server und Azure SQL-Datenbank finden.
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_tuning_recommendations
- dm_db_tuning_recommendations
- sys.dm_db_tuning_recommendations_TSQL
- dm_db_tuning_recommendations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database tuning recommendations feature [SQL Server], sys.dm_db_tuning_recommendations dynamic management view
- sys.dm_db_tuning_recommendations dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dbee7422bdf58d753c31c7aa57a81bc4b29d2568
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096233"
---
# <a name="sysdm_db_tuning_recommendations-transact-sql"></a>Empfehlungen für die sys.DM\_-Datenbankoptimierung (Transact-SQL)\_\_
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Gibt ausführliche Informationen zu Optimierungsempfehlungen zurück.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, dass diese Informationen verfügbar gemacht werden, wird jede Zeile, die Daten enthält, die nicht zum verbundenen Mandanten gehören, herausgefiltert.

| **Spaltenname** | **Datentyp** | **Beschreibung** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Eindeutiger Name der Empfehlung. |
| **type** | **nvarchar(4000)** | Der Name der automatischen Optimierungs Option, die die Empfehlung erzeugt hat, z. b.`FORCE_LAST_GOOD_PLAN` |
| **weshalb** | **nvarchar(4000)** | Grund, warum diese Empfehlung bereitgestellt wurde. |
| **gültig\_seit** | **datetime2** | Der erste Zeitpunkt, an dem diese Empfehlung generiert wurde. |
| **letzte\_Aktualisierung** | **datetime2** | Der Zeitpunkt, zu dem diese Empfehlung zuletzt generiert wurde. |
| **Land** | **nvarchar(4000)** | JSON-Dokument, das den Status der Empfehlung beschreibt. Folgende Felder sind verfügbar:<br />-   `currentValue`-Aktueller Status der Empfehlung.<br />-   `reason`-Konstante, die beschreibt, warum die Empfehlung den aktuellen Status aufweist.|
| **ist\_Ausführ\_Bare Aktion** | **bit** | 1 = die Empfehlung kann mithilfe eines [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Skripts für die Datenbank ausgeführt werden.<br />0 = die Empfehlung kann nicht für die Datenbank ausgeführt werden (z. b. "nur Informationen" oder "zurückgesetzte Empfehlung"). |
| **is\_revertable\_-Aktion** | **bit** | 1 = die Empfehlung kann von der Datenbank-Engine automatisch überwacht und wieder hergestellt werden.<br />0 = die Empfehlung kann nicht automatisch überwacht und wieder hergestellt werden. Die &quot;meisten&quot; ausführbaren Aktionen &quot;werden Rück&quot;gängig gemacht. |
| **\_Startzeit\_\_der Ausführungs Aktion** | **datetime2** | Datum, an dem die Empfehlung angewendet wird. |
| **Ausführungs\_\_Dauer** | **time** | Dauer der Ausführungs Aktion. |
| **von\_initiierte\_\_Aktion ausführen von** | **nvarchar(4000)** | `User`= Der Benutzer hat den Plan in der Empfehlung manuell erzwungen. <br /> `System`= Automatisch angewendete Empfehlung. |
| **initiierte\_\_Zeit\_für Ausführungs Aktion** | **datetime2** | Datum, an dem die Empfehlung angewendet wurde. |
| **\_Startzeit\_\_der Wiederherstellungs Aktion** | **datetime2** | Datum, an dem die Empfehlung wieder hergestellt wurde. |
| **Dauer\_der\_Aktions Wiederherstellung** | **time** | Dauer der Rückgängig-Aktion. |
| **zurück\_setzen\_von\_Aktionen initiiert von** | **nvarchar(4000)** | `User`= Benutzer manuell nicht erzwungener empfohlener Plan. <br /> `System`= System hat automatisch eine Empfehlung zurückgesetzt. |
| **\_Aktion zum\_initiieren\_der Aktion** | **datetime2** | Datum, an dem die Empfehlung wieder hergestellt wurde. |
| **Endergebnis** | **int** | Geschätzter Wert/Auswirkung für diese Empfehlung auf der 0-100-Skala (je höher die bessere) |
| **Einzel** | **nvarchar(max)** | JSON-Dokument, das weitere Details zur Empfehlung enthält. Folgende Felder sind verfügbar:<br /><br />`planForceDetails`<br />-    `queryId`-Abfrage\_-ID der zurück gestellten Abfrage.<br />-    `regressedPlanId`-plan_id des zurück gestellten Plans.<br />-   `regressedPlanExecutionCount`-Anzahl der Ausführungen der Abfrage mit einem zurück gestellten Plan, bevor die Regression erkannt wird.<br />-    `regressedPlanAbortedCount`-Anzahl der erkannten Fehler während der Ausführung des zurück gestellten Plans.<br />-    `regressedPlanCpuTimeAverage`-Die durchschnittliche CPU-Zeit, die von der zurück gestellten Abfrage beansprucht wird, bevor die Regression erkannt wird.<br />-    `regressedPlanCpuTimeStddev`-Standard Abweichung der CPU-Zeit, die von der zurück gestellten Abfrage beansprucht wird, bevor die Regression erkannt wird.<br />-    `recommendedPlanId`-plan_id des Plans, der erzwungen werden soll.<br />-   `recommendedPlanExecutionCount`-Anzahl der Ausführungen der Abfrage mit dem Plan, der erzwungen werden soll, bevor die Regression erkannt wird.<br />-    `recommendedPlanAbortedCount`-Anzahl der erkannten Fehler während der Ausführung des Plans, der erzwungen werden soll.<br />-    `recommendedPlanCpuTimeAverage`-Durchschnittliche CPU-Zeit, die von der mit dem Plan ausgeführten Abfrage beansprucht wird (berechnet, bevor die Regression erkannt wird).<br />-    `recommendedPlanCpuTimeStddev`Standard Abweichung der CPU-Zeit, die von der zurück gestellten Abfrage beansprucht wird, bevor die Regression erkannt wird.<br /><br />`implementationDetails`<br />-  `method`: Die Methode, die verwendet werden soll, um die Regression zu korrigieren. Der Wert ist `TSql`immer.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)]Skript, das ausgeführt werden soll, um den empfohlenen Plan zu erzwingen. |
  
## <a name="remarks"></a>Bemerkungen  
 Die von `sys.dm_db_tuning_recommendations` zurückgegebenen Informationen werden aktualisiert, wenn die Datenbank-Engine die mögliche Regression der Abfrageleistung identifiziert und nicht persistent ist. Empfehlungen werden nur beibehalten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bis neu gestartet wird. Datenbankadministratoren sollten regelmäßig Sicherungskopien der Optimierungs Empfehlung erstellen, wenn Sie Sie nach dem wieder verwenden des Servers beibehalten möchten. 

 `currentValue`das Feld in `state` der Spalte kann die folgenden Werte aufweisen:
 
 | Status | BESCHREIBUNG |
 |--------|-------------|
 | `Active` | Die Empfehlung ist aktiv und wurde noch nicht angewendet. Der Benutzer kann ein Empfehlungs Skript erstellen und manuell ausführen. |
 | `Verifying` | Die Empfehlung wird von [!INCLUDE[ssde_md](../../includes/ssde_md.md)] angewendet, und der interne Überprüfungsprozess vergleicht die Leistung des erzwungenen Plans mit dem zurück gestellten Plan. |
 | `Success` | Die Empfehlung wurde erfolgreich angewendet. |
 | `Reverted` | Die Empfehlung wurde zurückgesetzt, da es keine signifikanten Leistungssteigerungen gibt. |
 | `Expired` | Die Empfehlung ist abgelaufen und kann nicht mehr angewendet werden. |

Das JSON- `state` Dokument in der Spalte enthält den Grund, warum die Empfehlung im aktuellen Zustand ist. Die Werte im Feld "Grund" können wie folgt lauten: 

| `Reason` | BESCHREIBUNG |
|--------|-------------|
| `SchemaChanged` | Die Empfehlung ist abgelaufen, weil das Schema einer Tabelle geändert wird, auf die verwiesen wird. |
| `StatisticsChanged`| Die Empfehlung ist aufgrund der statistischen Änderung einer Tabelle, auf die verwiesen wird, abgelaufen. |
| `ForcingFailed` | Der empfohlene Plan kann für eine Abfrage nicht erzwungen werden. Suchen Sie `last_force_failure_reason` in der [sys. query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) -Sicht, um die Ursache des Fehlers zu ermitteln. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`die Option wird vom Benutzer während der Überprüfung deaktiviert. Aktivieren `FORCE_LAST_GOOD_PLAN` Sie die Option mithilfe von [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) -Anweisung, oder erzwingen Sie `[details]` den Plan manuell mithilfe des Skripts in der Spalte. |
| `UnsupportedStatementType` | Der Plan kann für die Abfrage nicht erzwungen werden. Beispiele für nicht unterstützte Abfragen sind Cursors `INSERT BULK` und Statement. |
| `LastGoodPlanForced` | Die Empfehlung wurde erfolgreich angewendet. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)]Es wurde eine potenzielle Leistungs Regression erkannt `FORCE_LAST_GOOD_PLAN` , aber die Option ist nicht aktiviert-siehe [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Anwenden der Empfehlung manuell oder `FORCE_LAST_GOOD_PLAN` Aktivieren der Option. |
| `VerificationAborted`| Der Überprüfungs Vorgang wurde aufgrund des Neustarts oder Abfragespeicher Bereinigungs Vorgangs abgebrochen. |
| `VerificationForcedQueryRecompile`| Die Abfrage wird neu kompiliert, weil keine signifikante Leistungsverbesserung vorliegt. |
| `PlanForcedByUser`| Der Benutzer hat den Plan mithilfe [sp_query_store_force_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) Prozedur manuell erzwungen. |
| `PlanUnforcedByUser` | Der Benutzer hat den Plan mithilfe [sp_query_store_unforce_plan &#40;Transact-SQL-&#41;Prozedur manuell enterzwingt](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) . |

 Die Statistik in der Spalte "Details" zeigt keine Statistiken für den Lauf Zeit Plan an (z. b. aktuelle CPU-Zeit). Die Empfehlungs Details werden zum Zeitpunkt der Regressions Erkennung verwendet, und es [!INCLUDE[ssde_md](../../includes/ssde_md.md)] wird beschrieben, warum die Leistungs Regression erkannt wurde. Verwenden `regressedPlanId` Sie `recommendedPlanId` und, um [Abfragespeicher Katalog Sichten](../../relational-databases/performance/how-query-store-collects-data.md) abzufragen, um genaue Lauf Zeit Plan Statistiken zu ermitteln.

## <a name="examples-of-using-tuning-recommendations-information"></a>Beispiele für die Verwendung von Optimierungs Empfehlungs Informationen  

### <a name="example-1"></a>Beispiel 1
Im folgenden wird das generierte [!INCLUDE[tsql](../../includes/tsql-md.md)] Skript abgerufen, das für eine bestimmte Abfrage einen guten Plan erzwingt:  
 
```sql
SELECT name, reason, score,
    JSON_VALUE(details, '$.implementationDetails.script') AS script,
    details.* 
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON(details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressed_plan_id int '$.regressedPlanId',
            last_good_plan_id int '$.recommendedPlanId') AS details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active';
```
### <a name="example-2"></a>Beispiel 2
Im folgenden wird das generierte [!INCLUDE[tsql](../../includes/tsql-md.md)] Skript abgerufen, das einen guten Plan für eine bestimmte Abfrage erzwingt, sowie zusätzliche Informationen zum geschätzten Gewinn:

```sql
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                  *(regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
      error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON (Details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressedPlanId int '$.regressedPlanId',
            recommendedPlanId int '$.recommendedPlanId',
            regressedPlanErrorCount int,
            recommendedPlanErrorCount int,
            regressedPlanExecutionCount int,
            regressedPlanCpuTimeAverage float,
            recommendedPlanExecutionCount int,
            recommendedPlanCpuTimeAverage float
          ) AS planForceDetails;
```

### <a name="example-3"></a>Beispiel 3
Im folgenden wird das generierte [!INCLUDE[tsql](../../includes/tsql-md.md)] Skript abgerufen, das einen guten Plan für eine bestimmte Abfrage erzwingt, sowie zusätzliche Informationen, die den Abfragetext und die in Abfragespeicher gespeicherten Abfrage Pläne enthalten:

```sql
WITH cte_db_tuning_recommendations
AS (SELECT reason,
        score,
        query_id,
        regressedPlanId,
        recommendedPlanId,
        current_state = JSON_VALUE(state, '$.currentValue'),
        current_state_reason = JSON_VALUE(state, '$.reason'),
        script = JSON_VALUE(details, '$.implementationDetails.script'),
        estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                * (regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
        error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
    FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(Details, '$.planForceDetails')
    WITH ([query_id] int '$.queryId',
        regressedPlanId int '$.regressedPlanId',
        recommendedPlanId int '$.recommendedPlanId',
        regressedPlanErrorCount int,    
        recommendedPlanErrorCount int,
        regressedPlanExecutionCount int,
        regressedPlanCpuTimeAverage float,
        recommendedPlanExecutionCount int,
        recommendedPlanCpuTimeAverage float
        )
    )
SELECT qsq.query_id,
    qsqt.query_sql_text,
    dtr.*,
    CAST(rp.query_plan AS XML) AS RegressedPlan,
    CAST(sp.query_plan AS XML) AS SuggestedPlan
FROM cte_db_tuning_recommendations AS dtr
INNER JOIN sys.query_store_plan AS rp ON rp.query_id = dtr.query_id
    AND rp.plan_id = dtr.regressedPlanId
INNER JOIN sys.query_store_plan AS sp ON sp.query_id = dtr.query_id
    AND sp.plan_id = dtr.recommendedPlanId
INNER JOIN sys.query_store_query AS qsq ON qsq.query_id = rp.query_id
INNER JOIN sys.query_store_query_text AS qsqt ON qsqt.query_text_id = qsq.query_text_id;
```

Weitere Informationen zu JSON-Funktionen, die verwendet werden können, um Werte in der Empfehlungs Ansicht abzufragen, finden Sie [!INCLUDE[ssde_md](../../includes/ssde_md.md)] [unter JSON-Unterstützung](../../relational-databases/json/index.md) in.
  
## <a name="permissions"></a>Berechtigungen  

Erfordert `VIEW SERVER STATE` die- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]Berechtigung in.   
Erfordert die `VIEW DATABASE STATE` -Berechtigung für die- [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]Datenbank in.   

## <a name="see-also"></a>Weitere Informationen  
 [Automatische Optimierung](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys. database_automatic_tuning_options &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys. database_query_store_options &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON-Unterstützung](../../relational-databases/json/index.md)
 
