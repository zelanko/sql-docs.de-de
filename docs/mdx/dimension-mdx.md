---
title: Dimension (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: af73d6f08432a63a207c06d361354d6e45b6a07d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577932"
---
# <a name="dimension-mdx"></a>Dimension (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Hierarchie zurück, die ein angegebenes Element, eine angegebene Ebene oder Hierarchie enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.Dimension  
  
Level syntax  
Level_Expression.Dimension  
  
Member syntax  
Member_Expression.Dimension  
  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **Dimension** -Funktion in Verbindung mit der **Namen** -Funktion verwendet, um den Hierarchienamen des angegebenen Elements zurück.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Name  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die Dimension-Funktion in Verbindung mit der Levels- und der Count-Funktion verwendet, um die Anzahl der Ebenen in der Hierarchie zurückzugeben, die das angegebene Element enthalten.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die **Dimension** -Funktion in Verbindung mit der **Elemente** und **Anzahl** -Funktion verwendet, um die Anzahl der Elemente in der Hierarchie, die das angegebene Element enthält zurückzugeben.  
  
```  
WITH member measures.x as [Product].[Product Model Lines].[Model].&[HL Road Tire].Dimension.Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anzahl &#40;Hierarchieebenen&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Anzahl &#40;festgelegt&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [Ebenen &#40;MDX&#41;](../mdx/levels-mdx.md)   
 [Mitglieder &#40;festgelegt&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
