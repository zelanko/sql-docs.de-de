---
title: TupleToStr (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7fb89e3529117ce83f37b83b15c3e32f9c085088
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581342"
---
# <a name="tupletostr-mdx"></a>TupleToStr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt eine Zeichenfolge im MDX-Format (Multidimensional Expressions) zurück, die einem angegebenen Tupel entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird zum Übertragen der Zeichenfolgendarstellung eines Tupels an eine externe Funktion zur Analyse verwendet. Die Zeichenfolge, die zurückgegeben wird, wird in geschweifte Klammern eingeschlossen {} und jedes Element, wenn mehr als eine nicht ausdrücklich im Tupel, definiert ist, wird durch ein Komma getrennt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Zeichenfolge ([Datum].[Kalenderjahr].&[2001],[Geography].[Geography].[Country].&[United States]) zurückgegeben:  
  
```  
WITH MEMBER Measures.x AS TupleToStr   
   (   
      ([Date].[Calendar Year].&[2001]  
         , [Geography].[Geography].[Country].&[United States]  
      )  
   )     
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die gleiche Zeichenfolge wie im vorherigen Beispiel zurückgegeben.  
  
```  
WITH SET s AS   
   {  
      ([Date].[Calendar Year].&[2001],  
         [Geography].[Geography].[Country].&[United States]  
      )   
   }  
MEMBER Measures.x AS TupleToStr ( s.Item(0) )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
