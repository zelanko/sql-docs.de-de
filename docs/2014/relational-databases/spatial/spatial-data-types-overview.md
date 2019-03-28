---
title: Übersicht über räumliche Datentypen | Microsoft-Dokumentation
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 135541d4474ab68fc8bdbc294663c8d9bcbc7c14
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526682"
---
# <a name="spatial-data-types-overview"></a>Übersicht über räumliche Datentypen
  Es gibt zwei Typen von räumlichen Daten. Der `geometry`-Datentyp unterstützt planare bzw. euklidische Daten. Der `geometry`-Datentyp entspricht der Open Geospatial Consortium (OGC) Simple Features for SQL Specification Version 1.1.0. und ist auch mit SQL MM (ISO-Standard) kompatibel.  
  
 Zudem unterstützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den `geography`-Datentyp, der ellipsenförmige Daten speichert, z. B. GPS-Breiten- und Längenkoordinaten.  
  
> [!IMPORTANT]  
>  Laden Sie für eine ausführliche Beschreibung und Beispiele der in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eingeführten räumlichen Funktionen (z.B. Erweiterungen der räumlichen Datentypen) das folgende Whitepaper herunter: [New Spatial Features in SQL Server Code-Named „Denali“](https://go.microsoft.com/fwlink/?LinkId=226407)(Neue räumliche Funktionen in SQL Server Codename „Denali“).  
  
##  <a name="objects"></a> Räumliche Datenobjekte  
 Der `geometry`-Datentyp und der `geography`-Datentyp unterstützen 16 räumliche Datenobjekte bzw. Instanztypen. Nur elf dieser Instanztypen sind jedoch *instanziierbar*. Sie können diese Instanzen erstellen und Sie in einer Datenbanken bearbeiten (oder instanziieren). Diese Instanzen leiten bestimmte Eigenschaften von ihren übergeordneten Datentypen, die sie als unterscheiden `Points`, **LineStrings, CircularStrings**, `CompoundCurves`, `Polygons`, `CurvePolygons` oder als mehrere `geometry`oder `geography` -Instanzen in einer `GeometryCollection`. Der `Geography`-Typ verfügt über einen zusätzlichen Instanztyp `FullGlobe`.  
  
 Die nachfolgende Abbildung stellt die `geometry`-Hierarchie dar, auf der der `geometry`-Datentyp und der `geography`-Datentyp basieren. Die instanziierbaren Typen von `geometry` und `geography` sind in blau angezeigt.  
  
 ![Hierarchie des geometrietyps](../../database-engine/media/geom-hierarchy.gif "Hierarchie des geometrietyps")  
  
 Wie in der Abbildung hervorgeht, die zehn instanziierbaren Typen von der `geometry` und `geography` Datentypen sind `Point`, `MultiPoint`, `LineString`, `CircularString`, `MultiLineString`, `CompoundCurve`, `Polygon`, `CurvePolygon`, `MultiPolygon`, und `GeometryCollection`. Es gibt einen zusätzlichen instanziierbaren Typen für den geography-Datentyp: `FullGlobe`. Die `geometry` und `geography` Typen können eine spezifische Instanz erkennen, solange es eine wohlgeformte Instanz handelt, auch wenn die Instanz nicht explizit definiert ist. Angenommen, Sie definieren eine `Point` -Instanz explizit mit der stpointfromtext()-Methode `geometry` und `geography` die Instanz als ein `Point`, sofern die methodeneingabe wohlgeformt ist. Wenn Sie die gleiche Instanz mit der `STGeomFromText()`-Methode definieren, erkennen sowohl der `geometry`-Datentyp als auch der `geography`-Datentyp die Instanz als `Point`.  
  
 Die Untertypen für geometry- und geography-Typen sind in einfache Typen und Auflistungstypen unterteilt.  Einige Methoden wie `STNumCurves()` funktionieren nur mit einfachen Typen.  
  
 Zu einfachen Typen gehören:  
  
-   [Point](../spatial/point.md)  
  
-   [LineString](../spatial/linestring.md)  
  
-   [CircularString](../spatial/circularstring.md)  
  
-   [CompoundCurve](../spatial/compoundcurve.md)  
  
-   [Polygon](../spatial/polygon.md)  
  
-   [CurvePolygon](../spatial/curvepolygon.md)  
  
 Zu Auflistungstypen gehören:  
  
-   [MultiPoint](../spatial/multipoint.md)  
  
-   [MultiLineString](../spatial/multilinestring.md)  
  
-   [MultiPolygon](../spatial/multipolygon.md)  
  
-   [GeometryCollection](../spatial/geometrycollection.md)  
  
  
##  <a name="differences"></a> Unterschiede zwischen den geometry- und geography-Datentypen  
 Die beiden Typen von räumlichen Daten verhalten sich oft ganz ähnlich. Es gibt aber einige wichtige Unterschiede in Bezug darauf, wie Daten gespeichert und bearbeitet werden.  
  
### <a name="how-connecting-edges-are-defined"></a>Definieren von verbindenden Rändern  
 Die definierenden Daten für die Typen `LineString` und `Polygon` sind nur Scheitelpunkte.  Der verbindende Rand zwischen zwei Scheitelpunkten in einer Geometrie ist eine gerade Linie.  Die verbindende Kante zwischen zwei Scheitelpunkten in einem Geografietyp ist ein kurzer elliptischer Bogen zwischen den beiden Scheitelpunkten.  Eine große Ellipse ist die Schnittmenge des Ellipsoids mit einer Ebene durch seinen Mittelpunkt, und ein großer elliptischer Bogen ist ein Bogensegment auf der großen Ellipse.  
  
### <a name="how-circular-arc-segments-are-defined"></a>Definieren von Kreisbogensegmenten  
 Kreisbogensegmente für geometry-Typen werden in der kartesischen XY-Koordinatenebene definiert (Z-Werte werden ignoriert). Kreisbogensegmente für geography-Typen werden von Kurvenabschnitten auf einer Verweiskugel definiert. Jede Parallele auf der Verweiskugel kann von zwei komplementären Kreisbögen definiert werden, wobei die Punkte für beide Bögen einen konstanten Breitenwinkel haben.  
  
### <a name="measurements-in-spatial-data-types"></a>Maße in räumlichen Datentypen  
 Im planaren bzw. euklidischen System werden Maße von Entfernungen und Flächen in der gleichen Maßeinheit angegeben wie die Koordinaten. Bei Verwendung des `geometry`-Datentyps beträgt die Entfernung zwischen (2, 2) und (5, 6) ungeachtet der verwendeten Maßeinheit 5 Einheiten.  
  
 Im ellipsenförmigen System werden Koordinaten in Breiten- und Längengraden angegeben. Längen und Flächen werden in der Regel in Meter und Quadratmeter gemessen. Die Maßeinheit kann jedoch vom SRID der `geography`-Instanz abhängen. Die gängigste Maßeinheit für den `geography`-Datentyp ist Meter.  
  
### <a name="orientation-of-spatial-data"></a>Ausrichtung von räumlichen Daten  
 Im planaren System ist die Ringausrichtung eines Polygons kein wichtiger Faktor. Beispielsweise entspricht das durch ((0, 0), (10, 0), (0, 20), (0, 0)) gegebene Polygon dem Polygon, das durch ((0, 0), (0, 20), (10, 0), (0, 0)) beschrieben wird. Die OGC Simple Features for SQL-Spezifikation schreibt keine Ringreihenfolge vor, und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erzwingt keine Ringreihenfolge.  
  
 In einem ellipsenförmigen System hat ein Polygon ohne Ausrichtung keine Bedeutung bzw. ist mehrdeutig. Beschreibt beispielsweise ein Ring um den Äquator die nördliche oder die südliche Hemisphäre? Wenn wir den `geography`-Datentyp zum Speichern von räumlichen Daten verwenden, müssen wir die Ausrichtung des Rings angeben und die Position der Instanz genau beschreiben. Der Innere des Polygons in einem ellipsoidförmigen System wird von der linken Regel definiert.  
  
 Wenn der Kompatibilitätsgrad 100 oder niedriger in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] die `geography` Datentyp gelten folgende Einschränkungen:  
  
-   Jede `geography`-Instanz muss in genau eine Hemisphäre passen. Es können keine räumlichen Objekte gespeichert werden, die größer als eine Hemisphäre sind.  
  
-   Jede `geography`-Instanz aus einer Darstellung des Typs Open Geospatial Consortium (OGC) Well-Known Text (WKT) oder Well-Known Binary (WKB), die ein Objekt ergibt, das größer als eine Hemisphäre ist, löst eine Ausnahme des Typs `ArgumentException` aus.  
  
-   Die `geography` -Datentypmethoden, die die Eingaben von zwei erfordern `geography` -Instanzen wie STIntersection(), STUnion(), STDifference() und STSymDifference(), null zurück, wenn die Ergebnisse der Methoden nicht in eine einzige Hemisphäre passen. STBuffer() gibt ebenfalls NULL zurück, wenn die Ausgabe eine Hemisphäre überschreitet.  
  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ist `FullGlobe` ein spezieller Polygontyp, der den gesamten Globus abdeckt. `FullGlobe` verfügt über einen Bereich, aber nicht über Rahmen oder Scheitelpunkte.  
  
### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a>Äußere und innere Ringe sind beim geography-Datentyp nicht von Bedeutung  
 Der OGC Simple Features for SQL-Spezifikation wird erläutert, äußere und innere Ringe jedoch diese Unterscheidung ist nicht sinnvoll, für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` -Datentyps; jeder Ring eines Polygons kann erstellt werden, die äußerer Ring interpretiert werden.  
  
 Weitere Informationen zu den OGC-Spezifikationen finden Sie in den folgenden Themen:  
  
-   [OGC Specifications, Simple Feature Access Part 1 - Common Architecture](https://go.microsoft.com/fwlink/?LinkId=93627)  
  
-   [OGC Specifications, Simple Feature Access Part 2: SQL Options (OGC-Spezifikationen, Simple Feature Access, Teil 2: SQL-Optionen)](https://go.microsoft.com/fwlink/?LinkId=93628)  
  
  
##  <a name="circular"></a> Kreisbogensegmente  
 Drei instanziierbare Typen können Kreisbogensegmente verwenden: `CircularString`, `CompoundCurve` und `CurvePolygon`.  Ein Kreisbogensegment wird von drei Punkten in einer zweidimensionalen Ebene definiert; der dritte Punkt darf nicht mit dem ersten Punkt identisch sein.  
  
 In Abbildung A und B sind typische Kreisbogensegmente dargestellt. Beachten Sie, dass jeder der drei Punkte auf dem Umkreis eines Kreises liegt.  
  
 In Abbildung C und D ist dargestellt, wie ein Liniensegment als Kreisbogensegment definiert werden kann.  Beachten Sie, dass auch hier, im Gegensatz zu einem regulären Liniensegment, das mit nur zwei Punkten definierten werden kann, drei Punkte erforderlich sind, um das Kreisbogensegment zu definieren.  
  
 Methoden, die für Kreisbogensegmenttypen ausgeführt werden, verwenden gerade Liniensegmente zur Annäherung an den Kreisbogen. Die Anzahl von Liniensegmenten, die zur Annäherung an den Bogen verwendet wird, ist von der Länge und der Krümmung des Bogens abhängig. Für jeden Kreisbogensegmenttyp können Z-Werte können gespeichert werden, diese werden jedoch von Methoden nicht in ihren Berechnungen verwendet.  
  
> [!NOTE]  
>  Wenn Z-Werte für Kreisbogensegmente angegeben werden, müssen diese für alle Punkte in dem Kreisbogensegment gleich sein, damit sie als Eingabe akzeptiert werden. Beispielsweise ist `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` zulässig, `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` jedoch nicht.  
  
### <a name="linestring-and-circularstring-comparison"></a>Vergleich von LineString und CircularString  
 Im folgenden Diagramm sind identische gleichschenklige Dreiecke dargestellt (Dreieck A verwendet Liniensegmente zur Definition des Dreiecks, Dreieck B verwendet Kreisbogensegmente zur Definition des Dreiecks):  
  
 ![](../../database-engine/media/7e382f76-59da-4b62-80dc-caf93e637c14.png "7e382f76-59da-4b62-80dc-caf93e637c14")  
  
 In diesem Beispiel wird gezeigt, wie die oben erwähnten gleichschenkligen Dreiecke mit einer `LineString`-Instanz und einer `CircularString`-Instanz gespeichert werden:  
  
```sql  
DECLARE @g1 geometry;  
DECLARE @g2 geometry;  
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);  
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);  
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1  
  BEGIN  
      SELECT @g1.ToString(), @g2.ToString()  
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]  
  END  
```  
  
 Beachten Sie, dass eine `CircularString`-Instanz sieben Punkte erfordert, um das Dreieck zu definieren, eine `LineString`-Instanz erfordert jedoch nur vier Punkte, um das Dreieck zu definieren. Der Grund hierfür ist, dass eine `CircularString`-Instanz Kreisbogensegmente und keine Liniensegmente speichert. Deshalb sind die Seiten des in der `CircularString`-Instanz gespeicherten Dreiecks ABC, CDE und EFA, wohingegen die Seiten des in der `LineString`-Instanz gespeicherten Dreiecks AC, CE und EA sind.  
  
 Sehen Sie sich den folgenden Codeausschnitt an:  
  
```sql  
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);  
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);  
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];  
```  
  
 Dieser Ausschnitt liefert die folgende Ergebnisse:  
  
```  
LS LengthCS Length  
5.65685...6.28318...  
```  
  
 Die folgende Abbildung zeigt, wie die einzelnen Typen gespeichert werden (rote Linie stellt `LineString``@g1`, die blaue Linie stellt `CircularString``@g2`):  
  
 ![](../../database-engine/media/e52157b5-5160-4a4b-8560-50cdcf905b76.png "e52157b5-5160-4a4b-8560-50cdcf905b76")  
  
 Wie die obige Abbildung zeigt, verwenden `CircularString`-Instanzen weniger Punkte, um Kurvenbegrenzungen mit größerer Genauigkeit zu speichern, als `LineString`-Instanzen. `CircularString`-Instanzen sind hilfreich für das Speichern von Kreisbegrenzungen, z. B. ein Suchradius von zwanzig Kilometern von einem bestimmten Punkt aus. `LineString`-Instanzen eignen sich für das Speichern von linearen Grenzen, z. B. ein Häuserblock.  
  
### <a name="linestring-and-compoundcurve-comparison"></a>Vergleich von LineString und CompoundCurve  
 In den folgenden Codebeispielen ist dargestellt, wie die gleiche Abbildung mit `LineString`- und `CompoundCurve`-Instanzen gespeichert wird:  
  
```sql  
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');  
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');  
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');  
```  
  
 oder  
  
 In den obigen Beispielen könnte die Abbildung entweder mit einer `LineString`-Instanz oder einer `CompoundCurve`-Instanz gespeichert werden.  Im nächsten Beispiel wird ein Kreisslice mithilfe eines `CompoundCurve` gespeichert:  
  
```sql  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');  
```  
  
 Eine `CompoundCurve`-Instanz kann das Kreisbogensegment (2 2, 1 3, 0 2) direkt speichern, wohingegen eine `LineString`-Instanz die Kurve in mehrere kleinere Liniensegmente konvertieren müsste.  
  
### <a name="circularstring-and-compoundcurve-comparison"></a>Vergleich von CircularString und CompoundCurve  
 Im folgenden Codebeispiel wird gezeigt, wie der Kreisslice in einer `CircularString`-Instanz gespeichert werden kann:  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');  
SELECT @g.ToString(), @g.STLength();  
```  
  
 Zum Speichern des Kreisslices mit einer `CircularString`-Instanz müssen drei Punkte für jedes Liniensegment verwendet werden.  Wenn ein Zwischenpunkt nicht bekannt wird, muss er entweder berechnet werden, oder der Endpunkt des Liniensegments muss verdoppelt werden, wie im folgenden Codeausschnitt dargestellt:  
  
```sql  
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');  
```  
  
 In `CompoundCurve`-Instanzen sind sowohl `LineString`- als auch `CircularString`-Komponenten zulässig, sodass nur zwei Punkte der Liniensegmente des Kreisslices bekannt sein müssen.  In diesem Codebeispiel wird gezeigt, wie ein `CompoundCurve` verwendet wird, um die gleiche Abbildung zu speichern:  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');  
SELECT @g.ToString(), @g.STLength();  
```  
  
### <a name="polygon-and-curvepolygon-comparison"></a>Vergleich von Polygon und CurvePolygon  
 `CurvePolygon`-Instanzen können beim Definieren ihrer äußeren und inneren Ringe `CircularString`- und `CompoundCurve`-Instanzen verwenden.  `Polygon`-Instanzen können keine Kreisbogensegmenttypen verwenden: `CircularString` und `CompoundCurve`.  
  
  
## <a name="see-also"></a>Siehe auch  
 [Räumliche Daten &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)   
 [geometry-Datentyp-Methodenverweis](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql)   
 [geography-Datentyp-Methodenverweis](/sql/t-sql/spatial-geography/spatial-types-geography)   
 [STNumCurves &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type)   
 [STNumCurves &#40;Geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type)   
 [STGeomFromText &#40;Geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)   
 [STGeomFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
  
