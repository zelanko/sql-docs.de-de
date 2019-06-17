---
title: CurrentOrdinal (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d6fe956591b6bde0c5e6b074115fec8724995a59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248197"
---
# <a name="currentordinal-mdx"></a>CurrentOrdinal (MDX)


  Gibt die aktuelle Iterationsnummer in einer Menge während einer Iteration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression.CurrentOrdinal  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Beim Durchlaufen der einen Satz an, wie z. B. mit der [Filter (MDX)](../mdx/filter-mdx.md) oder [Generate (MDX)](../mdx/generate-mdx.md) Funktionen, die **CurrentOrdinal** Funktion gibt die Iterationsnummer zurück.  
  
## <a name="examples"></a>Beispiele  
 Das folgende einfache Beispiel zeigt wie **CurrentOrdinal** kann verwendet werden, mit **generieren** gibt eine Zeichenfolge, die mit dem Namen jedes Elements in einem Satz mit seiner Position in der Gruppe zurück:  
  
 `WITH SET MySet AS [Customer].[Customer Geography].[Country].MEMBERS`  
  
 `MEMBER MEASURES.CURRENTORDINALDEMO AS`  
  
 `GENERATE(MySet, CSTR(MySet.CURRENTORDINAL) + ") " + MySet.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTORDINALDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
 Die praktische Nutzen von CurrentOrdinal beschränkt sich auf sehr komplexe Berechnungen. Das folgende Beispiel gibt die Anzahl der Produkte in der Gruppe, die eindeutig ist, mit der **Reihenfolge** Funktion, um die Reihenfolge der nicht leeren Tupel vor Verwendung der **Filter** Funktion. Die **CurrentOrdinal** Funktion zum Vergleichen und Ausschließen von Gleichrangigkeit verwendet wird.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , NOT((OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          ))  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
