---
description: Exists (MDX)
title: Vorhanden (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9c879d9091c692cfa7a93490b34c70ad84fa81c4
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193972"
---
# <a name="exists-mdx"></a>Exists (MDX)


  Gibt die Menge der Tupel der ersten angegebenen Menge zurück, die zusammen mit einem oder mehreren Tupeln der zweiten angegebenen Menge vorhanden sind. Diese Funktion führt die Operationen manuell aus, die Auto-exist automatisch ausführt. Weitere Informationen zu "automatisch vorhanden" finden Sie unter [Schlüsselkonzepte in MDX &#40;Analysis Services&#41;](/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services).  
  
 Wenn das optionale \<Measure Group Name> -bereitgestellt wird, gibt die-Funktion Tupel zurück, die mit einem oder mehreren Tupeln aus der zweiten Menge vorhanden sind, und den Tupeln, die Zeilen in der Fakten Tabelle der angegebenen Measure-Gruppe zugeordnet sind.  
  
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
  
## <a name="remarks"></a>Bemerkungen  
  
1.  Measure-Gruppen Zeilen mit Measures, die NULL-Werte enthalten, sind **vorhanden** , wenn das Argument "measregroupname" angegeben wird. Dies ist der Unterschied zwischen dieser Form von vorhanden und der NonEmpty-Funktion: Wenn die NullProcessing-Eigenschaft dieser Measures auf "preserve" festgelegt ist, bedeutet dies, dass die Measures NULL-Werte anzeigen, wenn Abfragen für diesen Teil des Cubes ausgeführt werden. NonEmpty entfernt immer Tupel aus einer Menge, die NULL-measurenwerte hat, während mit dem Argument "measregroupname" vorhanden ist, filtert keine Tupel mit zugeordneten Measure-Gruppen Zeilen, auch wenn die Measure-Werte NULL sind.  
  
2.  Wenn der Parameter " *measregroupname* " verwendet wird, sind die Ergebnisse davon abhängig, ob in der referenzierten Measure-Gruppe sichtbare Measures vorhanden sind. Wenn die Measure-Gruppe, auf die verwiesen wird, keine sichtbaren Measures enthält, gibt immer eine leere Menge zurück, unabhängig von den Werten *Set_Expression1* und *Set_Expression2*.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Crossjoin-&#40;MDX-&#41;](../mdx/crossjoin-mdx.md)   
 [NonEmptyCrossjoin-&#40;MDX-&#41;](../mdx/nonemptycrossjoin-mdx.md)   
 [Nicht leere &#40;MDX-&#41;](../mdx/nonempty-mdx.md)   
 [IsEmpty &#40;MDX-&#41;](../mdx/isempty-mdx.md)  
  
