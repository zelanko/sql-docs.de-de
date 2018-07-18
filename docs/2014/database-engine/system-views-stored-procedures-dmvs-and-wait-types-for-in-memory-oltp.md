---
title: Systemsichten, gespeicherte Prozeduren, DMVs und Wartetypen für In-Memory OLTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: efaa59e3-dbfa-407f-b1aa-cb0c6602ea17
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0a11867eafdcd747da207c2ff6783391ed3485f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245220"
---
# <a name="system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp"></a>Systemsichten, gespeicherte Prozeduren, DMVs und Wartetypen für In-Memory OLTP
  Dieses Thema enthält kurze Beschreibungen und Links zu vielen Datenbankobjekten, die In-Memory OLTP unterstützen.  
  
### <a name="system-views"></a>Systemsichten  
  
|Systemsicht|Description|In-Memory OLTP-Feature|  
|-----------------|-----------------|-----------------------------|  
|[sys.data_spaces &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-data-spaces-transact-sql)|Überprüfen, ob eine Dateigruppe speicheroptimierte Daten enthält.|Die folgenden Spalten werden zusätzliche Werte angezeigt: **Typ** und **Type_desc**.|  
|[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)|Überprüfen, ob ein Index für eine speicheroptimierte Tabelle vorliegt.|Die folgenden Spalten werden zusätzliche Werte angezeigt: **Typ** und **Type_desc**.|  
|[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql)|Überprüfen, ob ein Parameter keine NULL-Werte zulässt, (dies dient der effizienteren Ausführung von systemintern kompilierten gespeicherten Prozeduren).|**Is_nullable** Spalte.|  
|[Sys. all_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql)|Überprüfen, ob eine gespeicherte Prozedur systemintern kompiliert wird.|**Uses_native_compilation** Spalte.|  
|[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)|Überprüfen, ob eine gespeicherte Prozedur systemintern kompiliert wird.|**Uses_native_compilation** Spalte.|  
|[table_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-table-types-transact-sql)|Überprüfen, ob eine Tabelle speicheroptimiert ist.|**Is_memory_optimized** Spalte.|  
|[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)|Überprüfen, ob eine Tabelle speicheroptimiert ist, und Überprüfen der Dauerhaftigkeitseinstellung einer Tabelle.|**Dauerhaftigkeit**, **Durability_desc**, und **Is_memory_optimized** Spalten.|  
|[sys.hash_indexes (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-hash-indexes-transact-sql)|Anzeigen der Hashindizes einer speicheroptimierten Tabelle.|Für In-Memory OLTP spezifisch.|  
  
### <a name="metadata-functions"></a>Metadatenfunktionen  
  
|Metadatenfunktion|Description|In-Memory OLTP-Feature|  
|-----------------------|-----------------|-----------------------------|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)|Überprüfen, ob eine Datenbankobjekte speicheroptimiert sind.|**ExecIsWithNativeCompilation** und **TableIsMemoryOptimized** Eigenschaften.<br /><br /> Die **IsSchemaBound** -Eigenschaft unterstützt den prozedurobjekttyp (gibt 0 für Prozeduren anstelle von NULL).|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)|Überprüfen, ob ein Server In-Memory OLTP unterstützt.|**IsXTPSupported** Eigenschaft.|  
  
### <a name="system-stored-procedures"></a>Gespeicherte Systemprozeduren  
  
|Gespeicherte Prozedur|Description|  
|----------------------|-----------------|  
|[Sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)|Binden einer In-Memory OLTP-Datenbank an einen Ressourcenpool.|  
|[Sys.sp_xtp_checkpoint_force_garbage_collection &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-checkpoint-force-garbage-collection-transact-sql)|Initiieren der Garbage Collection für eine In-Memory OLTP-Datenbank.|  
|[Sys. sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql)|Aktivieren der Sammlung von statistischen Daten für systemintern kompilierte gespeicherte Prozeduren.|  
|[Sys. sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql)|Aktivieren der Sammlung von statistischen Daten pro Abfrage für systemintern kompilierte gespeicherte Prozeduren.|  
|[sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)|Zusammenführen von Daten- und Änderungsdateien.|  
|[Sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)|Entfernen der Bindung zwischen einer Datenbank und einem Ressourcenpool.|  
  
## <a name="dynamic-management-views-dmvs"></a>Dynamische Verwaltungssichten (DMVs)  
 Es gibt mehrere DMVs für speicheroptimierte Tabellen.  
  
 Weitere Informationen finden Sie unter [dynamische Verwaltungssichten für Speicheroptimierte Tabellen &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql).  
  
## <a name="wait-types"></a>Wartetypen  
 Es gibt mehrere Wartetypen, die In-Memory OLTP unterstützen.  
  
 Weitere Informationen finden Sie unter Wartetypen mit dem Präfix **WAIT_XTP**, und **XTPPROC** in die [Sys. dm_os_wait_stats &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql) Thema.  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Transact-SQL-Unterstützung für In-Memory-OLTP](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
