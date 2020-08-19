---
description: sys. pdw_health_component_status_mappings (Transact-SQL)
title: sys. pdw_health_component_status_mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2965fb53df87c09c1ccd99c42bed541272b91da7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490249"
---
# <a name="syspdw_health_component_status_mappings-transact-sql"></a>sys. pdw_health_component_status_mappings (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Definiert die Zuordnung zwischen den [!INCLUDE[ssDW](../../includes/ssdw-md.md)] Komponenten Status und den Hersteller definierten Komponentennamen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|Eindeutiger Bezeichner der Eigenschaft.<br /><br /> property_id, component_id und physical_name bilden den Schlüssel für diese Ansicht.|NOT NULL|  
|component_id|**int**|Die ID der Komponente. Weitere Informationen finden Sie unter [sys. pdw_health_components &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> property_id, component_id und physical_name bilden den Schlüssel für diese Ansicht.|NOT NULL|  
|physical_name|**nvarchar(32)**|Der Eigenschaftsname, wie er vom Hersteller definiert wurde.<br /><br /> property_id, component_id und physical_name bilden den Schlüssel für diese Ansicht.|NOT NULL|  
|logical_name|**nvarchar(255)**|Eigenschaftsname, wie durch definiert [!INCLUDE[ssDW](../../includes/ssdw-md.md)] .|NOT NULL<br /><br /> 0-die Geräte Instanz ist eindeutig.<br /><br /> 1: die Geräte Instanz ist nicht eindeutig.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
