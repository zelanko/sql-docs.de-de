---
title: STGeometryType (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryType (geography Data Type)
- STGeometryType_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryType method
ms.assetid: 3e169ead-a98e-44af-8d33-fd59a955cae4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 957615b665641afd3ffbfbcac8d789a2426b35cc
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555405"
---
# <a name="stgeometrytype-geography-data-type"></a>STGeometryType (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt den durch eine **geography**-Instanz dargestellten OGC-Typnamen (Open Geospatial Consortium) zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STGeometryType ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(4000)**  
  
 CLR-Rückgabetyp: **SqlString**  
  
## <a name="remarks"></a>Bemerkungen  
 Die OGC-Typnamen, die von `STGeometryType()` zurückgegeben werden können, sind **Point**, **LineString**, **CircularString**, **CompoundCurve**, **Polygon**, **CurvePolygon**, **GeometryCollection**, **MultiPoint**, **MultiLineString**, **MultiPolygon** und **FullGlobe**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiels wird eine Instanz von `Polygon` erstellt, und mit `STGeometryType()` wird bestätigt, dass es sich um ein Polygon handelt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STGeometryType();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
