---
title: Count (Menge) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31e048329fde26d947b7d7978ee2d364d4901b34
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285002"
---
# <a name="count-set-mdx"></a>Count (Menge) (MDX)


  Gibt die Anzahl der Zellen in einer Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Standard syntax  
Count(Set_Expression [ , ( EXCLUDEEMPTY | INCLUDEEMPTY ) ] )  
  
Alternate syntax  
Set_Expression.Count  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Count (Menge)** -Funktion ein- oder ausgeschlossen leere Zellen, abhängig von der verwendeten Syntax. Wenn die Standardsyntax verwendet wird, leere Zellen können aus- oder eingeschlossen werden mithilfe der **EXCLUDEEMPTY** oder **INCLUDEEMPTY** flags. Wird die alternative Syntax verwendet, schließt die Funktion leere Zellen immer ein.  
  
 Verwenden Sie zum Ausschließen von leerer Zellen in der Zählung einer Menge die Standardsyntax und das optionale **EXCLUDEEMPTY** Flag.  
  
> [!NOTE]  
>  Die **Count (Menge)** -Funktion zählt die leere Zellen in der Standardeinstellung. Im Gegensatz dazu die **Anzahl** -Funktion in OLE DB, die eine Menge zählt werden leere Zellen standardmäßig ausgeschlossen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Anzahl der Zellen in der Menge der Elemente bestimmt, die aus den untergeordneten Elementen der Model Name-Attributhierarchie in der Product-Dimension bestehen.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die Anzahl der Produkte in der Product-Dimension mithilfe der **DrilldownLevel** -Funktion in Verbindung mit der **Anzahl** Funktion.  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 Das folgende Beispiel gibt die Wiederverkäufer mit zurückgegangene Umsätze in Vergleich zum vorherigen Kalenderquartal, mit der **Anzahl** -Funktion in Verbindung mit der **Filter** -Funktion und eine Reihe von anderen -Funktionen. Diese Abfrage verwendet die **aggregieren** Funktion, um die Auswahl mehrerer Geography-Elemente wie z. B. für die Auswahl aus einer Dropdown-Liste in einer Clientanwendung zu unterstützen.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
   (Filter  
      (Existing(Reseller.Reseller.Reseller),  
         [Measures].[Reseller Sales Amount]   
         < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
      )  
   )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate  
   ( {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
   )  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})  
      })  
   ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,  
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
   ,[Measures].[Declining Reseller Sales])  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anzahl &#40;Dimension&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Anzahl &#40;Hierarchieebenen&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Tuple&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [Properties &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [Aggregate &#40;MDX&#41;](../mdx/aggregate-mdx.md)   
 [Filter &#40;MDX&#41;](../mdx/filter-mdx.md)   
 [PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
