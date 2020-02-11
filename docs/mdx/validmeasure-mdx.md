---
title: ValidMeasure (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b3bce4baf3dc3499621f67defd40a4579e9cd460
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037951"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **ValidMeasure** -Funktion gibt den Wert eines Tupels zurück, wobei Attribute ignoriert werden, die keine Beziehung zur Measure-Gruppe des Measures aufweisen, dessen Wert das Tupel zurückgibt. Ein Attribut kann aus zwei Gründen mit einem Measure nicht verbunden sein:  
  
-   Die Dimension des Attributs verfügt über keine Beziehung mit der Measuregruppe des Measure im Tupel.  
  
-   Die Dimension des Attributs verfügt über keine Beziehung mit der Measuregruppe im Measure, aber das Granularitätsattribut ist nicht das Schlüsselattribut, und das Granularitätsattribut verfügt über keine direkte Beziehung mit dem Attribut im Tupel.  
  
 Das von dieser Funktion angegebene Verhalten entspricht dem serverseitigen Standardverhalten und wird von der **IgnoreUnrelatedDimensions** -Eigenschaft für das Measure Group-Objekt gesteuert.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
