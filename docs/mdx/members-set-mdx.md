---
title: Members (Menge) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d3e5bb14455d2d2ea67c4187e8e1a2a420031944
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68138255"
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
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Hierarchie Ausdruck angegeben wird, gibt die **Members (Set)** -Funktion die Menge aller Elemente innerhalb der angegebenen Hierarchie zurück, ohne berechnete Elemente. Verwenden Sie zum Abrufen der Menge aller Elemente, die in einer Hierarchie berechnet werden, die [AllMembers-Funktion &#40;MDX-&#41;](../mdx/allmembers-mdx.md) .  
  
 Wenn ein Ebenenausdruck angegeben wird, gibt die **Members (Set)** -Funktion die Menge aller Elemente innerhalb der angegebenen Ebene zurück.  
  
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
  
 Im folgenden Beispiel werden die Bestellmengen im Jahr 2003 für jedes Element in der `[Product].[Products].[Product Line]`-Ebene zurückgegeben. Die **Members** -Funktion gibt eine Menge zurück, die alle Elemente in der Ebene darstellt.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
