---
title: Verwenden von Dimensionsausdrücken | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a5e26d56a52c8c922c43325bd2267fa623dc0e19
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743909"
---
# <a name="using-dimension-expressions"></a>Verwenden von Dimensionsausdrücken


  Dimensions- und Hierarchieausdrücke werden in MDX (Multidimensional Expressions) üblicherweise zur Übergabe von Parametern an Funktionen verwendet, um Elemente, Mengen oder Tupel einer Hierarchie zurückzugeben.  
  
 Dimensionsausdrücke können nur einfache Ausdrücke sein, da sie Objektbezeichner sind. Finden Sie unter [Ausdrücke &#40;MDX&#41; ](../mdx/expressions-mdx.md) eine Erläuterung der einfachen und komplexen Ausdrücken.  
  
## <a name="dimension-expressions"></a>Dimensionsausdrücke  
 Ein Dimensionsausdruck enthält entweder einen Dimensionsbezeichner oder eine Dimensionsfunktion.  
  
 Dimensionsausdrücke werden selten allein verwendet. Normalerweise wird in einer Dimension eine Hierarchie angegeben. Die einzige Ausnahme bildet die Measures-Dimension, die über keine Hierarchien verfügt.  
  
 Das folgende Beispiel zeigt ein berechnetes Element, das den Ausdruck [Measures] mit den Funktionen .Members und Count() verwendet, um die Anzahl der Elemente in der Measures-Dimension zurückzugeben.  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Ein dimensionsbezeichner wird als *Dimension_Name* in der BNF-Schreibweise zur Beschreibung von MDX-Anweisungen.  
  
## <a name="hierarchy-expressions"></a>Hierarchieausdrücke  
 Ein Hierarchieausdruck enthält entweder einen Hierarchiebezeichner oder eine Hierarchiefunktion. Im folgenden Beispiel wird der Hierarchieausdruck [Date].[Calendar] in Verbindung mit der .Levels- und der .Count-Funktion verwendet, um die Anzahl der Ebenen in der Calendar-Hierarchie der Date-Dimension zurückzugeben:  
  
 `WITH MEMBER [Measures].[CalendarLevelCount] AS`  
  
 `[Date].[Calendar].Levels.Count`  
  
 `SELECT [Measures].[CalendarLevelCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Am häufigsten werden Hierarchieausdrücke in Verbindung mit der .Members-Funktion verwendet, um die Anzahl aller Elemente einer Hierarchie zurückzugeben. Im folgenden Beispiel werden alle Elemente von [Date].[Calendar] auf der ROWS-Achse zurückgegeben:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Ein hierarchiebezeichner wird als *Dimension_Name **.** Hierarchiename* in der BNF-Schreibweise zur Beschreibung von MDX-Anweisungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrücke &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
