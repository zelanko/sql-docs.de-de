---
description: ParallelPeriod (MDX)
title: ParallelPeriod (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4c8a6c91bae50ca06be46926f34de172e424e613
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471722"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **ParallelPeriod** -Funktion ist zwar vergleichbar mit der [Cousin](../mdx/cousin-mdx.md) -Funktion, ist jedoch enger mit der Zeitreihe verknüpft. Die **ParallelPeriod** -Funktion nimmt den Vorgänger des angegebenen Elements auf der angegebenen Ebene, sucht das gleich geordnete Element mit dem angegebenen Rückstand und gibt schließlich den parallelen Zeitraum des angegebenen Elements unter den nachfolgenden Werten des gleich geordneten Elements zurück.  
  
 Die **ParallelPeriod** -Funktion hat die folgenden Standardwerte:  
  
-   Wenn weder ein Ebenenausdruck noch ein Element Ausdruck angegeben ist, ist der Standardelement Wert das aktuelle Element der ersten Hierarchie in der ersten Dimension mit einem *Zeit* Elementtyp in der Measure-Gruppe.  
  
-   Wenn ein Ebenenausdruck angegeben wird, aber kein Element Ausdruck angegeben ist, wird der Standardelement Wert *Level_Expression*. **Hierarchy. CurrentMember**.  
  
-   Der Standardindexwert ist 1.  
  
-   Die Standardebene ist die Ebene des dem angegebenen Element übergeordneten Elements.  
  
 Die **ParallelPeriod** -Funktion entspricht der folgenden MDX-Anweisung:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
