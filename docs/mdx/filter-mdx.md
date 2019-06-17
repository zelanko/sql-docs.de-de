---
title: Filter (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d740148052712a69a39e0de314496733b3b26a8b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63154631"
---
# <a name="filter-mdx"></a>Filter (MDX)


  Filtert eine angegebene Menge basierend auf einer Suchbedingung und gibt dann das Resultset zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Filter(Set_Expression, Logical_Expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Logical_Expression*  
 Ein gültiger logischer MDX-Ausdruck (Multidimensional Expressions), dessen Auswertung TRUE oder FALSE ergibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Filter** -Funktion wertet den angegebenen logischen Ausdruck für jedes Tupel in der angegebenen Menge. Die Funktion gibt einen Satz, der jedes Tupel in der angegebenen Menge besteht, in dem der logische Ausdruck wird zu **"true"** . Wenn kein Tupel ausgewertet **"true"** , ein leerer Satz zurückgegeben wird.  
  
 Die **Filter** Funktion funktioniert auf ähnliche Weise die [IIf](../mdx/iif-mdx.md) Funktion. Die **IIf** Funktionsergebnis ist nur eine der beiden Optionen, die zwar auf Grundlage der Auswertung eines logischen MDX-Ausdrucks, der **Filter** Funktionsergebnis ist eine Menge von Tupeln, die die angegebene Suchbedingung erfüllen. Tatsächlich die **Filter** Funktion führt `IIf(Logical_Expression, Set_Expression.Current, NULL)` für jedes Tupel in der Menge aus und gibt das sich ergebende Menge zurück.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Filter-Funktion auf der ROWS-Achse einer Abfrage verwendet, um nur Datumsangaben zurückzugeben, bei denen Internet Sales Amount größer als 10.000 US-Dollar ist:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Die Filter-Funktion kann auch in berechneten Elementdefinitionen verwendet werden. Das folgende Beispiel gibt die Summe aus der `Measures.[Order Quantity]` Elements, aggregiert über die ersten neun Monate von 2003 in die `Date` -Dimension, aus der **Adventure Works** Cube. Die **PeriodsToDate** -Funktion definiert die Tupel in der Gruppe, in dem die **aggregieren** -Funktion arbeitet. Die **Filter** -Funktion beschränkt die Tupel auf solche, die niedrigere Werte für das Reseller Sales Amount-Measure für den vorherigen Zeitraum zurückgegeben wird.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
