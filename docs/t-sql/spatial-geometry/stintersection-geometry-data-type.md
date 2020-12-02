---
description: STIntersection (geometry-Datentyp)
title: STIntersection (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIntersection_TSQL
- STIntersection (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection (geometry Data Type)
ms.assetid: 354843f5-cc14-478c-974a-04f363f9530f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6365d94822d8d291951de3e59c7c71fbed487163
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88479252"
---
# <a name="stintersection-geometry-data-type"></a>STIntersection (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt ein Objekt zurück, das die Punkte darstellt, an denen eine **geometry** -Instanz eine andere **geometry** -Instanz überschneidet.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STIntersection ( other_geometry )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *other_geometry*  
 Eine andere **geometry** -Instanz für den Vergleich mit der Instanz, in der `STIntersection()` aufgerufen wird, um zu bestimmen, wo sich die beiden Instanzen überschneiden.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="remarks"></a>Hinweise  
 `STIntersection()` gibt immer NULL zurück, wenn die SRIDs (Spatial Reference IDs) der **geometry**-Instanzen nicht übereinstimmen. Im Ergebnis können nur dann Kreisbogensegmente enthalten sein, wenn die Eingabeinstanzen auch Kreisbogensegmente enthalten.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-stintersection-on-polygon-instances"></a>A. Verwenden von STIntersection() auf Polygoninstanzen  
 Im folgenden Beispiel wird `STIntersection()` zum Berechnen der Schnittmenge zweier Polygone verwendet.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-using-stintersection-with-curvepolygon-instance"></a>B. Verwenden von STIntersection() mit CurvePolygon-Instanzen  
 Im folgenden Beispiel wird eine Instanz zurückgegeben, die ein Kreisbogensegment enthält.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STIntersection(@g).ToString();
 ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

