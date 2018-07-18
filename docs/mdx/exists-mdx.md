---
title: Vorhanden ist (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7237a4023bf9ad67f0050951b60b1ee33db4a53f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740609"
---
# <a name="exists-mdx"></a>Exists (MDX)


  Gibt die Menge der Tupel der ersten angegebenen Menge zurück, die zusammen mit einem oder mehreren Tupeln der zweiten angegebenen Menge vorhanden sind. Diese Funktion führt die Operationen manuell aus, die Auto-exist automatisch ausführt. Weitere Informationen zu Auto vorhanden ist, finden Sie unter [Schlüsselkonzepte in MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
 Wenn das optionale \<Measuregruppenname > angegeben wird, gibt die Funktion mit einem oder mehreren Tupeln vorhanden Tupel zurück, aus der zweiten Menge und solchen Tupeln, die Zeilen in der Faktentabelle der angegebenen Measuregruppe zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Exists( Set_Expression1 , Set_Expression2 [, MeasureGroupName] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *MeasureGroupName*  
 Ein gültiger Zeichenfolgenausdruck, der einen Measuregruppennamen angibt.  
  
## <a name="remarks"></a>Hinweise  
  
1.  Measuregruppenzeilen mit Measures, die null-Werte zu beitragen **Exists** Wenn das MeasureGroupName-Argument angegeben wird. Das ist der Unterschied zwischen dieser Form von Exists and der Nonempty-Funktion: wenn die NullProcessing-Eigenschaft dieser Measures als Preserve festgelegt ist, zeigen die Measures Null-Werte, wenn Abfragen für diesen Teil des Cubes ausgeführt werden; NonEmpty entfernt immer Tupel aus einem Satz, der NULL-Measurewerte hat, während Exists mit dem MeasureGroupName-Argument keine Tupel filtert, denen Measuregruppenzeilen zugeordnet sind, auch wenn die Measurewerte NULL sind.  
  
2.  Wenn *MeasureGroupName* Parameter verwendet wird, hängen Ergebnisse, ob es sichtbare Measures in der referenzierten Measuregruppe gibt; Wenn es keine sichtbaren Measures in der referenzierten Measuregruppe gibt EXISTS gibt stets eine leere Menge, unabhängig von den Werten der *Set_Expression1* und *Set_Expression2*.  
  
## <a name="examples"></a>Beispiele  
 Kunden in Kalifornien:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
) ON 1   
FROM [Adventure Works]  
  
```  
  
 Kunden in Kalifornien und Umsätze:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Customer].[State-Province].&[CA]&[US]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Kunden und Umsätze:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, , "Internet Sales") ON 1   
FROM [Adventure Works]  
  
```  
  
 Kunden, die Fahrräder gekauft haben:  
  
```  
SELECT [Measures].[Internet Sales Amount] ON 0,  
EXISTS(  
[Customer].[Customer].[Customer].MEMBERS  
, {[Product].[Product Categories].[Category].&[1]}  
, "Internet Sales") ON 1   
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Crossjoin &#40;MDX&#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [NonEmpty &#40;MDX&#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)  
  
  
