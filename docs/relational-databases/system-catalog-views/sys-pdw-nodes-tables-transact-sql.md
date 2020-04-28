---
title: sys. pdw_nodes_tables (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68001110"
---
# <a name="syspdw_nodes_tables-transact-sql"></a>sys. pdw_nodes_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jedes Tabellenobjekt, dem ein Prinzipal entweder gehört oder dem der Prinzipal eine Berechtigung erteilt hat.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|\<geerbte Spalten>||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects](../system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).||  
|lob_data_space_id|**int**||Immer 0.|  
|filestream_data_space_id|**int**|Datenspeicher-ID für eine FILESTREAM-Datei Gruppe oder[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**int**|Die von dieser Tabelle verwendete maximale Spalten-ID.||  
|lock_on_bulk_load|**bit**|Die Tabelle wird bei Massenladevorgängen gesperrt.|TBD|  
|uses_ansi_nulls|**bit**|Beim Erstellen der Tabelle war die Datenbankoption SET ANSI_NULLS auf ON festgelegt.|1|  
|is_replicated|**bit**|1 = die Tabelle wird mithilfe der Replikation veröffentlicht.|1,0 die Replikation wird nicht unterstützt.|  
|has_replication_filter|**bit**|1 = Die Tabelle hat einen Replikationsfilter.|0|  
|is_merge_published|**bit**|1 = Die Tabelle wird mithilfe der Mergereplikation veröffentlicht.|1,0 nicht unterstützt.|  
|is_sync_tran_subscribed|**bit**|1 = Die Tabelle wird mithilfe eines Abonnements mit sofortigem Update abonniert.|1,0 nicht unterstützt.|  
|has_unchecked_assembly_data|**bit**|1 = Die Tabelle enthält persistente Daten, die von einer Assembly abhängen, deren Definition bei der letzten ALTER ASSEMBLY-Anweisung geändert wurde. Der Wert wird nach der nächsten erfolgreichen Ausführung von DBCC CHECKDB oder DBCC CHECKTABLE auf 0 zurückgesetzt.|1,0 keine CLR-Unterstützung.|  
|text_in_row_limit|**int**|0 = die Option Text in row ist nicht festgelegt.|Immer 0.|  
|large_value_types_out_of_row|**bit**|1 = Umfangreiche Werttypen werden außerhalb der Zeile gespeichert.|Immer 0.|  
|is_tracked_by_cdc|**bit**|1 = Tabelle ist für Change Data Capture aktiviert|Immer 0; keine CDC-Unterstützung.|  
|lock_escalation|**tinyint**|Der Wert der LOCK_ESCALATION-Option für die Tabelle: 2 = Auto|Immer 2.|  
|lock_escalation_desc|**nvarchar(60)**|Eine Textbeschreibung der LOCK_ESCALATION Option.|Always ꞌ Auto ꞌ.|  
|pdw_node_id|**int**|Eindeutiger Bezeichner [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] eines Knotens.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
