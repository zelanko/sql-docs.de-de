---
description: CASE-Anweisung (MDX)
title: Case-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7a5907eb58fa102c46fa22af97116c4fad0f217a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466502"
---
# <a name="case-statement-mdx"></a>CASE-Anweisung (MDX)


  Ermöglicht die bedingte Rückgabe bestimmter Werte aus mehreren Vergleichen. Die folgenden zwei Arten von CASE-Anweisungen stehen zur Verfügung:  
  
-   Einfache CASE-Anweisungen, die einen Ausdruck mit mehreren einfachen Ausdrücken vergleichen, um bestimmte Werte zurückzugeben.  
  
-   Komplexe CASE-Anweisungen, die eine Menge boolescher Ausdrücke auswerten, um bestimmte Werte zurückzugeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Simple Case Statement  
CASE [input_expression]  
WHEN when_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
  
Search Case Statement  
CASE   
WHEN Boolean_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
```  
  
## <a name="arguments"></a>Argumente  
 *input_expression*  
 Ein MDX-Ausdruck (Multidimensional Expressions), dessen Auflösung einen Skalarwert ergibt.  
  
 *when_expression*  
 Ein angegebener Skalarwert, für den die *input_expression* ausgewertet wird. Wenn true ausgewertet wird, wird der Skalarwert des *else_result_expression*zurückgegeben.  
  
 *when_true_result_expression*  
 Der Skalarwert, der zurückgegeben wird, wenn die Auswertung der WHEN-Klausel den Wert true ergibt.  
  
 *else_result_expression*  
 Der Skalarwert, der zurückgegeben wird, wenn keine Auswertung von WHEN-Klauseln den Wert true ergibt.  
  
 *Boolean_expression*  
 Ein MDX-Ausdruck, dessen Auswertung einen Skalarwert ergibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Ist keine ELSE-Klausel angegeben, und werden alle WHEN-Klauseln zu FALSE ausgewertet, ist das Ergebnis eine leere Zelle.  
  
## <a name="simple-case-expression"></a>Einfache CASE-Ausdrücke  
 MDX wertet einen einfachen CASE-Ausdruck aus, indem er die *input_expression* in einen skalaren Wert auflöst. Dieser skalare Wert wird dann mit dem Skalarwert des *when_expression*verglichen. Wenn die beiden Skalarwerte Stimmen, gibt die Case-Anweisung den Wert der *when_true_expression*zurück. Wenn die beiden Skalarwerte nicht übereinstimmen, wird die nächste WHEN-Klausel ausgewertet. Wenn alle WHEN-Klauseln als false ausgewertet werden, wird der Wert *else_result_expression* aus der Else-Klausel, sofern vorhanden, zurückgegeben.  
  
 Im folgenden Beispiel wird das Reseller Order Count-Measure für mehrere WHEN-Klauseln ausgewertet und als Ergebnis der Wert des Reseller Order Count-Measures für jedes Jahr zurückgegeben. Für Reseller Order Count-Werte, die nicht mit einem skalaren Wert identisch sind, der in einer *when_expression* in einer When-Klausel angegeben ist, wird der Skalarwert des *else_result_expression* zurückgegeben.  
  
```  
WITH MEMBER [Measures].x AS   
CASE [Measures].[Reseller Order Count]  
   WHEN 0 THEN 'NONE'  
   WHEN 1 THEN 'SMALL'  
   WHEN 2 THEN 'SMALL'  
   WHEN 3 THEN 'MEDIUM'  
   WHEN 4 THEN 'MEDIUM'  
   WHEN 5 THEN 'LARGE'  
   WHEN 6 THEN 'LARGE'  
      ELSE 'VERY LARGE'  
END  
SELECT Calendar.[Calendar Year] on 0  
, NON EMPTY [Geography].[Postal Code].Members ON 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="searched-case-expression"></a>Komplexe CASE-Ausdrücke  
 Verwenden Sie komplexe CASE-Ausdrücke, wenn Sie komplexere Auswertungen mithilfe von CASE-Ausdrücken durchführen möchten. Mit dieser Variante des Suchausdrucks können Sie auswerten, ob ein Eingabeausdruck innerhalb eines bestimmten Wertebereichs liegt. MDX wertet die WHEN-Klauseln in der Reihenfolge aus, in der die Klauseln in der CASE-Anweisung vorliegen.  
  
 Im folgenden Beispiel wird das Reseller Order Count-Measure anhand der angegebenen *Boolean_expression* für jede der WHEN-Klauseln ausgewertet. Als Ergebnis wird der Wert des Reseller Order Count-Measures für jedes Jahr zurückgegeben. Da WHEN-Klausel in der Reihenfolge ausgewertet werden, in der sie vorliegen, können alle Werte, die größer als 6 sind, problemlos dem Wert "VERY LARGE" zugewiesen werden, ohne jeden einzelnen Wert explizit angeben zu müssen. Für Reseller Order Count-Werte, die nicht in einer When-Klausel angegeben sind, wird der Skalarwert der *else_result_expression* zurückgegeben.  
  
```  
WITH MEMBER [Measures].x AS   
CASE   
   WHEN [Measures].[Reseller Order Count] > 6 THEN 'VERY LARGE'  
   WHEN [Measures].[Reseller Order Count] > 4 THEN 'LARGE'  
   WHEN [Measures].[Reseller Order Count] > 2 THEN 'MEDIUM'  
   WHEN [Measures].[Reseller Order Count] > 0 THEN 'SMALL'  
   ELSE "NONE"  
END  
SELECT Calendar.[Calendar Year] on 0,  
NON EMPTY [Geography].[Postal Code].Members on 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Skriptanweisungen &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
