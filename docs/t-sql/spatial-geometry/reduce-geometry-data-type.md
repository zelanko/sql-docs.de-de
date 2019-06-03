---
title: Reduce (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: 132184bf-c4d2-4a27-900d-8373445dce2a
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: f66cdcebb92127486d75de270d93d0507131c4d3
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937362"
---
# <a name="reduce-geometry-data-type"></a>Reduce (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt einen Näherungswert für die angegebene **geometry**-Instanz zurück. Dieser Näherungswert wird unter Verwendung einer Erweiterung des Douglas-Peucker-Algorithmus mit der angegebenen Toleranz ermittelt.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Argumente  
 *tolerance*  
 Ein Wert vom Typ **float**. *tolerance* gibt die Toleranz an, die als Eingabe für den Näherungsalgorithmus verwendet werden soll.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Bei Auflistungstypen arbeitet dieser Algorithmus unabhängig für jeden **geometry** -Wert, der in der Instanz enthalten ist.  
  
 Dieser Algorithmus ändert keine **Point**-Instanzen.  
  
 In den Instanzen **LineString**, **CircularString** und **CompoundCurve** werden die ursprünglichen Start- und Endpunkte der Instanz vom Näherungsalgorithmus beibehalten. Der Algorithmus rechnet anschließend iterativ den Punkt aus der ursprünglichen Instanz hinzu, der am meisten vom Ergebnis abweicht. Dieser Vorgang wird so lange fortgesetzt, bis kein Punkt mehr über die angegebene Toleranz hinaus abweicht.  
  
 `Reduce()` gibt eine **LineString**-, **CircularString**- oder **CompoundCurve**-Instanz für **CircularString**-Instanzen zurück.  `Reduce()` gibt eine **CompoundCurve**- oder **LineString**-Instanz für **CompoundCurve**-Instanzen zurück.  
  
 Auf **Polygon** -Instanzen wird der Näherungsalgorithmus unabhängig für jeden Ring angewendet. Die Methode erzeugt eine `FormatException`-Ausnahme, wenn die zurückgegebene **Polygon**-Instanz ungültig ist. Eine ungültige **MultiPolygon**-Instanz wird beispielsweise dann erstellt, wenn `Reduce()` zur Vereinfachung jedes Rings in der Instanz angewendet wird und sich die ergebenden Ringe überschneiden.  Bei Instanzen von **CurvePolygon** mit einem äußeren Ring und ohne innere Ringe wird von `Reduce()` eine Instanz von **CurvePolygon**, **LineString** oder **Point** zurückgegeben.  Wenn **CurvePolygon** innere Ringe aufweist, wird eine Instanz von **CurvePolygon** oder eine Instanz von **MultiPoint** zurückgegeben.  
  
 Wenn ein Kreisbogensegment gefunden wird, überprüft der Näherungsalgorithmus, ob eine näherungsweise Bestimmung des Bogens durch die Sehne innerhalb der Hälfte der angegebenen Toleranz möglich ist. Wenn eine Sehne diese Kriterien erfüllt, wird der Kreisbogen in den Berechnungen durch die Sehne ersetzt. Wenn eine Sehne diese Kriterien nicht erfüllt, wird der Kreisbogen beibehalten, und der Näherungsalgorithmus wird für die verbleibenden Segmente übernommen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-reduce-to-simplify-a-linestring"></a>A. Vereinfachen eines LineString mithilfe von Reduce()  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und `Reduce()` verwendet, um die Instanz zu vereinfachen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0, 2 1, 3 0, 4 1)', 0);  
SELECT @g.Reduce(.75).ToString();  
```  
  
### <a name="b-using-reduce-with-varying-tolerance-levels-on-a-circularstring"></a>B. Verwenden von Reduce() in einem CircularString und veränderlichen Toleranzebenen  
 Im folgenden Beispiel wird `Reduce()` in einer **CircularString** -Instanz mit drei Toleranzebenen verwendet:  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0)'; 
 SELECT @g.Reduce(5).ToString(); 
 SELECT @g.Reduce(15).ToString(); 
 SELECT @g.Reduce(16).ToString();
 ```  
  
 Hierdurch wird folgende Ausgabe generiert:  
  
 ```
 CIRCULARSTRING (0 0, 8 8, 16 0, 20 -4, 24 0) 
 COMPOUNDCURVE (CIRCULARSTRING (0 0, 8 8, 16 0), (16 0, 24 0)) 
 LINESTRING (0 0, 24 0)
 ```  
  
 Alle zurückgegebenen Instanzen enthalten die Endpunkte (0 0) und (24 0).  
  
### <a name="c-using-reduce-with-varying-tolerance-levels-on-a-compoundcurve"></a>C. Verwenden von Reduce() in einer CompoundCurve mit veränderlichen Toleranzebenen  
 Im folgenden Beispiel wird `Reduce()` in einer **CompoundCurve** -Instanz mit drei Toleranzebenen verwendet:  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0),(24 0, 20 4, 16 0))';  
 SELECT @g.Reduce(15).ToString();  
 SELECT @g.Reduce(16).ToString();
 ```  
  
 Beachten Sie in diesem Beispiel, dass die zweite **SELECT** -Anweisung die **LineString** -Instanz mit drei Toleranzebenen verwendet: `LineString(0 0, 16 0)`.  
  
### <a name="showing-an-example-where-the-original-start-and-end-points-are-lost"></a>Anzeigen eines Beispiels mit verloren gegangenem Ausgangs- und Endpunkt  
 Im folgenden Beispiel wird veranschaulicht, dass der ursprüngliche Ausgangs- und Endpunkt von der resultierenden Instanz möglicherweise nicht beibehalten werden. Dieses Verhalten liegt darin begründet, dass andernfalls eine ungültige Instanz von **LineString** erzeugt würde.  
  
```  
DECLARE @g geometry = 'LINESTRING(0 0, 4 0, 2 .01, 1 0)';  
DECLARE @h geometry = @g.Reduce(1);  
SELECT @g.STIsValid() AS Valid  
SELECT @g.ToString() AS Original, @h.ToString() AS Reduced;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte statische geometry-Methoden](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
