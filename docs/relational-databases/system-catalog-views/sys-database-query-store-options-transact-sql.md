---
title: database_query_store_options (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de6033aaa70b415ff7d218c2a0d8c3138845c8fc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022641"
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Die Abfrage von Store-Optionen für diese Datenbank zurückgegeben.  
  
**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Gibt an, den gewünschten Betriebsmodus des Abfrage-Store, die explizit vom Benutzer festgelegt.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(60)**|Textbeschreibung für den gewünschten Betriebsmodus des Query Store:<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Gibt den Betriebsmodus des Abfrage-Store an. Zusätzlich zu der gewünschten Status seitens des Benutzers erforderlich kann die ist-Zustand Status "Fehler" sein.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = FEHLER|  
|**actual_state_desc**|**nvarchar(60)**|Die textbeschreibung der tatsächlichen Betriebsmodus des Abfrage-Store.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />Fehler<br /><br /> Es gibt Situationen, wenn der tatsächliche Zustand vom gewünschten Zustand abweicht:<br />– Wenn die Datenbank in den schreibgeschützten Modus festgelegt ist, oder wenn Query Store-Größe das konfigurierte Kontingent überschreitet, kann Query Store im Nur-Lese Modus betrieben werden, auch wenn die Lese-/ Schreibzugriff, die vom Benutzer angegeben wurde.<br />– In extremen Szenarien können Query Store Status "Fehler" aufgrund von internen Fehlern eingeben. In diesem, SQL 2017 und höher Fall können Query Store wiederhergestellt werden, durch Ausführen der `sp_query_store_consistency_check` gespeicherten Prozedur in die betroffene Datenbank aus. Wenn `sp_query_store_consistency_check` funktioniert nicht, und für SQL 2016, benötigen Sie die Daten durch Ausführen von gelöscht `ALTER DATABASE [YourDatabaseName] SET QUERY_STORE CLEAR ALL;`|  
|**readonly_reason**|**int**|Wenn die **Desired_state_desc** ist READ_WRITE und **Actual_state_desc** ist READ_ONLY, **Readonly_reason** gibt etwas angeben, warum die Query Store in zuordnen Schreibgeschützter Modus.<br /><br /> **1** -Datenbank befindet sich im schreibgeschützten Modus<br /><br /> **2** -Datenbank befindet sich im Einzelbenutzermodus<br /><br /> **4** -Datenbank befindet sich im Notfallmodus<br /><br /> **8** -Datenbank ist sekundären Replikat (gilt für Always On und [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] georeplikation). Dieser Wert kann nur auf effektiv beobachtet werden **lesbare** sekundäre Replikate<br /><br /> **65536** -die Query Store wurde erreicht das Größenlimit von der MAX_STORAGE_SIZE_MB-Option festgelegt.<br /><br /> **131072** -die Anzahl der verschiedene Anweisungen in Query Store hat das interne Arbeitsspeicherlimit erreicht. Entfernen Sie ggf. Abfragen, die Sie nicht benötigen oder ein Upgrade auf eine höhere Dienstebene zu aktivieren, übertragen Query Store in Lese-/ Schreibmodus fest.<br />**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> **262144** -Größe der Elemente im Arbeitsspeicher, die darauf warten, auf dem Datenträger beibehalten werden der internen Speicher erreicht hat. Query Store werden im Nur-Lese Modus ist vorübergehend, bis die Elemente im Arbeitsspeicher auf dem Datenträger beibehalten werden. <br />**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> **524288** -Datenbank hat die datenträgergrößenbegrenzung erreicht. Query Store ist Teil des Benutzerdatenbank, sodass es ist nicht mehr verfügbaren Speicherplatz für eine Datenbank, die das bedeutet, dass Query Store weiter wachsen kann nicht mehr.<br />**Gilt für:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. <br /> <br /> So wechseln Sie die Abfrage von Store-Vorgänge Modus Back Lese-/ Schreibzugriff, finden Sie unter **überprüfen Query Store wird das Sammeln von kontinuierlich** Abschnitt [bewährte Methoden für die Query Store](../../relational-databases/performance/best-practice-with-the-query-store.md#Verify).|  
|**current_storage_size_mb**|**bigint**|Die Größe des Abfrage-Store auf dem Datenträger in Megabyte.|  
|**flush_interval_seconds**|**bigint**|Der Zeitraum für das reguläre leeren Abfrage von Store-Daten auf dem Datenträger in Sekunden. Standardwert ist **900** (15 Min.).<br /><br /> Ändern Sie mithilfe der `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` Anweisung.|  
|**interval_length_minutes**|**bigint**|Die Statistiken aggregationsintervall in Minuten. Beliebige Werte sind nicht zulässig. Verwenden Sie einen der folgenden Werte: 1, 5, 10, 15, 30, 60 und 1440 Minuten. Der Standardwert ist **60** Minuten.|  
|**max_storage_size_mb**|**bigint**|Maximale Datenträgergröße für die Query Store in Megabyte (MB). Standardwert ist **100** MB.<br />Für [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition, Standard ist 1 GB und für [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition, Standardwert ist 10 MB.<br /><br /> Ändern Sie mithilfe der `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` Anweisung.|  
|**stale_query_threshold_days**|**bigint**|Anzahl der Tage, die Abfragen mit keine Richtlinieneinstellungen in Query Store gespeichert werden. Standardwert ist **30**. So deaktivieren Sie die Aufbewahrungsrichtlinie auf 0 festgelegt.<br />Für die Basic-Edition von [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ist der Standardwert 7 Tage.<br /><br /> Ändern Sie mithilfe der `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` Anweisung.|  
|**max_plans_per_query**|**bigint**|Beschränkt die maximale Anzahl von gespeicherten Pläne an. Standardwert ist **200**. Wenn der Höchstwert erreicht ist, beendet Query Store die Erfassung neuer Pläne für diese Abfrage. Einstellung auf 0 wird die Beschränkung im Hinblick auf die Anzahl der erfassten Pläne.<br /><br /> Ändern Sie mithilfe der `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` Anweisung.|  
|**query_capture_mode**|**smallint**|Die derzeit aktiven abfrageerfassungsmodus:<br /><br /> **1** = ALL - alle Abfragen werden erfasst. Dies ist der standardkonfigurationswert für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> 2 = die AUTO - Erfassung relevante Abfragen basierend auf Anzahl und Ausführung des Ressourcenverbrauchs. Dies ist der standardkonfigurationswert für [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = keine - Erfassung neuer Abfragen beendet. Der Abfragedatenspeicher sammelt weiterhin Statistiken zur Kompilierung und Runtime für Abfragen, die bereits erfasst wurden. Verwenden Sie diese Konfiguration mit Vorsicht, da Sie dadurch möglicherweise wichtige Abfragen zu erfassen.|  
|**query_capture_mode_desc**|**nvarchar(60)**|Die textbeschreibung der tatsächlichen Aufzeichnungsmodus Query Store:<br /><br /> Alle (Standard für [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> **AUTOMATISCHE** (Standard für [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> Keine|  
|**size_based_cleanup_mode**|**smallint**|Steuert, ob die Bereinigung automatisch aktiviert wird, wenn sich die Gesamtmenge der Daten der maximalen Größe nähert:<br /><br /> 0 = OFF - größenbasierte Cleanup wird nicht automatisch aktiviert.<br /><br /> **1** = die AUTO - größenbasierte Cleanup wird automatisch aktiviert, wenn der Wert auf dem Datenträger erreicht **90 Prozent** von *Max_storage_size_mb*. Dies ist der Standardkonfigurationswert.<br /><br />Ein auf der Größe basierendes Cleanup entfernt die am wenigsten aufwendigen und die ältesten Abfragen. Beendet, wenn ungefähr **80 Prozent** von *Max_storage_size_mb* erreicht ist.|  
|**size_based_cleanup_mode_desc**|**nvarchar(60)**|Die textbeschreibung der tatsächlichen größenbasierte Cleanup-Modus des Query Store:<br /><br /> OFF <br /> **AUTOMATISCHE** (Standard)|  
|**wait_stats_capture_mode**|**smallint**|Steuert, ob Query Store Erfassung von Statistiken zu abfragewartevorgängen ausführt: <br /><br /> 0 = OFF <br /> **1** = ON<br /> **Gilt für**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|**wait_stats_capture_mode_desc**|**nvarchar(60)**|Die textbeschreibung der tatsächlichen Wait Statistiken standarderfassungsmodus ein Modus: <br /><br /> OFF <br /> **ON** (Standard)<br /> **Gilt für**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW DATABASE STATE`-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [Query Store gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
