---
title: Arbeiten mit Elementen, Tupeln und Mengen (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 570d812400a35a45d59f97901b9be698abc21863
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48154090"
---
# <a name="working-with-members-tuples-and-sets-mdx"></a>Verwenden von Elementen, Tupeln und Mengen (MDX)
  MDX stellt eine Reihe von Funktionen bereit, die ein oder mehrere Elemente, Tupel oder Mengen zurückgeben bzw. diese als Argumente nehmen.  
  
## <a name="member-functions"></a>Elementfunktionen  
 MDX stellt viele Funktionen bereit, mit denen Elemente aus anderen MDX-Entitäten (z. B. Dimensionen, Ebenen, Mengen oder Tupeln) abgerufen werden können. Die [FirstChild](/sql/mdx/firstchild-mdx) -Funktion ist z. B. eine Funktion, die ein Element als Argument nimmt und ein Element zurückgibt.  
  
 Zum Abrufen des ersten untergeordneten Elements der Time-Dimension können Sie das Element explizit angeben (siehe folgendes Beispiel):  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 Sie können auch die `FirstChild` Funktion, um dasselbe Element an, wie im folgenden Beispiel zurückgegeben.  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 Weitere Informationen zu MDX-Elementfunktionen finden Sie unter [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="tuple-functions"></a>Tupelfunktionen  
 Es gibt mehrere MDX-Funktionen, die Tupel zurückgeben. Diese Funktionen können überall dort verwendet werden, wo ein Tupel zulässig ist. Die [Item-Funktion &#40;Tupel, MDX&#41;](/sql/mdx/item-tuple-mdx) kann z.B. verwendet werden, um das erste Tupel aus einer Menge zu extrahieren. Diese Funktion kann sehr nützlich sein, wenn die Menge aus einem einzelnen Tupel besteht und Sie dieses Tupel an eine Funktion übergeben möchten, die ein Tupel als Argument erfordert.  
  
 Im folgenden Beispiel wird das erste Tupel aus einer Menge von Tupeln auf der Spaltenachse zurückgegeben.  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 Weitere Informationen zu Tupelfunktionen finden Sie unter [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="set-functions"></a>Mengenfunktionen  
 Es gibt mehrere MDX-Funktionen, die Mengen zurückgeben. Das explizite Eingeben von in geschweiften Klammern eingeschlossenen Tupeln ist nicht die einzige Möglichkeit, eine Menge abzurufen. Weitere Informationen über die Elementfunktionen, die Mengen zurückgeben, finden Sie unter [Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md). Es stehen viele weitere Mengenfunktionen zur Verfügung.  
  
 Mithilfe des Doppelpunkt-Operators können Sie zum Erstellen einer Menge die natürliche Reihenfolge der Elemente verwenden. Beispielsweise enthält die im folgenden Beispiel gezeigte Menge Tupel für das erste bis vierte Quartal des Kalenderjahres 2002:  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 Dieselbe Menge von Elementen können Sie auch, anstatt den Doppelpunkt-Operator zu verwenden, wie im folgenden Beispiel durch Angeben der Tupel erstellen:  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 Der Doppelpunkt-Operator ist eine einschließende Funktion. Die Elemente auf beiden Seiten des Doppelpunkt-Operators werden in die Ergebnismenge eingeschlossen.  
  
 Weitere Informationen zu Mengenfunktionen finden Sie unter [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="array-functions"></a>Arrayfunktionen  
 Eine Arrayfunktion nimmt eine Menge als Argument und gibt ein Array zurück. Weitere Informationen zu Arrayfunktionen finden Sie unter [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="hierarchy-functions"></a>Hierarchiefunktionen  
 Ein Hierarchiefunktion gibt eine Hierarchie zurück und nimmt ein Element, eine Ebene, eine Hierarchie oder eine Zeichenfolge als Argument. Weitere Informationen zu Hierarchiefunktionen finden Sie unter [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="level-functions"></a>Ebenenfunktionen  
 Ein Ebenenfunktion gibt eine Ebene zurück und nimmt ein Element, eine Ebene oder eine Zeichenfolge als Argument. Weitere Informationen zu Ebenenfunktionen finden Sie unter [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="logical-functions"></a>Logische Funktionen  
 Eine logische Funktion nimmt einen MDX-Ausdruck als Argument und gibt Informationen zu Tupeln, Elementen oder Mengen in diesem Ausdruck zurück. Die [IsEmpty-Funktion &#40;MDX&#41;](/sql/mdx/isempty-mdx) wertet z.B. aus, ob ein Ausdruck einen leeren Zellenwert zurückgegeben hat. Weitere Informationen zu logischen Funktionen finden Sie unter [MDX-Funktionsreferenz &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="numeric-functions"></a>Numerische Funktionen  
 Eine numerische Funktion nimmt einen MDX-Ausdruck als Argument und gibt einen Skalarwert zurück. Die [Aggregate-Funktion &#40;MDX&#41;](/sql/mdx/aggregate-mdx) gibt z.B. einen Skalarwert zurück, der durch Aggregieren von Measures über die Tupel in einer angegebenen Menge berechnet wird. Weitere Informationen zu numerischen Funktionen finden Sie unter [MDX-Funktionsreferenz &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="string-functions"></a>Zeichenfolgenfunktionen  
 Eine Zeichenfolgenfunktion nimmt einen MDX-Ausdruck als Argument und gibt eine Zeichenfolge zurück. Die [UniqueName-Funktion &#40;MDX&#41;](/sql/mdx/uniquename-mdx) z.B. gibt einen Zeichenfolgenwert zurück, der den eindeutigen Namen einer Dimension, Hierarchie, Ebene oder eines Elements enthält. Weitere Informationen zu Zeichenfolgenfunktionen finden Sie unter [MDX-Funktionsreferenz &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegende Konzepte in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Grundlegendes zu MDX-Abfrage &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
