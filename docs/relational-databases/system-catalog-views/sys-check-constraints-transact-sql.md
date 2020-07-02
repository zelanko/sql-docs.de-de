---
title: sys. check_constraints (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.check_constraints
- sys.check_constraints_TSQL
- check_constraints_TSQL
- check_constraints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.check_constraints catalog view
ms.assetid: 940ebc5e-44ba-4dae-8b29-da94f2d1d6c4
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: af931a3ac76186b0ac583155b0d45e4dbe7ed055
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85718877"
---
# <a name="syscheck_constraints-transact-sql"></a>sys.check_constraints (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Enthält eine Zeile für jedes Objekt, bei dem es sich um eine Check-Einschränkung handelt, mit **sys. Objects. Type** = ' C '.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<Columns inherited from sys.objects>**||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_disabled**|**bit**|Die CHECK-Einschränkung ist deaktiviert.|  
|**is_not_for_replication**|**bit**|Die CHECK-Einschränkung wurde mit der Option NOT FOR REPLICATION erstellt.|  
|**is_not_trusted**|**bit**|Die CHECK-Einschränkung wurde nicht vom System für alle Zeilen überprüft.|  
|**parent_column_id**|**int**|0 gibt eine CHECK-Einschränkung auf Tabellenebene an.<br /><br /> Ein Wert ungleich 0 gibt an, dass es sich um eine CHECK-Einschränkung auf Spaltenebene handelt, die für die Spalte mit dem angegebenen ID-Wert definiert ist.|  
|**Definition**|**nvarchar(max)**|Ein SQL-Ausdruck, der die CHECK-Einschränkung definiert.|  
|**uses_database_collation**|**bit**|1 = Die Einschränkungsdefinition hängt hinsichtlich einer richtigen Auswertung von der Standardsortierung der Datenbank ab, andernfalls 0. Durch diese Abhängigkeit wird verhindert, dass die Standardsortierung der Datenbank geändert wird.|  
|**is_system_named**|**bit**|1 = Der Name wurde vom System generiert.<br /><br /> 0 = Der Name wurde vom Benutzer angegeben.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
