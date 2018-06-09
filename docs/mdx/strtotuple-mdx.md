---
title: StrToTuple (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 35cd9cf849ce35bf82c839f0bbeeb657a75e990c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743229"
---
# <a name="strtotuple-mdx"></a>StrToTuple (MDX)


  Gibt das durch eine Zeichenfolge im MDX-Format (Multidimensional Expressions) angegebene Tupel zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StrToTuple(Tuple_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Specification*  
 Ein gültiger Zeichenfolgenausdruck, der direkt oder indirekt ein Tupel angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **StrToTuple** -Funktion die angegebene Menge zurück. Die **StrToTuple** Funktion wird in der Regel mit benutzerdefinierten Funktionen verwendet, um eine tupelspezifikation aus einer externen Funktion an eine MDX-Anweisung zurückzugeben.  
  
-   Wenn das CONSTRAINED-Flag verwendet wird, muss die Tupelspezifikation qualifizierte oder nicht qualifizierte Elementnamen enthalten. Dieses Flag wird verwendet, um das Risiko von Injection-Angriffen über die angegebene Zeichenfolge zu reduzieren. Wenn eine Zeichenfolge bereitgestellt wird, die nicht direkt zu qualifizierten oder nicht qualifizierten Elementnamen aufgelöst werden kann, wird eine Fehlermeldung angezeigt, die besagt, dass die durch das CONSTRAINED-Flag in der STRTOTUPLE-Funktion vorgegebenen Einschränkungen verletzt wurden.  
  
-   Wenn das CONSTRAINED-Flag nicht verwendet wird, kann der angegebene Tupelausdruck zu einem gültigen MDX-Ausdruck (Multidimensional Expressions) aufgelöst werden, der ein Tupel zurückgibt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element für das Kalenderjahr 2004 zurückgegeben. Die Tupelspezifikation, die bereitgestellt wird, enthält einen gültigen MDX-Tupelausdruck.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element für das Kalenderjahr 2004 zurückgegeben. Die bereitgestellte Tupelspezifikation enthält qualifizierte Elementnamen, wie vom CONSTRAINED-Flag angefordert.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].[CY 2004], [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element für das Kalenderjahr 2004 zurückgegeben. Die Tupelspezifikation, die bereitgestellt wird, enthält einen gültigen MDX-Tupelausdruck.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird aufgrund des CONSTRAINED-Flags ein Fehler zurückgegeben. Die bereitgestellte Tupelspezifikation enthält zwar einen gültige MDX-Mengenausdruck, das CONSTRAINED-Flag erfordert jedoch qualifizierte oder nicht qualifizierte Elementnamen in der Tupelspezifikation.  
  
```  
SELECT StrToTuple ('([Geography].[State-Province].[Bayern],[Date].[Calendar Year].&[2003].NEXTMEMBER, [Measures].[Reseller Sales Amount])', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
