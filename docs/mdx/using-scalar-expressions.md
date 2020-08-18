---
description: Verwenden von Skalarausdrücken
title: Verwenden von skalaren Ausdrücken | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cc13d94aaf44e563a9519f797effee7cbeb74305
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491394"
---
# <a name="using-scalar-expressions"></a>Verwenden von Skalarausdrücken


  In MDX (Multidimensional Expressions) ist ein Skalarausdruck ein Element in der MDX-Syntax, das ausgewertet einen einzelnen Wert im Kontext der Auswertung zurückgibt.  
  
 Zu den Skalarausdrücken gehören Zeichenfolgen-, numerische und Datumsausdrücke in MDX.  
  
 Skalarausdrücke werden in der Regel in berechneten Elementdefinitionen verwendet, da berechnete Elemente einen Skalarwert zurückgeben müssen. Die folgende Abfrage zeigt Beispiele berechneter Elemente in der Measures-Dimension, die unterschiedliche Skalarausdrücke verwenden:  
  
 `WITH`  
  
 `MEMBER MEASURES.NumericValue AS 10`  
  
 `MEMBER MEASURES.NumericExpression AS 10 + 10`  
  
 `MEMBER MEASURES.NumericExpressionBasedOnMeasure AS [Measures].[Internet Sales Amount] + 10`  
  
 `MEMBER MEASURES.StringValue AS "10"`  
  
 `MEMBER MEASURES.ConcatenatedString AS "10" + "10"`  
  
 `MEMBER MEASURES.StringFunction AS MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.TodaysDate AS NOW()`  
  
 `SELECT`  
  
 `{MEASURES.NumericValue,MEASURES.NumericExpression,MEASURES.NumericExpressionBasedOnMeasure,`  
  
 `MEASURES.StringValue, MEASURES.ConcatenatedString, MEASURES.StringFunction, MEASURES.TodaysDate}`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 Der einzige Datentyp, den ein Measure, ob berechnet oder nicht, zurückgegeben kann, ist der OLE-Variantentyp. Deshalb kann es zuweilen notwendig sein, einen Measure-Wert in einen bestimmten Typ umzuwandeln, um das erwartete Verhalten zu erreichen. Die folgende Abfrage ist ein Beispiel dafür:  
  
```  
WITH  
//Two calculated measures that return strings  
MEMBER MEASURES.NumericString1 AS "10"  
MEMBER MEASURES.NumericString2 AS "10"  
//In this case, the + operator acts to concatenate the strings  
MEMBER MEASURES.Concatenation AS MEASURES.NumericString1 + MEASURES.NumericString2  
//Casting one value to an integer with the CINT function causes the second measure  
//to be treated as an integer too, so that the + operator now acts to add the values  
MEMBER MEASURES.Addition AS CINT(MEASURES.NumericString1) + MEASURES.NumericString2  
SELECT  
{MEASURES.NumericString1,MEASURES.NumericString2,MEASURES.Concatenation,MEASURES.Addition }  
ON COLUMNS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;MDX-&#41;](../mdx/expressions-mdx.md)  
  
  
