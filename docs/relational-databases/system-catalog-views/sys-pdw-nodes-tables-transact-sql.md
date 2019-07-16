---
title: Sys.pdw_nodes_tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 473b5d14-171b-4a16-9195-acf36d3f786c
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 5fa2412e61e30852497ffa00493ea6dbe244989a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001110"
---
# <a name="syspdwnodestables-transact-sql"></a>sys.pdw_nodes_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jedes Tabellenobjekt, das ein Prinzipals entweder der Besitzer ist oder auf dem der Prinzipal eine Berechtigung erteilt wurde.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|\<geerbte Spalten >||Eine Liste der Spalten, die in dieser Ansicht erbt, finden Sie unter [sys.objects](../system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).||  
|lob_data_space_id|**int**||Immer 0.|  
|filestream_data_space_id|**int**|ID des Datenspeicherplatzes für eine FILESTREAM-Dateigruppe oder [!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**int**|Höchste Spalten-ID, die von dieser Tabelle verwendet.||  
|lock_on_bulk_load|**bit**|Die Tabelle wird bei Massenladevorgängen gesperrt.|TBD|  
|uses_ansi_nulls|**bit**|Beim Erstellen der Tabelle war die Datenbankoption SET ANSI_NULLS auf ON festgelegt.|1|  
|is_replicated|**bit**|1 = Tabelle mithilfe einer Replikation veröffentlicht wird.|0; Replikation wird nicht unterstützt.|  
|has_replication_filter|**bit**|1 = Die Tabelle hat einen Replikationsfilter.|0|  
|is_merge_published|**bit**|1 = Die Tabelle wird mithilfe der Mergereplikation veröffentlicht.|0; nicht unterstützt.|  
|is_sync_tran_subscribed|**bit**|1 = Die Tabelle wird mithilfe eines Abonnements mit sofortigem Update abonniert.|0; nicht unterstützt.|  
|has_unchecked_assembly_data|**bit**|1 = Die Tabelle enthält persistente Daten, die von einer Assembly abhängen, deren Definition bei der letzten ALTER ASSEMBLY-Anweisung geändert wurde. Der Wert wird nach der nächsten erfolgreichen Ausführung von DBCC CHECKDB oder DBCC CHECKTABLE auf 0 zurückgesetzt.|0; CLR wird nicht unterstützt.|  
|text_in_row_limit|**int**|0 = Text in Zeile Option nicht festgelegt ist.|Immer 0.|  
|large_value_types_out_of_row|**bit**|1 = Umfangreiche Werttypen werden außerhalb der Zeile gespeichert.|Immer 0.|  
|is_tracked_by_cdc|**bit**|1 = Tabelle für Change Data Capture aktiviert ist|Immer 0; keine Unterstützung für CDC.|  
|lock_escalation|**tinyint**|Der Wert der LOCK_ESCALATION-Option für die Tabelle: 2 = AUTO|Immer 2.|  
|lock_escalation_desc|**nvarchar(60)**|Eine textbeschreibung der Lock_escalation-Option.|Immer ꞌAUTOꞌ.|  
|pdw_node_id|**int**|Der eindeutige Bezeichner des eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knoten.|NOT NULL|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
