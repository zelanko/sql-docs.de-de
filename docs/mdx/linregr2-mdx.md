---
title: LinRegR2 (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e38df1a24b76ee40aae3a5ab3c28dd9bca2b310
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905522"
---
# <a name="linregr2-mdx"></a>LinRegR2 (MDX)


  Berechnet die lineare Regression einer Menge und gibt den Koeffizienten der Bestimmung (R<sup>2</sup>) zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LinRegR2(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
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
  
 Die **LinRegR2** -Funktion wertet das angegebene Seton mit dem ersten numerischen Ausdruck aus, um die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion die angegebene Menge für den zweiten numerischen Ausdruck, sofern angegeben, aus, um die Werte für die X-Achse zu erhalten. Wenn das zweite numerische expressionis nicht angegeben ist, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die x-Achse. Für die Time-Dimension wird das X-Achsen-Argumenthäufig ausgelassen.  
  
 Nachdem Sie den Satz von Punkten erhalten haben, gibt die **LinRegR2** -Funktion den statistischen R<sup>2</sup> -Wert zurück, der die Anpassung der linearen Gleichung an die Punkte beschreibt.  
  
> [!NOTE]  
>  Die **LinRegR2** -Funktion ignoriert leere Zellen oder Zellen, die Text oder logische Werte enthalten. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die statistische R<sup>2</sup> zurückgegeben, die die Eignung der Formel für die lineare Regression an die Punkte für die Unit Sales-und Store Sales-Measures beschreibt.  
  
```  
LinRegR2(LastPeriods(10), [Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
