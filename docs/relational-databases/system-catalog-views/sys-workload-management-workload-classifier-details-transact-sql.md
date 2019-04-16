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
ms.openlocfilehash: 9afd00a887244c02849d40eed635500b06533709
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582723"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql-preview"></a>sys.workload_management_workload_classifier_details (Transact-SQL) (Preview)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

> [!Note]
> Workload-Klassifizierung ist für die Vorschau für SQL Data Warehouse Gen2 verfügbar. Workload-Management-Klassifizierung und Wichtigkeit-Vorschau ist für Builds mit Veröffentlichungsdatum am 9. April 2019 oder höher.  Benutzer sollten vor diesem Datum liegen mithilfe von Builds für das Workload Management testen.  Um festzustellen, ob der Build workloadverwaltung fähig ist, führen Sie select @@version beim Verbinden mit Ihrer SQL Data Warehouse-Instanz.

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
