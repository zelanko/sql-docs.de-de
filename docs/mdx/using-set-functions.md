---
title: Verwenden von Mengenfunktionen | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca9c5e1a3e110e1f1f2f14e9bd9b52e245d457a6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251590"
---
# <a name="using-set-functions"></a>Verwenden von Mengenfunktionen


  Eine Mengenfunktion ruft eine Menge aus einer Dimension, einer Hierarchie oder einer Ebene ab oder indem sie die absoluten und relativen Speicherorte von Elementen im jeweiligen Objekt traversiert, wobei die jeweilige Menge auf verschiedene Arten erstellt werden kann.  
  
 Mengenfunktionen sind, wie Elementfunktionen und Tupelfunktionen, wesentlich für das Aushandeln mehrdimensionaler Strukturen, die in Analysis Services zu finden sind. Mengenfunktionen sind außerdem unverzichtbar zum Erzielen von Ergebnissen aus MDX-Abfragen (Multidimensional Expressions), weil Mengenausdrücke die Achsen einer MDX-Abfrage definieren.  
  
 Eine der meistverwendeten Mengenfunktionen ist die [Mitglieder &#40;festgelegt&#41; &#40;MDX&#41; ](../mdx/members-set-mdx.md) -Funktion, die eine Gruppe, die alle Elemente aus einer Dimension, Hierarchie oder Ebene enthält abruft. Das folgende Beispiel veranschaulicht ihre Verwendung in einer Abfrage:  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns all of the members on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Eine andere häufig verwendete Funktion ist die [Crossjoin &#40;MDX&#41; ](../mdx/crossjoin-mdx.md) Funktion. Sie gibt eine Menge von Tupeln zurück, die dem kartesischen Produkt der Mengen entspricht, die ihr als Parameter übergeben werden. Mit dieser Funktion können Sie in Abfragen Achsen geschachtelt oder in Kreuztabellen erstellen:  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns a set containing every combination of all of the members`  
  
 `//on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension and all of the members on the Category level`  
  
 `//of the Category hierarchy on the Product dimension`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Die [Nachfolger &#40;MDX&#41; ](../mdx/descendants-mdx.md) -Funktion gleicht der **untergeordnete Elemente** funktionieren, aber leistungsfähiger ist. Es gibt die Nachfolger eines beliebigen Elements auf einer oder mehreren Ebenen in einer Hierarchie zurück:  
  
 SELECT  
  
 [Measures].[Internet Sales Amount]  
  
 ON Columns,  
  
 //Gibt eine Menge zurück, die alle Datumsangaben enthält, die unter Kalenderjahr  
  
 //2004 in der Kalenderhierarchie der Date-Dimension liegen  
  
 DESCENDANTS(  
  
 [Date]. [Calendar]. [Kalenderjahr]. & [2004]  
  
 , [Date].[Calendar].[Date])  
  
 ON Rows  
  
 FROM [Adventure Works]  
  
 Die [Reihenfolge &#40;MDX&#41; ](../mdx/order-mdx.md) -Funktion ermöglicht Ihnen, um den Inhalt einer Menge in aufsteigender oder absteigender Reihenfolge nach einem bestimmten numerischen Ausdruck zu sortieren. Die folgende Abfrage gibt dieselben Elemente in Zeilen zurück wie die vorherige Abfrage, ordnet diese aber nach dem Internet Sales Amount-Measure:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//ordered by Internet Sales Amount`  
  
 `ORDER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount], BDESC)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Diese Abfrage veranschaulicht, wie die von einer Mengenfunktion (DESCENDANTS) zurückgegebene Menge als Parameter an eine andere Mengenfunktion, (ORDER) übergeben wird.  
  
 Filtert eine Menge nach bestimmten Kriterien ist sehr nützlich, beim Schreiben von Abfragen und zu diesem Zweck können Sie die [Filter &#40;MDX&#41; ](../mdx/filter-mdx.md) Funktion, wie im folgenden Beispiel gezeigt:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//where Internet Sales Amount is greater than $70000`  
  
 `FILTER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount]>70000)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Es gibt weitere verfeinerte Funktionen, mit denen Sie eine Menge auf andere Weise filtern können. Z. B. die folgende Abfrage zeigt die [TopCount &#40;MDX&#41; ](../mdx/topcount-mdx.md) Funktion gibt die ersten n Elemente in einem Satz zurück:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing the top 10 Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension by Internet Sales Amount`  
  
 `TOPCOUNT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,10, [Measures].[Internet Sales Amount])`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Schließlich ist es möglich, eine Reihe logischer Mengenoperationen, z. B. ausführen [Intersect &#40;MDX&#41;](../mdx/intersect-mdx.md), [Union &#40;MDX&#41; ](../mdx/union-mdx.md) und [außer &#40;MDX&#41; ](../mdx/except-mdx-function.md) Funktionen. Die folgende Abfrage enthält Beispiele für die letzten beiden Funktionen:  
  
 `SELECT`  
  
 `//Returns a set containing the Measures Internet Sales Amount, Internet Tax Amount and`  
  
 `//Internet Total Product Cost`  
  
 `UNION(`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}`  
  
 `, {[Measures].[Internet Total Product Cost]}`  
  
 `)`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//except the January 1st 2004`  
  
 `EXCEPT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,{[Date].[Calendar].[Date].&[915]})`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)   
 [Verwenden von Memberfunktionen](../mdx/using-member-functions.md)   
 [Using Tuple Functions (Verwenden von Tupelfunktionen)](../mdx/using-tuple-functions.md)  
  
  
