---
title: CurrentMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7d47e12b95a92930bbdfceaba5cc8997c286eec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248891"
---
# <a name="currentmember-mdx"></a>CurrentMember (MDX)


  Gibt das aktuelle Element entlang einer angegebenen Hierarchie während einer Iteration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchy_Expression.CurrentMember  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Bei der Iteration durch eine Menge von Hierarchieelementen stellt bei jedem Iterationsschritt das jeweils bearbeitete Element das aktuelle Element dar. Die **CurrentMember** Funktion gibt dieses Element zurück.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension nur eine einzige sichtbare Hierarchie enthält, kann auf die Hierarchie entweder mit dem Dimensionsnamen oder mit dem Hierarchienamen verwiesen werden, weil der Dimensionsname in seine einzige sichtbare Hierarchie aufgelöst wird. `Measures.CurrentMember` ist z. B. ein gültiger MDX-Ausdruck, weil er in die einzige vorhandene Hierarchie in der Measures-Dimension aufgelöst wird.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage zeigt, wie **Currentmember** können verwendet werden, um das aktuelle Element aus Hierarchien für die Spalten, Zeilen und Slice-Achse zu finden:  
  
 `WITH MEMBER MEASURES.CURRENTDATE AS`  
  
 `[Date].[Calendar].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTPRODUCT AS`  
  
 `[Product].[Product Categories].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTMEASURE AS`  
  
 `MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTCUSTOMER AS`  
  
 `[Customer].[Customer Geography].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `[Product].[Product Categories].[Category].MEMBERS`  
  
 `*`  
  
 `{MEASURES.CURRENTDATE, MEASURES.CURRENTPRODUCT,MEASURES.CURRENTMEASURE, MEASURES.CURRENTCUSTOMER}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Customer].[Customer Geography].[Country].&[Australia])`  
  
 Das aktuelle Element ändert sich in einer Hierarchie, die auf einer Achse in einer Abfrage verwendet wird. Aus diesem Grund kann das aktuelle Element in anderen Hierarchien derselben Dimension, die nicht auf einer Achse verwendet werden, auch ändern; Dieses Verhalten wird aufgerufen, "Auto-exist" und Weitere Informationen finden Sie im [Schlüsselkonzepte in MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md). Die folgende Abfrage zeigt beispielsweise, wie sich das aktuelle Element in der Calendar Year-Hierarchie der Date-Dimension mit dem aktuellen Element der Calendar-Hierarchie ändert, wenn dieses auf der ROWS-Achse angezeigt wird:  
  
 `WITH MEMBER MEASURES.CURRENTYEAR AS`  
  
 `[Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `{MEASURES.CURRENTYEAR}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 **CurrentMember** ist sehr wichtig, um Berechnungen über den Kontext der Abfrage im verwendet wird. Das folgende Beispiel gibt die Bestellmenge jedes Produkts sowie den Prozentsatz der Bestellmengen nach Kategorie und Modell aus der **Adventure Works** Cube. Die **CurrentMember** -Funktion identifiziert das Produkt, dessen Bestellmenge während der Berechnung verwendet werden wird.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty  
(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
