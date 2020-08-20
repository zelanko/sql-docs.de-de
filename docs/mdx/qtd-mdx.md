---
description: Qtd (MDX)
title: QTD (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea3bd80fa85d95dd3adf52793d5895425b40b9fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500453"
---
# <a name="qtd-mdx"></a>Qtd (MDX)


  Gibt eine Menge von gleich geordneten Elementen von der gleichen Ebene wie ein angegebenes Element zurück, beginnend mit dem ersten gleich geordneten Element, das mit dem angegebenen Element endet, wie von der *Quartals* Ebene in der Time-Dimension eingeschränkt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Qtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Member expressionis nicht angegeben ist, wird standardmäßig der aktuelle Member der ersten Hierarchie mit einer Ebene vom Typ " *Quartale* " in der ersten Dimension des Typs " *time* " in der Measure-Gruppe angegeben.  
  
 Die **QTD** -Funktion ist eine Verknüpfungs Funktion für die [PeriodsToDate-&#40;MDX&#41;](../mdx/periodstodate-mdx.md) -Funktion, deren ebenenausdrucks-Argument auf *Quarter*festgelegt ist. Somit ist `Qtd(Member_Expression)` funktionell äquivalent zu `PeriodsToDate(Quarter_Level_Expression, Member_Expression)`.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Summe des-Elements `Measures.[Order Quantity]` , aggregiert über die ersten zwei Monate des dritten Quartals des Kalender Jahrs 2003, das in der Dimension enthalten `Date` ist, aus dem **Adventure Works** -Cube zurückgegeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
