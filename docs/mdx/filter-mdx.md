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
ms.openlocfilehash: 3a70bceed4cdccf6a22f0cfea4e5093634f88f1f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68132691"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **Filter** -Funktion wertet den angegebenen logischen Ausdruck für jedes Tupel in der angegebenen Menge aus. Die-Funktion gibt eine Menge zurück, die aus jedem Tupel in der angegebenen Menge besteht, in der der logische Ausdruck **true**ergibt. Wenn keine Tupel als **true**ausgewertet werden, wird eine leere Menge zurückgegeben.  
  
 Die **Filter** -Funktion funktioniert ähnlich wie die [IIf](../mdx/iif-mdx.md) -Funktion. Die **IIf** -Funktion gibt nur eine von zwei Optionen basierend auf der Auswertung eines logischen MDX-Ausdrucks zurück, während die **Filter** Funktion eine Menge von Tupeln zurückgibt, die die angegebene Such Bedingung erfüllen. In der Tat wird die **Filter** - `IIf(Logical_Expression, Set_Expression.Current, NULL)` Funktion für jedes Tupel in der Menge ausgeführt und gibt die resultierende Menge zurück.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Filter-Funktion auf der ROWS-Achse einer Abfrage verwendet, um nur Datumsangaben zurückzugeben, bei denen Internet Sales Amount größer als 10.000 US-Dollar ist:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `FILTER(`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `,  [Measures].[Internet Sales Amount]>10000)`  
  
 `ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 Die Filter-Funktion kann auch in berechneten Elementdefinitionen verwendet werden. Im folgenden Beispiel wird die Summe des `Measures.[Order Quantity]` -Elements, aggregiert über die ersten neun Monate 2003 in der `Date` -Dimension, aus dem **Adventure Works** -Cube zurückgegeben. Die **PeriodsToDate** -Funktion definiert die Tupel in der Menge, über die die **Aggregat** Funktion ausgeführt wird. Die **Filter** -Funktion schränkt diese Tupel ein, die für das Reseller Sales Amount-Measure für den vorherigen Zeitraum zurückgegeben werden.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
