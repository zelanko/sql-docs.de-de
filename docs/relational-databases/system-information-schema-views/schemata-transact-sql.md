---
description: SCHEMATA (Transact-SQL)
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 847e046c89a11ec8d26db47d33f6f605c24cef28
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97474711"
---
# <a name="schemata-transact-sql"></a>SCHEMATA (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt eine Zeile für jedes Schema in der aktuellen Datenbank zurück. Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen **INFORMATION_SCHEMA an.** _view_name_. Zum Abrufen von Informationen zu allen Datenbanken in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fragen Sie die [sys.-Datenbanken &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) -Katalog Sicht ab.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**CATALOG_NAME**|**sysname**|Name der aktuellen Datenbank|  
|**SCHEMA_NAME**|**nvarchar (** 128 **)**|Gibt den Namen des Schemas zurück.|  
|**SCHEMA_OWNER**|**nvarchar (** 128 **)**|Name des Schemabesitzers.<br /><br /> **&#42;&#42; wichtige &#42;&#42;** Verwenden Sie INFORMATION_SCHEMA Sichten nicht, um das Schema eines Objekts zu bestimmen. INFORMATION_SCHEMA Sichten stellen nur eine Teilmenge der Metadaten eines Objekts dar. Die einzig zuverlässige Möglichkeit, das Schema eines Objekts zu finden, besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**DEFAULT_CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|Gibt immer NULL zurück.|  
|**DEFAULT_CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|Gibt immer NULL zurück.|  
|**DEFAULT_CHARACTER_SET_NAME**|**sysname**|Gibt den Namen des Standardzeichensatzes zurück.|  

**Beispiel**  
Im folgenden Beispiel werden Informationen zu den Schemas in der Master-Datenbank zurückgegeben:  
```sql  
SELECT * FROM master.INFORMATION_SCHEMA.SCHEMATA;
```  

## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](../../t-sql/language-reference.md)   
 [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.schemas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.sysZeichensätzen &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)  
  
