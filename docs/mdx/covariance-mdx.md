---
title: Kovarianz (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea3755fb103362b797735d74c9cbe67523aace59
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047187"
---
# <a name="covariance-mdx"></a>Covariance (MDX)


  Gibt die Auffüllungskovarianz von X-Y-Wertepaaren zurück, die über einer Menge mithilfe der Formel für die unausgewogene Auffüllung (geteilt durch die Anzahl der X-Y-Paare) berechnet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Covariance(Set_Expression,Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression_y*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die Y-Achse dar.  
  
 *Numeric_Expression_x*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die X-Achse dar.  
  
## <a name="remarks"></a>Hinweise  
 Die **Kovarianz** Funktion wertet die angegebene Menge für den ersten numerischen Ausdruck aus, um die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion die angegebene Menge für den zweiten numerischen Ausdruck aus, um die Werte für die X-Achse zu erhalten. Wenn Sie den zweiten numerischen AusdruckIS nicht angegeben ist, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die x-Achse an.  
  
 Die **Kovarianz** -Funktion verwendet die Formel für die unausgewogene Auffüllung berechnet wurde. Dies ist im Gegensatz zu den [CovarianceN](../mdx/covariancen-mdx.md) Funktion an, der nicht unausgewogenen Auffüllungsformel (geteilt durch die Anzahl der X-y-Paare, dann 1 subtrahiert) verwendet.  
  
> [!NOTE]  
>  Die **Kovarianz** Funktion ignoriert leere Zellen oder Zellen, die Text enthalten oder logische Werte werden ignoriert. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der Covariance-Funktion veranschaulicht:  
  
```  
WITH   
MEMBER [Measures].[CovarianceDemo] AS  
COVARIANCE([Date].[Date].[Date].Members, [Measures].[Internet Sales Amount], [Measures].[Internet Order Count])   
SELECT {[Measures].[CovarianceDemo]} ON 0   
FROM  
[Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
