---
title: ValidMeasure (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ddcc65d93ebd9d1ea1e9465b40fe1e6027834e37
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743700"
---
# <a name="validmeasure-mdx"></a>ValidMeasure (MDX)


  Gibt den Wert eines Measures in einem Cube zurück, indem beim Zurückgeben des Ergebnisses für ein angegebenes Tupel für nicht passende Dimensionen ihre Alle-Ebene (oder, wenn nicht aggregierbar, ihr Standardelement) erzwungen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ValidMeasure(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **ValidMeasure** Funktion gibt den Wert eines Tupels, ignoriert Attribute, die keine Beziehung mit der Measuregruppe des Measures, dessen Wert verfügen das Tupel zurückgibt. Ein Attribut kann aus zwei Gründen mit einem Measure nicht verbunden sein:  
  
-   Die Dimension des Attributs verfügt über keine Beziehung mit der Measuregruppe des Measure im Tupel.  
  
-   Die Dimension des Attributs verfügt über keine Beziehung mit der Measuregruppe im Measure, aber das Granularitätsattribut ist nicht das Schlüsselattribut, und das Granularitätsattribut verfügt über keine direkte Beziehung mit dem Attribut im Tupel.  
  
 Das Verhalten dieser Funktion ist das Standardverhalten für die serverseitige und wird gesteuert, indem die **IgnoreUnrelatedDimensions** -Eigenschaft für das measuregruppenobjekt.  
  
 Für alle Attribute im angegebenen Tupel mit Granularität (wenn das Element im Tupel nicht das Alle-Element ist) wird die aktuelle Koordinate für jedes einzelne dieser Attribute wie folgt verschoben:  
  
-   Mit dem angegebenen Attributelement verknüpfte Attribute werden zu dem zusammen mit dem aktuellen Element vorhandenen Element verschoben.  
  
-   Mit dem angegebenen Attributelement verknüpfende Attribute werden zum Alle-Element verschoben (oder zum Standardelement, wenn die Hierarchie nicht aggregierbar ist).  
  
-   Nicht verknüpfte Attribute werden (Measure-basiert) zum Alle-Element verschoben.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage zeigt, wie die ValidMeasure-Funktion verwendet werden kann, um das Verhalten der IgnoreUnrelatedDimensions-Eigenschaft zu überschreiben. Im Adventure Works-Cube ist IgnoreUnrelatedDimensions für die Sales Targets-Measuregruppe auf False festgelegt; da die Date-Dimension bei der Kalenderquartalsgranularität zu dieser Measuregruppe verknüpft, bedeutet dies, dass das Sales Quota-Measure unter Kalenderquartal standardmäßig NULL zurückgibt (obwohl es auch eine Berechnung im MDX-Skript gibt, das Werte bis hinunter zur Monatsebene zuordnet). Die ValidMeasure-Funktion in einem berechneten Measure kann verwendet werden, um ein Verhalten für das Sales Quota-Measure zu bewirken, als ob IgnoreUnrelatedDimensions auf True festgelegt wurde und Sales Quota zwingt, den Wert des aktuellen Kalenderquartals anzuzeigen.  
  
```  
WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])  
SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,  
[Date].[Calendar].MEMBERS ON 1  
FROM [Adventure Works]  
```  
  
 Auf ähnliche Weise hat das Sales Targets-Measure keine Beziehung mit der Promotion-Dimension; unterhalb des Alle-Elements jeder Hierarchie auf Promotion gibt es NULL zurück. Dieses Verhalten kann ebenfalls mittels ValidMeasure geändert werden:  
  
 `WITH MEMBER MEASURES.VTEST AS VALIDMEASURE([Measures].[Sales Amount Quota])`  
  
 `SELECT {[Measures].[Sales Amount Quota], MEASURES.VTEST} ON 0,`  
  
 `[Promotion].[Promotions].members ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
