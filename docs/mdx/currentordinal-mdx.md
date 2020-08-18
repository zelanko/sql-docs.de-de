---
description: CurrentOrdinal (MDX)
title: CurrentOrdinal (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 68119266fd9460a28e036914fce036ec165e553a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413156"
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
  
## <a name="remarks"></a>Bemerkungen  
 Beim Durchlaufen einer Menge, wie z. b. mit den [Filter (MDX)](../mdx/filter-mdx.md) -oder [Generate (MDX)](../mdx/generate-mdx.md) -Funktionen, gibt die **CurrentOrdinal** -Funktion die Iterations Nummer zurück.  
  
## <a name="examples"></a>Beispiele  
 Das folgende einfache Beispiel zeigt, wie **CurrentOrdinal** mit **Generate** verwendet werden kann, um eine Zeichenfolge mit dem Namen der einzelnen Elemente in einer Menge zusammen mit der Position in der Menge zurückzugeben:  
  
 `WITH SET MySet AS [Customer].[Customer Geography].[Country].MEMBERS`  
  
 `MEMBER MEASURES.CURRENTORDINALDEMO AS`  
  
 `GENERATE(MySet, CSTR(MySet.CURRENTORDINAL) + ") " + MySet.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTORDINALDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
 Die praktische Nutzen von CurrentOrdinal beschränkt sich auf sehr komplexe Berechnungen. Im folgenden Beispiel wird die Anzahl der Produkte in der Menge zurückgegeben, die eindeutig sind. dabei wird die **Order** -Funktion verwendet, um die nicht leeren Tupel vor der Verwendung der **Filter** Funktion zu sortieren. Die **CurrentOrdinal** -Funktion wird zum Vergleichen und Entfernen von Beziehungen verwendet.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
