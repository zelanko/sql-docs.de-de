---
title: Members (Menge) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bd4fe92c064f4665a4b397e47a45ae5bde50f39
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742689"
---
# <a name="members-set-mdx"></a>Members (Menge) (MDX)


  Gibt die Menge der Elemente in einer Dimension, Ebene oder Hierarchie zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Hierarchieausdruck angegeben wird, die **Members (Menge)** -Funktion die Menge aller Elemente innerhalb der angegebenen Hierarchie, außer von berechneten Elementen zurück. Die Menge aller Elemente, berechnete abrufen oder verwenden Sie andernfalls in einer Hierarchie die [AllMembers &#40;MDX&#41; ](../mdx/allmembers-mdx.md) Funktion  
  
 Wenn ein Ebenenausdruck angegeben wird, die **Members (Menge)** -Funktion die Menge aller Elemente innerhalb der angegebenen Ebene zurück.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension nur eine einzige sichtbare Hierarchie enthält, kann auf die Hierarchie entweder mit dem Dimensionsnamen oder mit dem Hierarchienamen verwiesen werden, weil der Dimensionsname in diesem Szenario in seine einzige sichtbare Hierarchie aufgelöst wird. Measures.Members ist z. B. ein gültiger MDX-Ausdruck, weil er in die einzige Hierarchie in der Measures-Dimension aufgelöst wird.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Menge aller Elemente der Calendar Year-Hierarchie im Adventure Works-Cube zurückgegeben.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 Im folgenden Beispiel werden die Bestellmengen im Jahr 2003 für jedes Element in der `[Product].[Products].[Product Line]`-Ebene zurückgegeben. Die **Elemente** Funktion gibt einen Satz, der alle Elemente in der Ebene darstellt.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
