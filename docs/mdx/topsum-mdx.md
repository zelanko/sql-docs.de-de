---
description: TopSum (MDX)
title: TopSum (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 665a1ace9df98303da19b861cdd3ce6340ec8368
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412907"
---
# <a name="topsum-mdx"></a>TopSum (MDX)


  Sortiert eine Menge und gibt die obersten Elemente zurück, deren kumulative Summe mindestens einem angegebenen Wert entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TopSum(Set_Expression, Value, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Wert*  
 Ein gültiger numerischer Ausdruck, der den Wert angibt, mit dem die Tupel verglichen werden.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) handelt, der ein Measure zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **TopSum** -Funktion berechnet die Summe eines angegebenen Measures, die für eine angegebene Menge ausgewertet wurde, und sortiert die Menge in absteigender Reihenfolge. Anschließend gibt die Funktion die Elemente mit den höchsten Werten zurück, deren Gesamtwert des angegebenen numerischen Ausdrucks mindestens dem angegebenen Wert entspricht. Diese Funktion gibt die kleinste Teilmenge einer Menge zurück, deren kumulativer Gesamtwert mindestens dem angegebenen Wert entspricht. Die zurückgegebenen Elemente werden der Größe nach absteigend sortiert.  
  
> [!IMPORTANT]  
>  Wie die [BottomSum](../mdx/bottomsum-mdx.md) -Funktion unterbricht die **TopSum** -Funktion immer die Hierarchie.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird für die Bike-Kategorie die kleinste Menge der Elemente der City-Ebene in der Geography-Hierarchie in der Geography-Dimension zurückgegeben, deren kumulativer Gesamtwert bezüglich des Reseller Sales Amount-Measures mindestens einer Summe von 6.000.000 (beginnend mit den Elementen dieser Menge, die den höchsten Umsatz aufweisen) entspricht.  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopSum  
   ({[Geography].[Geography].[City].Members}  
   , 6000000  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].Bikes)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
