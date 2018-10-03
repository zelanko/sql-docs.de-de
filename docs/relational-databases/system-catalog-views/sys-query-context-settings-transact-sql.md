---
title: Sys.query_context_settings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/22/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_CONTEXT_SETTINGS_TSQL
- SYS.QUERY_CONTEXT_SETTINGS_TSQL
- SYS.QUERY_CONTEXT_SETTINGS
- QUERY_CONTEXT_SETTINGS
dev_langs:
- TSQL
helpviewer_keywords:
- sys.query_context_settings catalog view
ms.assetid: 3c1887df-6bd8-491e-82fc-d25ad9589faf
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de36098ec2c2792e45724cdb023897b1482ac9cf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638488"
---
# <a name="sysquerycontextsettings-transact-sql"></a>Sys.query_context_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Enthält Informationen über die Auswirkungen auf das die kontexteinstellungen mit einer Abfrage verknüpften Semantik. Es stehen eine Reihe von kontexteinstellungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die die Semantik der Abfrage (definieren das richtige Ergebnis der Abfrage) beeinflussen. Derselbe Abfragetext mit unterschiedlichen Einstellungen kompiliert möglicherweise zu unterschiedlichen Ergebnissen (abhängig von den zugrunde liegenden Daten) führen.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**context_settings_id**|**bigint**|Der Primärschlüssel. Dieser Wert wird für Abfragen in Showplan XML verfügbar gemacht.|  
|**Set_Options**|**varbinary(8)**|Die Bitmaske kritischem Zustand, der mehrere SET-Optionen. Weitere Informationen finden Sie unter [dm_exec_plan_attributes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md).|  
|**language_id**|**smallint**|Die Id der Sprache. Weitere Informationen finden Sie unter [sys.syslanguages &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).|  
|**date_format**|**smallint**|Das Datum das Format. Weitere Informationen finden Sie unter [SET DATEFORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/set-dateformat-transact-sql.md).|  
|**date_first**|**tinyint**|Der erste Datumswert. Weitere Informationen finden Sie unter [SET DATEFIRST &#40;Transact-SQL&#41;](../../t-sql/statements/set-datefirst-transact-sql.md).|  
|**status**|**varbinary(2)**|Bitmaske-Feld, das gibt Typ der Abfrage oder einen Kontext, in dem Abfrage ausgeführt wurde. <br />Spaltenwert möglich Kombination mehrerer Flags (im Hexadezimalformat ausgedrückt):<br /><br /> 0 x 0 – reguläre Abfrage (keine bestimmten Flags)<br /><br /> 0 x 1 – Abfragen, die über eine der Cursor APIs, die gespeicherten Prozeduren ausgeführt wurde<br /><br /> 0 x 2 – Abfrage für die Benachrichtigung<br /><br /> 0 x 4 – interner<br /><br /> 0 x 8 – automatisch parametrisierten Abfrage ohne universelle Parametrisierung<br /><br /> 0 x 10: Cursor-Fetch Abfrage aktualisieren<br /><br /> 0 x 20 - Abfrage, die in Anforderungen zum Aktualisieren von Cursor verwendet wird<br /><br /> 0 x 40 - erste Resultset wird zurückgegeben, wenn ein Cursor geöffnet wird (Cursor automatisch abrufen)<br /><br /> 0 x 80 – verschlüsselte Abfrage<br /><br /> 0 x 100-Abfrage im Kontext der Sicherheit auf Zeilenebene Prädikat|  
|**required_cursor_options**|**int**|Vom Benutzer angegebene Cursoroptionen, z. B. der Cursortyp.|  
|**acceptable_cursor_options**|**int**|Cursoroptionen, in die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine implizite Konvertierung vorgenommen werden kann, um die Ausführung der Anweisung zu unterstützen.|  
|**merge_action_type**|**smallint**|Der Typ des triggerausführungsplans, die als Ergebnis verwendet eine **MERGE** Anweisung.<br /><br /> 0 gibt an, eine nicht-triggerplan an, einen triggerplan, der nicht als Ergebnis ausgeführt wird ein **MERGE** -Anweisung oder einen triggerplan, der als Ergebnis ausgeführt wird ein **MERGE** -Anweisung, die nur eine an**Löschen** Aktion.<br /><br /> 1 gibt an ein **einfügen** -triggerplan an, der als das Ergebnis wird ein **MERGE** Anweisung.<br /><br /> 2 Gibt an ein **UPDATE** -triggerplan an, der als das Ergebnis wird ein **MERGE** Anweisung.<br /><br /> 3 gibt einen **löschen** -triggerplan an, die als Ergebnis ausgeführt wird ein **MERGE** -Anweisung mit einer entsprechenden **einfügen** oder **UPDATE** die Aktion.<br /><br /> <br /><br /> Für geschachtelte Trigger, die durch kaskadierende Aktionen ausgeführt werden, ist dieser Wert die Aktion der **MERGE** -Anweisung, die das Kaskadieren verursacht wurde.|  
|**default_schema_id**|**int**|Die ID des Standardschemas, die verwendet wird, um Namen aufzulösen, die nicht vollqualifiziert sind.|  
|**is_replication_specific**|**bit**|Für die Replikation verwendet.|  
|**is_contained**|**varbinary(1)**|1 gibt an, eine eigenständige Datenbank.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **VIEW DATABASE STATE** Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [Sys. query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [Sys. query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)   
 [Sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Gespeicherte Prozeduren für den Abfragespeicher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
