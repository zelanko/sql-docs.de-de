---
title: Head (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 05cfcb3c23a0369f010b8440d4a27e94ffacdb21
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63125566"
---
# <a name="head-mdx"></a>Head (MDX)


  Gibt die erste angegebene Anzahl von Elementen aus einer Menge zurück, wobei doppelte Werte beibehalten werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Head(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Die **Head** Funktion gibt die angegebene Anzahl von Tupeln vom Anfang der angegebenen Menge zurück. Die Reihenfolge der Elemente wird beibehalten. Der Standardwert für Count ist 1. Wenn die angegebene Anzahl der Tupel kleiner als 1 ist die **Head** Funktion eine leere Menge zurück. Wenn die angegebene Anzahl der Tupel größer ist als die Anzahl der Tupel in der Menge, gibt die Funktion die ursprüngliche Menge zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die fünf bestverkauften Produktunterkategorien unabhängig von der Hierarchie basierend auf Reseller Gross Profit zurückgegeben. Die **Head** Funktion wird verwendet, um nur die ersten 5 Mengen aus dem Ergebnis zurückzugeben, nach dem Sortieren des Ergebnisses mithilfe der **Reihenfolge** Funktion.  
  
```  
SELECT   
[Measures].[Reseller Gross Profit] ON 0,  
Head  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,5  
   ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tail &#40;MDX&#41;](../mdx/tail-mdx.md)   
 [Element &#40;Tupel&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md)   
 [Element &#40;Member&#41; &#40;MDX&#41;](../mdx/item-member-mdx.md)   
 [Rank &#40;MDX&#41;](../mdx/rank-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
