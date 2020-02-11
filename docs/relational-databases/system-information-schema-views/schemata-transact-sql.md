---
title: Schemata (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SCHEMATA_TSQL
- SCHEMATA
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
- SCHEMATA view
ms.assetid: 69617642-0f54-4b25-b62f-5f39c8909601
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 16b2a23c696b4da405e4983689217abb15074f03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078433"
---
# <a name="schemata-transact-sql"></a>SCHEMATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jedes Schema in der aktuellen Datenbank zurück. Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen **INFORMATION_SCHEMA an.** _view_name_. Zum Abrufen von Informationen zu allen Datenbanken in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von Fragen Sie die [sys.-Datenbanken &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) -Katalog Sicht ab.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**CATALOG_NAME**|**sysname**|Name der aktuellen Datenbank|  
|**SCHEMA_NAME**|**nvarchar (** 128 **)**|Gibt den Namen des Schemas zurück.|  
|**SCHEMA_OWNER**|**nvarchar (** 128 **)**|Name des Schemabesitzers.<br /><br /> **&#42;&#42; wichtige &#42;&#42;** Verwenden Sie INFORMATION_SCHEMA Sichten nicht, um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit, das Schema eines Objekts zu finden, besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**DEFAULT_CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|Gibt immer NULL zurück.|  
|**DEFAULT_CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|Gibt immer NULL zurück.|  
|**DEFAULT_CHARACTER_SET_NAME**|**sysname**|Gibt den Namen des Standardzeichensatzes zurück.|  

**Beispiel**  
Im folgenden Beispiel werden Informationen zu den Schemas in der Master-Datenbank zurückgegeben:  
```sql  
SELECT * FROM master.INFORMATION_SCHEMA.SCHEMATA;
```  

## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys. Schemas &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys. syscharsets &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)  
  
  
