---
title: Tuplerestr (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d6cde1f60274d1437517d89e48b111e9e7298b9d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097372"
---
# <a name="tupletostr-mdx"></a>TupleToStr (MDX)


  Gibt eine Zeichenfolge im MDX-Format (Multidimensional Expressions) zurück, die einem angegebenen Tupel entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion wird zum Übertragen der Zeichenfolgendarstellung eines Tupels an eine externe Funktion zur Analyse verwendet. Die zurückgegebene Zeichenfolge wird in geschweifte {} Klammern eingeschlossen, und jedes Element wird, wenn mehr als eine ausdrücklich im Tupel definiert ist, durch ein Komma getrennt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Zeichenfolge ([Date]. [ Calendar Year]. & [2001], [Geography]. [Geography]. [Land]. & [USA]):  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
