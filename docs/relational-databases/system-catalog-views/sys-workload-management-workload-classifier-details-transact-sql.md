---
title: sys. workload_management_workload_classifier_details (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 58b3f3315309a734a22e2732af5207b64e2f0a9d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73632928"
---
# <a name="sysworkload_management_workload_classifier_details-transact-sql"></a>sys. workload_management_workload_classifier_details (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Gibt Details zu jedem Klassifizierer zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|ID des Klassifizierers.  Lässt keine NULL-Werte zu.|
|classifier_type|**sysname**|Joinfähig mit [sys. workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md).|`membername`</br>`wlm_label`</br>`wlm_context`</br>`start_time`</br>`end_time`|
|classifier_value|**sysname**|Der Wert des Klassifizierers. Lässt keine NULL-Werte zu.||

## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="next-steps"></a>Nächste Schritte
  
Eine Liste aller Katalog Sichten für SQL Data Warehouse und parallele Data Warehouse finden Sie unter [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Informationen zum Erstellen eines workloadklassifizierers finden Sie unter CREATE worklofier [Classifier](../../t-sql/statements/create-workload-classifier-transact-sql.md) Weitere Informationen zur Klassifizierung der Arbeitsauslastung finden Sie unter SQL Data Warehouse Arbeits Auslastungs [Klassifizierung](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) und [Arbeitsauslastung](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
