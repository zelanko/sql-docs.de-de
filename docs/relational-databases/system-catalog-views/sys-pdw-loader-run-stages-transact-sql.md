---
title: sys. pdw_loader_run_stages (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127452"
---
# <a name="syspdw_loader_run_stages-transact-sql"></a>sys. pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu laufenden und abgeschlossenen Ladevorgängen [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]in. Die Informationen persistieren über Systemneustarts.  
  
|||||  
|-|-|-|-|  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|run_id|**int**|Eindeutiger Bezeichner einer loadertestlauf.||  
|Stufe|**nvarchar(30)**|Die aktuelle Phase für den Testlauf.|' CREATE_STAGING ', ' DMS_LOAD ', ' LOAD_INSERT ', ' LOAD_CLEANUP '|  
|request_id|**nvarchar(32)**|ID der Anforderung, die diese Phase ausgeführt hat.||  
|status|**nvarchar (16)**|Status dieser Phase.||  
|start_time|**datetime**|Der Zeitpunkt, zu dem die Phase gestartet wurde.||  
|end_time|**datetime**|Der Zeitpunkt, zu dem die Phase beendet wurde (sofern vorhanden).|NULL, wenn nicht gestartet oder in Bearbeitung.|  
|total_elapsed_time|**int**|Gesamte Zeit, die diese Phase ausgeführt hat (oder bisher aufgewendet).|Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl (24,8 Tage in Millisekunden) überschreitet, führt dies zu einem Materialisierungs Fehler aufgrund eines Überlaufs.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
