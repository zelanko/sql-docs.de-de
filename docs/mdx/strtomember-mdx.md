---
description: StrToMember (MDX)
title: "\"Straume\" (MDX) | Microsoft-Dokumentation"
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 68d2d99bb51412a98919d1ab1626c7a86bd86245
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386806"
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)


  Gibt das durch eine Zeichenfolge im MDX-Format (Multidimensional Expressions) angegebene Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Name*  
 Ein gültiger Zeichenfolgenausdruck, der direkt oder indirekt ein Element angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die " **strautomember** "-Funktion gibt den im Zeichen folgen Ausdruck angegebenen Member zurück. Die Funktion " **Strauch** " wird in der Regel mit benutzerdefinierten Funktionen verwendet, um eine Element Spezifikation aus einer externen Funktion an eine MDX-Anweisung zurückzugeben, oder wenn eine MDX-Abfrage parametrisiert wird.  
  
-   Wenn das CONSTRAINED-Flag verwendet wird, muss der Elementname direkt zu einem qualifizierten oder nicht qualifizierten Elementnamen aufgelöst werden können. Dieses Flag wird verwendet, um das Risiko von Injection-Angriffen über die angegebene Zeichenfolge zu verringern. Wenn eine Zeichenfolge bereitgestellt wird, die nicht direkt zu einem qualifizierten oder nicht qualifizierten Elementnamen aufgelöst werden kann, wird eine Fehlermeldung angezeigt, die besagt, dass die durch das CONSTRAINED-Flag in der STRTOMEMBER-Funktion vorgegebenen Einschränkungen verletzt wurden.  
  
-   Wenn das CONSTRAINED-Flag nicht verwendet wird, kann das angegebene Element entweder direkt zu einem Elementnamen aufgelöst werden oder zu einem gültigen MDX-Ausdruck (Multidimensional Expressions) aufgelöst werden, der zu einem Namen aufgelöst wird.  
  
-   Weitere Informationen zu den Unterschieden zwischen Mengen und Elementen finden Sie in den Abschnitten "Verwenden von Mengenausdrücken" und "Verwenden von Elementausdrücken".  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element in der State-Province-Attribut Hierarchie mithilfe der-Funktion " **strauberember** " zurückgegeben. Die angegebene Zeichenfolge stellt den qualifizierten Elementnamen bereit.  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element mithilfe der-Funktion " **strauberember** " zurückgegeben. Da der Elementname nur einen nicht qualifizierten Elementnamen bereitstellt, gibt die Abfrage die erste Instanz des angegebenen Elements zurück, die sich in diesem Fall in der Customer Geography-Hierarchie in der Customer-Dimension befindet, die sich nicht mit Reseller Sales überschneidet. Die bewährte Methode sieht vor, immer den qualifizierten Namen anzugeben, um erwartete Ergebnisse zu erhalten.  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird das Reseller Sales Amount-Measure für das Bayern-Element in der State-Province-Attribut Hierarchie mithilfe der-Funktion " **strauberember** " zurückgegeben. Der bereitgestellte Elementname wird zu einem qualifizierten Elementnamen aufgelöst.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
