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
ms.openlocfilehash: 3b023654728375aee76bfb0c4434a8413dc81e7d
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582563"
---
# <a name="sysworkloadmanagementworkloadclassifiers-transact-sql-preview"></a>Sys.workload_management_workload_classifiers (Transact-SQL) (Vorschau)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

> [!Note]
> Workload-Klassifizierung ist für die Vorschau für SQL Data Warehouse Gen2 verfügbar. Workload-Management-Klassifizierung und Wichtigkeit-Vorschau ist für Builds mit Veröffentlichungsdatum am 9. April 2019 oder höher.  Benutzer sollten vor diesem Datum liegen mithilfe von Builds für das Workload Management testen.  Um festzustellen, ob der Build workloadverwaltung fähig ist, führen Sie select @@version beim Verbinden mit Ihrer SQL Data Warehouse-Instanz.

 Gibt die Details für die arbeitsauslastung Klassifizierer.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|Eindeutige ID der Klassifizierung. Lässt keine NULL-Werte zu.||
group_name|**sysname**|Name der Arbeitsauslastungsgruppe des Klassifizierers zugewiesen ist. Lässt keine NULL-Werte zu. |Statische Ressourcenklassen</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80 </br> </br>Dynamische Ressourcenklassen</br>smallrc</br>mediumrc</br>largerc</br>xlargerc|
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
