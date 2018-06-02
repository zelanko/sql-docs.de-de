---
title: ParallelPeriod (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8cde031af19fff309520cd72e145b6c04dc19d9c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580822"
---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 Obwohl ähnelt der [Cousin](../mdx/cousin-mdx.md) -Funktion, die **ParallelPeriod** -Funktion enger mit Zeitreihen. Die **ParallelPeriod** Funktion nimmt den Vorgänger des angegebenen Elements auf der angegebenen Ebene, sucht nach dem Vorgänger gleichgeordnete Element mit der angegebenen Verzögerung und schließlich die parallele Periode des angegebenen Elements unter den nachfolgenden Werten des nebengeordneten Elements zurückgegeben.  
  
 Die **ParallelPeriod** Funktion weist die folgenden Standardwerte:  
  
-   Wenn weder ein Ebenenausdruck noch ein Elementausdruck angegeben ist, wird als standardelementwert das aktuelle Element der ersten Hierarchie auf der ersten Dimension vom Typ *Zeit* in der Measuregruppe.  
  
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
  
  
