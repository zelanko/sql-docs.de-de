---
title: MultiLineString | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 053af2980857e1bde0ea4b3812b64a276ee9e171
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157260"
---
# <a name="multilinestring"></a>MultiLineString
  Ein `MultiLineString` ist eine Sammlung von NULL oder mehr `geometry` oder **GeographyLineString** Instanzen.  
  
## <a name="multilinestring-instances"></a>MultiLineString-Instanzen  
 Die nachfolgende Abbildung enthält Beispiele für `MultiLineString` Instanzen.  
  
 ![Beispiele für MultiLineString-Geometrieinstanzen](../../database-engine/media/multilinestring.gif "Examples of geometry MultiLineString instances")  
  
 Folgendes wird dargestellt:  
  
-   Abbildung 1 zeigt eine einfache `MultiLineString` Instanz, deren Begrenzung aus den vier Endpunkten ihrer beiden `LineString` Elemente.  
  
-   Abbildung 2 zeigt eine einfache `MultiLineString`-Instanz, da sich nur die Endpunkte der `LineString`-Elemente überschneiden. Die Begrenzung besteht aus den zwei nicht überlappenden Endpunkten.  
  
-   Abbildung 3 zeigt eine nicht einfache `MultiLineString`-Instanz, da der Innenbereich eines ihrer `LineString`-Elemente geschnitten wird. Die Begrenzung dieser `MultiLineString` Instanz besteht aus den vier Endpunkten.  
  
-   Abbildung 4 zeigt eine nicht einfache, nicht geschlossene `MultiLineString`-Instanz.  
  
-   Abbildung 5 zeigt eine einfache, nicht geschlossene `MultiLineString`-Instanz. Es ist nicht geschlossen, da die `LineStrings` -Elemente nicht geschlossen sind. Es ist ganz einfach weil keiner der Innenbereiche der der `LineStrings` Instanzen überschneiden.  
  
-   Abbildung 6 zeigt eine einfache, geschlossen `MultiLineString` Instanz. Sie ist geschlossen, weil alle ihre Elemente geschlossen sind. Sie ist einfach, weil keines ihrer Elemente sich im Innenbereich mit anderen überschneidet.  
  
### <a name="accepted-instances"></a>Akzeptierte Instanzen  
 Für eine `MultiLineString` -Instanz akzeptiert wird, muss Sie entweder leer sein, oder der nur `LineString` bestehen, die akzeptiert werden. Weitere Informationen über akzeptierte `LineString` -Instanzen finden Sie unter [LineString](../spatial/linestring.md). In den folgenden Beispielen werden akzeptierte `MultiLineString`-Instanzen veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 Das folgende Beispiel löst eine `System.FormatException` da die zweite `LineString` -Instanz ist ungültig.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>Gültige Instanzen  
 Für eine `MultiLineString` -Instanz gültig ist, muss die folgenden Kriterien erfüllen:  
  
1.  Alle Instanzen, die die `MultiLineString`-Instanz beinhalten, müssen gültige `LineString`-Instanzen sein.  
  
2.  Zwei `LineString`-Instanzen, die die `MultiLineString`-Instanz beinhalten, dürfen sich nicht  im Verlauf eines Intervalls überlappen. Die `LineString`-Instanzen können sich nur mit einer endlichen Anzahl von Punkten überschneiden oder sich selbst oder andere `LineString`-Instanzen berühren.  
  
 Im folgenden Beispiel werden drei gültige `MultiLineString`-Instanzen und eine nicht gültige `MultiLineString`-Instanz gezeigt.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` gilt nicht da die zweite `LineString` Instanz überschneidet sich mit der ersten `LineString` Instanz in einem Intervall. Sie berühren sich mit einer unendlichen Anzahl von Punkten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine einfache `geometry``MultiLineString` -Instanz erstellt, die zwei `LineString` -Elemente mit der SRID 0 enthält.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 Um diese Instanz mit einem anderen SRID zu instanziieren, verwenden Sie `STGeomFromText()` oder `STMLineStringFromText()`. Sie können auch `Parse()` verwenden und den SRID dann ändern, wie im folgenden Beispiel gezeigt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [STLength &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STIsClosed &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [LineString](../spatial/linestring.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)  
  
  
