---
title: Sys. check_constraints (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d79720c8e4e966c7f0129371dd6a22be4217f356
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788528"
---
# <a name="syscheckconstraints-transact-sql"></a>sys.check_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Objekt, das eine CHECK-Einschränkung mit **sys.objects.type** = 'C'.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**\<Spalten, der von sys.objects geerbten >**||Eine Liste der Spalten, die in dieser Ansicht erbt, finden Sie unter [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_disabled**|**bit**|Die CHECK-Einschränkung ist deaktiviert.|  
|**is_not_for_replication**|**bit**|Die CHECK-Einschränkung wurde mit der Option NOT FOR REPLICATION erstellt.|  
|**Sys. check_constraints**|**bit**|Die CHECK-Einschränkung wurde nicht vom System für alle Zeilen überprüft.|  
|**parent_column_id**|**int**|0 gibt eine CHECK-Einschränkung auf Tabellenebene an.<br /><br /> Ein Wert ungleich 0 gibt an, dass es sich um eine CHECK-Einschränkung auf Spaltenebene handelt, die für die Spalte mit dem angegebenen ID-Wert definiert ist.|  
|**definition**|**nvarchar(max)**|Ein SQL-Ausdruck, der die CHECK-Einschränkung definiert.|  
|**uses_database_collation**|**bit**|1 = Die Einschränkungsdefinition hängt hinsichtlich einer richtigen Auswertung von der Standardsortierung der Datenbank ab, andernfalls 0. Durch diese Abhängigkeit wird verhindert, dass die Standardsortierung der Datenbank geändert wird.|  
|**is_system_named**|**bit**|1 = Der Name wurde vom System generiert.<br /><br /> 0 = Der Name wurde vom Benutzer angegeben.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
