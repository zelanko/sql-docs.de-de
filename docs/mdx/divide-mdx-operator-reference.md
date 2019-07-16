---
title: (Division) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8dd20a0b60e105ac48a54d533055717e3f07a006
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049325"
---
# <a name="divide---mdx-operator-reference"></a>Divide - MDX-Operatorreferenz


  Führt eine arithmetische Operation aus, die eine Zahl durch eine andere dividiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>Parameter  
 *Dividend*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen numerischen Wert zurückgibt.  
  
 *Divisor*  
 Ein gültiger MDX-Ausdruck, der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Datentyp des Parameters, der in der Rangfolge höher eingestuft ist.  
  
## <a name="remarks"></a>Hinweise  
 Den eigentlichen Rückgabewert, der von der **/ (Division)** Operator entspricht dem Quotienten aus dem ersten Ausdruck geteilt durch den zweiten Ausdruck.  
  
 Beide Ausdrücke müssen denselben Datentyp haben, oder es muss möglich sein, einen Ausdruck implizit in den Datentyp des anderen Ausdrucks zu konvertieren. Wenn *Divisor* einen null-Wert, löst der Operator einen Fehler ergibt. Wenn beide *Divisor* und *Dividend* ausgewertet, ein null-Wert, der Operator gibt einen null-Wert zurück.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators.  
  
```  
-- This query returns the freight cost per user,  
-- for products, averaged by month.   
With Member [Measures].[Freight Per Customer] as  
    [Measures].[Internet Freight Cost]  
    /   
    [Measures].[Customer Count]  
  
SELECT   
    [Ship Date].[Calendar].[Calendar Year] Members ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
 Die Division eines Werts ungleich 0 oder ungleich NULL durch 0 oder NULL ergibt den Wert „Unendlich“. Dieser wird in Abfrageergebnissen als „1.#INF” dargestellt. In den meisten Fällen sollten Sie auf Division durch 0 prüfen, um diese Situation zu vermeiden. Das folgende Beispiel zeigt Ihnen wie:  
  
 `//Returns 1.#INF when Internet Sales Amount is zero or null`  
  
 `Member [Measures].[Reseller to Internet Ratio] AS`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `//Traps the division by zero scenario and returns null instead of 1.#INF`  
  
 `Member [Measures].[Reseller to Internet Ratio With Error Handling] AS`  
  
 `IIF([Measures].[Internet Sales Amount]=0, NULL,`  
  
 `[Measures].[Reseller Sales Amount]`  
  
 `/`  
  
 `[Measures].[Internet Sales Amount])`  
  
 `SELECT`  
  
 `{[Measures].[Reseller to Internet Ratio],[Measures].[Reseller to Internet Ratio With Error Handling]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
## <a name="see-also"></a>Siehe auch  
 [IIf &#40;MDX&#41;](../mdx/iif-mdx.md)   
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
