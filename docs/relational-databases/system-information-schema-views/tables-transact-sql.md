---
title: Tabellen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- TABLES_TSQL
- TABLES
dev_langs:
- TSQL
helpviewer_keywords:
- TABLES view
- INFORMATION_SCHEMA.TABLES view
ms.assetid: 723a9e63-8f6e-4d6e-b570-468cfaf03201
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0d1382d32941eb69cbeb8d9dcf6071657c14cbf9
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590734"
---
# <a name="tables-transact-sql"></a>TABLES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jede Tabelle in der aktuellen Datenbank zurück, für die der aktuelle Benutzer Berechtigungen besitzt.  
  
 Geben Sie zum Abrufen von Informationen aus diesen Sichten den vollqualifizierten Namen der **INFORMATION_SCHEMA.** _View_name_.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**Nvarchar (** 128 **)**|Tabellenqualifizierer|  
|**TABLE_SCHEMA**|**Nvarchar (** 128 **)**|Der Name des Schemas, das die Tabelle enthält.<br /><br /> <strong>\*\* Wichtige \* \*</strong>  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit, das Schema eines Objekts zu finden, besteht darin, die sys.objects-Katalogsicht abzufragen. INFORMATION_SCHEMA-Sichten sind möglicherweise unvollständig, da sie nicht für alle neuen Funktionen aktualisiert werden.|  
|**TABLE_NAME**|**sysname**|Tabellenname.|  
|**TABLE_TYPE**|**Varchar (** 10 **)**|Typ der Tabelle. VIEW oder BASE TABLE|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informationsschemasichten &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
  
