---
title: Sys.workload_management_workload_classifier_details (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2019
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: ed7694f087a8e1b10697ed2083dbae8bf879528c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513307"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql-preview"></a>sys.workload_management_workload_classifier_details (Transact-SQL) (Preview)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Gibt die Details für jeden Klassifizierer.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Die ID der Klassifizierung. Beigetreten werden kann, um [sys.workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md). Lässt keine NULL-Werte zu.|
|classifier_type|**sysname**|Die Entität, auf die Klassifizierung ausgeführt werden. Lässt keine NULL-Werte zu.|MEMBERNAME|
|classifier_value|**sysname**|Der Wert der Klassifizierung. Lässt keine NULL-Werte zu.||

## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="next-steps"></a>Nächste Schritte
  
 Eine Übersicht über die Katalogsichten für SQL Data Warehouse und Parallel Data Warehouse finden Sie unter [SQL Data Warehouse und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Um einen Klassifizierer für die arbeitsauslastung zu erstellen, finden Sie unter [erstellen WORKLOAD KLASSIFIZIERER](../../t-sql/statements/create-workload-classifier-transact-sql.md). Weitere Informationen zu den Workload-Klassifizierung, finden Sie unter SQL Data Warehouse [Workload Klassifizierung](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification) und [Workload Wichtigkeit](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
