---
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7b8935bc203c616f88a7e5929bd19e10a41592d3
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591034"
---
# <a name="domainconstraints-transact-sql"></a>DOMAIN_CONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jeden Aliasdatentyp in der aktuellen Datenbank zurück, an die eine Regel gebunden ist und auf die der aktuelle Benutzer zugreifen kann.  
  
 Geben Sie zum Abrufen von Informationen aus diesen Sichten den vollqualifizierten Namen der **INFORMATION_SCHEMA.** _View_name_.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**Nvarchar (** 128 **)**|Datenbank, in der die Regel vorhanden ist.|  
|**CONSTRAINT_SCHEMA**|**Nvarchar (** 128 **)**|Name des Schemas, das die Einschränkung enthält.<br /><br /> <strong>\*\* Wichtige \* \*</strong>  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**CONSTRAINT_NAME**|**sysname**|Name der Regel.|  
|**DOMAIN_CATALOG**|**Nvarchar (** 128 **)**|Datenbank, in der der Aliasdatentyp vorhanden ist.|  
|**DOMAIN_SCHEMA**|**Nvarchar (** 128 **)**|Name des Schemas, das den Aliasdatentyp enthält.<br /><br /> <strong>\*\* Wichtige \* \*</strong>  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Datentyps zu bestimmen. Die einzige zuverlässige Möglichkeit zum Finden des Schemas eines Typs besteht darin, die TYPEPROPERTY-Funktion zu verwenden.|  
|**DOMÄNENNAME**|**sysname**|Aliasdatentyp.|  
|**IS_DEFERRABLE**|**Varchar (** 2 **)**|Gibt an, ob die einschränkungsüberprüfung verzögert werden. Es wird immer NO zurückgegeben.|  
|**INITIALLY_DEFERRED**|**Varchar (** 2 **)**|Gibt an, ob die Einschränkungsüberprüfung zu Beginn zurückgestellt wird. Es wird immer NO zurückgegeben.|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informationsschemasichten &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
