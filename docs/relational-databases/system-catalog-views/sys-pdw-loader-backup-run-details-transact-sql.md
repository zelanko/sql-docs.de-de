---
title: sys. pdw_loader_backup_run_details (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: dead5962987f7fb132f21bb4e3517f7cc9249601
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127646"
---
# <a name="syspdw_loader_backup_run_details-transact-sql"></a>sys. pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält weitere ausführliche Informationen über die Informationen in [sys. pdw_loader_backup_runs &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), zu laufenden und abgeschlossenen Sicherungs-und Wiederherstellungs [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Vorgängen in sowie zu laufenden und abgeschlossenen Sicherungs-, Wiederherstellungs [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]-und Ladevorgängen in. Die Informationen persistieren über Systemneustarts.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Eindeutiger Bezeichner für eine bestimmte Sicherung oder Wiederherstellung.<br /><br /> run_id und pdw_node_id den Schlüssel für diese Ansicht bilden.||  
|pdw_node_id|**int**|Eindeutiger Bezeichner eines Appliance-Knotens, für den dieser Datensatz Details enthält.<br /><br /> run_id und pdw_node_id den Schlüssel für diese Ansicht bilden.|Weitere Informationen finden Sie unter node_id in [sys. dm_pdw_nodes &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar (16)**|Der aktuelle Status des Testlaufs.|"abgebrochen", "abgeschlossen", "fehlerhaft", "in Warteschlange", "wird ausgeführt"|  
|start_time|**datetime**|Der Zeitpunkt, zu dem der Vorgang auf diesem bestimmten Knoten gestartet wurde.||  
|end_time|**datetime**|Der Zeitpunkt, zu dem der Vorgang auf diesem bestimmten Knoten beendet wurde (sofern vorhanden).||  
|total_elapsed_time|**int**|Die Gesamtzeit, für die der Vorgang auf diesem bestimmten Knoten ausgeführt wurde.|Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl (24,8 Tage in Millisekunden) überschreitet, führt dies zu einem Materialisierungs Fehler aufgrund eines Überlaufs.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
|Fortschritt|**int**|Der Fortschritt des Vorgangs als Prozentsatz.|0 bis 100|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
