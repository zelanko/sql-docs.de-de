---
title: CompoundCurve | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 983711f4ac679cdb12fa7c31509725f13fba8bb3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62524437"
---
# <a name="compoundcurve"></a>CompoundCurve
  Eine `CompoundCurve` ist eine Auflistung von 0 (null) oder mehr fortlaufenden `CircularString`-Instanzen oder `LineString`-Instanzen von geometry- oder geography-Typen.  
  
> [!IMPORTANT]  
>  Für eine ausführliche Beschreibung und Beispiele der neuen räumlichen Funktionen in dieser Version einschließlich der `CompoundCurve` Untertyp, können Sie das Whitepaper zur [neue räumliche Funktionen in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).  
  
 Eine leere `CompoundCurve`-Instanz kann instanziiert werden. Damit eine `CompoundCurve` gültig ist, muss sie jedoch die folgenden Kriterien erfüllen:  
  
1.  Sie muss mindestens eine `CircularString`-Instanz oder `LineString`-Instanz enthalten.  
  
2.  Die Sequenz von `CircularString`-Instanzen oder `LineString`-Instanzen muss fortlaufend sein.  
  
 Wenn eine `CompoundCurve` enthält eine Sequenz von mehrerem `CircularString` und `LineString` Instanzen, den abschließende Endpunkt für jede Instanz mit Ausnahme der letzten Instanz der beginnende Endpunkt für die nächste Instanz in der Sequenz sein muss. Wenn also der Endpunkt der vorhergehenden Instanz in der Sequenz (4 3 7 2) ist, muss der Anfangspunkt für die nächste Instanz in der Sequenz (4 3 7 2) sein. Beachten Sie, dass die Z-Werte (Höhe) und die M-Werte (Measure) für den Punkt ebenfalls gleich sein müssen. Wenn sich die beiden Punkte unterscheiden, wird ein `System.FormatException` ausgelöst. Punkte in einer `CircularString` müssen über keinen Z-Wert oder M-Wert verfügen. Wenn keine Z- oder M-Werte für den Endpunkt der vorherigen Instanz angegeben sind, kann der Anfangspunkt der nächsten Instanz keine Z- oder M-Werte einschließen. Wenn der Endpunkt für die vorherige Sequenz (4 3) ist, muss der Anfangspunkt für die nächste Sequenz (4 3) sein; (4 3 7 2) ist hingegen nicht möglich. Alle Punkte in einer `CompoundCurve`-Instanz dürfen entweder über keinen Z-Wert verfügen, oder sie müssen denselben Z-Wert aufweisen.  
  
## <a name="compoundcurve-instances"></a>CompoundCurve-Instanzen  
 In der folgenden Abbildung sind gültige `CompoundCurve`-Typen dargestellt.  
  
 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")  
  
### <a name="accepted-instances"></a>Akzeptierte Instanzen  
 Die `CompoundCurve`-Instanz wird akzeptiert, wenn sie leer ist bzw. die folgenden Kriterien erfüllt.  
  
1.  Alle von der `CompoundCurve`-Instanz enthaltenen Instanzen sind akzeptierte Kreisbogensegment-Instanzen. Weitere Informationen zu akzeptierten Kreisbogensegment-Instanzen finden Sie unter [LineString](linestring.md) und [CircularString](circularstring.md).  
  
2.  Alle Kreisbogensegmente in der `CompoundCurve`-Instanz sind verbunden. Der erste Punkt jedes nachfolgenden Kreisbogensegments entspricht dem letzten Punkt des jeweils vorgehenden Kreisbogensegments.  
  
    > [!NOTE]  
    >  Dies schließt die Z- und M-Koordinaten ein. Daher müssen alle vier Koordinaten X, Y, Z und M identisch sein.  
  
3.  Bei keiner der enthaltenen Instanzen handelt es sich um leere Instanzen.  
  
 Im folgenden Beispiel werden akzeptierte `CompoundCurve`-Instanzen veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
```  
  
 Im folgenden Beispiel werden nicht akzeptierte `CompoundCurve`-Instanzen veranschaulicht. Diese Instanzen lösen eine `System.FormatException`aus.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';  
```  
  
### <a name="valid-instances"></a>Gültige Instanzen  
 Eine `CompoundCurve`-Instanz ist gültig, wenn sie die folgenden Kriterien erfüllt.  
  
1.  Die `CompoundCurve`-Instanz wird akzeptiert.  
  
2.  Alle in der `CompoundCurve`-Instanz enthaltenen Kreisbogensegment-Instanzen sind gültige Instanzen.  
  
 Im folgenden Beispiel werden gültige `CompoundCurve`-Instanzen veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
  
```  
  
 `@g3` ist gültig, da die `CircularString`-Instanz gültig ist. Weitere Informationen zur Gültigkeit der `CircularString` Instanz ist, finden Sie unter [CircularString](circularstring.md).  
  
 Im folgenden Beispiel werden `CompoundCurve` -Instanzen veranschaulicht, die nicht gültig sind.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';  
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g1` ist ungültig, da die zweite Instanz keine gültige LineString-Instanz ist. `@g2` ist ungültig, da die `LineString`-Instanz ungültig ist. `@g3` ist ungültig, da die `CircularString`-Instanz ungültig ist. Weitere Informationen zu gültigen `CircularString` und `LineString` -Instanzen finden Sie unter [CircularString](circularstring.md) und [LineString](linestring.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a>A. Instanziieren einer geometry-Instanz mit einer leeren CompoundCurve  
 Im folgenden Beispiel wird veranschaulicht, wie eine leere `CompoundCurve` -Instanz erstellt wird:  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a>B. Deklarieren und Instanziieren einer geometry-Instanz, die eine CompoundCurve in derselben Anweisung verwendet  
 Im folgenden Beispiel wird veranschaulicht, wie eine `geometry` -Instanz mit einer `CompoundCurve`in derselben Anweisung deklariert und instanziiert wird:  
  
```sql  
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a>C. Instanziieren einer geography-Instanz mit einer CompoundCurve  
 Im folgenden Beispiel wird veranschaulicht, wie eine `geography`-Instanz mit einer `CompoundCurve` deklariert und initialisiert wird:  
  
```sql  
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a>D. Speichern eines Quadrats in einer CompoundCurve-Instanz  
 Im folgenden Beispiel werden zwei verschiedene Möglichkeiten gezeigt, wie mithilfe einer `CompoundCurve` -Instanz ein Quadrat gespeichert werden kann.  
  
```sql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');  
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');  
SELECT @g1.STLength(), @g2.STLength();  
```  
  
 Die Länge von `@g1` und die Länge von `@g2` sind identisch. Anhand des Beispiels können Sie feststellen, dass von einer `CompoundCurve`-Instanz eine oder mehrere Instanzen von `LineString` gespeichert werden können.  
  
### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a>E. Instanziieren einer geometry-Instanz mithilfe einer CompoundCurve mit mehreren CircularStrings  
 Im folgenden Beispiel wird gezeigt, wie mithilfe von zwei verschiedenen `CircularString` -Instanzen eine `CompoundCurve`initialisiert werden kann.  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT @g.STLength();  
```  
  
 Hierdurch wird folgende Ausgabe generiert: 12. 566370…... Dies entspricht 4 Zuweisen von gruppenlizenzen finden. Von der `CompoundCurve` -Instanz im Beispiel wird ein Kreis mit dem Radius 2 gespeichert. In den beiden vorherigen Codebeispielen musste keine `CompoundCurve`verwendet werden. Für das erste Beispiel wäre eine `LineString` -Instanz einfacher gewesen, während sich für das zweite Beispiel eher eine `CircularString` -Instanz empfiehlt. Im nächsten Beispiel wird jedoch verdeutlich, in welchen Fällen eine `CompoundCurve` eine bessere Alternative darstellt.  
  
### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a>F. Speichern eines Halbkreises mithilfe einer CompoundCurve  
 Im folgenden Beispiel wird ein Halbkreis mithilfe einer `CompoundCurve` -Instanz gespeichert.  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');  
SELECT @g.STLength();  
```  
  
### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a>G. Speichern mehrerer CircularString- und LineString-Instanzen in einer CompoundCurve  
 Im folgenden Beispiel wird gezeigt, wie mehrere `CircularString` -Instanzen und `LineString` -Instanzen mit einer `CompoundCurve`gespeichert werden können.  
  
```sql  
DECLARE @g geometry  
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');  
SELECT @g.STLength();  
```  
  
### <a name="h-storing-instances-with-z-and-m-values"></a>H. Speichern von Instanzen mit Z- und M-Werten  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe einer `CompoundCurve` -Instanz eine Sequenz von `CircularString` -Instanzen und `LineString` -Instanzen mit Z- und M-Werten gespeichert wird.  
  
```sql  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');  
```  
  
### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a>I. Gründe für die explizite Deklaration von CircularString-Instanzen  
 Im folgenden Beispiel wird erläutert, weshalb `CircularString` -Instanzen explizit deklariert werden müssen. Der Programmierer versucht, in einer `CompoundCurve` -Instanz einen Kreis zu speichern.  
  
```sql  
DECLARE @g1 geometry;    
DECLARE @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');  
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount  
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount  
```  
  
 Es wird folgende Ausgabe erhalten:  
  
```  
Circle One11.940039...  
Circle Two12.566370...  
```  
  
 Der Umfang für Circle Two ist ca. 4 Zuweisen von gruppenlizenzen finden, dies ist der tatsächliche Wert für den Umfang. Der Umkreis für Circle One ist jedoch sehr ungenau. Durch die `CompoundCurve` -Instanz von Circle One werden ein Kreisbogensegment (ABC) und zwei Liniensegmente (CD, DA) gespeichert. Von der `CompoundCurve` -Instanz müssen zwei Kreisbogensegmente (ABC, CDA) gespeichert werden, um einen Kreis zu definieren. Eine `LineString` -Instanz definiert die zweite Punktmenge (4 2, 2 4, 0 2) in der `CompoundCurve` -Instanz von Circle One. Sie müssen in einer `CircularString` explizit eine `CompoundCurve`-Instanz deklarieren.  
  
## <a name="see-also"></a>Siehe auch  
 [STIsValid &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STLength &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [LineString](linestring.md)   
 [CircularString](circularstring.md)   
 [Übersicht über räumliche Datentypen](spatial-data-types-overview.md)   
 [Punkt](point.md)  
  
  
