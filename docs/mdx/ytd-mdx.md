---
description: Ytd (MDX)
title: YTD (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 14f286a304e03624a9ce20c1bd7b045dffc38688
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491368"
---
# <a name="ytd-mdx"></a>Ytd (MDX)


  Gibt eine Menge von gleich geordneten Elementen von der gleichen Ebene wie ein angegebenes Element zurück, beginnend mit dem ersten gleich geordneten Element, das mit dem angegebenen Element endet, wie von der *year* -Ebene in der Time-Dimension eingeschränkt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn kein Element Ausdruck angegeben ist, wird standardmäßig der aktuelle Member der ersten Hierarchie mit einer Ebene des Typs " *years* " in der ersten Dimension des Typs " *time* " in der Measure-Gruppe angegeben.  
  
 Die **YTD** -Funktion ist eine Verknüpfungs Funktion für die [PeriodsToDate](../mdx/periodstodate-mdx.md) -Funktion, bei der die Type-Eigenschaft der Attribut Hierarchie, auf der die Ebene basiert, auf *years*festgelegt ist. Somit ist `Ytd(Member_Expression)` äquivalent zu `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Beachten Sie, dass diese Funktion nicht funktioniert, wenn die Type-Eigenschaft auf " *fscalyears*" festgelegt ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Summe des-Elements `Measures.[Order Quantity]` , aggregiert über die ersten acht Monate des Kalender Jahrs 2003, das in der `Date` Dimension enthalten ist, aus dem **Adventure Works** -Cube zurückgegeben.  
  
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
  
 **YTD** wird häufig in Kombination mit nicht angegebenen Parametern verwendet. Dies bedeutet, dass die [CurrentMember-&#40;MDX-&#41;](../mdx/currentmember-mdx.md) Funktion eine laufende kumulative Jahressumme in einem Bericht anzeigt, wie in der folgenden Abfrage dargestellt:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
