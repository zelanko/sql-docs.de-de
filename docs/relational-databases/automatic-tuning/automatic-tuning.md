---
title: Die automatische Optimierung | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67934557"
---
# <a name="automatic-tuning"></a>Automatische Optimierung
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Die automatische Datenbankoptimierung bietet einen Einblick in die potentiellen Abfrageleistungsprobleme, empfiehlt Lösungen und kann identifizierte Probleme automatisch beheben.

Automatische Optimierung in [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] benachrichtigt Sie, wenn ein mögliches Leistungsproblem erkannt wird. zudem Sie die korrigierende Aktionen angewendet werden sollen können, oder Sie können die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Leistungsprobleme automatisch beheben.
Automatische Optimierung in [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] ermöglicht es Ihnen, identifizieren und Beheben von Leistungsproblemen aufgrund **Execution Plan Choice abfrageregressionen**. Automatische Optimierung in [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] auch die erforderlichen Indizes erstellt und löscht nicht verwendete Indizes. Weitere Informationen zu Abfrageausführungspläne, finden Sie unter [Ausführungspläne](../../relational-databases/performance/execution-plans.md).

Die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verbessert die Leistung der Workload, überwacht die Abfragen, die in der Datenbank und automatisch ausgeführt werden. Die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] verfügt über einen integrierten intelligenten Funktionen Mechanismus, der automatisch optimiert werden kann, und Verbessern der Leistung Ihrer Abfragen durch die dynamische Anpassung der Datenbank an Ihre Workload. Es gibt zwei Automatische Optimierung Features, die verfügbar sind:

 -  **Automatische plankorrektur** problematische Abfragen, Pläne und korrigiert abfrageausführung Leistungsprobleme Plänen identifiziert. **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]) und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
 -  **Automatische indexverwaltung** identifiziert Indizes, die in der Datenbank hinzugefügt werden soll, und solche, die entfernt werden soll. **Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

## <a name="why-automatic-tuning"></a>Warum die automatische Optimierung?

Drei der Hauptaufgabe bei der Verwaltung von klassischen Datenbanken sind das Überwachen der Workload, identifizieren kritische [!INCLUDE[tsql_md](../../includes/tsql-md.md)] abfragt, Indizes, die hinzugefügt, um die Leistung zu verbessern und identifizierende selten verwendet werden sollen. Die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] bietet detaillierte Einblicke in die Abfragen und Indizes, die Sie überwachen müssen. Kontinuierliche Überwachung der eine Datenbank ist jedoch eine schwierige und aufwendige Aufgabe, insbesondere bei sehr vielen Datenbanken. Verwalten einer großen Anzahl von Datenbanken möglicherweise nicht möglich, effizient durchführen. Anstelle der manuellen Überwachung und Optimierung Ihrer Datenbank, sollten Sie erwägen, einige für die Überwachung zu delegieren und Optimieren von Aktionen, die die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] mithilfe von Features zur automatischen Optimierung.

### <a name="how-does-automatic-tuning-work"></a>Wie funktioniert die automatische Optimierung?

Die automatische Optimierung ist eine kontinuierliche Überwachung und Analyseprozess, der über die Merkmale Ihrer Workload ständig lernen und identifizieren Sie potenzielle Probleme und verbesserungsmöglichkeiten.

![Automatischer Optimierungsprozess](./media/tuning-process.png)

Dieser Prozess ermöglicht es Datenbank eine dynamische Anpassung an Ihre Workload durch suchen, welche Indizes und Pläne die Leistung Ihrer Workloads verbessern können und welche Indizes Ihre Workloads auswirken. Basierend auf diesen ermittelten, gilt die automatische Optimierung optimierungsaktionen, die die Leistung Ihrer Workload zu verbessern. Darüber hinaus überwacht Datenbank kontinuierlich die Leistung nach jeder Änderung, die von der automatischen Optimierung vorgenommen werden, um sicherzustellen, dass sie die Leistung Ihrer Workload verbessert. Alle Aktionen, die Leistung zu verbessern, nicht haben wird automatisch zurückgesetzt. Diese Überprüfung ist ein wichtiges Feature, das sicherstellt, dass jede Änderung, die von der automatischen Optimierung der Leistung Ihrer Workload nicht verringert.

## <a name="automatic-plan-correction"></a>Automatische plankorrektur

Automatische plankorrektur ist ein Feature der automatischen Optimierung, die identifiziert **Wahl Regression von Ausführungsplänen** und automatisch das Problem beheben, indem Sie den letzten bekannten guten Plan zu erzwingen. Weitere Informationen zu Abfrageausführungspläne und der Abfrageoptimierer, finden Sie unter den [Query Processing Architecture Guide](../../relational-databases/query-processing-architecture-guide.md).

### <a name="what-is-execution-plan-choice-regression"></a>Was ist die Ausführung von planauswahlen?

Die [!INCLUDE[ssdenoversion_md](../../includes/ssdenoversion_md.md)] können Sie verschiedenen Ausführungsplänen führen Sie die [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Abfragen. Abfragepläne, abhängig von der Statistik, Indizes und anderen Faktoren ab. Der optimale Plan, die verwendet werden soll, um einige auszuführen [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Abfrage im Laufe der Zeit ändern kann. In einigen Fällen der neue Plan besser als die vorherige Version möglicherweise nicht, und der neue Plan kann einem Leistungsverlust führen.

 ![Abfragen von planauswahlen Ausführung](media/plan-choice-regression.png "Ausführung planauswahlen Abfragen") 

Wenn Sie eine Regression der Planauswahl feststellen, sollten finden Sie einige vorherige gute Planung und ihn zwingen, anstatt die aktuelle eine `sp_query_store_force_plan` Verfahren.
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] in [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] enthält Informationen zu einem Regress geführt hatten Pläne und korrigierende Maßnahmen empfohlen.
Darüber hinaus [!INCLUDE[ssde_md](../../includes/ssde_md.md)] ermöglicht es Ihnen, vollständig diesen Prozess auch automatisieren, und lassen Sie [!INCLUDE[ssde_md](../../includes/ssde_md.md)] beheben Sie alle gefundenen Probleme im Zusammenhang mit den Änderungen an Abfrageplänen.

### <a name="automatic-plan-choice-correction"></a>Automatische Korrektur der Planauswahl

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] können automatisch in den letzten bekannten guten Plan wechselt, wenn Regression der Planauswahl erkannt wird.

![Fragen Sie die Ausführung der Planauswahl](media/force-last-good-plan.png "Abfragen die Ausführung der Planauswahl") 

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] erkennt automatisch alle potenziellen planauswahlen, einschließlich des Plans, der statt des falschen Plans verwendet werden soll.
Wenn die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] wendet den letzten bekannten geeigneten Plan, automatisch die Leistung des erzwungenen Plans überwacht. Wenn der erzwungene Plan nicht besser als der zurückgestellte Plan ist, wird der neue Plan mehr erzwungen werden und die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] wird einen neuen Plan kompiliert. Wenn die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] bestätigt, dass der erzwungene Plan besser als der zurückgestellte Plan ist, wird der erzwungene Plan beibehalten werden, ist es besser, als der zurückgestellte Plan ist, bis zum Auftreten eine Neukompilierung (z. B. auf die nächste Änderung der Statistiken aktualisieren "oder" Schema).

> [!NOTE]
> Jede Ausführung Pläne automatisch erzwungen werden nicht beibehalten, nach einem Neustart von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz.

### <a name="enabling-automatic-plan-choice-correction"></a>Aktivieren der automatischen Korrektur der Planauswahl

Sie können die automatische Optimierung pro Datenbank aktivieren und angeben, dass der letzte geeignete Plan erzwungen werden soll, wenn eine Regression der Planänderung erkannt wird. Die automatische Optimierung wird durch folgenden Befehl aktiviert:

```sql   
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON ); 
```

Nachdem Sie diese Option aktiviert die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] automatisch jede Empfehlung, in denen die geschätzte CPU-Gewinn größer als 10 Sekunden ist, oder die Anzahl von Fehlern im neuen Plan ist höher als die Anzahl von Fehlern im empfohlenen Plan, und überprüfen Sie, ob die Erzwungene Plan ist besser als die der aktuellen Aktivität.

### <a name="alternative---manual-plan-choice-correction"></a>Alternative – manuelle Korrektur der Planauswahl

Ohne die automatische Optimierung müssen Benutzer ihr System regelmäßig überwachen und nach zurückgestellten Abfragen suchen. Wenn Pläne zurückgestellt wurden, sollten Benutzer gefunden, einige vorherige gute Planung und ihn zwingen, anstatt die aktuelle eine `sp_query_store_force_plan` Verfahren. Die bewährte Methode wäre, die den letzten bekannten guten Plan erzwungen werden, weil ältere Pläne möglicherweise aufgrund von Änderungen der Statistik oder ein Index ungültig. Der Benutzer, die erzwingt, die letzten bekannten guten Plan dass sollte Überwachen der Leistung der Abfragen, die mit der erzwungene Plan ausgeführt wird, und überprüfen Sie, der erzwungenen Plan wie erwartet funktioniert. Abhängig von den Ergebnissen der Überwachung und Analyse Plan erzwungen werden soll, oder Benutzer sollte eine andere Möglichkeit zum Optimieren der Abfrage zu suchen.
Manuell erzwungene Plänen sollte nicht dauerhaft, erzwungen werden, da die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] optimalen Plänen anwenden können. Der Benutzer oder der Datenbankadministrator sollte schließlich Erzwingung der Plan mit `sp_query_store_unforce_plan` Prozedur ab, und die [!INCLUDE[ssde_md](../../includes/ssde_md.md)] den optimalen Plan zu finden. 

> [!TIP]
> Alternativelly, verwenden die **Abfragen mit erzwungenen Plänen** Query Store Sicht zu suchen und die Erzwingung des Plans.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst alle erforderlichen Sichten und Prozeduren zum Überwachen der Leistung und Beheben von Problemen in Query Store erforderlich sind.

In [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], finden Sie Plan planauswahlregression Systemsichten Query Store verwenden. In [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)], [!INCLUDE[ssde_md](../../includes/ssde_md.md)] erkennt und zeigt potenzielle planregressionen Wahl und die empfohlenen Aktionen, die in angewendet werden sollen die [dm_db_tuning_recommendations &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) anzeigen. Die Ansicht zeigt Informationen über das Problem, das die Wichtigkeit des Problems und Details wie den identifizierten Abfragen, die von der zurückgestellte Plan-ID, die ID des Plans, der als Baseline zum Vergleich verwendet wurde und die [!INCLUDE[tsql_md](../../includes/tsql-md.md)] -Anweisung, die ausgeführt werden kann, lösen Sie die Problem.

| Typ | description | DATETIME | score | Details | ... |
| --- | --- | --- | --- | --- | --- |
| `FORCE_LAST_GOOD_PLAN` | CPU-Zeit, die von 4 ms in 14 ms geändert | 3/17/2017 | 83 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |
| `FORCE_LAST_GOOD_PLAN` | CPU-Zeit, die von 37 ms in 84 ms geändert | 3/16/2017 | 26 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |

Einige Spalten in dieser Ansicht werden in der folgenden Liste beschrieben:
 - Typ, der die empfohlene Aktion: `FORCE_LAST_GOOD_PLAN`
 - Beschreibung, die Informationen, warum enthält [!INCLUDE[ssde_md](../../includes/ssde_md.md)] davon ausgeht, dass diese Änderung des Plans ein potenzieller Leistungsverlust wird
 - "DateTime", wenn die mögliche Regression erkannt wird
 - Bewertung von dieser Empfehlung
 - Details zu den Problemen wie z. B. die ID des erkannten Plan-ID des der zurückgestellte Plan mit der ID des Plans, die erzwungen werden soll, um das Problem zu beheben [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Skripts, die zum Beheben des Problems usw. angewendet werden kann. Details werden gespeichert, [JSON-Format](../../relational-databases/json/index.md)

Verwenden Sie die folgende Abfrage aus, um ein Skript zu erhalten, die das Problem und zusätzliche Informationen zu den geschätzten Korrekturen erhalten:

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

| reason | score | Skript (script) | Abfrage\_Id | Aktueller Plan\_Id | Empfohlene Plan\_Id | Geschätzte\_zu erhalten | Fehler\_fehleranfällig
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| CPU-Zeit von 3 ms in 46 ms geändert | 36 | EXEC sp\_Abfrage\_speichern\_erzwingen\_Plan 12, 17; | 12 | 28 | 17 | 11.59 | 0

`estimated_gain` Stellt die geschätzte Anzahl von Sekunden an, die gespeichert werden würde, wenn es sich bei der empfohlenen Plan statt des aktuellen Plans ausgeführt werden. Empfohlene Plan sollte anstelle der aktuellen Plan erzwungen werden, wenn der Gewinn größer als 10 Sekunden ist. Wenn weitere Fehler vorliegen (z. B. Timeouts oder abgebrochene Ausführungen) im aktuellen Plan als in der empfohlenen planen, die Spalte `error_prone` festgelegt werden sollen, auf den Wert `YES`. Fehler verursachenden Plan ist ein weiterer Grund, warum die empfohlenen Plan anstelle des aktuellen erzwungen werden soll.

Obwohl [!INCLUDE[ssde_md](../../includes/ssde_md.md)] enthält alle Informationen, die zum Identifizieren Ihrer Wahl planregressionen; kontinuierliche das überwachungs- und das Beheben von Leistungsproblemen erforderlich sind, möglicherweise eine mühsame Angelegenheit. Die automatische Optimierung vereinfacht diesen Prozess.

> [!NOTE]
> Daten in der DMV dm_db_tuning_recommendations werden nicht beibehalten, nach einem Neustart von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz.

## <a name="automatic-index-management"></a>Automatische indexverwaltung

In [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], indexverwaltung ist einfach weil [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] Features, die über Ihre arbeitsauslastung und stellt sicher, dass Ihre Daten immer optimal indiziert sind. Das richtige indexdesign ist entscheidend für eine optimale Leistung Ihrer Workload und automatische indexverwaltung können Sie die Optimierung Ihrer Indizes. Automatische indexverwaltung kann entweder beheben Sie Leistungsprobleme in falsch indizierten Datenbanken oder verwalten und verbessern Sie die Indizes auf das vorhandene Datenbankschema. Automatische Optimierung in [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] führt folgende Aktionen aus:

 - Identifiziert Indizes, die Leistung verbessern könnten Ihre [!INCLUDE[tsql_md](../../includes/tsql-md.md)] Abfragen, die Daten aus den Tabellen zu lesen.
 - Identifiziert die redundante Indizes oder Indizes, die in längeren Zeitraum nicht verwendet wurden, die entfernt werden konnte. Entfernen unnötiger Indizes verbessert die Leistung der Abfragen, die Daten in Tabellen zu aktualisieren.

### <a name="why-do-you-need-index-management"></a>Warum benötigen Sie die indexverwaltung?

Indizes, beschleunigen Sie einige Abfragen, die Daten aus den Tabellen zu lesen; Allerdings können sie die Abfragen verlangsamt, die Daten aktualisieren. Sie müssen sorgfältig analysieren Sie beim Erstellen einen Index und welche Spalten in den Index aufgenommen werden sollen. Einige Indizes können nicht nach einiger Zeit erforderlich sein. Daher müssten Sie regelmäßig identifizieren und verwerfen die Indizes, die kein Vorteilen führen. Wenn Sie die nicht genutzten Indizes ignorieren, würde Leistung der Abfragen, die Daten aktualisieren, ohne dass sich Vorteile für Abfragen verringert werden, die Daten lesen. Nicht verwendete Indizes wirken sich auch auf die gesamtleistung des Systems aus, da zusätzliche Updates unnötige Protokollierung erforderlich ist.

Ermitteln des optimalen Satzes mit Indizes, die Leistung der Abfragen zu verbessern, die Daten aus Ihren Tabellen gelesen und eine minimale Auswirkung auf Updates möglicherweise eine fortlaufende und komplexe Analyse.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] verwendet integrierte Intelligenz und erweiterte Regeln, die Ihren Abfragen zu analysieren, identifizieren Indizes, die für Ihre aktuellen Workloads optimal, und die Indizes entfernt werden können. Azure SQL-Datenbank wird sichergestellt, dass Sie einen erforderlichen Mindestsatz von Indizes verfügen, die die Abfragen zu optimieren, die Daten mit Auswirkungen auf andere Abfragen zu lesen.

### <a name="automatic-index-management"></a>Automatische indexverwaltung

Zusätzlich zur Erkennung [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] identifizierte Empfehlungen automatisch angewendet werden können. Wenn Sie feststellen, dass die integrierten Regeln die Leistung Ihrer Datenbank verbessern, können Sie möglicherweise [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] automatisch Ihre Indizes zu verwalten.

Zum Aktivieren der automatischen Optimierung [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] und ermöglicht das automatische Abstimmungsfeature vollständig Ihrer Workload zu verwalten, finden Sie unter [Aktivieren der automatischen Optimierung in Azure SQL-Datenbank mithilfe von Azure-Portal](/azure/sql-database/sql-database-automatic-tuning-enable).

Wenn die [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] gilt eine CREATE Index- oder DROP INDEX-Empfehlung, es überwacht automatisch die Leistung von Abfragen, die der Index betroffen sind. Neuer Index werden nur dann, wenn die Leistung der betroffen Abfragen verbessert werden beibehalten. Der gelöschte Index werden automatisch neu erstellt, wenn einige Abfragen, die aufgrund eines fehlenden Indexes langsamer ausgeführt.

### <a name="automatic-index-management-considerations"></a>Aspekte der automatischen indexverwaltung

Die erforderlichen Aktionen zum Erstellen von erforderlichen Indizes in [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] möglicherweise verbrauchen Ressourcen und Workloads vorübergehend beeinträchtigt. Zur Minimierung der Auswirkung der indexerstellung für die arbeitsauslastungsleistung, [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] findet das passende Zeitfenster für jeden Index-Management-Vorgang. Optimierungsvorgang wird verschoben, wenn die Datenbank Ressourcen zum Ausführen Ihrer Workload benötigt, und gestartet, wenn die Datenbank mit ausreichend freiem ungenutzte Ressourcen, die für die Wartungsaufgabe verwendet werden können. Ein wichtiges Feature der automatischen indexverwaltung ist eine Überprüfung der Aktionen. Wenn [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] erstellt oder löscht Index ein Überwachungsprozess analysiert die Leistung Ihrer Workload, um sicherzustellen, dass die Aktion, die Leistung verbessert. Wenn sie bedeutende Verbesserung - bringen nicht wird die Aktion sofort rückgängig gemacht werden. Auf diese Weise [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] wird sichergestellt, dass automatische Aktionen nicht negativ auf Leistung Ihrer Workload auswirken. Indizes, die von der automatischen Optimierung erstellt sind für den Wartungsvorgang des zugrunde liegenden Schemas transparent. Schemaänderungen wie das Verwerfen oder Umbenennen von Spalten werden durch das Vorhandensein von automatisch erstellten Indizes nicht blockiert. Indizes, die automatisch, indem erstellt werden [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] werden sofort gelöscht wird, wenn im Zusammenhang, Tabelle oder Spalten verworfen.

### <a name="alternative---manual-index-management"></a>Alternative – manuelle indexverwaltung

Ohne automatische indexverwaltung, Benutzer manuell Abfragen müssten [Sys. dm_db_missing_index_details &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) anzeigen oder verwenden Sie den Bericht Leistungsdashboard in [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] Indizes suchen, die möglicherweise die verbessern Sie Leistung, erstellen Sie Indizes, die mithilfe der Informationen in dieser Ansicht und manuell überwachen Sie der Leistung der Abfrage. Um die Indizes zu finden, die gelöscht werden sollen, sollten Benutzer operational Nutzungsstatistiken für die die Indizes zu suchen, die nur selten verwendete Indizes überwachen.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] vereinfacht diesen Vorgang. [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] die arbeitsauslastung analysiert, werden die Abfragen identifiziert, die mit einem neuen Index schneller ausgeführt werden konnte und identifiziert nicht verwendete oder duplizierte Indizes. Suche nach Informationen zur Identifikation von Indizes, die Sie auf Ändern [finden Sie im Azure-Portal indexempfehlungen](https://docs.microsoft.com/azure/sql-database/sql-database-advisor-portal).

## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)  
 [dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)     
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)           
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [JSON-Funktionen](../../relational-databases/json/index.md)    
 [Ausführungspläne](../../relational-databases/performance/execution-plans.md)    
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Tools für die Leistungsüberwachung und -optimierung](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [Abfrage Optimierung-Assistent](../../relational-databases/performance/upgrade-dbcompat-using-qta.md)
