---
description: KEY_COLUMN_USAGE (Transact-SQL)
title: KEY_COLUMN_USAGE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- KEY_COLUMN_USAGE_TSQL
- KEY_COLUMN_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.KEY_COLUMN_USAGE view
- KEY_COLUMN_USAGE view
ms.assetid: ec1e18c2-63a1-4d2b-ba9a-c13857403782
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bfc4132397d73aeaf99053ac5c9852614775d4a0
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543763"
---
# <a name="key_column_usage-transact-sql"></a>KEY_COLUMN_USAGE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt eine Zeile für jede Spalte zurück, die in der aktuellen Datenbank als Schlüssel eingeschränkt wurde. Diese Informationsschemasicht gibt Informationen zu den Objekten zurück, für die der aktuelle Benutzer Berechtigungen besitzt.  
  
 Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen **INFORMATION_SCHEMA an.** _view_name_.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Einschränkungsqualifizierer|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Name des Schemas, das die Einschränkung enthält.<br /><br /> Wichtig verwenden Sie keine INFORMATION_SCHEMA Sichten, um das Schema eines Objekts zu bestimmen. <strong> \* \* \* \* </strong> INFORMATION_SCHEMA Sichten stellen nur eine Teilmenge der Metadaten eines Objekts dar. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**CONSTRAINT_NAME**|**nvarchar (** 128 **)**|Einschränkungsname|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Tabellenqualifizierer|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Der Name des Schemas, das die Tabelle enthält.<br /><br /> Wichtig verwenden Sie keine INFORMATION_SCHEMA Sichten, um das Schema eines Objekts zu bestimmen. <strong> \* \* \* \* </strong> INFORMATION_SCHEMA Sichten stellen nur eine Teilmenge der Metadaten eines Objekts dar. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|Tabellenname.|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|Spaltenname.|  
|**ORDINAL_POSITION**|**int**|Ordnungsposition der Spalte.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. foreign_keys &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)   
 [sys. key_constraints &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
  
