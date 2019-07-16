---
title: BottomCount-Funktion (Multidimensional Expressions) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bd09c823e09270ebf7c9851b3c6760baf720db39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016947"
---
# <a name="bottomcount-mdx"></a>BottomCount (MDX)


  Sortiert eine Menge in aufsteigender Reihenfolge und gibt die angegebene Anzahl von Tupeln in der angegebenen Menge mit den niedrigsten Werten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BottomCount(Set_Expression, Count [,Numeric_Expression])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Ausdruck angegeben wird, sortiert die Funktion die Tupel in der angegebenen Menge nach dem Wert des angegebenen Ausdrucks, ausgewertet über die Menge, in aufsteigender Reihenfolge. Die **BottomCount** Funktion gibt dann die angegebene Anzahl von Tupeln mit dem niedrigsten Wert zurück.  
  
> [!IMPORTANT]  
>  Die **BottomCount** ordnungsgemäß verwendet werden, wie z. B. die [TopCount](../mdx/topcount-mdx.md) funktionieren, unterbricht immer die Hierarchie.  
  
 Wenn ein numerischer Ausdruck nicht angegeben wird, die Funktion gibt die Menge der Elemente in natürlicher Reihenfolge ohne Sortierung, verhält, wie die [Tail (MDX)](../mdx/tail-mdx.md) Funktion.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Reseller Order Quantity-Measure für jedes Kalenderjahr für die fünf geringsten Product SubCategory-Umsätze in der vom Reseller Sales Amount-Measure vorgegebenen Reihenfolge zurückgegeben.  
  
```  
SELECT BottomCount([Product].[Product Categories].[Subcategory].Members  
   , 10  
   , [Measures].[Reseller Sales Amount]) ON 0,  
   [Date].[Calendar].[Calendar Year].Members ON 1  
  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Reseller Order Quantity]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
