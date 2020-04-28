---
title: sys. workload_management_workload_classifiers (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 585eb4551fb688f4f6a620729310b0245462cbff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73632966"
---
# <a name="sysworkload_management_workload_classifiers-transact-sql"></a>sys. workload_management_workload_classifiers (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Gibt Details zu workloaderklassifizierern zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Eindeutige ID des Klassifizierers. Lässt keine NULL-Werte zu.||
group_name|**sysname**|Der Name der Arbeits Auslastungs Gruppe, der der Klassifizierer zugewiesen ist. Lässt keine NULL-Werte zu. Joinfähig mit sys. workload_management_workload_groups ||
Name|**sysname**|Der Name des Klassifizierers. Muss für die-Instanz eindeutig sein. Lässt keine NULL-Werte zu.||
|importance|**sysname**|Die relative Wichtigkeit einer Anforderung in dieser Arbeits Auslastungs Gruppe und zwischen Arbeits Auslastungs Gruppen für freigegebene Ressourcen.  Die in der Klassifizierung angegebene Wichtigkeit überschreibt die Wichtigkeits Einstellung der Arbeits Auslastungs Gruppe. Lässt NULL-Werte zu.  Bei Null wird die Einstellung für die Arbeits Auslastungs Gruppen Wichtigkeit verwendet.|niedrig, below_normal, normal (Standard), above_normal, hoch |
|create_time|**datetime**|Uhrzeit, zu der der Klassifizierer erstellt wurde. Lässt keine NULL-Werte zu.||
modify_time|**datetime**|Uhrzeit, zu der die Klassifizierung zuletzt geändert wurde. Lässt keine NULL-Werte zu.||
is_enabled|**bit**|INTERNAL||
|&nbsp;||||
  
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="next-steps"></a>Nächste Schritte

 Eine Liste aller Katalog Sichten für SQL Data Warehouse und parallele Data Warehouse finden Sie unter [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Informationen zum Erstellen eines workloadklassifizierers finden Sie unter CREATE worklofier [Classifier](../../t-sql/statements/create-workload-classifier-transact-sql.md) Weitere Informationen zur Klassifizierung der Arbeitsauslastung finden [Workload Classification](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) Sie unter workloadklassifizierung.
