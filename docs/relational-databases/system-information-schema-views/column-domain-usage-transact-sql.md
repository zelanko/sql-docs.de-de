---
title: COLUMN_DOMAIN_USAGE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COLUMN_DOMAIN_USAGE_TSQL
- COLUMN_DOMAIN_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.COLUMN_DOMAIN_USAGE view
- COLUMN_DOMAIN_USAGE view
ms.assetid: deb20037-6a51-47ae-9f49-7601698fafaf
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f0edc7373b10ae9819858f65a703a86792cf14b2
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43078063"
---
# <a name="columndomainusage-transact-sql"></a>COLUMN_DOMAIN_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Spalte in der aktuellen Datenbank zurück, die einen Aliasdatentyp besitzt. Diese Informationsschemasicht gibt Informationen zu den Objekten zurück, für die der aktuelle Benutzer Berechtigungen besitzt.  
  
 Geben Sie zum Abrufen von Informationen aus diesen Sichten den vollqualifizierten Namen der **INFORMATION_SCHEMA. *** View_name*.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**DOMAIN_CATALOG**|**Nvarchar (** 128 **)**|Datenbank, in der der Aliasdatentyp vorhanden ist.|  
|**DOMAIN_SCHEMA**|**Nvarchar (** 128 **)**|Name des Schemas, das den Aliasdatentyp enthält.<br /><br /> **\*\* Wichtige \* \***  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Datentyps zu bestimmen. Die einzige zuverlässige Möglichkeit zum Finden des Schemas eines Typs besteht darin, die TYPEPROPERTY-Funktion zu verwenden.|  
|**DOMÄNENNAME**|**sysname**|Aliasdatentyp.|  
|**TABLE_CATALOG**|**Nvarchar (** 128 **)**|Tabellenqualifizierer|  
|**TABLE_SCHEMA**|**Nvarchar (** 128 **)**|Tabellenbesitzer.<br /><br /> **\*\* Wichtige \* \***  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**TABLE_NAME**|**sysname**|Tabelle, in der der Aliasdatentyp verwendet wird.|  
|**COLUMN_NAME**|**sysname**|Spalte, die den Aliasdatentyp verwendet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informationsschemasichten &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
