---
title: LinRegPoint (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cc47b5910f0d5323b1b7e29cd3313b36d615265c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63136074"
---
# <a name="linregpoint-mdx"></a>LinRegPoint (MDX)


  Berechnet die lineare Regression einer Menge und gibt den Wert des der *y-Achsenabschnitt* in der regressionsgleichung y = Ax + b für einen bestimmten Wert von X.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LinRegPoint(Slice_Expression_x, Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Slice_Expression_x*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die Slicerachse dar.  
  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression_y*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die Y-Achse dar.  
  
 *Numeric_Expression_x*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die X-Achse dar.  
  
## <a name="remarks"></a>Hinweise  
 Die lineare Regression berechnet mit der Methode der kleinsten Quadrate die Gleichung einer Regressionsgeraden (d. h. der Ausgleichsgeraden für eine Reihe von Punkten). Die Regressionszeile hat die folgende Gleichung, in denen eine die Neigung und b ist das Konstante Glied:  
  
 y = ax+b  
  
 Die **LinRegPoint** Funktion wertet die angegebene Menge für den zweiten numerischen Ausdruck aus, um die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion die angegebene Menge für den dritten numerischen Ausdruck, sofern angegeben, aus, um die Werte für die X-Achse zu erhalten. Wenn kein dritter numerischer Ausdruck angegeben wird, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die X-Achse. Das x-Achsen-Argument nicht angegeben, wird häufig mit der Time-Dimension verwendet.  
  
 Nach Abschluss der Berechnung der linearen Regressionsgeraden wird das Ergebnis der Gleichung für den ersten numerischen Ausdruck berechnet und zurückgegeben.  
  
> [!NOTE]  
>  Die **LinRegPoint** Funktion ignoriert leere Zellen oder Zellen, die Text enthalten. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der vorhergesagte Wert für Unit Sales für die vergangenen 10 Zeiträume basierend auf den statistischen Beziehungen zwischen Unit Sales und Store Sales zurückgegeben.  
  
```  
LinRegPoint([Measures].[Unit Sales],LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
