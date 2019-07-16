---
title: Sys. spatial_index_tessellations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_index_tessellations
- sys.spatial_index_tessellations_TSQL
- spatial_index_tessellations_TSQL
- sys.spatial_index_tessellations
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_index_tessellations catalog view
ms.assetid: 8b17a9a4-b57f-4220-8138-fc73581b1670
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4f2f4b8ea0184d063a6423f27fdf2cf9c450a05
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078651"
---
# <a name="sysspatialindextessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 Stellt die Informationen zum Mosaikschema und zu den Parametern jedes räumlichen Indexes dar.  
  
> [!NOTE]  
>  Informationen zu Mosaiken finden Sie unter [Spatial Indexes Overview](../../relational-databases/spatial/spatial-indexes-overview.md).  
  

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Die ID des Objekts, für das der Index definiert wird. Jeder (Object_id, Index_id) Paar besitzt einen entsprechenden Eintrag im [Sys. spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md).|  
|index_id|**int**|Die ID des räumlichen Indexes, in dem die indizierte Spalte definiert wird.|  
|tessellation_scheme|**sysname**|Der Name des Mosaikschemas, z. B.: GEOMETRY_GRID, GEOGRAPHY_GRID|  
|bounding_box_xmin|**float(53)**|X-Koordinate der unteren linken Ecke des umgebenden Felds, eines der: NULL = nicht zutreffend für ein bestimmtes Mosaikschema (z. B. GEOGRAPHY_GRID) *n* = Wenn Tessellation_scheme GEOMETRY_GRID lautet, die X-Koordinatenwert.                     **Hinweis**: Durch die Parameter des Begrenzungsrahmens definierten Koordinaten werden für jedes Objekt entsprechend interpretiert die [(SRID, Spatial Reference Identifier)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).|  
|bounding_box_ymin|**float(53)**|Y-Koordinate der unteren linken Ecke des umgebenden Felds, eines der: NULL = nicht zutreffend für ein bestimmtes Mosaikschema (z. B. GEOGRAPHY_GRID) *n* = Wenn Tessellation_scheme GEOMETRY_GRID lautet, der minimale y-Koordinatenwert|  
|bounding_box_xmax|**float(53)**|X-Koordinate der oberen rechten Ecke des umgebenden Felds, eines der: NULL = nicht zutreffend für ein bestimmtes Mosaikschema (z. B. GEOGRAPHY_GRID) *n* = Wenn Tessellation_scheme GEOMETRY_GRID lautet, der maximale X-Koordinatenwert|  
|bounding_box_ymax|**float(53)**|Y-Koordinate der oberen rechten Ecke des umgebenden Felds, eines der: NULL = nicht zutreffend für ein bestimmtes Mosaikschema (z. B. GEOGRAPHY_GRID) *n* = Wenn Tessellation_scheme GEOMETRY_GRID lautet, der maximale y-Koordinatenwert|  
|level_1_grid|**smallint**|Die Dichte des Rasters der obersten Ebene. Wenn Tessellation_scheme GEOMETRY_GRID oder GEOGRAPHY_GRID ist:          16 = 4 x 4-Raster (niedrig) 64 = 8 x 8-Raster (MEDIUM) 256 = 16 x 16-Raster (HIGH) NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|level_1_grid_desc|**nvarchar(60)**|Die Dichte des Rasters des Rasters der obersten Ebene, einer der: Niedrig Mittel hohe NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|level_2_grid|**smallint**|Die Dichte des Rasters der zweiten Ebene. Wenn Tessellation_scheme GEOMETRY_GRID oder GEOGRAPHY_GRID ist: 16 = 4 x 4-Raster (niedrig) 64 = 8 x 8-Raster (MEDIUM) 256 = 16 x 16-Raster (HIGH) NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|level_2_grid_desc|**nvarchar(60)**|Die Dichte des Rasters für das Raster der 2. Ebene, einer der: Niedrig Mittel hohe NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|level_3_grid|**smallint**|Die Dichte des Rasters der dritten Ebene.   Wenn Tessellation_scheme GEOMETRY_GRID oder GEOGRAPHY_GRID ist: 16 = 4 x 4-Raster (niedrig) 64 = 8 x 8-Raster (MEDIUM) 256 = 16 x 16-Raster (HIGH) NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|level_3_grid_desc|**nvarchar(60)**|Die Dichte des Rasters für das Raster der Ebene 3., eines: LOW Mittel hohe NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|level_4_grid|**smallint**|Die Dichte des Rasters der vierten Ebene. Wenn Tessellation_scheme GEOMETRY_GRID oder GEOGRAPHY_GRID ist: 16 = 4 x 4-Raster (niedrig) 64 = 8 x 8-Raster (MEDIUM) 256 = 16 x 16-Raster (HIGH) NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|level_4_grid_desc|**nvarchar(60)**|Die Dichte des Rasters für das Raster der Ebene ab der 4., eines: < Niedrig Mittel hohe NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes.  NULL wird zurückgegeben, wenn das neue Mosaikschema von SQL Server 11 verwendet wird.|  
|cells_per_object|**int**|Die Anzahl von Zellen pro räumlichem Objekt, z. B.: Wenn Tessellation_scheme GEOMETRY_GRID oder GEOGRAPHY_GRID ist, *n* = Anzahl der Zellen pro Objekt NULL = nicht zutreffend für einen bestimmten Typ oder ein bestimmtes Mosaikschema Schema des räumlichen Indexes|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
