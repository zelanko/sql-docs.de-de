---
title: sys.query_store_plan (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_PLAN_TSQL
- SYS.QUERY_STORE_PLAN
- SYS.QUERY_STORE_PLAN_TSQL
- QUERY_STORE_PLAN
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_plan catalog view
- sys.query_store_plan catalog view
ms.assetid: b4d05439-6360-45db-b1cd-794f4a64935e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7adf4a825fb93b6c87714476607b30e9f4ec97a7
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833573"
---
# <a name="sysquerystoreplan-transact-sql"></a>sys.query_store_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Enthält Informationen über jeden Ausführungsplan, der mit einer Abfrage verbunden.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|
|**plan_id**|**bigint**|Der Primärschlüssel.|  
|**query_id**|**bigint**|Fremdschlüssel. Verknüpft mit [query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md).|  
|**plan_group_id**|**bigint**|Die ID der Gruppe "Plan". Cursorabfragen erfordern in der Regel mehrere (Auffüllen und fetch) Pläne. Füllen und Fetch-Pläne, die zusammen kompiliert werden, befinden sich in derselben Gruppe.<br /><br /> 0 bedeutet, dass der Plan nicht in einer Gruppe ist.|  
|**engine_version**|**nvarchar(32)**|Version des Moduls verwendet, um den Plan im Kompilieren **"major.minor.build.revision"** Format.|  
|**compatibility_level**|**smallint**|Der Kompatibilitätsgrad der Datenbank, die in der Abfrage verwiesen wird.|  
|**query_plan_hash**|**binary(8)**|MD5-Hash des einzelnen Plans.|  
|**query_plan**|**nvarchar(max)**|Showplan XML für den Abfrageplan.|  
|**is_online_index_plan**|**bit**|Plan wurde während einer onlineindexerstellung verwendet. <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**is_trivial_plan**|**bit**|Plan ist ein trivialer Plan (die Ausgabe in Phase 0 der Abfrageoptimierer). <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**is_parallel_plan**|**bit**|Plan ist parallel. <br/>**Hinweis**: Azure SQL Data Warehouse wird immer eins (1) zurückgegeben.|  
|**is_forced_plan**|**bit**|Plan wird markiert, da erzwungen, wenn Benutzer die gespeicherte Prozedur ausführt **sys.sp_query_store_force_plan**. Nutzungsplanerzwingungsmechanismus *garantiert keine* dieser verwendet genau diesen Plan für die Abfrage verweist **Query_id**. Bewirkt, dass die Abfrage erneut kompiliert werden und in der Regel erzeugt genau den gleichen oder ähnlichen Plan für den Plan aus, auf die verwiesen wird durch das Erzwingen eines Plans **Plan_id**. Wenn das Erzwingen eines Plans nicht gelingt, **Force_failure_count** wird erhöht, und **Last_force_failure_reason** mit Fehlerursache aufgefüllt wird. <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**is_natively_compiled**|**bit**|Plan enthält Speicheroptimierte systemintern kompilierte Prozeduren. (0 = FALSE, 1 = TRUE). <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**force_failure_count**|**bigint**|Anzahl der Fälle, in denen dieser Plan erzwingen ein Fehler aufgetreten ist. Er kann erhöht werden, nur, wenn die Abfrage erneut kompiliert wird (*nicht bei jeder Ausführung*). Es auf 0 zurückgesetzt wird jedes Mal **Is_plan_forced** ändert sich von **"false"** zu **"true"** . <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**last_force_failure_reason**|**int**|Der Grund, warum das Erzwingen eines Plans fehlgeschlagen ist.<br /><br /> 0: kein Fehler, die andernfalls Fehlernummer des Fehlers, der verursacht hat, der erzwungen wird fehlschlagen<br /><br /> 8637: ONLINE_INDEX_BUILD<br /><br /> 8683: INVALID_STARJOIN<br /><br /> 8684: TIME_OUT<br /><br /> 8689: NO_DB<br /><br /> 8690: HINT_CONFLICT<br /><br /> 8691: SETOPT_CONFLICT<br /><br /> 8694: DQ_NO_FORCING_SUPPORTED<br /><br /> 8698: NO_PLAN<br /><br /> 8712: NO_INDEX<br /><br /> 8713: VIEW_COMPILE_FAILED<br /><br /> \<anderer Wert >: GENERAL_FAILURE <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**last_force_failure_reason_desc**|**nvarchar(128)**|Textbeschreibung des Last_force_failure_reason_desc.<br /><br /> ONLINE_INDEX_BUILD: Abfrage versucht, um Daten zu ändern, während die Zieltabelle einen Index verfügt, der online erstellt wird<br /><br /> INVALID_STARJOIN: Plan enthält ungültige StarJoin-Spezifikation<br /><br /> TIME_OUT: Anzahl zulässiger Vorgänge bei der Suche nach anhand des erzwungenen Plan Optimizer überschritten<br /><br /> NO_DB: Eine Datenbank, die im Plan angegeben ist nicht vorhanden.<br /><br /> HINT_CONFLICT: Abfrage kann nicht kompiliert werden, da der Plan mit einem Abfragehinweis steht in Konflikt<br /><br /> DQ_NO_FORCING_SUPPORTED: Abfrage kann nicht ausgeführt werden, da der Plan mit Verwendung der verteilten Abfrage oder volltextvorgänge in Konflikt steht.<br /><br /> NO_PLAN: Abfrageprozessor konnte keine Abfrageplan erstellen, da der erzwungene Plan nicht überprüft werden konnte, für die Abfrage gültig ist<br /><br /> NO_INDEX: Index, der im Plan angegeben sind, nicht mehr vorhanden ist.<br /><br /> VIEW_COMPILE_FAILED: Abfrageplan konnte aufgrund eines Problems in einer indizierten Sicht, die im Plan verwiesen wird nicht erzwungen werden.<br /><br /> GENERAL_FAILURE: Allgemeiner erzwingen-Fehler (nicht mit den oben genannten Gründen behandelt) <br/>**Hinweis**: Azure SQL Data Warehouse gibt stets *NONE*.|  
|**count_compiles**|**bigint**|Planen Sie die Kompilierung Statistiken.|  
|**initial_compile_start_time**|**datetimeoffset**|Planen Sie die Kompilierung Statistiken.|  
|**last_compile_start_time**|**datetimeoffset**|Planen Sie die Kompilierung Statistiken.|  
|**last_execution_time**|**datetimeoffset**|Zeitpunkt der letzten Ausführung bezeichnet die letzte Beendigungszeit der den Abfrageplan.|  
|**avg_compile_duration**|**float**|Planen Sie die Kompilierung Statistiken. <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**last_compile_duration**|**bigint**|Planen Sie die Kompilierung Statistiken. <br/>**Hinweis**: Azure SQL Data Warehouse gibt immer 0 (null) zurück.|  
|**plan_forcing_type**|**int**|Planen Sie das Erzwingen des Typs.<br /><br />0: Keine<br /><br />1: MANUAL<br /><br />2: AUTO|  
|**plan_forcing_type_desc**|**nvarchar(60)**|Beschreibung des Plan_forcing_type.<br /><br />NONE: Keine Erzwingung eines Plans<br /><br />MANUELL: Vom Benutzer erzwungenen Plan<br /><br />AUTO: Von der automatischen Optimierung erzwungener Plan|  

## <a name="plan-forcing-limitations"></a>Einschränkungen für die planerzwingung
Der Abfragedatenspeicher verfügt über eine Mechanismus, der den Abfrageoptimierer dazu zwingen kann, einen bestimmten Ausführungsplan zu verwenden. Es gibt allerdings Einschränkungen, die dazu führen können, dass das Erzwingen eines Plans verhindert wird. 

Erstens, wenn der Plan die folgenden Konstruktionen enthält:
* INSERT BULK-Anweisung
* einen Verweis auf eine externe Tabelle
* eine verteilte Abfrage oder Volltextvorgänge
* globale Abfragen 
* Dynamischen oder Keyset-Cursor 
* eine ungültige Sternverknüpfungsspezifikation 

> [!NOTE]
> Azure SQL-Datenbank und SQL Server-2019 (Vorschau) unterstützt das Erzwingen eines Plans für statische und schnellen Vorlauf Cursor.

Zweitens, wenn Objekte, die der Plan verwendet, nicht mehr zur Verfügung stehen:
* eine Datenbank (wenn die Datenbank, aus der der Plan kommt, nicht mehr existiert)
* ein Index (nicht mehr vorhanden oder deaktiviert)

Und drittens, bei Problemen mit dem Plan selbst:
* Er darf nicht abgefragt werden.
* Der Abfrageoptimierer hat die Zahl an zulässigen Vorgängen überschritten.
* Die XML des Plans ist ungültig formuliert.

## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW DATABASE STATE** Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Query Store gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
