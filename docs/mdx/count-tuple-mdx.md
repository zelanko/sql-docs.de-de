---
title: Count (Tupel) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 486c68e1947bfad67bc0288751d03c6042cd7f3e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68047275"
---
# <a name="count-tuple-mdx"></a>Count (Tupel) (MDX)


  Gibt die Anzahl der Dimensionen in einem Tupel zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Gibt die Anzahl der Dimensionen in einem Tupel zurück.  
  
## <a name="example"></a>Beispiel  
 Das berechnete Measure in der folgenden Abfrage gibt den Wert 2 zurück, der die Anzahl der Hierarchien im Tupel `([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])` wiedergibt:  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzahl &#40;Dimensions&#41; &#40;MDX-&#41;](../mdx/count-dimension-mdx.md)   
 [&#40;Hierarchieebenen&#41; &#40;MDX-&#41;zählen](../mdx/count-hierarchy-levels-mdx.md)   
 [Anzahl &#40;fest geleg&#41; &#40;MDX-&#41;](../mdx/count-set-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
