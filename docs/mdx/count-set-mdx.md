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
ms.openlocfilehash: aac2f72cc8cd91e1964fd7734b858be8215cfdd8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68047294"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **count (Set)** -Funktion schließt leere Zellen ein oder aus, je nach verwendeter Syntax. Wenn die Standard Syntax verwendet wird, können leere Zellen mithilfe der **EXCLUDEEMPTY** -bzw. **INCLUDEEMPTY** -Flags ausgeschlossen oder eingeschlossen werden. Wird die alternative Syntax verwendet, schließt die Funktion leere Zellen immer ein.  
  
 Um leere Zellen in der Anzahl einer Menge auszuschließen, verwenden Sie die Standard Syntax und das optionale **EXCLUDEEMPTY** -Flag.  
  
> [!NOTE]  
>  Die **count (Set)** -Funktion zählt standardmäßig leere Zellen. Im Gegensatz dazu schließt die **count** -Funktion in OLE DB, die einen Satz zählt, standardmäßig leere Zellen aus.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Anzahl der Zellen in der Menge der Elemente bestimmt, die aus den untergeordneten Elementen der Model Name-Attributhierarchie in der Product-Dimension bestehen.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Model Name].children.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die Anzahl der Produkte in der Product-Dimension mithilfe der **DrilldownLevel** -Funktion in Verbindung mit der **count** -Funktion gezählt.  
  
```  
Count(DrilldownLevel (   
   [Product].[Product].[Product]))  
```  
  
 Im folgenden Beispiel werden die Wiederverkäufer mit abnehmenden Verkäufen im Vergleich zum vorherigen Kalenderquartal zurückgegeben, indem die **count** -Funktion in Verbindung mit der **Filter** -Funktion und einer Reihe weiterer Funktionen verwendet wird. Diese Abfrage verwendet die **Aggregat** Funktion, um die Auswahl mehrerer geography-Elemente zu unterstützen, z. b. für die Auswahl in einer Dropdown Liste in einer Client Anwendung.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzahl &#40;Dimensions&#41; &#40;MDX-&#41;](../mdx/count-dimension-mdx.md)   
 [&#40;Hierarchieebenen&#41; &#40;MDX-&#41;zählen](../mdx/count-hierarchy-levels-mdx.md)   
 [Count &#40;Tupel&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [DrilldownLevel-&#40;MDX-&#41;](../mdx/drilldownlevel-mdx.md)   
 [AddCalculatedMembers &#40;MDX-&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Hierarchize &#40;MDX-&#41;](../mdx/hierarchize-mdx.md)   
 [Eigenschaften &#40;MDX-&#41;](../mdx/properties-mdx.md)   
 [&#40;MDX-&#41;aggregieren](../mdx/aggregate-mdx.md)   
 [&#40;MDX-&#41;Filtern](../mdx/filter-mdx.md)   
 [PrevMember &#40;MDX-&#41;](../mdx/prevmember-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
