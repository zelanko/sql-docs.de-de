---
title: StDev (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a1ef1d720928298e8a44e075f45937903d178ef6
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743039"
---
# <a name="stdev-mdx"></a>Stdev (MDX)


  Gibt die Stichproben-Standardabweichung eines über einer Menge ausgewerteten numerischen Ausdrucks zurück, die mithilfe der Formel für die ausgewogene Auffüllung (geteilt durch n-1) berechnet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stdev(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **Stdev** -Funktion verwendet die ausgewogene Auffüllung Formel, während die [StdevP](../mdx/stdevp-mdx.md) Funktion der Formel für die unausgewogene Auffüllung verwendet.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Standardabweichung für Internet Order Quantity, ausgewertet über die ersten drei Monate des Kalenderjahres 2003, mithilfe der Formel für die ausgewogene Auffüllung zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS   
   Stdev   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
