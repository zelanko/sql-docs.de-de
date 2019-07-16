---
title: Sys.pdw_loader_run_stages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5d10a3bcbf02e88e054c12060299e9462af3004d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127452"
---
# <a name="syspdwloaderrunstages-transact-sql"></a>sys.pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu laufenden und abgeschlossenen Ladevorgänge in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Die Informationen persistieren über Systemneustarts.  
  
|||||  
|-|-|-|-|  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|run_id|**int**|Eindeutiger Bezeichner des ein Ladeprogramm ausführen.||  
|Stufe|**nvarchar(30)**|Die aktuelle Phase für die Ausführung.|'CREATE_STAGING', 'DMS_LOAD', 'LOAD_INSERT', 'LOAD_CLEANUP'|  
|request_id|**nvarchar(32)**|Die ID der Anforderung dieser Phase ausgeführt.||  
|status|**nvarchar(16)**|Der Status dieser Phase.||  
|start_time|**datetime**|Zeitpunkt, an dem die Phase gestartet wurde.||  
|end_time|**datetime**|Zeitpunkt, zu dem die Phase beendet wurde, sofern vorhanden.|NULL, wenn nicht gestartet oder ausgeführt.|  
|total_elapsed_time|**int**|Gesamtzeit dieser Phase hat (oder hat bisher) ausgeführt.|Überschreitet Total_elapsed_time den maximalen Wert für eine ganze Zahl (rund 24,8 Tage in Millisekunden), wird es Materialisierung Fehler aufgrund einer zu einem Überlauf führen.<br /><br /> Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
