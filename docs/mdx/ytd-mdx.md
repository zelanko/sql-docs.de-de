---
title: YTD (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 67df625611f2451c3442d5d59b56c76dfc14a74a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743859"
---
# <a name="ytd-mdx"></a>Ytd (MDX)


  Gibt einen Satz von gleichgeordneten Elementen aus der gleichen Ebene wie ein angegebenes Element aus, beginnend mit dem ersten gleichgeordneten Element und endend mit dem angegebenen Element, entsprechend der Einschränkung durch die *Jahr* in der Zeitdimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Elementausdruck nicht angegeben ist, wird die Standardeinstellung ist das aktuelle Element der ersten Hierarchie mit einer Ebene des Typs *Jahre* in der ersten Dimension des Typs *Zeit* in der Measuregruppe.  
  
 Die **Ytd** Funktion ist eine Verknüpfungsfunktion für die [PeriodsToDate](../mdx/periodstodate-mdx.md) Funktion, die Typeigenschaft der Attributhierarchie, auf dem die Ebene basiert, auf festgelegt ist *Jahre*. Somit ist `Ytd(Member_Expression)` äquivalent zu `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Beachten Sie, die diese Funktion nicht verwendet werden, wenn die Type-Eigenschaft, um festgelegt ist *FiscalYears*.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt die Summe aus der `Measures.[Order Quantity]` Elements, aggregiert über die ersten acht Monate des Kalenderjahres 2003 in der `Date` Dimension, aus der **Adventure Works** Cube.  
  
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
  
 **YTD** wird häufig in Kombination verwendet, ohne Parameter angegeben wird, was bedeutet, dass die [CurrentMember &#40;MDX&#41; ](../mdx/currentmember-mdx.md) Funktion wird eine kumulative Summe der Jahr-bis-heute in einem Bericht angezeigt, entsprechend der folgende Abfrage:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
