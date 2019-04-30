---
title: StrToMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0c5878a553895dccc3350ddbae9397d5a48c6349
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149273"
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)


  Gibt das durch eine Multidimensional Expressions MDX-formatierte Zeichenfolge angegebene Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Name*  
 Ein gültiger Zeichenfolgenausdruck, der direkt oder indirekt ein Element angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **StrToMember** Funktion gibt den im Zeichenfolgenausdruck angegebene Element zurück. Die **StrToMember** Funktion wird in der Regel mit benutzerdefinierten Funktionen verwendet, um eine Elementspezifikation aus einer externen Funktion zurückzugeben, an ein MDX-Anweisung, oder wenn eine MDX-Abfrage parametrisiert wird.  
  
-   Wenn das CONSTRAINED-Flag verwendet wird, muss der Elementname direkt zu einem qualifizierten oder nicht qualifizierten Elementnamen aufgelöst werden können. Dieses Flag wird verwendet, um das Risiko von Injection-Angriffen über die angegebene Zeichenfolge zu verringern. Wenn eine Zeichenfolge bereitgestellt wird, die nicht direkt zu einem qualifizierten oder nicht qualifizierten Elementnamen aufgelöst werden kann, wird der folgende Fehler angezeigt: "Die Einschränkungen durch das CONSTRAINED-Flag in der STRTOMEMBER-Funktion wurden verletzt."  
  
-   Wenn das CONSTRAINED-Flag nicht verwendet wird, kann das angegebene Element entweder direkt zu einem Elementnamen aufgelöst werden oder zu einem gültigen MDX-Ausdruck (Multidimensional Expressions) aufgelöst werden, der zu einem Namen aufgelöst wird.  
  
-   Weitere Informationen zu den Unterschieden zwischen Mengen und Elementen finden Sie in den Abschnitten "Verwenden von Mengenausdrücken" und "Verwenden von Elementausdrücken".  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element zurückgibt, in der State-Province-Attributhierarchie mithilfe der **StrToMember** Funktion. Die angegebene Zeichenfolge stellt den qualifizierten Elementnamen bereit.  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Das folgende Beispiel gibt das Reseller Sales Amount-Measure für das Bayern-Element, das mit der **StrToMember** Funktion. Da der Elementname nur einen nicht qualifizierten Elementnamen bereitstellt, gibt die Abfrage die erste Instanz des angegebenen Elements zurück, die sich in diesem Fall in der Customer Geography-Hierarchie in der Customer-Dimension befindet, die sich nicht mit Reseller Sales überschneidet. Die bewährte Methode sieht vor, immer den qualifizierten Namen anzugeben, um erwartete Ergebnisse zu erhalten.  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element zurückgibt, in der State-Province-Attributhierarchie mithilfe der **StrToMember** Funktion. Der bereitgestellte Elementname wird zu einem qualifizierten Elementnamen aufgelöst.  
  
```  
SELECT {StrToMember('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird aufgrund des CONSTRAINED-Flags ein Fehler zurückgegeben. Die bereitgestellte Elementnamen-Zeichenfolge enthält zwar einen gültigen MDX-Elementausdruck, der zu einem qualifizierten Elementnamen aufgelöst wird, das CONSTRAINED-Flag erfordert jedoch qualifizierte oder nicht qualifizierten Elementnamen in der Elementnamen-Zeichenfolge.  
  
```  
SELECT StrToMember ('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
