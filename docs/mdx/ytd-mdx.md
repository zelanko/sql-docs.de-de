---
title: Seit Jahresbeginn (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e3fcd823dea5d651cd7be9295fa4c6bba25380c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125762"
---
# <a name="ytd-mdx"></a>Ytd (MDX)


  Gibt einen Satz von gleichgeordneten Elementen aus der gleichen Ebene wie ein angegebenes Element, mit dem ersten gleichgeordneten Element beginnend und endend mit dem angegebenen Element, entsprechend der Einschränkung durch die *Jahr* Ebene in der Time-Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Elementausdruck nicht angegeben ist, wird der Standardwert ist das aktuelle Element der ersten Hierarchie mit einer Ebene des Typs *Jahre* in der ersten Dimension des Typs *Zeit* in der Measuregruppe.  
  
 Die **seit Jahresbeginn** -Funktion ist eine Verknüpfungsfunktion für die [PeriodsToDate](../mdx/periodstodate-mdx.md) Funktion, in denen die Typeigenschaft der Attributhierarchie, auf dem die Ebene basiert, auf ist *Jahre*. Somit ist `Ytd(Member_Expression)` äquivalent zu `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Beachten Sie, die diese Funktion nicht funktionieren, wenn die Type-Eigenschaft, um festgelegt ist *FiscalYears*.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt die Summe der der `Measures.[Order Quantity]` Elements, aggregiert über die ersten acht Monate des Kalenderjahres 2003, die in befinden die `Date` -Dimension, aus der **Adventure Works** Cube.  
  
```  
WITH MEMBER [Date].[Calendar].[First8MonthsCY2003] AS  
    Aggregate(  
        YTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First8MonthsCY2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **Seit Jahresbeginn** wird häufig in Kombination verwendet, ohne Parameter angegeben wird, was bedeutet, dass die [CurrentMember &#40;MDX&#41; ](../mdx/currentmember-mdx.md) Funktion wird eine kumulative Summe der Jahr-bis-heute in einem Bericht angezeigt, siehe die folgende Abfrage:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
