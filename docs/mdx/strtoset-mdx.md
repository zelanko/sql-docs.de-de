---
title: StrToSet (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ee1e0cbeaa4e33be223e1b777ff243b5c3ef2d01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150186"
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)


  Gibt die durch eine Zeichenfolge Multidimensional Expressions MDX-Format angegebene Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Specification*  
 Ein gültiger Zeichenfolgenausdruck, der direkt oder indirekt eine Menge angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **StrToSet** Funktion gibt den im Zeichenfolgenausdruck angegebenen Satz zurück. Die **StrToSet** Funktion wird in der Regel mit benutzerdefinierten Funktionen verwendet, um eine mengenspezifikation aus einer externen Funktion zurückzugeben, an ein MDX-Anweisung, oder wenn eine MDX-Abfrage parametrisiert wird.  
  
-   Wenn das CONSTRAINED-Flag verwendet wird, darf die mengenspezifikation qualifizierte oder nicht qualifizierte Elementnamen enthalten oder eine Menge von Tupeln, die mit der qualifizierte oder nicht qualifizierte Elementnamen in geschweiften Klammern {}. Dieses Flag wird verwendet, um das Risiko von Injection-Angriffen über die angegebene Zeichenfolge zu verringern. Wenn eine Zeichenfolge, die bereitgestellt wird ist nicht direkt aufgelöst werden kann, um qualifizierte oder nicht qualifizierte Elementnamen, die folgende Fehlermeldung angezeigt: "Die Einschränkungen durch das CONSTRAINED-Flag in der STRTOSET-Funktion wurden verletzt."  
  
-   Wenn das CONSTRAINED-Flag nicht verwendet wird, kann der angegebene Mengenausdruck zu einem gültigen MDX-Ausdruck (Multidimensional Expressions) aufgelöst werden, der eine Menge zurückgibt.  
  
-   Weitere Informationen zu den Unterschieden zwischen Mengen und Elementen finden Sie in den Abschnitten "Verwenden von Mengenausdrücken" und "Verwenden von Elementausdrücken".  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die Menge der Elemente der State-Province-Attributhierarchie mithilfe der **StrToSet** Funktion. Die Mengenspezifikation stellt einen gültigen MDX-Mengenausdruck bereit.  
  
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
  
  
