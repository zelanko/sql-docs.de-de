---
title: Hierarchize (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8ab2c866f201c53684c316282a143b4f672cb8e9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105436"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **Hierarchize** -Funktion organisiert die Elemente der angegebenen Menge in hierarchischer Reihenfolge. Die Funktion behält Duplikate immer bei.  
  
-   Wenn **Post** nicht angegeben wird, sortiert die Funktion Elemente in der natürlichen Reihenfolge in einer Ebene. Die natürliche Reihenfolge stellt die Standardsortierung der Elemente in der Hierarchie dar, wenn keine anderen Sortierbedingungen angegeben werden. Untergeordnete Elemente werden unmittelbar nach ihren übergeordneten Elementen angeordnet.  
  
-   Wenn **Post** angegeben wird, sortiert die **Hierarchize** -Funktion die Elemente in einer Ebene in der Post-Natural-Reihenfolge. Untergeordnete Elemente gehen also den ihnen übergeordneten Elementen voran.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Drillup für das Canada-Element durchgeführt. Die **Hierarchize** -Funktion wird verwendet, um die angegebenen Satz Elemente in hierarchischer Reihenfolge zu organisieren, die für die **DrillupMember** -Funktion erforderlich ist.  
  
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
  
 Im folgenden Beispiel wird die Summe des `Measures.[Order Quantity]` -Elements, aggregiert über die ersten neun Monate 2003 in der `Date` -Dimension, aus dem **Adventure Works** -Cube zurückgegeben. Die **PeriodsToDate** -Funktion definiert die Tupel in der Menge, über die die Aggregatfunktion ausgeführt wird. Die **Hierarchize** -Funktion organisiert die Member der angegebenen Menge von Elementen aus der Product-Dimension in hierarchischer Reihenfolge.  
  
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
  
  
