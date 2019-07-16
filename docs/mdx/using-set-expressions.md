---
title: Verwenden von Mengenausdrücken | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 622458f3ea3f8baf74b3aaa4aa9c46f94972f490
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038020"
---
# <a name="using-set-expressions"></a>Verwenden von Mengenausdrücken


  Eine Menge besteht aus einer geordneten Liste von null oder mehr Tupeln. Eine Menge, die keine Tupel enthält, wird als leere Menge bezeichnet.  
  
 Der vollständige Ausdruck einer Menge besteht aus null oder mehr explizit angegebenen Tupeln, die in geschweiften Klammern stehen:  
  
 {[{ *Tuple_expression* | *Member_expression* } [, { *Tuple_expression* | *Member_expression* } ] ... ] }  
  
 Die in einem Mengenausdruck angegebenen Elementausdrücke werden in Tupelausdrücke mit einem Element konvertiert.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden zwei Mengenausdrücke auf der COLUMNS- und der ROWS-Achse einer Abfrage verwendet:  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]} ON COLUMNS,`  
  
 `{([Product].[Product Categories].[Category].&[4], [Date].[Calendar].[Calendar Year].&[2004]),`  
  
 `([Product].[Product Categories].[Category].&[1], [Date].[Calendar].[Calendar Year].&[2003]),`  
  
 `([Product].[Product Categories].[Category].&[3], [Date].[Calendar].[Calendar Year].&[2004])}`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Auf der COLUMNS-Achse die Menge  
  
 {[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}  
  
 besteht aus zwei Elementen der Measures-Dimension. Auf der ROWS-Achse besteht die Menge  
  
 {([Product]. [Product Categories]. [Category]. & [4], [Date]. [Calendar]. [Kalenderjahr]. & [2004]),  
  
 ([Product]. [Product Categories]. [Category]. & [1], [Date]. [Calendar]. [Kalenderjahr]. & [2003]),  
  
 ([Product]. [Product Categories]. [Category]. & [3], [Date]. [Calendar]. [Calendar Year]. & [2004])}  
  
 aus drei Tupeln, von denen jede zwei explizite Verweise auf Elemente in der Product Categories-Hierarchie der Product-Dimension und der Calendar-Hierarchie der Date-Dimension enthält.  
  
 Beispiele für Funktionen, die Mengen zurückgeben, finden Sie unter [arbeiten mit Elementen, Tupeln und Mengen &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrücke &#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
