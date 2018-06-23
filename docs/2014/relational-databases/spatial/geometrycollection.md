---
title: GeometryCollection | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1a5c21c01ab776a17d3e160fee51167c426dfa0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150095"
---
# <a name="geometrycollection"></a>GeometryCollection
  Ein `GeometryCollection` ist eine Auflistung von NULL oder mehr `geometry` oder `geography` Instanzen. Ein `GeometryCollection` kann leer sein.  
  
## <a name="geometrycollection-instances"></a>GeometryCollection-Instanzen  
  
### <a name="accepted-instances"></a>Akzeptierte Instanzen  
 Damit eine `GeometryCollection`-Instanz akzeptiert wird, muss es sich um eine leere `GeometryCollection`-Instanz handeln, oder alle Instanzen, die die `GeometryCollection` beinhalten, müssen akzeptierte Instanzen sein. Im folgenden Beispiel werden akzeptierte Instanzen veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 Das folgende Beispiel löst eine `System.FormatException` da die `LinesString` Instanz die `GeometryCollection` Instanz wird nicht akzeptiert.  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a>Gültige Instanzen  
 Eine `GeometryCollection`-Instanz ist gültig, wenn alle Instanzen, die die `GeometryCollection`-Instanz beinhalten, gültig sind. Im folgenden werden drei gültige `GeometryCollection` -Instanzen und eine Instanz, die nicht gültig ist.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` ist nicht gültig, da die `Polygon`-Instanz in der `GeometryCollection`-Instanz nicht gültig ist.  
  
 Weitere Informationen über akzeptierte und gültige Instanzen finden Sie unter [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [Polygon](polygon.md)und [MultiPolygon](multipolygon.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `geometry``GeometryCollection` mit Z-Werten im SRID 1 instanziiert, der eine `Point` -Instanz und eine `Polygon` -Instanz enthält.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  