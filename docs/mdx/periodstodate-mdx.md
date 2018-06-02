---
title: PeriodsToDate (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9d5e15800ed0f7118e14a90d7879faa5cef9bcd7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580892"
---
# <a name="periodstodate-mdx"></a>PeriodsToDate (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt eine Menge von gleichgeordneten Elementen zurück, die derselben Ebene angehören wie ein angegebenes Element. Die Menge beginnt mit dem ersten gleichgeordneten Element und endet mit dem angegebenen Element, entsprechend der Einschränkung durch die angegebene Ebene in der Time-Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PeriodsToDate( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Innerhalb des Bereichs der angegebenen Ebene der **PeriodsToDate** -Funktion die Menge der Zeiträume auf derselben Ebene wie die angegebenen Member auf, angefangen mit der ersten Periode und endend mit angegebenen Element zurück.  
  
-   Wenn eine Ebene angegeben ist, wird das aktuelle Element der Hierarchie abgeleitet *Hierarchie*. **CurrentMember**, wobei *Hierarchie*ist die Hierarchie der angegebenen Ebene.  
  
-   Wenn weder eine Ebene noch ein Element angegeben wird, ist die Ebene die übergeordnete Ebene des aktuellen Elements der ersten Hierarchie auf der ersten Dimension des Typs Zeit in der Measuregruppe.  
  
 `PeriodsToDate( Level_Expression, Member_Expression )` ist funktionell gleichwertig mit dem folgenden MDX-Ausdruck:  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die Summe aus der `Measures.[Order Quantity]` Elements, aggregiert über die ersten acht Monate des Kalenderjahres 2003 in der `Date` Dimension, aus der **Adventure Works** Cube.  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Im folgenden Beispiel wird über die ersten zwei Monate des zweiten Semesters des Kalenderjahres 2003 aggregiert.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
