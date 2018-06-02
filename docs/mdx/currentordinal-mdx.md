---
title: CurrentOrdinal (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 281edfa10d371c94b831319bdca528b99310a10a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578732"
---
# <a name="currentordinal-mdx"></a>CurrentOrdinal (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die aktuelle Iterationsnummer in einer Menge während einer Iteration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression.CurrentOrdinal  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Beim Durchlaufen einer Menge an, wie z. B. mit der [Filter (MDX)](../mdx/filter-mdx.md) oder [Generate (MDX)](../mdx/generate-mdx.md) Funktionen, die **CurrentOrdinal** -Funktion die Iterationsnummer zurück.  
  
## <a name="examples"></a>Beispiele  
 Das folgende einfache Beispiel zeigt wie **CurrentOrdinal** genutzt werden **generieren** gibt eine Zeichenfolge mit dem Namen jedes Elements in einer Menge mit seiner Position im Satz zurück:  
  
 `WITH SET MySet AS [Customer].[Customer Geography].[Country].MEMBERS`  
  
 `MEMBER MEASURES.CURRENTORDINALDEMO AS`  
  
 `GENERATE(MySet, CSTR(MySet.CURRENTORDINAL) + ") " + MySet.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTORDINALDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
 Die praktische Nutzen von CurrentOrdinal beschränkt sich auf sehr komplexe Berechnungen. Im folgende Beispiel gibt die Anzahl der Produkte in der Gruppe, die eindeutig sind, mithilfe der **Reihenfolge** Funktion, um die Reihenfolge der nicht leeren Tupel vor Verwendung der **Filter** Funktion. Die **CurrentOrdinal** Funktion zu vergleichen und Ausschließen von Gleichrangigkeit verwendet wird.  
  
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
  
  
