---
title: ParallelPeriod (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c1f495ce1fad9a318ea5e6c1f3fadd88f8313cd6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63473078"
---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (MDX)


  Gibt ein Element aus einer früheren Periode in derselben relativen Position wie ein angegebenes Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Index*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der parallelen Perioden angibt, die vor dem Element liegen sollen.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Zwar ähnlich wie die [Cousin](../mdx/cousin-mdx.md) -Funktion, die **ParallelPeriod** -Funktion enger mit Zeitreihen. Die **ParallelPeriod** Funktion nimmt den Vorgänger des angegebenen Elements auf der angegebenen Ebene, sucht nach den Vorgänger des gleichgeordnetes Element mit der angegebenen Verzögerung und gibt schließlich die parallele Periode des angegebenen Elements unter den die nachfolgenden Elemente des nebengeordneten Elements.  
  
 Die **ParallelPeriod** Funktion besitzt die folgenden Standardwerte:  
  
-   Wenn weder ein Ebenenausdruck noch ein Elementausdruck angegeben ist, wird als standardelementwert das aktuelle Element der ersten Hierarchie auf der ersten Dimension des Typs *Zeit* in der Measuregruppe.  
  
-   Wenn ein Ebenenausdruck angegeben ist, aber ein Elementausdruck nicht angegeben ist, wird als standardelementwert *Level_Expression*. **Hierarchy.CurrentMember**.  
  
-   Der Standardindexwert ist 1.  
  
-   Die Standardebene ist die Ebene des dem angegebenen Element übergeordneten Elements.  
  
 Die **ParallelPeriod** -Funktion ist gleichbedeutend mit der folgenden MDX-Anweisung:  
  
 `Cousin(Member_Expression, Ancestor(Member_Expression, Level_Expression) .Lag(Numeric_Expression))`  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird basierend auf der Quarter-Ebene die parallele Periode für den Monat Oktober 2003 zurückgegeben, die drei Perioden zurückliegt, d. h. der Monat Januar 2003.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Quarter]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird basierend auf der Semester-Ebene die parallele Periode für den Monat Oktober 2003 zurückgegeben, die drei Perioden zurückliegt, d. h. der Monat April 2002.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Semester]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
