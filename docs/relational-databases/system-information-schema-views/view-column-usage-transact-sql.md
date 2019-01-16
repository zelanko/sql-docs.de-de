---
title: VIEW_COLUMN_USAGE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- VIEW_COLUMN_USAGE
- VIEW_COLUMN_USAGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.VIEW_COLUMN_USAGE view
- VIEW_COLUMN_USAGE view
ms.assetid: fc0b3608-a7e8-4532-8215-32235d6670f1
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c666150eea9e6f99cc3c9e555b4aeb5caf45bf96
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255095"
---
# <a name="viewcolumnusage-transact-sql"></a>VIEW_COLUMN_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jede Spalte in der aktuellen Datenbank zurück, die in einer Sichtdefinition verwendet wird. Diese Informationsschemasicht gibt Informationen zu den Objekten zurück, für die der aktuelle Benutzer Berechtigungen besitzt.  
  
 Geben Sie zum Abrufen von Informationen aus diesen Sichten den vollqualifizierten Namen der **INFORMATION_SCHEMA.** _View_name_.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**VIEW_CATALOG**|**nvarchar(** 128 **)**|Sichtqualifizierer|  
|**VIEW_SCHEMA**|**nvarchar(** 128 **)**|Der Name des Schemas, das die Sicht enthält.<br /><br /> **&#42;&#42;Wichtige &#42; &#42;**  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**VIEW_NAME**|**sysname**|Ansichtsname.|  
|**TABLE_CATALOG**|**nvarchar(** 128 **)**|Tabellenqualifizierer|  
|**TABLE_SCHEMA**|**nvarchar(** 128 **)**|Der Name des Schemas, das die Tabelle enthält.<br /><br /> **&#42;&#42;Wichtige &#42; &#42;**  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**TABLE_NAME**|**sysname**|Basistabelle.|  
|**COLUMN_NAME**|**sysname**|Name der Spalte.|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informationsschemasichten &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.sql_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
