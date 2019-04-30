---
title: QTD (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 182a86a05cd0dae6adf85d2168fe884ace910a82
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63278419"
---
# <a name="qtd-mdx"></a>Qtd (MDX)


  Gibt einen Satz von gleichgeordneten Elementen aus der gleichen Ebene wie ein angegebenes Element, mit dem ersten gleichgeordneten Element beginnend und endend mit dem angegebenen Element, entsprechend der Einschränkung durch die *Quartal* Ebene in der Time-Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Element AusdruckIS nicht angegeben ist, wird standardmäßig das aktuelle Element der ersten Hierarchie mit einer Ebene des Typs *Quartale* in der ersten Dimension des Typs *Zeit* in der Measuregruppe.  
  
 Die **Qtd** -Funktion ist eine Verknüpfungsfunktion für die [PeriodsToDate &#40;MDX&#41; ](../mdx/periodstodate-mdx.md) Funktion, deren Ebenenausdruck-Argument NA hodnotu nastaven *Quartal*. Somit ist `Qtd(Member_Expression)` funktionell äquivalent zu `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt die Summe der der `Measures.[Order Quantity]` Elements, aggregiert über die ersten zwei Monate des dritten Quartals des Kalenderjahres 2003, die in befinden die `Date` -Dimension, aus der **Adventure Works** Cube.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        QTD([Date].[Calendar].[Month].[August 2003])  
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
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
