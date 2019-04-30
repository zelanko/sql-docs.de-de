---
title: HIERARCHIZE (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4478fb9657ef4577bcae8b5641f53154b2a0486c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224904"
---
# <a name="hierarchize-mdx"></a>Hierarchize (MDX)


  Ordnet die Elemente einer Menge hierarchisch an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Hierarchize** -Funktion ordnet die Elemente der angegebenen Menge in hierarchischer Reihenfolge. Die Funktion behält Duplikate immer bei.  
  
-   Wenn **POST** nicht angegeben wird, sortiert die Funktion die Elemente in einer Ebene in ihrer natürlichen Reihenfolge. Die natürliche Reihenfolge stellt die Standardsortierung der Elemente in der Hierarchie dar, wenn keine anderen Sortierbedingungen angegeben werden. Untergeordnete Elemente werden unmittelbar nach ihren übergeordneten Elementen angeordnet.  
  
-   Wenn **POST** angegeben wird, die **Hierarchize** -Funktion sortiert die Elemente einer Ebene in der Postorder-Reihenfolge. Untergeordnete Elemente gehen also den ihnen übergeordneten Elementen voran.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Drillup für das Canada-Element durchgeführt. Die **Hierarchize** Funktion wird verwendet, um die angegebenen Elemente der Menge in hierarchischer Reihenfolge zu organisieren, die erforderlich ist der **DrillUpMember** Funktion.  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 Das folgende Beispiel gibt die Summe aus der `Measures.[Order Quantity]` Elements, aggregiert über die ersten neun Monate von 2003 in die `Date` -Dimension, aus der **Adventure Works** Cube. Die **PeriodsToDate** -Funktion definiert die Tupel in der Gruppe, in dem die Aggregatfunktion ausgeführt wird. Die **Hierarchize** -Funktion ordnet die Elemente der angegebenen Menge von Elementen aus der Product-Dimension in hierarchischer Reihenfolge.  
  
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
  
  
