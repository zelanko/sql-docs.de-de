---
title: STCentroid (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCentroid_TSQL
- STCentroid (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STCentroid (geometry Data Type)
ms.assetid: 4dc5a004-7a53-4cce-81dd-9f5e1dd0db78
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5663bc7a7236a49b6b97c41ed5c96e53f337c186
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67930174"
---
# <a name="stcentroid-geometry-data-type"></a>STCentroid (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Gibt das geometrische Zentrum einer **geometry**-Instanz zurück, die aus einem oder mehreren Polygonen besteht.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STCentroid ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC)-Typ: **Point**  
  
## <a name="remarks"></a>Bemerkungen  
 `STCentroid()` gibt NULL zurück, wenn es sich bei der **geometry**-Instanz nicht um einen **Polygon-, CurvePolygon**- oder **MultiPolygon**-Typ handelt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-computing-the-centroid-of-a-polygon-instance"></a>A. Berechnen des Schwerpunkts einer Polygon-Instanz  
 Im folgenden Beispiel wird mithilfe von `STCentroid()` der Schwerpunkt einer `polygon``geometry`-Instanz berechnet:  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STCentroid().ToString();  
```  
  
### <a name="b-computing-the-centroid-of-a-curvepolygon-instance"></a>B. Berechnen des Schwerpunkts einer CurvePolygon-Instanz  
 Im folgenden Beispiel wird der Schwerpunkt für eine `CurvePolygon`-Instanz berechnet:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))';  
 SELECT @g.STCentroid().ToString() AS Centroid
 ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

