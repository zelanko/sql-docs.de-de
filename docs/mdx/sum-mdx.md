---
description: Sum (MDX)
title: Sum (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f65525836157f5ac106cfa7ba0d5458689583def
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449622"
---
# <a name="sum-mdx"></a>Sum (MDX)


  Gibt die Summe eines numerischen Ausdrucks zurück, der für eine angegebene Menge ausgewertet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Sum( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Mengenausdruck (Multidimensional Expressions).  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein numerischer Ausdruck angegeben ist, wird der angegebene numerische Ausdruck über die Menge ausgewertet und anschließend die Summe gebildet. Wenn kein numerischer Ausdruck angegeben ist, wird die angegebene Menge im aktuellen Kontext der Elemente der Menge ausgewertet und anschließend die Summe gebildet. Wenn die SUM-Funktion auf einen nicht numerischen Ausdruck angewendet wird, sind die Ergebnisse nicht definiert.  
  
> [!NOTE]  
>  Analysis Services ignoriert Nullen, wenn die Summe einer Menge von Zahlen berechnet wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Summe von Reseller Sales Amounts für alle Elemente der Product.Category-Attributhierarchie für die Kalenderjahre 2001 und 2002 zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS SUM  
   ( { [Date].[Calendar Year].&[2001]  
         , [Date].[Calendar Year].&[2002] }  
      , [Measures].[Reseller Sales Amount]  
    )  
SELECT Measures.x ON 0  
,[Product].[Category].Members ON 1  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die Summe der Monat-bis-Datum-Frachtkosten für Internetverkäufe für den Monat Juli 2002 bis einschließlich 20. Juli zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird das with Member-Schlüsselwort und die **Sum** -Funktion verwendet, um ein berechnetes Element in der Measures-Dimension zu definieren, das die Summe des Reseller Sales Amount-Measures für die Kanadas-und USA-Member der Country-Attribut Hierarchie in der Geography-Dimension enthält.  
  
```  
WITH MEMBER Measures.NorthAmerica AS SUM   
      (  
         {[Geography].[Country].&[Canada]  
            , [Geography].[Country].&[United States]}  
       ,[Measures].[Reseller Sales Amount]  
      )  
SELECT {[Measures].[NorthAmerica]} ON 0,  
[Product].[Category].members ON 1  
FROM [Adventure Works]  
```  
  
 Häufig wird die **Sum** -Funktion mit der **CurrentMember** -Funktion oder Funktionen wie **YTD** verwendet, die eine Menge zurückgeben, die abhängig vom CurrentMember einer Hierarchie variiert. Die folgende Abfrage gibt z. B. die Summe der Internet Sales Amount-Measure für alle Datumsangaben ab Beginn des Kalenderjahrs bis zu dem Datum an, das auf der Zeilenachse angezeigt wird:  
  
 `WITH MEMBER MEASURES.YTDSUM AS`  
  
 `SUM(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDSUM} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
