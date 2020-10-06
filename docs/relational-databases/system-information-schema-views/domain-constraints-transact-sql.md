---
description: DOMAIN_CONSTRAINTS (Transact-SQL)
title: DOMAIN_CONSTRAINTS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DOMAIN_CONSTRAINTS
- DOMAIN_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.DOMAIN_CONSTRAINTS view
- DOMAIN_CONSTRAINTS view
ms.assetid: 436c4480-f1e3-403f-b2bd-de04539afe3c
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 20f675d11a58af2f5a1a433b8fdba41d07d4b01b
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753571"
---
# <a name="domain_constraints-transact-sql"></a>DOMAIN_CONSTRAINTS (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt eine Zeile für jeden Aliasdatentyp in der aktuellen Datenbank zurück, an die eine Regel gebunden ist und auf die der aktuelle Benutzer zugreifen kann.  
  
 Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen **INFORMATION_SCHEMA an.** _view_name_.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Datenbank, in der die Regel vorhanden ist.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Name des Schemas, das die Einschränkung enthält.<br /><br /> Wichtig verwenden Sie keine INFORMATION_SCHEMA Sichten, um das Schema eines Objekts zu bestimmen. <strong> \* \* \* \* </strong> INFORMATION_SCHEMA Sichten stellen nur eine Teilmenge der Metadaten eines Objekts dar. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**CONSTRAINT_NAME**|**sysname**|Name der Regel.|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|Datenbank, in der der Aliasdatentyp vorhanden ist.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Name des Schemas, das den Aliasdatentyp enthält.<br /><br /> Wichtig verwenden Sie keine INFORMATION_SCHEMA Sichten, um das Schema eines Datentyps zu bestimmen. <strong> \* \* \* \* </strong> Die einzige zuverlässige Möglichkeit zum Finden des Schemas eines Typs besteht darin, die TYPEPROPERTY-Funktion zu verwenden.|  
|**DOMAIN_NAME**|**sysname**|Aliasdatentyp.|  
|**IS_DEFERRABLE**|**varchar (** 2 **)**|Gibt an, ob die Einschränkungs Überprüfung verzögert werden kann. Es wird immer NO zurückgegeben.|  
|**INITIALLY_DEFERRED**|**varchar (** 2 **)**|Gibt an, ob die Einschränkungsüberprüfung zu Beginn zurückgestellt wird. Es wird immer NO zurückgegeben.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](../../t-sql/language-reference.md)   
 [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
