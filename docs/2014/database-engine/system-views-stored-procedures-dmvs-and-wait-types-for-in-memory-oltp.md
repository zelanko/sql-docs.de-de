---
title: System Sichten, gespeicherte Prozeduren, DMVs und warte Typen für in-Memory-OLTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f15e1e55f0646f2cd42fe5a7154a606684961af
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928431"
---
# <a name="system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp"></a>Systemsichten, gespeicherte Prozeduren, DMVs und Wartetypen für In-Memory-OLTP
  Dieses Thema enthält kurze Beschreibungen und Links zu vielen Datenbankobjekten, die In-Memory OLTP unterstützen.  
  
### <a name="system-views"></a>Systemsichten  
  
|Systemsicht|Beschreibung|In-Memory OLTP-Feature|  
|-----------------|-----------------|-----------------------------|  
|[sys.data_spaces &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-data-spaces-transact-sql)|Überprüfen, ob eine Dateigruppe speicheroptimierte Daten enthält.|In den folgenden Spalten werden zusätzliche Werte angezeigt: **Type** und **type_desc**.|  
|[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)|Überprüfen, ob ein Index für eine speicheroptimierte Tabelle vorliegt.|In den folgenden Spalten werden zusätzliche Werte angezeigt: **Type** und **type_desc**.|  
|[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql)|Überprüfen, ob ein Parameter keine NULL-Werte zulässt, (dies dient der effizienteren Ausführung von systemintern kompilierten gespeicherten Prozeduren).|**IS_NULLABLE** Spalte.|  
|[sys. all_sql_modules &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql)|Überprüfen, ob eine gespeicherte Prozedur systemintern kompiliert wird.|**uses_native_compilation** Spalte.|  
|[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)|Überprüfen, ob eine gespeicherte Prozedur systemintern kompiliert wird.|**uses_native_compilation** Spalte.|  
|[sys. table_types &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-table-types-transact-sql)|Überprüfen, ob eine Tabelle speicheroptimiert ist.|**is_memory_optimized** Spalte.|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Überprüfen Sie, ob eine Tabelle Speicher optimiert ist, und überprüfen Sie die Dauerhaftigkeits Einstellung einer Tabelle.|Dauerhaftigkeits **-,** **durability_desc**-und **is_memory_optimized** Spalten.|  
|[sys.hash_indexes (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-hash-indexes-transact-sql)|Anzeigen der Hashindizes einer speicheroptimierten Tabelle.|Für In-Memory OLTP spezifisch.|  
  
### <a name="metadata-functions"></a>Metadatenfunktionen  
  
|Metadatenfunktion|Beschreibung|In-Memory OLTP-Feature|  
|-----------------------|-----------------|-----------------------------|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)|Überprüfen, ob eine Datenbankobjekte speicheroptimiert sind.|**Execiswithnativecompilation** -und **tableismemoryoptimierte** -Eigenschaften.<br /><br /> Die **isschema** -Eigenschaft unterstützt den Prozedur Objekttyp (gibt 0 für Prozeduren anstelle von NULL zurück).|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)|Überprüfen, ob ein Server In-Memory OLTP unterstützt.|**Isxtpsupported** -Eigenschaft.|  
  
### <a name="system-stored-procedures"></a>Gespeicherte Systemprozeduren  
  
|Gespeicherte Prozedur|Beschreibung|  
|----------------------|-----------------|  
|[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)|Binden einer In-Memory OLTP-Datenbank an einen Ressourcenpool.|  
|[sys. sp_xtp_checkpoint_force_garbage_collection &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-checkpoint-force-garbage-collection-transact-sql)|Initiieren der Garbage Collection für eine In-Memory OLTP-Datenbank.|  
|[sys. sp_xtp_control_proc_exec_stats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql)|Aktivieren der Sammlung von statistischen Daten für systemintern kompilierte gespeicherte Prozeduren.|  
|[sys. sp_xtp_control_query_exec_stats &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql)|Aktivieren der Sammlung von statistischen Daten pro Abfrage für systemintern kompilierte gespeicherte Prozeduren.|  
|[sys. sp_xtp_merge_checkpoint_files &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)|Zusammenführen von Daten- und Änderungsdateien.|  
|[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)|Entfernen der Bindung zwischen einer Datenbank und einem Ressourcenpool.|  
  
## <a name="dynamic-management-views-dmvs"></a>Dynamische Verwaltungssichten (DMVs)  
 Es gibt mehrere DMVs für speicheroptimierte Tabellen.  
  
 Weitere Informationen finden Sie unter [dynamische Verwaltungs Sichten für Speicher optimierte Tabellen &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql).  
  
## <a name="wait-types"></a>Wartetypen  
 Es gibt mehrere Wartetypen, die In-Memory OLTP unterstützen.  
  
 Weitere Informationen finden Sie unter warte Typen mit dem Präfix **WAIT_XTP**und **xtpproc** im Thema [sys. dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;in-Memory-Optimierung&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Transact-SQL-Unterstützung für In-Memory OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
