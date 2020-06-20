---
title: LineString | Microsoft-Dokumentation
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- LineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: e50d0b86-8b31-4285-be71-ad05c7712cbd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5a0f77959cfe4492eca6c38951ba2868452d41ad
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84996332"
---
# <a name="linestring"></a>LineString
  Ein `LineString` ist ein eindimensionales Objekt, das eine Sequenz aus Punkten und die sie verbindenden Liniensegmente darstellt.

## <a name="linestring-instances"></a>LineString-Instanzen
 Die nachfolgende Abbildung enthält Beispiele für `LineString`-Instanzen.

 ![Beispiele für LineString-Geometrieinstanzen](../../database-engine/media/linestring.gif "Beispiele für LineString-Geometrieinstanzen")

 Folgendes wird dargestellt:

-   Abbildung 1 zeigt eine einfache, nicht geschlossene `LineString`-Instanz.

-   Abbildung 2 zeigt eine nicht einfache, nicht geschlossene `LineString`-Instanz.

-   Abbildung 3 zeigt eine einfache, geschlossene `LineString`-Instanz und daher einen Ring.

-   Abbildung 4 zeigt eine nicht einfache, geschlossene `LineString`-Instanz und daher keinen Ring.

### <a name="accepted-instances"></a>Akzeptierte Instanzen
 Akzeptierte `LineString`-Instanzen können in eine geometry-Variable eingegeben werden. Möglicherweise sind sie jedoch keine gültigen `LineString`-Instanzen. Damit eine `LineString`-Instanz akzeptiert wird, müssen die folgenden Kriterien erfüllt sein. Die Instanz muss aus mindestens zwei Punkten gebildet werden, oder sie muss leer sein. Die folgenden LineString-Instanzen werden akzeptiert.

```
DECLARE @g1 geometry = 'LINESTRING EMPTY';
DECLARE @g2 geometry = 'LINESTRING(1 1,2 3,4 8, -6 3)';
DECLARE @g3 geometry = 'LINESTRING(1 1, 1 1)';
```

 `@g3` zeigt, dass eine `LineString`-Instanz zwar akzeptiert werden kann, dass sie möglicherweise jedoch nicht gültig ist.

 Die folgende `LineString`-Instanz wird nicht akzeptiert. Sie löst eine `System.FormatException`aus.

```
DECLARE @g geometry = 'LINESTRING(1 1)';
```

### <a name="valid-instances"></a>Gültige Instanzen
 Damit eine `LineString`-Instanz gültig ist, muss sie die folgenden Kriterien erfüllen.

1.  Die `LineString`-Instanz muss akzeptiert sein.

2.  Wenn eine `LineString`-Instanz nicht leer ist, muss sie mindestens zwei unterschiedliche Punkte enthalten.

3.  Die `LineString`-Instanz kann sich über ein Intervall von zwei oder mehr aufeinanderfolgenden Punkten nicht selbst überschneiden.

 Die folgenden `LineString`-Instanzen sind gültig.

```
DECLARE @g1 geometry= 'LINESTRING EMPTY';
DECLARE @g2 geometry= 'LINESTRING(1 1, 3 3)';
DECLARE @g3 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0)';
DECLARE @g4 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();

```

 Die folgenden `LineString`-Instanzen sind nicht gültig.

```
DECLARE @g1 geometry = 'LINESTRING(1 4, 3 4, 2 4, 2 0)';
DECLARE @g2 geometry = 'LINESTRING(1 1, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

> [!WARNING]
>  Die Erkennung von `LineString`-Überschneidungen basiert auf Gleitkommaberechnungen, die nicht genau sind.

## <a name="examples"></a>Beispiele
 Das folgende Beispiel zeigt, wie eine `geometry``LineString` -Instanz aus drei Punkten und mit der SRID 0 (null) erstellt wird:

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1, 2 4, 3 9)', 0);
```

 Jeder Punkt in der `LineString` -Instanz kann Z- (Erweiterung) und M-Werte (Measure) enthalten. In diesem Beispiel werden M-Werte zur `LineString` -Instanz hinzugefügt, die im Beispiel weiter oben erstellt wurde. M und Z können NULL-Werte sein.

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1 NULL 0, 2 4 NULL 12.3, 3 9 NULL 24.5)', 0);
```

 Im folgenden Beispiel wird veranschaulicht, wie eine `geometry LineString` -Instanz mit zwei Punkten erstellt wird, die identisch sind. Ein Aufruf von `IsValid` gibt an, dass die `LineString`-Instanz nicht gültig ist, und durch einen Aufruf von `MakeValid` wird die `LineString`-Instanz in einen `Point` konvertiert.

```sql
DECLARE @g geometry
SET @g = geometry::STGeomFromText('LINESTRING(1 3, 1 3)',0);
IF @g.STIsValid() = 1
  BEGIN
     SELECT @g.ToString() + ' is a valid LineString.';  
  END
ELSE
  BEGIN
     SELECT @g.ToString() + ' is not a valid LineString.';
     SET @g = @g.MakeValid();
     SELECT @g.ToString() + ' is a valid Point.';  
  END

```

 Der obige Codeausschnitt gibt Folgendes zurück:

```
LINESTRING(1 3, 1 3) is not a valid LineString
POINT(1 3) is a valid Point.
```

## <a name="see-also"></a>Weitere Informationen
 [STLength &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;Geometry](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) -Datentyp&#41;[STEndpoint &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry-Datentyp](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)&#41;[STNumPoints &#40;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)&#41;der geometry-Datentyp &#40;[STIsRing](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)&#41;&#40;der geometry-Datentyp&#41;&#40;der geometry-Datentyp [&#41;&#40;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) für [räumliche Daten](../spatial/spatial-data-sql-server.md) SQL Server&#41;


