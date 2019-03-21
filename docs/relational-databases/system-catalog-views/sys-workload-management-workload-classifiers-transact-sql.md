---
title: Sys.workload_management_workload_classifiers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2019
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
ms.openlocfilehash: 7f655c94d0c77747a4e64c93bf7ad880419aacb4
ms.sourcegitcommit: 05bb10710489bef16bb2c53b3803e9b8eea1429a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "57988750"
---
# <a name="sysworkloadmanagementworkloadclassifiers-transact-sql-preview"></a>Sys.workload_management_workload_classifiers (Transact-SQL) (Vorschau)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Gibt die Details für die arbeitsauslastung Klassifizierer.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Eindeutige ID der Klassifizierung. Lässt keine NULL-Werte zu.||
group_name|**sysname**|Name der Arbeitsauslastungsgruppe des Klassifizierers zugewiesen ist. Lässt keine NULL-Werte zu. |Statische Ressourcenklassen</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80 </br>Dynamische Ressourcenklassen</br>"smallrc"</br>mediumrc</br>"Largerc"</br>xlargerc|
NAME|**sysname**|Der Name der Klassifizierung. Muss auf die Instanz eindeutig sein. Lässt keine NULL-Werte zu.||
|importance|**sysname**|Ist die relative Wichtigkeit einer Anforderung in dieser Arbeitsauslastungsgruppe und für Arbeitsauslastungsgruppen für freigegebene Ressourcen.  Wichtigkeit in der Klassifizierung überschreibt die Wichtigkeit der Arbeitsauslastungsgruppe festgelegt.|low, below_normal, normal, above_normal, high |
|create_time|**datetime**|Zeitpunkt, zu der Klassifizierer erstellt wurde. Lässt keine NULL-Werte zu.||
modify_time|**datetime**|Zeitpunkt, zu der letzten die Klassifizierung Änderung. Lässt keine NULL-Werte zu.||
is_enabled|**bit**|Zeigt an, ob die Klassifizierung oder nicht aktiviert ist. Ist standardmäßig aktiviert. Lässt keine NULL-Werte zu.|0 = die Klassifizierung ist nicht aktiviert. </br> 1 = die Klassifizierung ist aktiviert.|
|&nbsp;||||
  
## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.

## <a name="next-steps"></a>Nächste Schritte

 Eine Übersicht über die Katalogsichten für SQL Data Warehouse und Parallel Data Warehouse finden Sie unter [SQL Data Warehouse und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Um einen Klassifizierer für die arbeitsauslastung zu erstellen, finden Sie unter [erstellen WORKLOAD KLASSIFIZIERER](../../t-sql/statements/create-workload-classifier-transact-sql.md). Weitere Informationen zu den Workload-Klassifizierung, finden Sie unter [SQL DATA Warehouse-Workload-Klassifizierung](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)