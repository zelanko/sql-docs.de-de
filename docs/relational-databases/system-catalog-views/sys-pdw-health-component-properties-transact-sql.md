---
title: sys.pdw_health_component_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 60e82089b66ff4a8a4263dd56b9ec2871a92869a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>sys.pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Speichert die Eigenschaften, die ein Gerät zu beschreiben. Einige Eigenschaften zeigen Gerätestatus, und einige Eigenschaften beschreiben das Gerät selbst.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Eindeutiger Bezeichner der Eigenschaft einer Komponente.<br /><br /> Property_id und Component_id bilden den Schlüssel für diese Ansicht ein.|NOT NULL|  
|component_id|**int**|Die ID der Komponente. Finden Sie unter [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> Property_id und Component_id bilden den Schlüssel für diese Ansicht ein.|NOT NULL|  
|property_name|**nvarchar(255)**|Der Name der Eigenschaft.|NOT NULL|  
|physical_name|**nvarchar(32)**|Eigenschaftenname, wie vom Hersteller definiert.|NOT NULL|  
|is_key|**bit**|Bestimmt, ob der Geräteinstanz eindeutig oder nicht eindeutig ist.|NOT NULL<br /><br /> 0 – Geräteinstanz ist eindeutig.<br /><br /> 1 - Geräteinstanz ist nicht eindeutig.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
