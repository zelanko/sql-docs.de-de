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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **Kovarianz** -Funktion wertet die angegebene Menge für den ersten numerischen Ausdruck aus, um die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion die angegebene Menge für den zweiten numerischen Ausdruck aus, um die Werte für die X-Achse zu erhalten. Wenn kein zweiter numerischer Ausdruckangegeben wird, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die X-Achse.  
  
 Die **Kovarianz** Funktion verwendet die Formel für die unausgewogene Auffüllung. Dies steht im Gegensatz zur [CovarianceN](../mdx/covariancen-mdx.md) -Funktion, die die Formel für die unausgewogene Auffüllung verwendet (dividiert die Anzahl der x-y-Paare und subtrahieren 1).  
  
> [!NOTE]  
>  Die **Kovarianz** Funktion ignoriert leere Zellen, oder Zellen, die Text oder logische Werte enthalten, werden ignoriert. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
