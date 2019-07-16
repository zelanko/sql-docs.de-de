---
title: Sys.workload_management_workload_classifier_details (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/01/2019
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
ms.openlocfilehash: f9314b9297af7e8156ed86b2bfa2dadd18896bb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061295"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql"></a>Sys.workload_management_workload_classifier_details (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Gibt die Details für jeden Klassifizierer.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Die ID der Klassifizierung. Beigetreten werden kann, um [sys.workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md). Lässt keine NULL-Werte zu.|
|classifier_type|**sysname**|Die Entität, auf die Klassifizierung ausgeführt werden. Lässt keine NULL-Werte zu.|MEMBERNAME|
|classifier_value|**sysname**|Der Wert der Klassifizierung. Lässt keine NULL-Werte zu.||

## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="next-steps"></a>Nächste Schritte
  
 Eine Übersicht über die Katalogsichten für SQL Data Warehouse und Parallel Data Warehouse finden Sie unter [SQL Data Warehouse und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Um einen Klassifizierer für die arbeitsauslastung zu erstellen, finden Sie unter [erstellen WORKLOAD KLASSIFIZIERER](../../t-sql/statements/create-workload-classifier-transact-sql.md). Weitere Informationen zu den Workload-Klassifizierung, finden Sie unter SQL Data Warehouse [Workload Klassifizierung](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) und [Workload Wichtigkeit](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
