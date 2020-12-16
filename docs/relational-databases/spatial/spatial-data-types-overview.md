---
description: Übersicht über räumliche Datentypen
title: Übersicht über räumliche Datentypen | Microsoft-Dokumentation
ms.date: 07/21/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 668d1fda7e4b979e52377c03daaddb0cb2286cdd
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97462961"
---
# <a name="spatial-data-types-overview"></a>Übersicht über räumliche Datentypen

[!INCLUDE [SQL Server Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/sql-asdb-asdbmi.md)]
  
Es gibt zwei Typen von räumlichen Daten. Der **geometry** -Datentyp unterstützt planare bzw. euklidische Daten (flache Erdabbildung). Der **geometry**-Datentyp entspricht der Version 1.1.0. der *Simple Features for SQL-Spezifikation des Open Geospatial Consortium (OGC)* und ist auch mit SQL MM (ISO-Standard) kompatibel.
Zudem unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den **geography**-Datentyp, der ellipsenförmige Daten speichert (runde Erdabbildung), z. B. GPS-Breiten- und -Längenkoordinaten.

## <a name="spatial-data-objects"></a>Räumliche Datenobjekte

Der **geometry**-Datentyp und der **geography**-Datentyp unterstützen 16 räumliche Datenobjekte bzw. Instanztypen. Nur elf dieser Instanztypen sind jedoch *instanziierbar*. Sie können diese Instanzen erstellen und Sie in einer Datenbank bearbeiten (oder instanziieren). Diese Instanzen leiten bestimmte Eigenschaften von ihren übergeordneten Datentypen ab.

Die nachfolgende Abbildung stellt die geometry-Hierarchie dar, auf der der **geometry**-Datentyp und der **geography**-Datentyp basieren. Die instanziierbaren Typen von **geometry** und **geography** sind in Blau dargestellt.  

![geom_hierarchy](../../relational-databases/spatial/media/geom-hierarchy.png)

Es gibt einen zusätzlichen instanziierbaren Typen für den geography-Datentyp: **FullGlobe**. Die Typen **geometry** und **geography** können eine spezifische Instanz erkennen, wenn es sich um eine wohlgeformte Instanz handelt. Dies gilt auch, wenn die Instanz nicht explizit definiert ist. Wenn Sie beispielsweise eine **Point**-Instanz explizit mit der Methode STPointFromText() definieren, erkennen **geometry** und **geography** die Instanz als **Point**, sofern die Methodeneingabe wohlgeformt ist. Wenn Sie die gleiche Instanz mit der `STGeomFromText()` -Methode definieren, erkennen sowohl der **geometry** - als auch der **geography** -Datentyp die Instanz als **Point**.  

Die Untertypen für geometry- und geography-Typen sind in einfache Typen und Auflistungstypen unterteilt.  Einige Methoden wie `STNumCurves()` funktionieren nur mit einfachen Typen.  

Einfache Typen sind:

- [Point](../../relational-databases/spatial/point.md)  
- [LineString](../../relational-databases/spatial/linestring.md)  
- [CircularString](../../relational-databases/spatial/circularstring.md)  
- [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
- [Polygon](../../relational-databases/spatial/polygon.md)  
- [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  

Auflistungstypen sind:

- [MultiPoint](../../relational-databases/spatial/multipoint.md)  
- [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
- [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
- [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  

## <a name="geometry-and-geography-data-type-differences"></a>Unterschiede zwischen geometry- und geography-Datentypen

Die beiden räumlichen Datentypen verhalten sich oft ähnlich. Es gibt einige wichtige Unterschiede in der Art und Weise, wie die Daten gespeichert und bearbeitet werden.  

### <a name="how-connecting-edges-are-defined"></a>Definieren von verbindenden Rändern

Die definierenden Daten für die Typen **LineString** und **Polygon** sind nur Scheitelpunkte. Der verbindende Rand zwischen zwei Scheitelpunkten in einer Geometrie ist eine gerade Linie. Die verbindende Kante zwischen zwei Scheitelpunkten in einem Geografietyp ist ein kurzer elliptischer Bogen zwischen den beiden Scheitelpunkten. Eine Ellipse ist die Schnittmenge des Ellipsoids mit einer Ebene durch seinen Mittelpunkt. Ein elliptischer Bogen ist ein Bogensegment auf der großen Ellipse.  

### <a name="how-circular-arc-segments-are-defined"></a>Definieren von Kreisbogensegmenten

Kreisbogensegmente für geometry-Typen werden in der kartesischen XY-Koordinatenebene definiert (Z-Werte werden ignoriert). Kreisbogensegmente für geography-Typen werden von Kurvenabschnitten auf einer Verweiskugel definiert. Jede Parallele auf der Verweiskugel kann von zwei komplementären Kreisbögen definiert werden, wobei die Punkte für beide Bögen einen konstanten Breitenwinkel haben.  

### <a name="measurements-in-spatial-data-types"></a>Maße in räumlichen Datentypen

Im planaren bzw. euklidischen System werden Maße von Entfernungen und Flächen in der gleichen Maßeinheit angegeben wie die Koordinaten. Bei Verwendung des **geometry**-Datentyps beträgt die Entfernung zwischen (2, 2) und (5, 6) ungeachtet der verwendeten Maßeinheit fünf Einheiten.  

Im ellipsenförmigen System werden Koordinaten in Breiten- und Längengraden angegeben. Längen und Flächen werden in der Regel in Meter und Quadratmeter gemessen. Die Maßeinheit kann jedoch von den [SRID (Spatial Reference Identifiers)](./spatial-reference-identifiers-srids.md) der **geography**-Instanz abhängen. Die gängigste Maßeinheit für den **geography** -Datentyp ist Meter.  

### <a name="orientation-of-spatial-data"></a>Ausrichtung von räumlichen Daten

Im planaren System ist die Ringausrichtung eines Polygons kein wichtiger Faktor. Die *OGC Simple Features for SQL-Spezifikation* schreibt keine Ringreihenfolge vor, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erzwingt keine Ringreihenfolge.  

In einem ellipsenförmigen System hat ein Polygon ohne Ausrichtung keine Bedeutung bzw. ist mehrdeutig. Beschreibt beispielsweise ein Ring um den Äquator die nördliche oder die südliche Hemisphäre? Wenn wir den **geography** -Datentyp zum Speichern von räumlichen Daten verwenden, müssen wir die Ausrichtung des Rings angeben und die Position der Instanz genau beschreiben.

Das Innere des Polygons in einem ellipsoidischen System wird über die „Linksregel“ definiert: Wenn Sie sich vorstellen, dass Sie auf dem Ring eines geography-Polygons die Punkte in der Reihenfolge ablaufen, in der sie aufgeführt sind, wird der Bereich links als das Innere des Polygons und der Bereich rechts als das Äußere des Polygons behandelt.

Wenn der Kompatibilitätsgrad in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 100 oder niedriger ist, weist der **geography** -Datentyp die folgenden Einschränkungen auf:

- Jede **geography** -Instanz muss in genau eine Hemisphäre passen. Es können keine räumlichen Objekte gespeichert werden, die größer als eine Hemisphäre sind.

- Jede **geography** -Instanz aus einer OGC-Darstellung (Open Geospatial Consortium) des Typs „Well-Known Text (WKT)“ oder „Well-Known Binary (WKB), die ein Objekt ergibt, das größer als eine Hemisphäre ist, führt zu einer Ausnahme des Typs **ArgumentException**“.  

- Die Methoden des **geography** -Datentyps, die Eingaben von zwei **geography** -Instanzen wie STIntersection(), STUnion(), STDifference() und STSymDifference() erfordern, geben NULL zurück, wenn das Ergebnis der Methode nicht in eine Hemisphäre passt. STBuffer() gibt ebenfalls NULL zurück, wenn die Ausgabe eine Hemisphäre überschreitet.  

In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ist **FullGlobe** ein spezieller Polygontyp, der den gesamten Globus abdeckt. Es verfügt über einen Bereich, aber nicht über Rahmen oder Scheitelpunkte.  

### <a name="outer-and-inner-rings-in-geography-data-type"></a>Äußere und innere Ringe beim `geography`-Datentyp

In der *Simple Features for SQL-Spezifikation des OGC* werden äußere und innere Ringe erörtert. Diese Unterscheidung ist für den **geography**-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]allerdings nicht sinnvoll: Jeder Ring eines Polygons kann als äußerer Ring interpretiert werden.  

Weitere Informationen zu den OGC-Spezifikationen finden Sie in den folgenden Dokumenten:

- [OGC Specifications, Simple Feature Access Part 1 - Common Architecture](https://go.microsoft.com/fwlink/?LinkId=93627)  
- [OGC Specifications, Simple Feature Access Part 2: SQL Options (OGC-Spezifikationen, Simple Feature Access, Teil 2: SQL-Optionen)](https://go.microsoft.com/fwlink/?LinkId=93628)  

## <a name="circular-arc-segments"></a>Kreisbogensegmente

Drei instanziierbare Typen können Kreisbogensegmente verwenden: **CircularString**, **CompoundCurve** und **CurvePolygon**.  Ein Kreisbogensegment wird von drei Punkten in einer zweidimensionalen Ebene definiert, und der dritte Punkt darf nicht mit dem ersten Punkt identisch sein. Einige Beispiele für Kreisbogensegmente:

![circular_arc_segments](../../relational-databases/spatial/media/7e382f76-59da-4b62-80dc-caf93e637c14.gif)

Die ersten beiden Beispiele sind typische Kreisbogensegmente. Beachten Sie, dass jeder der drei Punkte auf dem Umkreis eines Kreises liegt.  

Die anderen beiden Beispiele zeigen, wie ein Liniensegment als Kreisbogensegment definiert werden kann. Im Gegensatz zu einem regulären Liniensegment, das mit nur zwei Punkten definiert werden kann, sind dennoch drei Punkte erforderlich, um das Kreisbogensegment zu definieren.

Methoden, die für Kreisbogensegmenttypen ausgeführt werden, verwenden gerade Liniensegmente zur Annäherung an den Kreisbogen. Die Anzahl von Liniensegmenten, die zur Annäherung an den Bogen verwendet wird, ist von der Länge und der Krümmung des Bogens abhängig. Für jeden Kreisbogensegmenttyp können Z-Werte gespeichert werden, diese werden jedoch nicht in den Berechnungen verwendet.  

> [!NOTE]  
> Wenn Z-Werte für Kreisbogensegmente angegeben werden, müssen diese für alle Punkte in dem Kreisbogensegment gleich sein, damit sie als Eingabe akzeptiert werden. Beispielsweise ist `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` zulässig, `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` jedoch nicht.  

### <a name="linestring-and-circularstring-comparison"></a>Vergleich von LineString und CircularString

In diesem Beispiel wird gezeigt, wie die identischen gleichschenkligen Dreiecke mit einer **LineString**-Instanz und einer **CircularString**-Instanz gespeichert werden:  

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

Beachten Sie, dass eine **CircularString**-Instanz sieben Punkte erfordert, um das Dreieck zu definieren. Eine **LineString**-Instanz erfordert nur vier Punkte, um das Dreieck zu definieren. Der Grund hierfür ist, dass eine **CircularString** -Instanz Kreisbogensegmente und keine Liniensegmente speichert. Die Seiten des Dreiecks, die in der **CircularString**-Instanz gespeichert sind, sind ABC, CDE und EFA. Die Seiten des Dreiecks, die in der **LineString**-Instanz gespeichert sind, sind AC, CE und EA.  

Betrachten Sie das folgenden Beispiel:  

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```sql
LS Length    CS Length
5.65685...   6.28318...
```

**CircularString**-Instanzen verwenden weniger Punkte, um Kurvenbegrenzungen mit größerer Genauigkeit zu speichern, als **LineString**-Instanzen. **CircularString**-Instanzen sind hilfreich für das Speichern von Kreisbegrenzungen, z. B. ein Suchradius von zwanzig Meilen von einem bestimmten Punkt aus. **LineString** -Instanzen eignen sich für das Speichern von linearen Grenzen, z. B. ein Häuserblock.  

### <a name="linestring-and-compoundcurve-comparison"></a>Vergleich von LineString und CompoundCurve

In den folgenden Codebeispielen ist dargestellt, wie die gleiche Abbildung mit **LineString** - und **CompoundCurve** -Instanzen gespeichert wird:

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

In den obigen Beispielen könnte die Abbildung entweder mit einer **LineString** -Instanz oder einer **CompoundCurve** -Instanz gespeichert werden.  Im nächsten Beispiel wird ein Kreisslice mithilfe eines **CompoundCurve** gespeichert:  

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');  
```  

Eine **CompoundCurve**-Instanz kann das Kreisbogensegment (2 2, 1 3, 0 2) direkt speichern, aber eine **LineString**-Instanz müsste die Kurve in mehrere kleinere Liniensegmente konvertieren.  

### <a name="circularstring-and-compoundcurve-comparison"></a>Vergleich von CircularString und CompoundCurve

Im folgenden Codebeispiel wird gezeigt, wie der Kreisslice in einer **CircularString** -Instanz gespeichert werden kann:  

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

Zum Speichern des Kreissegments mit einer **CircularString**-Instanz müssen drei Punkte für jedes Liniensegment verwendet werden. Wenn ein Zwischenpunkt nicht bekannt ist, muss er entweder berechnet werden, oder der Endpunkt des Liniensegments muss verdoppelt werden, wie im folgenden Codeausschnitt dargestellt:  

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

In **CompoundCurve** -Instanzen sind sowohl **LineString** - als auch **CircularString** -Komponenten zulässig, sodass nur zwei Punkte der Liniensegmente des Kreisslices bekannt sein müssen.  In diesem Codebeispiel wird gezeigt, wie ein **CompoundCurve** verwendet wird, um die gleiche Abbildung zu speichern:

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a>Vergleich von Polygon und CurvePolygon

**CurvePolygon** -Instanzen können beim Definieren ihrer äußeren und inneren Ringe **CircularString** - und **CompoundCurve** -Instanzen verwenden. **Polygon**-Instanzen können dies nicht.

## <a name="see-also"></a>Weitere Informationen

- [Räumliche Daten (SQL Server)](./spatial-data-sql-server.md)
- [geometry-Datentyp-Methodenverweis](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md)
- [geography-Datentyp-Methodenverweis](../../t-sql/spatial-geography/spatial-types-geography.md)
- [STNumCurves &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)
- [STNumCurves &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)
- [STGeomFromText &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stgeomfromtext-geometry-data-type.md)
- [STGeomFromText &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)