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
ms.openlocfilehash: 7a8856b28d8eec76d2bc262c4209b007c0a7fa04
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020639"
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
 Im folgenden Beispiel wird die Summe des `Measures.[Order Quantity]` -Elements, aggregiert über die ersten zwei Monate des dritten Quartals des Kalender Jahrs 2003, das in der `Date` Dimension enthalten ist, aus dem **Adventure Works** -Cube zurückgegeben.  
  
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
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
