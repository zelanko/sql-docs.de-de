---
title: Linregvarianz (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b45328614bbefe730c815f528e82f220ad0093e9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905514"
---
# <a name="linregvariance-mdx"></a>LinRegVariance (MDX)


  Berechnet die lineare Regression einer Menge und gibt die Varianz zurück, die der Regressions Zeile zugeordnet ist, y = ax + b.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LinRegVariance(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression_y*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die Y-Achse dar.  
  
 *Numeric_Expression_x*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die X-Achse dar.  
  
## <a name="remarks"></a>Hinweise  
 Die lineare Regression berechnet mit der Methode der kleinsten Quadrate die Gleichung einer Regressionsgeraden (d. h. der Ausgleichsgeraden für eine Reihe von Punkten). Die Regressionslinie weist die folgende Gleichung auf, wobei a für die Steigung und b das Abfangen ist:  
  
 y = ax+b  
  
 Die **linregvarianz** -Funktion wertet das angegebene Seton für den ersten numerischen Ausdruck aus, um die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion die angegebene Mengefür den zweiten numerischen Ausdruck, sofern angegeben, aus, um die Werte für die X-Achse zu erhalten. Wenn das zweite numerische expressionis nicht angegeben ist, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die x-Achse. Wenn Sie das Argument der x-Achse nicht angeben, wird es häufig mit der Time-Dimension verwendet.  
  
 Nach dem Abrufen des Satzes von Punkten gibt die **linregvarianz** -Funktion die statistische Varianz zurück, die die Anpassung der linearen Gleichung an die Punkte beschreibt.  
  
> [!NOTE]  
>  Die **linregvarianz** -Funktion ignoriert leere Zellen oder Zellen, die Text oder logische Werte enthalten. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die statistische Varianz zurückgegeben, die die Übereinstimmung der linearen Gleichung mit den Punkten für die Unit Sales- und die Store Sales-Measures beschreibt.  
  
```  
LinRegVariance(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
