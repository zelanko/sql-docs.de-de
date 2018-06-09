---
title: StrToSet (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7184dc872624f6589ec6e93911b39c9f8b4e4aa3
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742979"
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)


  Gibt die durch eine Zeichenfolge im MDX-Format (Multidimensional Expressions) angegebene Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Specification*  
 Ein gültiger Zeichenfolgenausdruck, der direkt oder indirekt eine Menge angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **StrToSet** Funktion gibt den im Zeichenfolgenausdruck angegebenen Satz zurück. Die **StrToSet** Funktion wird in der Regel mit benutzerdefinierten Funktionen verwendet, um eine mengenspezifikation aus einer externen Funktion zurück, an eine MDX-Anweisung, oder wenn eine MDX-Abfrage parametrisiert wird.  
  
-   Wenn das CONSTRAINED-Flag verwendet wird, darf die mengenspezifikation qualifizierte oder nicht qualifizierte Elementnamen enthalten oder eine Menge von Tupeln, die qualifizierte oder nicht qualifizierte Elementnamen in geschweiften Klammern enthält {}. Dieses Flag wird verwendet, um das Risiko von Injection-Angriffen über die angegebene Zeichenfolge zu reduzieren. Wenn eine Zeichenfolge bereitgestellt wird, die nicht direkt zu qualifizierten oder nicht qualifizierten Elementnamen aufgelöst werden kann, wird eine Fehlermeldung angezeigt, die besagt, dass die durch das CONSTRAINED-Flag in der STRTOSET-Funktion vorgegebenen Einschränkungen verletzt wurden.  
  
-   Wenn das CONSTRAINED-Flag nicht verwendet wird, kann der angegebene Mengenausdruck zu einem gültigen MDX-Ausdruck (Multidimensional Expressions) aufgelöst werden, der eine Menge zurückgibt.  
  
-   Weitere Informationen zu den Unterschieden zwischen Mengen und Elementen finden Sie in den Abschnitten "Verwenden von Mengenausdrücken" und "Verwenden von Elementausdrücken".  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die Menge der Elemente der State-Province-Attributhierarchie mit der **StrToSet** Funktion. Die Mengenspezifikation stellt einen gültigen MDX-Mengenausdruck bereit.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird aufgrund des CONSTRAINED-Flags ein Fehler zurückgegeben. Die Mengenspezifikation stellt zwar einen gültigen MDX-Mengenausdruck bereit, das CONSTRAINED-Flag erfordert jedoch qualifizierte oder nicht qualifizierte Elementnamen in der Mengenspezifikation.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für die Country-Elemente Germany und Canada zurückgegeben. Die in der angegebenen Zeichenfolge bereitgestellte Mengenspezifikation enthält qualifizierte Elementnamen, wie vom CONSTRAINED-Flag angefordert.  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
