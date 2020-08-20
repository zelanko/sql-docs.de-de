---
description: PeriodsToDate (MDX)
title: PeriodsToDate (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8b18fe4d90a8a0c56424c5e0a7f3607ceea0eae4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471702"
---
# <a name="periodstodate-mdx"></a>PeriodsToDate (MDX)


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
  
## <a name="remarks"></a>Bemerkungen  
 Innerhalb des Bereichs der angegebenen Ebene gibt die **PeriodsToDate** -Funktion den Satz von Zeiträumen auf derselben Ebene wie das angegebene Element zurück, beginnend mit dem ersten Zeitraum und endet mit dem angegebenen Element.  
  
-   Wenn eine Ebene angegeben wird, wird das aktuelle Element der *Hierarchie abgeleitet.* **CurrentMember**, wobei *Hierarchie*die Hierarchie der angegebenen Ebene ist.  
  
-   Wenn weder eine Ebene noch ein Element angegeben wird, ist die Ebene die übergeordnete Ebene des aktuellen Elements der ersten Hierarchie auf der ersten Dimension des Typs Zeit in der Measuregruppe.  
  
 `PeriodsToDate( Level_Expression, Member_Expression )` ist funktionell gleichwertig mit dem folgenden MDX-Ausdruck:  
  
 `TopCount(Descendants(Ancestor(Member_Expression, Level_Expression), Member_Expression.Level), 1):Member_Expression`  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Summe des-Elements `Measures.[Order Quantity]` , aggregiert über die ersten acht Monate des Kalender Jahrs 2003, das in der `Date` Dimension enthalten ist, aus dem **Adventure Works** -Cube zurückgegeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [TopCount &#40;MDX-&#41;](../mdx/topcount-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
