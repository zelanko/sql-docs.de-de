---
title: Vorgänger (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e30774aa9173bfcb7851096a25363c81d7abe9f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577072"
---
# <a name="ancestor-mdx"></a>Ancestor (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Eine Funktion, die den Vorgänger eines angegebenen Elements auf einer angegebenen Ebene oder in einem angegebenen Abstand vom Element zurückgibt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Level syntax  
Ancestor(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestor(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Abstand*  
 Ein gültiger numerischer Ausdruck, der den Abstand vom angegebenen Element angibt.  
  
## <a name="remarks"></a>Hinweise  
 Mit der **Vorgänger** -Funktion, Sie stellen die Funktion einen MDX-Elementausdruck bereit und anschließend entweder einen MDX-Ausdruck einer Ebene, die sich um einen Vorgänger des Elements oder eines numerischen Ausdrucks, der die Anzahl der Ebenen oberhalb dieses Elements darstellt. Anhand dieser Informationen die **Vorgänger** Funktion gibt das Vorgängerelement auf dieser Ebene zurück.  
  
> [!NOTE]  
>  Einen Satz, enthält das Vorgängerelement, statt nur das Vorgängerelement zurückzugebenden verwenden die [Vorgänger &#40;MDX&#41; ](../mdx/ancestors-mdx.md) Funktion.  
  
 Wenn ein Ebenenausdruck angegeben wird, die **Vorgänger** Funktion gibt den Vorgänger eines angegebenen Elements auf der angegebenen Ebene zurück. Wenn sich das angegebene Element nicht innerhalb der gleichen Hierarchie wie die angegebene Ebene befindet, gibt die Funktion einen Fehler zurück.  
  
 Wenn ein Abstand angegeben ist, die **Vorgänger** Funktion gibt den Vorgänger des angegebenen Elements, das die Anzahl der Schritte, die sich in der von der im Elementausdruck angegebenen Hierarchie angegeben ist. Ein Element kann als Element einer Attributhierarchie, einer benutzerdefinierten Hierarchie oder, in einigen Fällen, als Element einer Über-/Unterordnungshierarchie angegeben werden. 1 gibt das übergeordnete Element eines Elements und 2 das diesem übergeordnete Element (sofern vorhanden) zurück. 0 gibt das Element selbst zurück.  
  
> [!NOTE]  
>  Verwenden Sie dieses Formular von der **Vorgänger** -Funktion in Fällen, in dem die Ebene des übergeordneten Elements ist unbekannt oder nicht benannt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Ebenenausdruck verwendet und Internet Sales Amount für alle Bundesstaaten in Australien sowie deren prozentualer Anteil an der Summe von Internet Sales Amount für Australien zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
   [Measures].[Internet Sales Amount],    
      Ancestor   
         (  
         [Customer].[Customer Geography].CurrentMember,  
            [Customer].[Customer Geography].[Country]  
         )  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
        [Customer].[Customer Geography].[Country].&[Australia],  
           [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird ein numerischer Ausdruck verwendet und Internet Sales Amount für alle Bundesstaaten in Australien sowie dessen prozentualer Anteil an der Summe von Internet Sales Amount für alle Länder zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   (  
      [Measures].[Internet Sales Amount],  
         Ancestor   
            ([Customer].[Customer Geography].CurrentMember, 2)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{  
   Descendants   
      (  
         [Customer].[Customer Geography].[Country].&[Australia],  
            [Customer].[Customer Geography].[State-Province], SELF   
      )  
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
