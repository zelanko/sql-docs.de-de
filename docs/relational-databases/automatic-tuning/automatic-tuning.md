---
title: Automatische Optimierung | Microsoft-Dokumentation
description: Erfahren Sie mehr über die automatische Optimierung in SQL Server und Azure SQL-Datenbank
ms.custom: ''
ms.date: 08/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- performance tuning [SQL Server]
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4ad185085c19d8286fa6a09e46742860a948849a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67934557"
---
# <a name="automatic-tuning"></a>Automatische Optimierung
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Die automatische Datenbankoptimierung bietet einen Einblick in die potentiellen Abfrageleistungsprobleme, empfiehlt Lösungen und kann identifizierte Probleme automatisch beheben.

Durch die automatische [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] Optimierung in werden Sie benachrichtigt, sobald ein mögliches Leistungsproblem erkannt wird, und Sie können Korrekturmaßnahmen anwenden oder [!INCLUDE[ssde_md](../../includes/ssde_md.md)] die automatische Behebung von Leistungsproblemen durchführen lassen.
Die automatische Optimierung [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] in ermöglicht es Ihnen, Leistungsprobleme zu identifizieren und zu beheben, die durch **Abfrage Ausführungsplan Auswahl Regressionen**verursacht werden. Bei der automatischen [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] Optimierung in werden auch erforderliche Indizes erstellt und nicht verwendete Indizes gelöscht. Weitere Informationen zu Abfrage Ausführungsplänen finden Sie unter [Ausführungspläne](../../relational-databases/performance/execution-plans.md).

[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Überwacht die Abfragen, die für die Datenbank ausgeführt werden, und verbessert die Leistung der Arbeitsauslastung automatisch. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Verfügt über einen integrierten Intelligence-Mechanismus, mit dem die Leistung Ihrer Abfragen automatisch optimiert und verbessert werden kann, indem die Datenbank dynamisch an ihre Arbeitsauslastung angepasst wird. Es stehen zwei Features für die automatische Optimierung zur Verfügung:

 -  Die **Automatische Plan Korrektur** identifiziert problematische Abfrage Ausführungspläne und korrigiert Leistungsprobleme beim Abfrage Ausführungsplan. **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
 -  Die **Automatische Index Verwaltung** identifiziert Indizes, die in der Datenbank hinzugefügt werden sollen, und Indizes, die entfernt werden sollen. **Gilt für**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

## <a name="why-automatic-tuning"></a>Gründe für die automatische Optimierung

Zu den drei Hauptaufgaben bei der klassischen Datenbankverwaltung gehören die Überwachung der Arbeits [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Auslastung, das Identifizieren kritischer Abfragen, Indizes, die hinzugefügt werden sollen, um die Leistung zu verbessern und die Identifizierung seltener verwendeter [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Bietet detaillierte Einblicke in die Abfragen und Indizes, die Sie überwachen müssen. Eine kontinuierliche Überwachung der Datenbank ist jedoch eine schwierige und aufwendige Aufgabe, insbesondere bei sehr vielen Datenbanken. Die Verwaltung einer großen Anzahl von Datenbanken ist möglicherweise nicht effizient. Anstatt die Datenbank manuell zu überwachen und zu optimieren, empfiehlt es sich ggf., einige der Überwachungs-und [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Optimierungs Aktionen an die Funktion zur automatischen Optimierung zu delegieren.

### <a name="how-does-automatic-tuning-work"></a>Wie funktioniert die automatische Optimierung?

Die automatische Optimierung ist ein kontinuierlicher Überwachungs-und Analyseprozess, der ständig die Merkmale Ihrer Arbeitsauslastung erfährt und potenzielle Probleme und Verbesserungen identifiziert.

![Automatischer Optimierungsprozess](./media/tuning-process.png)

Durch diesen Prozess kann die Datenbank dynamisch an ihre Arbeitsauslastung angepasst werden, indem ermittelt wird, welche Indizes und Pläne die Leistung Ihrer Workloads verbessern können und welche Indizes ihre Workloads beeinflussen. Basierend auf diesen ermittelten Informationen werden bei der automatischen Optimierung Optimierungsaktionen angewendet, um die Leistung Ihrer Workload zu verbessern. Außerdem überwacht die Datenbank kontinuierlich die Leistung nach jeder durch die automatische Optimierung vorgenommenen Änderung, um sicherzustellen, dass Sie die Leistung Ihrer Arbeitsauslastung verbessert. Jede Aktion, die die Leistung nicht verbessert hat, wird automatisch rückgängig gemacht. Diese Überprüfung ist ein wichtiges Feature, mit dem dafür gesorgt wird, dass Änderungen, die von der automatischen Optimierung vorgenommen werden, für Ihre Workload keine Leistungsverschlechterung bewirken.

## <a name="automatic-plan-correction"></a>Automatische Plan Korrektur

Die automatische Plan Korrektur ist eine Funktion zur automatischen Optimierung, die die **Auswahl der Ausführungspläne** identifiziert und das Problem automatisch durch Erzwingen des letzten bekannten guten Plans korrigiert. Weitere Informationen zu Abfrage Ausführungsplänen und zum Abfrageoptimierer finden Sie im [Handbuch zur Architektur der Abfrage Verarbeitung](../../relational-databases/query-processing-architecture-guide.md).

### <a name="what-is-execution-plan-choice-regression"></a>Was ist eine Regression der Ausführungsplan Auswahl?

Der [!INCLUDE[ssdenoversion_md](../../includes/ssdenoversion_md.md)] kann verschiedene Ausführungspläne zum Ausführen der [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Abfragen verwenden. Abfrage Pläne sind abhängig von den Statistiken, Indizes und anderen Faktoren. Der optimale Plan, der zum Ausführen einer [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Abfrage verwendet werden sollte, kann im Laufe der Zeit geändert werden. In einigen Fällen ist der neue Plan möglicherweise nicht besser als der vorherige Plan, und der neue Plan kann zu einer Leistungs Regression führen.

 ![Regression der Abfrage Ausführungsplan Auswahl](media/plan-choice-regression.png "Regression der Abfrage Ausführungsplan Auswahl") 

Wenn Sie die Regression der Plan Auswahl bemerken, sollten Sie einen vorherigen guten Plan finden und ihn anstelle des aktuellen Verfahrens mit `sp_query_store_force_plan` der Prozedur erzwingen.
[!INCLUDE[ssde_md](../../includes/ssde_md.md)]in [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] enthält Informationen zu zurück gestellten Plänen und empfohlenen Korrekturmaßnahmen.
Außerdem ermöglicht [!INCLUDE[ssde_md](../../includes/ssde_md.md)] es Ihnen, diesen Prozess vollständig zu automatisieren [!INCLUDE[ssde_md](../../includes/ssde_md.md)] und das Problem zu beheben, das im Zusammenhang mit den Planänderungen zu finden ist.

### <a name="automatic-plan-choice-correction"></a>Automatische Korrektur der Planauswahl

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]kann automatisch zum letzten bekannten guten Plan wechseln, wenn die Plan Auswahl Regression erkannt wird.

![Auswahl Korrektur für Abfrage Ausführungsplan](media/force-last-good-plan.png "Auswahl Korrektur für Abfrage Ausführungsplan") 

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]erkennt automatisch jede potenzielle Plan Auswahl Regression, einschließlich des Plans, der anstelle des falschen Plans verwendet werden sollte.
Wenn das [!INCLUDE[ssde_md](../../includes/ssde_md.md)] den letzten bekannten guten Plan anwendet, wird automatisch die Leistung des erzwungenen Plans überwacht. Wenn der erzwungene Plan nicht besser als der zurück gestellte Plan ist, wird der neue Plan nicht erzwungen, und der [!INCLUDE[ssde_md](../../includes/ssde_md.md)] kompiliert einen neuen Plan. Wenn [!INCLUDE[ssde_md](../../includes/ssde_md.md)] überprüft, ob der erzwungene Plan besser als der zurück gestellte Plan ist, wird der erzwungene Plan beibehalten, wenn er besser als der zurück gestellte Plan ist, bis eine erneute Kompilierung stattfindet (z. b. bei der nächsten Statistik Aktualisierung oder bei der Schema Änderung).

> [!NOTE]
> Die automatische erzwungene Ausführung von Ausführungsplänen wird zwischen den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Neustarts der-Instanz nicht beibehalten.

### <a name="enabling-automatic-plan-choice-correction"></a>Aktivieren der automatischen Korrektur der Planauswahl

Sie können die automatische Optimierung pro Datenbank aktivieren und angeben, dass der letzte geeignete Plan erzwungen werden soll, wenn eine Regression der Planänderung erkannt wird. Die automatische Optimierung wird durch folgenden Befehl aktiviert:

```sql   
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON ); 
```

Nachdem Sie diese Option aktiviert haben, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] wird von automatisch jede Empfehlung erzwungen, bei der der geschätzte CPU-Zuwachs mehr als 10 Sekunden beträgt, oder die Anzahl der Fehler im neuen Plan ist höher als die Anzahl der Fehler im empfohlenen Plan und überprüft, ob der erzwungene Plan besser als der aktuelle ist.

### <a name="alternative---manual-plan-choice-correction"></a>Alternative – manuelle Korrektur der Planauswahl

Ohne die automatische Optimierung müssen Benutzer ihr System regelmäßig überwachen und nach zurückgestellten Abfragen suchen. Wenn ein Plan rückgängig gemacht wurde, sollte der Benutzer einen vorherigen guten Plan suchen und ihn anstelle des aktuellen Verfahrens `sp_query_store_force_plan` mit der Prozedur erzwingen. Die bewährte Vorgehensweise besteht darin, den letzten als funktionierend bekannten Plan zu erzwingen, da ältere Pläne aufgrund von Statistik-oder Indexänderungen möglicherweise ungültig sind. Der Benutzer, der den letzten bekannten guten Plan erzwingt, sollte die Leistung der Abfrage überwachen, die mit dem erzwungenen Plan ausgeführt wird, und überprüfen, ob der erzwungene Plan erwartungsgemäß funktioniert. Abhängig von den Ergebnissen der Überwachung und Analyse sollte der Plan erzwungen werden, oder der Benutzer sollte eine andere Möglichkeit finden, um die Abfrage zu optimieren.
Manuell erzwungene Pläne sollten nicht immer erzwungen werden, da der [!INCLUDE[ssde_md](../../includes/ssde_md.md)] in der Lage sein sollte, optimale Pläne anzuwenden. Der Benutzer oder DBA sollte die Erzwingungs Planung des `sp_query_store_unforce_plan` Plans schließlich mithilfe der Prozedur [!INCLUDE[ssde_md](../../includes/ssde_md.md)] erzwingen und den optimalen Plan suchen lassen. 

> [!TIP]
> Verwenden Sie in alternativelly die **Abfragen mit erzwungenen Plänen** Abfragespeicher Ansicht, um Pläne zu suchen und deren Erzwingung zu erzwingen.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]bietet alle notwendigen Sichten und Prozeduren, die zur Überwachung der Leistung und Behebung von Problemen in Abfragespeicher erforderlich sind.

In [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)]können Sie mit Abfragespeicher System Sichten Plan Auswahl Regressionen suchen. In [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] [!INCLUDE[ssde_md](../../includes/ssde_md.md)] erkennt und zeigt mögliche Regressionen der Plan Auswahl und die empfohlenen Aktionen an, die in der&#41;Sicht [sys. dm_db_tuning_recommendations &#40;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) angewendet werden sollen. Die Sicht zeigt Informationen zum Problem, die Wichtigkeit des Problems und Details wie z. b. die identifizierte Abfrage, die ID des zurück gestellten Plans, die ID des Plans, der als Baseline für den Vergleich verwendet wurde, und [!INCLUDE[tsql_md](../../includes/tsql-md.md)] die Anweisung, die ausgeführt werden kann, um das Problem zu beheben.

| type | description | datetime | Ergebnis Ihrer App | Details | ... |
| --- | --- | --- | --- | --- | --- |
| `FORCE_LAST_GOOD_PLAN` | Die CPU-Zeit wurde von 4 ms auf 14 ms geändert. | 3/17/2017 | 83 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |
| `FORCE_LAST_GOOD_PLAN` | Die CPU-Zeit wurde von 37 MS auf 84 MS geändert. | 3/16/2017 | 26 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |

Einige Spalten aus dieser Sicht werden in der folgenden Liste beschrieben:
 - Typ der empfohlenen Aktion:`FORCE_LAST_GOOD_PLAN`
 - Beschreibung, die Informationen enthält [!INCLUDE[ssde_md](../../includes/ssde_md.md)] , warum diese Planänderung eine potenzielle Leistungs Regression ist
 - DateTime-Wert, wenn die potenzielle Regression erkannt wird
 - Bewertung dieser Empfehlung
 - Details zu den Problemen, wie z. b. die ID des erkannten Plans, die ID des zurück gestellten Plans, die ID des Plans, der zur Behebung des [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Problems gezwungen werden soll, das Skript, das ggf. zur Behebung des Problems verwendet werden kann, usw. Details werden im [JSON-Format](../../relational-databases/json/index.md) gespeichert.

Verwenden Sie die folgende Abfrage zum Abrufen eines Skripts, das das Problem behebt, und zusätzliche Informationen zum geschätzten Gewinn:

```sql   
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                  * (regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
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

[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]     

| reason | Ergebnis Ihrer App | script | Abfrage\_-ID | ID des\_aktuellen Plans | Empfohlene Plan\_-ID | Geschätzter\_Gewinn | Fehler\_anfällig
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Die CPU-Zeit wurde von 3 MS in 46 MS geändert. | 36 | Exec SP\_Query\_Store\_Force\_Plan 12, 17; | 12 | 28 | 17 | 11,59 | 0

`estimated_gain`stellt die geschätzte Anzahl von Sekunden dar, die gespeichert werden, wenn der empfohlene Plan anstelle des aktuellen Plans ausgeführt würde. Der empfohlene Plan sollte anstelle des aktuellen Plans erzwungen werden, wenn der Gewinn größer als 10 Sekunden ist. Wenn im aktuellen Plan mehr Fehler (z. b. Timeouts oder abgebrochene Ausführungen) als im empfohlenen Plan vorhanden sind, wird die Spalte `error_prone` auf den Wert `YES`festgelegt. Der fehleranfällige Plan ist ein weiterer Grund, warum der empfohlene Plan anstelle des aktuellen Plans erzwungen werden sollte.

Stellt [!INCLUDE[ssde_md](../../includes/ssde_md.md)] zwar alle Informationen bereit, die zum Identifizieren von Plan Auswahl Regressionen erforderlich sind, die kontinuierliche Überwachung und das Beheben von Leistungsproblemen kann ein mühsamer Prozess sein. Durch die automatische Optimierung wird dieser Prozess erheblich vereinfacht.

> [!NOTE]
> Die Daten in der sys. dm_db_tuning_recommendations-DMV werden zwischen den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Neustarts der Instanz nicht beibehalten.

## <a name="automatic-index-management"></a>Automatische Indexverwaltung

In [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]ist die Index Verwaltung einfach, [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] da ihre Arbeitsauslastung erfährt und sicherstellt, dass Ihre Daten immer optimal indiziert werden. Das richtige Indexdesign ist von entscheidender Bedeutung für die optimale Leistung Ihrer Workload, und die automatische Indexverwaltung kann Ihnen bei der Optimierung Ihrer Indizes behilflich sein. Mit der automatischen Indexverwaltung können entweder Leistungsprobleme in falsch indizierten Datenbanken behoben werden, oder es können Indizes im vorhandenen Datenbankschema verwaltet und verbessert werden. Die automatische Optimierung [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] in führt die folgenden Aktionen aus:

 - Identifiziert Indizes, die die Leistung Ihrer [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Abfragen verbessern können, die Daten aus den Tabellen lesen.
 - Identifiziert die redundanten Indizes oder Indizes, die nicht in längerer Zeit verwendet wurden, die entfernt werden konnten. Durch das Entfernen unnötiger Indizes wird die Leistung von Abfragen verbessert, die Daten in Tabellen aktualisieren.

### <a name="why-do-you-need-index-management"></a>Gründe für die Nutzung der Indexverwaltung

Mit Indizes werden einige Ihrer Abfragen beschleunigt, mit denen Daten aus Ihren Tabellen gelesen werden. Für die Abfragen, mit denen Daten aktualisiert werden, können sie aber eine Verlangsamung bewirken. Sie müssen sorgfältig analysieren, wann Sie einen Index erstellen und welche Spalten Sie in den Index einbinden müssen. Einige Indizes werden nach einiger Zeit unter Umständen nicht mehr benötigt. Aus diesem Grund müssen Sie die Indizes, die nicht zu Vorteilen führen, regelmäßig identifizieren und verwerfen. Wenn Sie die nicht genutzten Indizes ignorieren, verringert sich die Leistung der Abfragen, mit denen Daten aktualisiert werden, ohne dass sich Vorteile für die Abfragen zum Lesen von Daten ergeben. Nicht verwendete Indizes wirken sich außerdem auf die Gesamtleistung des Systems aus, da für zusätzliche Updates eine unnötige Protokollierung erforderlich ist.

Zur Ermittlung des optimalen Satzes mit Indizes, mit denen die Leistung der Abfragen zum Lesen von Daten aus Ihren Tabellen verbessert wird und die eine minimale Auswirkung auf Updates hat, ist ggf. eine fortlaufende und komplexe Analyse erforderlich.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]verwendet integrierte und erweiterte Regeln, mit denen Ihre Abfragen analysiert, Indizes identifiziert werden, die für Ihre aktuellen Workloads optimal geeignet sind, und die Indizes möglicherweise entfernt werden. Mit Azure SQL-Datenbank wird sichergestellt, dass Sie über einen erforderlichen Mindestsatz von Indizes verfügen, mit denen die Abfragen zum Lesen von Daten optimiert werden und sich nur geringe Auswirkungen auf andere Abfragen ergeben.

### <a name="automatic-index-management"></a>Automatische Indexverwaltung

Zusätzlich zur Erkennung können identifizierte [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] Empfehlungen von automatisch angewendet werden. Wenn Sie feststellen, dass die integrierten Regeln die Leistung Ihrer Datenbank verbessern, können Sie die [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] Indizes automatisch verwalten.

Informationen zum Aktivieren der automatischen [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] Optimierung in und zur vollständigen Verwaltung der Arbeitsauslastung durch die Funktion zur automatischen Optimierung finden Sie unter [Aktivieren der automatischen Optimierung in Azure SQL-Datenbank mithilfe von Azure-Portal](/azure/sql-database/sql-database-automatic-tuning-enable).

Wenn eine [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] Create Index-oder Drop Index-Empfehlung anwendet, wird automatisch die Leistung der Abfragen überwacht, die vom Index betroffen sind. Der neue Index wird nur beibehalten, wenn die Leistung der betroffenen Abfragen verbessert wird. Der gelöschte Index wird automatisch neu erstellt, wenn einige Abfragen aufgrund der Abwesenheit des Indexes langsamer ausgeführt werden.

### <a name="automatic-index-management-considerations"></a>Aspekte der automatischen Indexverwaltung

Aktionen, die erforderlich sind, um [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] erforderliche Indizes in zu erstellen, können Ressourcen beanspruchen und die workloadleistung temporell Um die Auswirkungen der Indexerstellung auf die workloadleistung zu minimieren, [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] sucht das entsprechende Zeitfenster für jeden Index Verwaltungsvorgang. Ein Optimierungsvorgang wird verschoben, wenn die Datenbank Ressourcen zum Ausführen Ihrer Workload benötigt, und gestartet, wenn die Datenbank über genügend ungenutzte Ressourcen verfügt, die für die Wartungsaufgabe verwendet werden können. Ein wichtiges Feature der automatischen Indexverwaltung ist die Überprüfung der Aktionen. Wenn [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] Index erstellt oder gelöscht wird, analysiert ein Überwachungsprozess die Leistung der Arbeitsauslastung, um zu überprüfen, ob die Leistung durch die Aktion verbessert wurde. Wenn dies nicht zu einer erheblichen Verbesserung geführt hat, wird die Aktion sofort wieder hergestellt. Auf diese Weise [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] wird sichergestellt, dass sich automatische Aktionen nicht negativ auf die Leistung der Arbeitsauslastung auswirken. Indizes, die mit der automatischen Optimierung erstellt werden, sind für den Wartungsvorgang des zugrunde liegenden Schemas transparent. Schemaänderungen, wie das Verwerfen oder Umbenennen von Spalten, werden durch das Vorhandensein von automatisch erstellten Indizes nicht blockiert. Indizes, die automatisch von [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] erstellt werden, werden sofort gelöscht, wenn verknüpfte Tabellen oder Spalten gelöscht werden.

### <a name="alternative---manual-index-management"></a>Alternative: manuelle Index Verwaltung

Ohne die automatische Index Verwaltung müsste der Benutzer [sys. dm_db_missing_index_details &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) anzeigen oder den leistungsdashboardbericht in [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] verwenden, um Indizes zu suchen, die möglicherweise die Leistung verbessern, Indizes mithilfe der in dieser Ansicht bereitgestellten Details erstellen und die Leistung der Abfrage manuell überwachen. Um die Indizes zu ermitteln, die gelöscht werden sollen, sollten die Benutzer die Betriebs Verwendungs Statistik der Indizes überwachen, um selten verwendete Indizes zu finden.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]vereinfacht diesen Prozess. [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]analysiert ihre Arbeitsauslastung, identifiziert die Abfragen, die mit einem neuen Index schneller ausgeführt werden können, und identifiziert nicht verwendete oder duplizierte Indizes. Weitere Informationen zur Identifikation von Indizes, die geändert werden sollten, finden Sie unter [Azure SQL Database Advisor im Azure-Portal](https://docs.microsoft.com/azure/sql-database/sql-database-advisor-portal).

## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys. database_automatic_tuning_options &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)  
 [sys. dm_db_tuning_recommendations &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 [sys. dm_db_missing_index_details &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sp_query_store_force_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)     
 [sp_query_store_unforce_plan &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)           
 [sys. database_query_store_options &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON-Funktionen](../../relational-databases/json/index.md)    
 [Ausführungspläne](../../relational-databases/performance/execution-plans.md)    
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Tools für die Leistungsüberwachung und -optimierung](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [Abfrageoptimierungs-Assistent](../../relational-databases/performance/upgrade-dbcompat-using-qta.md)
