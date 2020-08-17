---
description: sys.spatial_indexes (Transact-SQL)
title: sys. spatial_indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.spatial_indexes_TSQL
- spatial_indexes
- spatial_indexes_TSQL
- sys.spatial_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_indexes catalog view
ms.assetid: 40e967d5-2e8d-45af-bf5e-5251493cf7cb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b686ab4eb7d8e8ada45a5026dbbaa4e4357db4c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88376166"
---
# <a name="sysspatial_indexes-transact-sql"></a>sys.spatial_indexes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Stellt die wichtigsten Indexinformationen der räumlichen Indizes dar.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|\<inherited columns>||Erbt Spalten von [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|spatial_index_type|**tinyint**|Typ des räumlichen Indexes:<br /><br /> 1 = Geometrischer räumlicher Index<br /><br /> 2 = Geografischer räumlicher Index|  
|spatial_index_type_desc|**nvarchar(60)**|Typbeschreibung des räumlichen Indexes:<br /><br /> GEOMETRY = geometrischer räumlicher Index<br /><br /> GEOGRAPHY = geografischer räumlicher Index|  
|tessellation_scheme|**sysname**|Name des Mosaikschemas:<br /><br /> GEOMETRY_GRID, GEOMETRY_AUTO_GRID,<br /><br /> GEOGRAPHY_GRID, GEOGRAPHY_AUTO_GRID<br /><br /> Hinweis: Informationen zu Mosaik Schemas finden Sie unter Übersicht über [räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md).|  
|\<inherited columns>||Erbt Spalten von [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).<br /><br /> Die geerbten has_filter- und filter_definition-Spalten werden nach den spezifischen Spalten für räumliche Indizes angezeigt.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_index_tessellations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-index-tessellations-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)  
  
  
