---
title: sys.dm_db_tuning_recommendations (Transact-SQL) | Microsoft Docs
description: Erfahren Sie, wie Sie potenzielle Leistungsprobleme und empfohlene Fehlerbehebungen in SQL Server und Azure SQL-Datenbank finden
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
ms.openlocfilehash: e8c18ce07ba5e36dcbdb5750db77edf17495c7b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285473"
---
# <a name="sysdm_db_tuning_recommendations-transact-sql"></a>sys.dm\_\_db-Tuning-Empfehlungen\_(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Gibt detaillierte Informationen zu Optimierungsempfehlungen zurück.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, dass diese Informationen angezeigt werden, wird jede Zeile, die Daten enthält, die nicht zum verbundenen Mandanten gehören, herausgefiltert.

| **Spaltenname** | **Datentyp** | **Beschreibung** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Eindeutiger Name der Empfehlung. |
| **type** | **nvarchar(4000)** | Der Name der automatischen Tuning-Option, die die Empfehlung erzeugte, z. B.`FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar(4000)** | Grund für diese Empfehlung. |
| **gültig\_seit** | **datetime2** | Das erste Mal wurde diese Empfehlung generiert. |
| **letzte\_Aktualisierung** | **datetime2** | Das letzte Mal wurde diese Empfehlung generiert. |
| **Staat** | **nvarchar(4000)** | JSON-Dokument, das den Status der Empfehlung beschreibt. Folgende Felder sind verfügbar:<br />-   `currentValue`- aktueller Stand der Empfehlung.<br />-   `reason`- Konstante, die beschreibt, warum sich die Empfehlung im aktuellen Zustand befindet.|
| **ist\_ausführbare\_Aktion** | **bit** | 1 = Die Empfehlung kann über [!INCLUDE[tsql_md](../../includes/tsql-md.md)] ein Skript für die Datenbank ausgeführt werden.<br />0 = Die Empfehlung kann nicht für die Datenbank ausgeführt werden (z. B. nur Informationen oder zurückgesetzte Empfehlung) |
| **ist\_eine\_ehrfürchtisch eitel Aktion** | **bit** | 1 = Die Empfehlung kann automatisch überwacht und vom Datenbankmodul zurückgesetzt werden.<br />0 = Die Empfehlung kann nicht automatisch überwacht und zurückgesetzt werden. Die &quot;meisten&quot; ausführbaren Aktionen sind &quot;andächtbar.&quot; |
| **Ausführen\_\_der\_Aktionsstartzeit** | **datetime2** | Datum der Anwendung der Empfehlung. |
| **Ausführen\_\_der Aktionsdauer** | **time** | Dauer der Ausführungsaktion. |
| **Ausgeführte\_\_Aktion,\_die von** | **nvarchar(4000)** | `User`= Manuell erzwungener Plan in der Empfehlung. <br /> `System`= System automatisch angewendete Empfehlung. |
| **\_Ausgeführte\_\_Aktion initiierte Zeit** | **datetime2** | Datum der Anwendung der Empfehlung. |
| **\_Aktionsstartzeit\_zurücksetzen\_** | **datetime2** | Datum, an dem die Empfehlung zurückgesetzt wurde. |
| **\_Aktionsdauer wiederherstellen\_** | **time** | Dauer der Zurücksetzen-Aktion. |
| **Aktion\_zurücksetzen,\_die\_von** | **nvarchar(4000)** | `User`= Manuell nicht erzwungener empfohlener Plan. <br /> `System`= System automatisch zurückgesetzte Empfehlung. |
| **Zurücksetzen\_\_der\_initiierten Zeit** | **datetime2** | Datum, an dem die Empfehlung zurückgesetzt wurde. |
| **Ergebnis** | **int** | Geschätzter Wert/Auswirkung für diese Empfehlung auf der Skala 0-100 (je größer, desto besser) |
| **Details** | **nvarchar(max)** | JSON-Dokument, das weitere Details zur Empfehlung enthält. Folgende Felder sind verfügbar:<br /><br />`planForceDetails`<br />-    `queryId`-\_Abfrage-ID der zurücksedrierten Abfrage.<br />-    `regressedPlanId`- plan_id des rückschrittten Plans.<br />-   `regressedPlanExecutionCount`- Anzahl der Ausführungen der Abfrage mit einem zurücküberschrittten Plan, bevor die Regression erkannt wird.<br />-    `regressedPlanAbortedCount`- Anzahl der erkannten Fehler bei der Ausführung des zurückgedrungenen Plans.<br />-    `regressedPlanCpuTimeAverage`- Durchschnittliche CPU-Zeit (in Mikrosekunden), die von der zurückgesendeten Abfrage verbraucht wird, bevor die Regression erkannt wird.<br />-    `regressedPlanCpuTimeStddev`- Standardabweichung der CPU-Zeit, die von der zurückgeleiteten Abfrage verbraucht wird, bevor die Regression erkannt wird.<br />-    `recommendedPlanId`- plan_id des Plans, der erzwungen werden sollte.<br />-   `recommendedPlanExecutionCount`- Anzahl der Ausführungen der Abfrage mit dem Plan, der erzwungen werden soll, bevor die Regression erkannt wird.<br />-    `recommendedPlanAbortedCount`- Anzahl der erkannten Fehler während der Ausführung des Plans, die erzwungen werden sollen.<br />-    `recommendedPlanCpuTimeAverage`- Durchschnittliche CPU-Zeit (in Mikrosekunden), die von der Abfrage verbraucht wird, die mit dem Plan ausgeführt wird, der erzwungen werden soll (berechnet, bevor die Regression erkannt wird).<br />-    `recommendedPlanCpuTimeStddev`Standardabweichung der CPU-Zeit, die von der zurückgeleiteten Abfrage verbraucht wird, bevor die Regression erkannt wird.<br /><br />`implementationDetails`<br />-  `method`- Die Methode, die verwendet werden sollte, um die Regression zu korrigieren. Wert ist `TSql`immer .<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)]Skript, das ausgeführt werden soll, um den empfohlenen Plan zu erzwingen. |
  
## <a name="remarks"></a>Bemerkungen  
 Von zurückgegebene `sys.dm_db_tuning_recommendations` Informationen werden aktualisiert, wenn das Datenbankmodul eine potenzielle Abfrageleistungsregression identifiziert, und wird nicht beibehalten. Empfehlungen werden nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bis zum Neustart beibehalten. Datenbankadministratoren sollten regelmäßig Sicherungskopien der Optimierungsempfehlung erstellen, wenn sie sie nach dem Serverrecycling beibehalten möchten. 

 `currentValue`Feld in `state` der Spalte kann die folgenden Werte haben:
 
 | Status | BESCHREIBUNG |
 |--------|-------------|
 | `Active` | Die Empfehlung ist aktiv und wird noch nicht umgesetzt. Der Benutzer kann Empfehlungsskript nehmen und manuell ausführen. |
 | `Verifying` | Die Empfehlung [!INCLUDE[ssde_md](../../includes/ssde_md.md)] wird von und der interne Überprüfungsprozess vergleicht die Leistung des erzwungenen Plans mit dem zurückgedrängten Plan. |
 | `Success` | Die Empfehlung wird erfolgreich angewendet. |
 | `Reverted` | Die Empfehlung wird zurückgesetzt, da keine signifikanten Leistungssteigerungen bestehen. |
 | `Expired` | Die Empfehlung ist abgelaufen und kann nicht mehr angewendet werden. |

JSON-Dokument `state` in Spalte enthält den Grund, der beschreibt, warum die Empfehlung im aktuellen Zustand ist. Die Werte im Ursachenfeld können sein: 

| `Reason` | Beschreibung |
|--------|-------------|
| `SchemaChanged` | Die Empfehlung ist abgelaufen, da das Schema einer referenzierten Tabelle geändert wird. Neue Empfehlung wird erstellt, wenn eine neue Abfrageplanregression auf dem neuen Schema erkannt wird. |
| `StatisticsChanged`| Die Empfehlung ist aufgrund der statistischen Änderung in einer referenzierten Tabelle abgelaufen. Neue Empfehlung wird erstellt, wenn eine neue Abfrageplanregression basierend auf neuen Statistiken erkannt wird. |
| `ForcingFailed` | Der empfohlene Plan kann für eine Abfrage nicht erzwungen werden. Suchen `last_force_failure_reason` Sie die in der [Ansicht sys.query_store_plan,](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) um den Fehlergrund zu ermitteln. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`Option wird vom Benutzer während des Überprüfungsprozesses deaktiviert. Aktivieren `FORCE_LAST_GOOD_PLAN` Sie die Option mit [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;-Anweisung](../../t-sql/statements/alter-database-transact-sql-set-options.md) oder erzwingen Sie den Plan manuell mithilfe des Skripts in `[details]` der Spalte. |
| `UnsupportedStatementType` | Der Plan kann für die Abfrage nicht erzwungen werden. Beispiele für nicht unterstützte Abfragen `INSERT BULK` sind Cursor und Anweisung. |
| `LastGoodPlanForced` | Die Empfehlung wird erfolgreich angewendet. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)]Erkannte potenzielle Leistungsregression, `FORCE_LAST_GOOD_PLAN` aber die Option ist nicht aktiviert - siehe [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Wenden Sie die `FORCE_LAST_GOOD_PLAN` Empfehlung manuell an oder aktivieren Sie die Option. |
| `VerificationAborted`| Der Überprüfungsprozess wird aufgrund des Neustarts oder der Abfragespeicherbereinigung abgebrochen. |
| `VerificationForcedQueryRecompile`| Die Abfrage wird neu kompiliert, da keine signifikante Leistungsverbesserung vorliegt. |
| `PlanForcedByUser`| Der Benutzer erzwang den Plan manuell mit [sp_query_store_force_plan &#40;Transact-SQL-&#41;-Prozedur.](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) Das Datenbankmodul wendet die Empfehlung nicht an, wenn der Benutzer sich ausdrücklich dazu entschließt, einen Plan zu erzwingen. |
| `PlanUnforcedByUser` | Der Benutzer hat den Plan manuell mit [sp_query_store_unforce_plan &#40;Transact-SQL-&#41;-Prozedur](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) nicht erzwungen. Da der Benutzer den empfohlenen Plan explizit zurückgesetzt hat, verwendet das Datenbankmodul weiterhin den aktuellen Plan und generiert eine neue Empfehlung, wenn in Zukunft eine Planregression auftritt. |

 Die Statistik in der Spalte Details zeigt keine Laufzeitplanstatistiken an (z. B. die aktuelle CPU-Zeit). Die Empfehlungsdetails werden zum Zeitpunkt der [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Regressionserkennung übernommen und beschreiben, warum die erkannte Leistungsregression erkannt wurde. Verwenden `regressedPlanId` `recommendedPlanId` und abfragen Sie Katalogansichten des [Abfragespeichers,](../../relational-databases/performance/how-query-store-collects-data.md) um genaue Laufzeitplanstatistiken zu finden.

## <a name="examples-of-using-tuning-recommendations-information"></a>Beispiele für die Verwendung von Optimierungsempfehlungen  

### <a name="example-1"></a>Beispiel 1
Im Folgenden wird [!INCLUDE[tsql](../../includes/tsql-md.md)] das generierte Skript abgefragt, das einen guten Plan für eine bestimmte Abfrage erzwingt:  
 
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
Im Folgenden wird [!INCLUDE[tsql](../../includes/tsql-md.md)] das generierte Skript abgefragt, das einen guten Plan für eine bestimmte Abfrage und zusätzliche Informationen über den geschätzten Gewinn erzwingt:

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
Im Folgenden wird [!INCLUDE[tsql](../../includes/tsql-md.md)] das generierte Skript abgesucht, das einen guten Plan für eine bestimmte Abfrage und zusätzliche Informationen erzwingt, die den Abfragetext und die im Abfragespeicher gespeicherten Abfragepläne enthalten:

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

Weitere Informationen zu JSON-Funktionen, die zum Abfragen von Werten in [!INCLUDE[ssde_md](../../includes/ssde_md.md)]der Empfehlungsansicht verwendet werden können, finden Sie unter [JSON-Support](../../relational-databases/json/index.md) in .
  
## <a name="permissions"></a>Berechtigungen  

Erfordert `VIEW SERVER STATE` die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]Berechtigung in .   
Erfordert `VIEW DATABASE STATE` die Berechtigung für [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]die Datenbank in .   

## <a name="see-also"></a>Weitere Informationen  
 [Automatisches Tuning](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON-Unterstützung](../../relational-databases/json/index.md)
 
