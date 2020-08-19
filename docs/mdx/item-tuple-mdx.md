---
description: Item (Tupel) (MDX)
title: Item (Tupel) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1e98e6901c018a6c8be5187024e5462cc8d19547
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483953"
---
# <a name="item-tuple-mdx"></a>Item (Tupel) (MDX)


  Gibt ein Tupel aus einer Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Index syntax  
Set_Expression.Item(Index)  
  
String expression syntax  
Set_Expression.Item(String_Expression1 [ ,String_Expression2,...n])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *String_Expression1*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich normalerweise um ein als Zeichenfolge ausgedrücktes Tupel handelt.  
  
 *String_Expression2*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich normalerweise um ein als Zeichenfolge ausgedrücktes Tupel handelt.  
  
 *Index*  
 Ein gültiger numerischer Ausdruck, der ein bestimmtes Tupel über die Position in der zurückzugebenden Menge angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Item** -Funktion gibt ein Tupel aus der angegebenen Menge zurück. Es gibt drei Möglichkeiten, die **Item** -Funktion aufzurufen:  
  
-   Wenn ein einzelner Zeichen folgen Ausdruck angegeben wird, gibt die **Item** -Funktion das angegebene Tupel zurück. Beispiel: "([2005].Q3, [Store05])".  
  
-   Wenn mehr als ein Zeichen folgen Ausdruck angegeben wird, gibt die **Item** -Funktion das von den angegebenen Koordinaten definierte Tupel zurück. Die Anzahl der Zeichenfolgen muss der Anzahl der Achsen entsprechen, und jede Zeichenfolge muss eine eindeutige Hierarchie identifizieren. Beispiel: "[2005].Q3", "[Store05]".  
  
-   Wenn eine ganze Zahl angegeben wird, gibt die **Item** -Funktion das Tupel zurück, das sich an der durch den *Index*angegebenen Null basierten Position befindet.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ([1996],Sales) zurückgegeben:  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 Im folgenden Beispiel wird ein Ebenenausdruck verwendet und Internet Sales Amount für alle Bundesstaaten in Australien sowie deren prozentualer Anteil an der Summe von Internet Sales Amount für Australien zurückgegeben. In diesem Beispiel wird die Item-Funktion verwendet, um das erste (und einzige Tupel) aus der von der **Vorgänger Funktion zurück** gegebenen Menge zu extrahieren.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],    
      Ancestors   
      ( [Customer].[Customer Geography].CurrentMember,  
        [Customer].[Customer Geography].[Country]  
      ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{ Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],  
     [Customer].[Customer Geography].[State-Province], SELF   
   )   
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
