---
title: Verwenden von Tupelfunktionen | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 578192fa982b8bbf65527f4ff1d71b6595a2400d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63251635"
---
# <a name="using-tuple-functions"></a>Verwenden von Tupelfunktionen


  Eine Tupelfunktion ruft ein Tupel aus einer Menge oder dadurch ab, dass sie die Zeichenfolgendarstellung eines Tupels auflöst.  
  
 Tupelfunktionen sind, wie Elementfunktionen und Mengenfunktionen, wesentlich für das Aushandeln mehrdimensionaler Strukturen, die in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zu finden sind.  
  
 Es gibt drei Tupelfunktionen in MDX [aktuelle &#40;MDX&#41;](../mdx/current-mdx.md), [Element &#40;Tupel&#41; &#40;MDX&#41; ](../mdx/item-tuple-mdx.md) und [StrToTuple &#40;MDX&#41;](../mdx/strtotuple-mdx.md). Die folgende Beispielabfrage veranschaulicht, wie sie verwendet werden:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)   
 [Verwenden von Memberfunktionen](../mdx/using-member-functions.md)   
 [Using Set Functions (Verwenden von Mengenfunktionen)](../mdx/using-set-functions.md)  
  
  
