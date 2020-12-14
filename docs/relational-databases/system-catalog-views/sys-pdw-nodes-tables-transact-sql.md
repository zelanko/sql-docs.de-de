---
description: sys.pdw_nodes_tables (Transact-SQL)
title: sys.pdw_nodes_tables (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: aeaa545dd0658900b6cca8f17ec153ac1b6f25bb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97404423"
---
# <a name="syspdw_nodes_tables-transact-sql"></a>sys.pdw_nodes_tables (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält eine Zeile für jedes Tabellenobjekt, dem ein Prinzipal entweder gehört oder dem der Prinzipal eine Berechtigung erteilt hat.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|\<inherited columns>||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects](../system-catalog-views/sys-objects-transact-sql.md).||  
|lob_data_space_id|**int**||Immer 0.|  
|filestream_data_space_id|**int**|Datenspeicher-ID für eine FILESTREAM-Datei Gruppe oder [!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
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
|pdw_node_id|**int**|Eindeutiger Bezeichner eines [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knotens.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
