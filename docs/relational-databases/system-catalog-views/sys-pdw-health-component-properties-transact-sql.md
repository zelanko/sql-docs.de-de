---
title: sys. pdw_health_component_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2b31baacea8d4754fbc81e1c1c747a2c95b1402b
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627059"
---
# <a name="syspdw_health_component_properties-transact-sql"></a>sys. pdw_health_component_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Speichert Eigenschaften, mit denen ein Gerät beschrieben wird. Einige Eigenschaften zeigen den Gerätestatus an, und einige Eigenschaften beschreiben das Gerät selbst.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Eindeutiger Bezeichner der Eigenschaft einer Komponente.<br /><br /> property_id und component_id den Schlüssel für diese Ansicht bilden.|NOT NULL|  
|component_id|**int**|Die ID der Komponente. Weitere Informationen finden Sie unter [sys. pdw_health_components &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id und component_id den Schlüssel für diese Ansicht bilden.|NOT NULL|  
|property_name|**nvarchar(255)**|Der Name der Eigenschaft.|NOT NULL|  
|physical_name|**nvarchar(32)**|Der Eigenschaftsname, wie er vom Hersteller definiert wurde.|NOT NULL|  
|is_key|**bit**|Bestimmt, ob die Geräte Instanz eindeutig oder nicht eindeutig ist.|NOT NULL<br /><br /> 0-die Geräte Instanz ist eindeutig.<br /><br /> 1: die Geräte Instanz ist nicht eindeutig.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
