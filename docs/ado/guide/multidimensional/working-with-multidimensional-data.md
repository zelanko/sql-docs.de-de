---
title: Arbeiten mit mehrdimensionalen Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- multidimensional data [ADO]
ms.assetid: 84387746-aa3e-44fd-ad6c-a8214a6966dc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: afe8ff8c788a740ca98eca385146ecc71b6e1e95
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704395"
---
# <a name="working-with-multidimensional-data"></a>Arbeiten mit mehrdimensionalen Daten
Ein *Cellset* ist das Ergebnis einer Abfrage auf mehrdimensionalen Daten. Es besteht aus einer Auflistung von Achsen, in der Regel nicht mehr als vier Achsen und in der Regel nur zwei oder drei. Ein *Achse* ist eine Sammlung von Elementen aus einer oder mehreren Dimensionen, die zum Suchen oder Filtern von bestimmten Werten in einem Cube verwendet wird.  
  
 Ein *Position* ist ein Punkt auf einer Achse. Für eine Achse, bestehend aus einer einzelnen Dimensions sind diese Positionen für eine Teilmenge der Dimensionselemente. Wenn eine Achse besteht aus mehr als eine Dimension, und klicken Sie dann jede Position ist eine zusammengesetzte Entität, die *n* Teile Where *n* ist die Anzahl der Dimensionen, die entlang dieser Achse ausgerichtet. Jeder Teil der Position ist ein Element aus einer einzelnen Dimension.  
  
 Z. B. wenn die geografischen Daten und Dimensionen aus einem Cube mit Verkaufsdaten entlang der x-Achse eines cellSets ausgerichtet werden, kann eine Position entlang dieser Achse Member "USA" und "Computer". enthalten In diesem Beispiel erfordert eine Position entlang der x-Achse zu bestimmen, dass Elemente aus jeder Dimension auf der Achse ausgerichtet werden.  
  
 Ein *Zelle* ist ein Objekt, positioniert am Schnittpunkt der Achsenkoordinaten. Jede Zelle verfügt über mehrere Informationspakete zugeordnet, wie z.B. die Daten selbst eine formatierte Zeichenfolge (die anzeigbarer Form von Zellendaten) und den Ordnungswert der Zelle. (Jede Zelle ist eine eindeutige Ordinalwert im Cellset dar. Der Ordinalwert des ersten Zelle in das Cellset ist 0 (null), während die äußerste linke Zelle in der zweiten Zeile eines cellSets mit acht Spalten einen Ordnungswert des acht müssten.)  
  
 Ein Cube enthält beispielsweise die folgenden sechs Dimensionen (Beachten Sie, dass diese Cubeschema von den in dem Beispiel geringfügig [Übersicht über multidimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)):  
  
-   Vertriebsmitarbeiter  
  
-   Geography (natürliche Hierarchie) – Kontinente, Länder, Status usw.  
  
-   Viertel-Quartale, Monate, Tage  
  
-   Years  
  
-   Measures - Prozent, Verkäufe BudgetedSales  
  
-   Products  
  
 Das folgende Cellset stellt Umsatz für 1991 für alle Produkte dar:  
  
> [!NOTE]
>  Die Zellenwerte im Beispiel können als Paare von Achse Position Ordnungszahlen angezeigt werden, wobei die erste Ziffer Position auf der x-Achse und die zweite Zahl die Position der y-Achse darstellt.  
  
 Die Merkmale dieser Cellset lauten wie folgt aus:  
  
-   Achsendimensionen: Quartale Vertriebsmitarbeiters Geography  
  
-   Filterdimensionen: Measures, Jahren Produkte  
  
-   Zwei Achsen: Spalten-(X oder Achse 0) und (Achse 1 oder y)  
  
-   x-Achse: zwei geschachtelte Dimensionen "," Vertriebsmitarbeiter "und" Geography  
  
-   y-Achse: Viertel-dimension  
  
 Die x-Achse besitzt zwei geschachtelten Dimensionen: Verkäufer "und" Geography ". Von Geography sind vier Elemente ausgewählt: Seattle, Boston, USA Süd und Japan. Es werden zwei Elemente von Vertriebsmitarbeiter ausgewählt: Valentine und Nash. Dies ergibt insgesamt acht Positionen auf dieser Achse (8 = 4 * 2).  
  
 Die einzelnen Koordinaten werden als eine Position mit zwei Membern - eine von der Vertriebsmitarbeiter-Dimension und eine andere von der Geography-Dimension dargestellt:  
  
```console
(Valentine, Seattle), (Valentine, Boston), (Valentine, USA_North),  
(Valentine, Japan), (Nash, Seattle), (Nash, Boston), (Nash, USA_North),  
(Nash, Japan)  
```  
  
 Die y-Achse enthält nur eine Dimension mit den folgenden acht Positionen:  
  
```console
Jan, Feb, Mar, Qtr2, Qtr3, Oct, Nov, Dec  
```  
  
 CellSets, Zellen, Achsen und Positionen werden alle durch die entsprechenden Objekte in ADO MD dargestellt: [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md), [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md), und [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (Multidimensional) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Übersicht über multidimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)
