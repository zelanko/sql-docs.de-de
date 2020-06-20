---
title: sys. workload_management_workload_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: b103ff109c946262367467673da0bf9c8ef8f5eb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011434"
---
# <a name="sysworkload_management_workload_groups-transact-sql"></a>sys. workload_management_workload_groups (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Gibt Details zu Arbeits Auslastungs Gruppen zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|
|group_id|**int**|Eindeutige ID der Arbeitsauslastungsgruppe Lässt keine NULL-Werte zu.||
|Name|**sysname**|Name der Arbeitsauslastungsgruppe. Muss für die-Instanz eindeutig sein.  Lässt keine NULL-Werte zu.||
|importance|**nvarchar(128)**|Die relative Wichtigkeit einer Anforderung in dieser Arbeits Auslastungs Gruppe und zwischen Arbeits Auslastungs Gruppen für freigegebene Ressourcen. Lässt keine NULL-Werte zu.|niedrig, below_normal, normal (Standard), above_normal, hoch||
|min_percentage_resource|**tinyint**|Garantierte Menge an Ressourcen für Anforderungen in der Arbeits Auslastungs Gruppe. Ressourcen werden nicht für andere Arbeits Auslastungs Gruppen freigegeben. Lässt keine NULL-Werte zu.||
|cap_percentage_resource|**tinyint**|Feste Obergrenze für die Ressourcen Belegung in Prozent für Anforderungen in der Arbeits Auslastungs Gruppe. Begrenzt die maximale Anzahl von Ressourcen, die der angegebenen Ebene zugeordnet sind. Der zulässige Bereich für den Wert ist 1 bis 100.||
|request_min_resource_grant_percent|**Dezimalzahl (5, 2)**|Gibt die minimale Menge an Ressourcen an, die einer Anforderung zugeordnet sind. Der zulässige Bereich für den Wert liegt zwischen 0,75 und 100.||
|request_max_resource_grant_percent |**Dezimalzahl (5, 2)**|Gibt die maximale Menge von Ressourcen an, die einer Anforderung zugeordnet sind.||
|query_execution_timeout_sec|**int**|Der Ausführungs Zeitraum (in Sekunden), der vor dem Abbrechen der Abfrage zulässig ist.  Abfragen können nicht abgebrochen werden, sobald Sie die Rückgabe Ausführungsphase erreicht haben.  query_execution_timeout_sec enthält keine Zeit in Warteschlange eingereiht.|
|query_wait_timeout_sec|**int**|INTERNAL||
|create_time|**datetime**|Uhrzeit der Erstellung der Arbeits Auslastungs Gruppe. Lässt keine NULL-Werte zu.||
modify_time|**datetime**|Uhrzeit der letzten Änderung der Arbeits Auslastungs Gruppe. Lässt keine NULL-Werte zu.||
|&nbsp;||||
  
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="next-steps"></a>Nächste Schritte

 Eine Liste aller Katalog Sichten für SQL Data Warehouse und parallele Data Warehouse finden Sie unter [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Informationen zum Erstellen einer Arbeits Auslastungs Gruppe finden Sie unter [Create](../../t-sql/statements/create-workload-group-transact-sql.md)beitragen Weitere Informationen zur Klassifizierung der Arbeitsauslastung finden [Workload Isolation](/azure/sql-data-warehouse/sql-data-warehouse-workload-isolation) Sie unter workloadisolation.
