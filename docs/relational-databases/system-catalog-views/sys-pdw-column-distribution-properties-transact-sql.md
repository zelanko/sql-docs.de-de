---
title: Sys.pdw_column_distribution_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 46b74f99-2e22-4dbd-872a-533fce0e239c
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b351139cb96ae58c114b57833d55ab97cce25a9b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102224"
---
# <a name="syspdwcolumndistributionproperties-transact-sql"></a>sys.pdw_column_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Verteilungsinformationen zur für Spalten.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Die ID des Objekts, zu der die Spalte gehört.||  
|**column_id**|**int**|ID der Spalte.||  
|**distribution_ordinal**|**tinyint**|Ordinalzahl (1-basiert) innerhalb einer Gruppe der Verteilung.|0 = nicht für eine verteilungsspalte. 1 = [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ist diese Spalte verwenden, um die übergeordnete Tabelle zu verteilen.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
