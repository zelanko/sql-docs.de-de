---
title: dm_db_tuning_recommendations (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie potenzielle Leistungsprobleme zu finden und empfohlene Problembehebungen in SQL Server und Azure SQL-Datenbank
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 3f8e2957802d527a4e4845e95eedb2ea7cdcd375
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "40394242"
---
# <a name="sysdmdbtuningrecommendations-transact-sql"></a>Sys.DM\_Db\_Optimierung\_Empfehlungen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Gibt ausführliche Informationen zu optimierungsempfehlungen.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, dass diese Informationen verfügbar gemacht werden, wird jede Zeile mit Daten, die zum verbundenen Mandanten gehören, herausgefiltert.

| **Spaltenname** | **Data type** | **Beschreibung** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Eindeutiger Name der Empfehlung. |
| **type** | **nvarchar(4000)** | Der Name, der die automatische Optimierungsoption, die die Empfehlung, z. B. erstellt werden soll, `FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar(4000)** | Der Grund, warum diese Empfehlung bereitgestellt wurde. |
| **gültige\_da** | **datetime2** | Diese Empfehlung wurde zum ersten Mal generiert. |
| **last\_refresh** | **datetime2** | Zeitpunkt der letzten, die diese Empfehlung generiert wurde. |
| **state** | **nvarchar(4000)** | JSON-Dokument, das den Status der Empfehlung beschrieben. Folgende Felder sind verfügbar:<br />-   `currentValue` -aktuellen Status der Empfehlung.<br />-   `reason` -Konstante, die beschreibt, warum die Empfehlung in den aktuellen Zustand ist.|
| **ist\_ausführbare\_Aktion** | **bit** | 1 = die Empfehlung ausgeführt werden kann, für die Datenbank über [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Skript.<br />0 = die Empfehlung kann nicht für die Datenbank ausgeführt werden (z. B.: Informationen nur oder wiederhergestellten Empfehlung) |
| **ist\_revertable\_Aktion** | **bit** | 1 = die Empfehlung automatisch überwacht und von Datenbank-Engine zurückgesetzt.<br />0 = die Empfehlung kann nicht automatisch überwacht und werden zurückgesetzt. Die meisten &quot;ausführbare&quot; Maßnahmen &quot;revertable&quot;. |
| **Führen Sie\_Aktion\_starten\_Zeit** | **datetime2** | Datum, an die Empfehlung angewendet wurde. |
| **Führen Sie\_Aktion\_Dauer** | **Uhrzeit** | Die Dauer der Aktion ausführen. |
| **execute\_action\_initiated\_by** | **nvarchar(4000)** | `User` = Benutzer erzwungen manuell Plan in der Empfehlung. <br /> `System` = System werden Empfehlungen automatisch angewendet. |
| **Führen Sie\_Aktion\_initiiert\_Zeit** | **datetime2** | Datum, an die Empfehlung angewendet wurde. |
| **REVERT\_Aktion\_starten\_Zeit** | **datetime2** | Datum, an die Empfehlung zurückgesetzt wurde. |
| **REVERT\_Aktion\_Dauer** | **Uhrzeit** | Die Dauer der Aktion wiederherstellen. |
| **REVERT\_Aktion\_initiiert\_durch** | **nvarchar(4000)** | `User` = Benutzer empfohlener Plan manuell mehr erzwungen. <br /> `System` = Empfehlung wird von System automatisch wiederhergestellt. |
| **REVERT\_Aktion\_initiiert\_Zeit** | **datetime2** | Datum, an die Empfehlung zurückgesetzt wurde. |
| **score** | **int** | Geschätzter Wert/Auswirkungen auf diese Empfehlung wird auf der 0-100 skalieren (je größer die besser) |
| **Details** | **nvarchar(max)** | JSON-Dokument, das weitere Details zur Empfehlung enthält. Folgende Felder sind verfügbar:<br /><br />`planForceDetails`<br />-    `queryId` -Abfrage\_-Id der zurückgestellte Abfrage.<br />-    `regressedPlanId` -Plan_id des zurückgestellten Plans.<br />-   `regressedPlanExecutionCount` -Die Anzahl von Ausführungen der Abfrage mit der zurückgestellte Plan, bevor Sie die Regression erkannt wird.<br />-    `regressedPlanAbortedCount` -Anzahl der erkannten Fehler während der Ausführung des zurückgestellten Plans.<br />-    `regressedPlanCpuTimeAverage` -Durchschnittliche CPU-Zeit, die von der zurückgestellte Abfrage genutzt werden, bevor die Regression erkannt wird.<br />-    `regressedPlanCpuTimeStddev` – Standardabweichung der CPU-Zeit, die von der zurückgestellte Abfrage vor der Regression genutzt wurde erkannt.<br />-    `recommendedPlanId` -Plan_id des Plans, die erzwungen werden soll.<br />-   `recommendedPlanExecutionCount`-Anzahl der Ausführungen der Abfrage mit dem Plan, der erzwungen werden soll, bevor die Regression erkannt wird.<br />-    `recommendedPlanAbortedCount` -Anzahl der erkannten Fehler während der Ausführung des Plans, die erzwungen werden soll.<br />-    `recommendedPlanCpuTimeAverage` -Durchschnittliche CPU-Zeit, die von der Abfrage ausgeführt wird, mit dem Plan erzwungen werden soll (wird berechnet, bevor die Regression erkannt wird) genutzt.<br />-    `recommendedPlanCpuTimeStddev` Standardabweichung der CPU-Zeit, die von der zurückgestellte Abfrage vor der Regression genutzt wurde erkannt.<br /><br />`implementationDetails`<br />-  `method` – Die Methode, die verwendet werden soll, um die Regression zu beheben. Wert ist immer `TSql`.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Skript, das ausgeführt werden soll, um die empfohlenen Plan zu erzwingen. |
  
## <a name="remarks"></a>Hinweise  
 Informationen, die vom `sys.dm_db_tuning_recommendations` wird aktualisiert, wenn die Datenbank-Engine identifiziert potenzielle Regression der abfrageleistung und wird nicht beibehalten. Empfehlungen werden nur bis zum beibehalten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu gestartet wird. Datenbankadministratoren sollten regelmäßig Sicherungskopien von der optimierungsempfehlung, wenn sie es nach dem wiederverwenden des Servers beibehalten möchten. 

 `currentValue` im Feld der `state` Spalte kann die folgenden Werte aufweisen:
 | Status | Description |
 |--------|-------------|
 | `Active` | Es wird empfohlen, active und noch nicht angewendet. Benutzer profitieren von Empfehlungsskript und manuell ausführen. |
 | `Verifying` | Empfehlung wird angewendet, indem [!INCLUDE[ssde_md](../../includes/ssde_md.md)] und interne Überprüfung vergleicht die Leistung des erzwungenen Plans mit der zurückgestellte Plan. |
 | `Success` | Die Empfehlung wurde erfolgreich angewendet. |
 | `Reverted` | Die Empfehlung wurde zurückgesetzt, da es keine erhebliche Leistungssteigerungen sind. |
 | `Expired` | Empfehlung ist abgelaufen und kann nicht mehr angewendet werden. |

JSON-Dokuments in `state` Spalte enthält den Grund an, die beschreibt, warum die Empfehlung in den aktuellen Zustand ist. Unter Umständen Werte in das Feld "Grund": 

| Reason | Description |
|--------|-------------|
| `SchemaChanged` | Empfehlung ist abgelaufen, weil das Schema einer Tabelle verwiesen wird, geändert wird. |
| `StatisticsChanged`| Empfehlung abgelaufen aufgrund der Änderung der Statistik für eine Tabelle verwiesen wird. |
| `ForcingFailed` | Empfohlener Plan kann nicht auf einer Abfrage erzwungen werden. Suchen der `last_force_failure_reason` in die [Sys. query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) anzeigen, um die Ursache des Fehlers zu finden. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN` Option ist während der Überprüfung durch den Benutzer deaktiviert. Aktivieren Sie `FORCE_LAST_GOOD_PLAN` -Option [ALTER DATABASE festgelegt AUTOMATIC_TUNING &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) -Anweisung oder erzwingen Sie den Plan manuell mithilfe des Skripts im `[details]` Spalte. |
| `UnsupportedStatementType` | Plan kann nicht in der Abfrage erzwungen werden. Beispiele für nicht unterstützte Abfragen sind Cursor und `INSERT BULK` Anweisung. |
| `LastGoodPlanForced` | Die Empfehlung wurde erfolgreich angewendet. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)] identifiziert potenzielle Leistungsverlust, aber die `FORCE_LAST_GOOD_PLAN` nicht aktiviert ist – siehe [ALTER DATABASE festgelegt AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Anwenden einer Empfehlung manuell, oder aktivieren Sie `FORCE_LAST_GOOD_PLAN` Option. |
| `VerificationAborted`| Überprüfung wird aufgrund der Neustart oder Query Store Bereinigung abgebrochen. |
| `VerificationForcedQueryRecompile`| Abfrage wird neu kompiliert werden, da keine deutliche leistungsverbesserung vorhanden ist. |
| `PlanForcedByUser`| Benutzer manuell erzwungen, die mit [Sp_query_store_force_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) Verfahren. |
| `PlanUnforcedByUser` | Benutzer manuell unforced der Plan mit [Sp_query_store_unforce_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) Verfahren. |

 Statistik in der Spalte "Details" zeigt nicht an Plan Laufzeitstatistiken (z. B. aktuelle CPU-Zeit). Die Details zur Empfehlung sind zum Zeitpunkt der Erkennung von Regression und beschrieben, warum [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Leistungsverlust identifiziert. Verwendung `regressedPlanId` und `recommendedPlanId` Abfrage [Query Store Katalogsichten](../../relational-databases/performance/how-query-store-collects-data.md) genaue Laufzeitstatistiken für Plan gefunden.

## <a name="using-tuning-recommendations-information"></a>Verwenden die Optimierung Empfehlungsinformationen  
Sie können die folgende Abfrage zum Abrufen der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript, das das Problem zu beheben, wird:  
 
```sql
SELECT name, reason, score,
        JSON_VALUE(details, '$.implementationDetails.script') as script,
        details.* 
FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(details, '$.planForceDetails')
                WITH (  query_id int '$.queryId',
                        regressed_plan_id int '$.regressedPlanId',
                        last_good_plan_id int '$.recommendedPlanId') as details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active'
```
  
 Weitere Informationen zu JSON-Funktionen, die Abfrage Werte in der Empfehlung Ansicht verwendet werden können, finden Sie unter [JSON-Unterstützung](../../relational-databases/json/index.md) in [!INCLUDE[ssde_md](../../includes/ssde_md.md)].
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="see-also"></a>Siehe auch  
 [Die automatische Optimierung](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON-Unterstützung](../../relational-databases/json/index.md)
 
