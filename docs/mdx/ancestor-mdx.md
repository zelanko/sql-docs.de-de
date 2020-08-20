---
description: Ancestor (MDX)
title: Vorgänger (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9e08a0f281a9e48c3416bb00f6ee47322d554d9c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461662"
---
# <a name="ancestor-mdx"></a>Ancestor (MDX)


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
  
 *Entfernung*  
 Ein gültiger numerischer Ausdruck, der den Abstand vom angegebenen Element angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der **Vorgänger** Funktion stellen Sie der Funktion einen MDX-Element Ausdruck bereit und stellen dann entweder einen MDX-Ausdruck einer Ebene bereit, die ein Vorgänger des Members ist, oder einen numerischen Ausdruck, der die Anzahl der Ebenen oberhalb dieses Elements darstellt. Mit diesen Informationen gibt die **Vorgänger Funktion den** Vorgänger Member auf dieser Ebene zurück.  
  
> [!NOTE]  
>  Verwenden Sie zum Zurückgeben einer Menge, die das übergeordnete Element enthält, anstelle des Vorgänger Elements die Vorgänger [&#40;MDX-&#41;](../mdx/ancestors-mdx.md) Funktion.  
  
 Wenn ein Ebenenausdruck angegeben wird, gibt die **Vorgänger** Funktion den Vorgänger des angegebenen Elements auf der angegebenen Ebene zurück. Wenn sich das angegebene Element nicht innerhalb der gleichen Hierarchie wie die angegebene Ebene befindet, gibt die Funktion einen Fehler zurück.  
  
 Wenn ein Abstand angegeben wird, gibt die **Vorgänger** Funktion den Vorgänger des angegebenen Elements zurück, der die Anzahl der in der durch den Element Ausdruck angegebenen Hierarchie angegebenen Schritte ist. Ein Element kann als Element einer Attributhierarchie, einer benutzerdefinierten Hierarchie oder, in einigen Fällen, als Element einer Über-/Unterordnungshierarchie angegeben werden. 1 gibt das übergeordnete Element eines Elements und 2 das diesem übergeordnete Element (sofern vorhanden) zurück. 0 gibt das Element selbst zurück.  
  
> [!NOTE]  
>  Verwenden Sie diese Form der **Vorgänger** Funktion in Fällen, in denen die Ebene des übergeordneten Elements unbekannt ist oder nicht benannt werden kann.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
