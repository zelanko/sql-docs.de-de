---
description: sys.pdw_loader_backup_run_details (Transact-SQL)
title: sys.pdw_loader_backup_run_details (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 3d87972ff03cadb35468e7cdb6e9d0943b055874
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472921"
---
# <a name="syspdw_loader_backup_run_details-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält weitere ausführliche Informationen über die Informationen in [sys.pdw_loader_backup_runs &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)zu laufenden und abgeschlossenen Sicherungs-und Wiederherstellungs Vorgängen in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sowie zu laufenden und abgeschlossenen Sicherungs-, Wiederherstellungs-und Ladevorgängen in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] . Die Informationen persistieren über Systemneustarts.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Eindeutiger Bezeichner für eine bestimmte Sicherung oder Wiederherstellung.<br /><br /> run_id und pdw_node_id den Schlüssel für diese Ansicht bilden.||  
|pdw_node_id|**int**|Eindeutiger Bezeichner eines Appliance-Knotens, für den dieser Datensatz Details enthält.<br /><br /> run_id und pdw_node_id den Schlüssel für diese Ansicht bilden.|Weitere Informationen finden Sie unter node_id in [sys.dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar (16)**|Der aktuelle Status des Testlaufs.|"abgebrochen", "abgeschlossen", "fehlerhaft", "in Warteschlange", "wird ausgeführt"|  
|start_time|**datetime**|Der Zeitpunkt, zu dem der Vorgang auf diesem bestimmten Knoten gestartet wurde.||  
|end_time|**datetime**|Der Zeitpunkt, zu dem der Vorgang auf diesem bestimmten Knoten beendet wurde (sofern vorhanden).||  
|total_elapsed_time|**int**|Die Gesamtzeit, für die der Vorgang auf diesem bestimmten Knoten ausgeführt wurde.|Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl (24,8 Tage in Millisekunden) überschreitet, führt dies zu einem Materialisierungs Fehler aufgrund eines Überlaufs.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
|Fortschritt|**int**|Der Fortschritt des Vorgangs als Prozentsatz.|0 bis 100|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
