---
description: Verwenden von Dimensionsausdrücken
title: Verwenden von Dimensions Ausdrücken | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e8fb367f0e4ab1cc99a1a84ed51e3cca3cab75ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341116"
---
# <a name="using-dimension-expressions"></a>Verwenden von Dimensionsausdrücken


  Dimensions- und Hierarchieausdrücke werden in MDX (Multidimensional Expressions) üblicherweise zur Übergabe von Parametern an Funktionen verwendet, um Elemente, Mengen oder Tupel einer Hierarchie zurückzugeben.  
  
 Dimensionsausdrücke können nur einfache Ausdrücke sein, da sie Objektbezeichner sind. Eine Erläuterung zu einfachen und komplexen Ausdrücken finden Sie unter [Ausdrücke &#40;MDX-&#41;](../mdx/expressions-mdx.md) .  
  
## <a name="dimension-expressions"></a>Dimensionsausdrücke  
 Ein Dimensionsausdruck enthält entweder einen Dimensionsbezeichner oder eine Dimensionsfunktion.  
  
 Dimensionsausdrücke werden selten allein verwendet. Normalerweise wird in einer Dimension eine Hierarchie angegeben. Die einzige Ausnahme bildet die Measures-Dimension, die über keine Hierarchien verfügt.  
  
 Das folgende Beispiel zeigt ein berechnetes Element, das den Ausdruck [Measures] mit den Funktionen .Members und Count() verwendet, um die Anzahl der Elemente in der Measures-Dimension zurückzugeben.  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Ein Dimensions Bezeichner wird als *Dimension_Name* in der BNF-Notation angezeigt, mit der MDX-Anweisungen beschrieben werden.  
  
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
  
 Ein Hierarchie Bezeichner wird als *Dimension_Name. Hierarchy_Name* in der BNF-Notation zum Beschreiben von MDX-Anweisungen angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;MDX-&#41;](../mdx/expressions-mdx.md)  
  
  
