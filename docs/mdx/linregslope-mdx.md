---
title: LinRegSlope (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 108156c215840162bc93152db20a35f666c093bf
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579032"
---
# <a name="linregslope-mdx"></a>LinRegSlope (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Berechnet die lineare Regression einer Menge und gibt den Wert des Regressionskoeffizienten in der regressionsgleichung y = Ax + b.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LinRegSlope(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression_y*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die Y-Achse dar.  
  
 *Numeric_Expression_x*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die X-Achse dar.  
  
## <a name="remarks"></a>Hinweise  
 Die lineare Regression berechnet mit der Methode der kleinsten Quadrate die Gleichung einer Regressionsgeraden (d. h. der Ausgleichsgeraden für eine Reihe von Punkten). Die Regressionszeile hat die folgende Gleichung, in denen eine die Neigung und b das Konstante Glied:  
  
 y = ax+b  
  
 Die **LinRegSlope** Funktion wertet die angegebene Menge für den ersten numerischen Ausdruck aus, um die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion den angegebenen Mengenausdruck für den zweiten numerischen Ausdruck, sofern angegeben, aus, um die Werte für die X-Achse zu erhalten. Wenn kein zweiter numerischer Ausdruck angegeben wird, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die X-Achse. Das x-Achsen-Argument nicht angeben wird häufig mit der Time-Dimension verwendet.  
  
 Nach dem Erhalt des Satzes von Punkten, die **LinRegSlope** Funktion gibt den Regressionskoeffizienten der Regressionszeile (einer in der vorherigen Formel).  
  
> [!NOTE]  
>  Die **LinRegSlope** Funktion ignoriert leere Zellen oder Zellen, die Text oder logische Werte enthalten. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Wert für den Regressionskoeffizienten einer Regressionsgeraden für die Unit Sales- und Store Sales-Measures zurückgegeben.  
  
```  
LinRegSlope(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
