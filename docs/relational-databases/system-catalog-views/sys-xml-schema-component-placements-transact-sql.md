---
description: sys.xml_schema_component_placements (Transact-SQL)
title: sys.xml_schema_component_placements (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_component_placements
- xml_schema_component_placements_TSQL
- xml_schema_component_placements
- sys.xml_schema_component_placements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_component_placements catalog view
ms.assetid: 2d3c8828-e4b3-423d-bf11-990464c1341b
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: b4b971fe631671d193340fc3c68b8e4e235c178f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88400706"
---
# <a name="sysxml_schema_component_placements-transact-sql"></a>sys.xml_schema_component_placements (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile pro Platzierung für XML-Schemakomponenten zurück.  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|ID der XML-Schemakomponente, die diese Platzierung besitzt.|  
|**placement_id**|**int**|ID der Platzierung. Diese ist eindeutig innerhalb der besitzenden XML-Schemakomponente.|  
|**placed_xml_component_id**|**int**|ID der platzierten XML-Schemakomponente.|  
|**is_default_fixed**|**bit**|1 = Der Standardwert ist ein fester Wert. Dieser Wert kann in einer XML-Instanz nicht überschrieben werden.<br /><br /> 0 = Der Wert kann überschrieben werden. (Standard)|  
|**min_occurrences**|**int**|Mindestzahl der platzierten Komponenten.|  
|**max_occurrences**|**int**|Höchstzahl der platzierten Komponenten.|  
|**default_value**|**nvarchar (4000)**|Standardwert, sofern bereitgestellt. Ist NULL, wenn kein Standardwert angegeben wird.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML-Schemas &#40;XML-Typsystem&#41; Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
