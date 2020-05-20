---
title: sys. dm_db_xtp_object_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_object_stats_TSQL
- sys.dm_db_xtp_object_stats
- dm_db_xtp_object_stats
- sys.dm_db_xtp_object_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_object_stats dynamic management view
ms.assetid: 07300b59-3cab-4d3e-8138-5ea8f584f88f
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bf3997a3c0f8ed4c51651e3d32311b0c43725d59
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830774"
---
# <a name="sysdm_db_xtp_object_stats-transact-sql"></a>sys.dm_db_xtp_object_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Meldet die Anzahl der Zeilen, die von den Vorgängen betroffen sind, die seit dem letzten Neustart der Datenbank für die einzelnen [!INCLUDE[hek_2](../../includes/hek-2-md.md)] -Objekte ausgeführt wurden. Die Statistiken werden aktualisiert, wenn der Vorgang ausgeführt wird, und zwar unabhängig davon, ob für die Transaktion ein Commit oder Rollback ausgeführt wurde.  
  
 Mithilfe von sys.dm_db_xtp_object_stats können Sie ermitteln, welche speicheroptimierten Tabellen am häufigsten geändert werden. Sie können selten oder nicht verwendete Tabellenindizes entfernen, da jeder Index die Leistung beeinflusst. Bei Verwendung von Hashindizes sollte die Bucketanzahl regelmäßig neu ausgewertet werden. Weitere Informationen finden Sie unter [Determining the Correct Bucket Count for Hash Indexes](https://msdn.microsoft.com/library/6d1ac280-87db-4bd8-ad43-54353647d8b5).  
  
 Mithilfe von sys.dm_db_xtp_object_stats können Sie ermitteln, welche speicheroptimierten Tabellen Write-Write-Konflikte verursachen, die möglicherweise die Anwendungsleistung beeinträchtigen. Wenn Sie beispielsweise Wiederholungslogik für Transaktionen implementiert haben, muss ein und dieselbe Anweisung u. U. mehrfach ausgeführt werden. Außerdem können Sie anhand dieser Informationen die Tabellen (und folglich die Geschäftslogik) identifizieren, die eine Behandlung von Write-Write-Fehlern erfordern.  
  
 Diese Sicht enthält eine Zeile für jede speicheroptimierte Tabelle in der Datenbank.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|Die ID des Objekts.|  
|row_insert_attempts|**bigint**|Die Anzahl der Zeilen, die seit dem letzten Neustart der Datenbank von Transaktionen, für die ein Commit oder Abbruch ausgeführt wurde, in die Tabelle eingefügt wurden.|  
|row_update_attempts|**bigint**|Die Anzahl der Zeilen, die seit dem letzten Neustart der Datenbank von Transaktionen, für die ein Commit oder Abbruch ausgeführt wurde, in der Tabelle aktualisiert wurden.|  
|row_delete_attempts|**bigint**|Die Anzahl der Zeilen, die seit dem letzten Neustart der Datenbank von Transaktionen, für die ein Commit oder Abbruch ausgeführt wurde, aus der Tabelle gelöscht wurden.|  
|write_conflicts|**bigint**|Die Anzahl der Schreibkonflikte, die seit dem letzten Neustart der Datenbank aufgetreten sind.|  
|unique_constraint_violations|**bigint**|Die Anzahl der Verletzungen von UNIQUE-Einschränkungen, die seit dem letzten Neustart der Datenbank aufgetreten sind.|  
|object_address|**varbinary(8)**|Nur zur internen Verwendung.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung für die aktuelle Datenbank.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten für speicheroptimierte Tabellen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
