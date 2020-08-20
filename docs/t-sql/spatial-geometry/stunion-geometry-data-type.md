---
description: STUnion (geometry-Datentyp)
title: STUnion (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STUnion (geometry Data Type)
- STUnion_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STUnion (geometry Data Type)
ms.assetid: 5b168118-137d-402f-9173-fee3f365a89c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 857428b0dee48336ae41f22e79c82a02f2f7b241
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458916"
---
# <a name="stunion-geometry-data-type"></a>STUnion (geometry-Datentyp)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Gibt ein Objekt zurück, das die Vereinigung einer **geometry** -Instanz mit einer weiteren **geometry** -Instanz darstellt.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STUnion ( other_geometry )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *other_geometry*  
 Eine andere **geometry** -Instanz zur Vereinigung mit der Instanz, in der `STUnion()` aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gibt immer NULL zurück, wenn die SRIDs (Spatial Reference IDs) der **geometry** -Instanzen nicht übereinstimmen. Im Ergebnis können nur dann Kreisbogensegmente enthalten sein, wenn die Eingabeinstanzen auch Kreisbogensegmente enthalten.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-computing-the-union-of-two-polygon-instances"></a>A. Berechnen der Union von zwei Polygon-Instanzen  
 Im folgenden Beispiel wird `STUnion()` zum Berechnen der Vereinigung zweier `Polygon` -Instanzen verwendet.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STUnion(@h).ToString();  
```  
  
### <a name="b-computing-the-union-of-a-polygon-instance-with-a-curvepolygon-instance"></a>B. Berechnen der Union einer Polygon-Instanz und einer CurvePolygon-Instanz  
 Im folgenden Beispiel wird eine `GeometryCollection` -Instanz zurückgegeben, die ein Kreisbogensegment enthält.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON((5 -1, 5 -3, 7 -3, 7 -1, 5 -1))';  
 SELECT @g.STUnion(@h).ToString();
 ```  
  
 `STUnion()` gibt ein Ergebnis zurück, das ein Kreisbogensegment enthält, da die Instanz, die `STUnion()` aufgerufen hat, ein Kreisbogensegment enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

