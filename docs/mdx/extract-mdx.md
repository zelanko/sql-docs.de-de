---
title: Extrahieren (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a3c58799cc3e95efd7d49b3aff0bf31a1fce22b1
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740309"
---
# <a name="extract-mdx"></a>Extract (MDX)


  Gibt eine Menge von Tupeln aus extrahierten Hierarchieelementen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Hierarchy_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Hierarchy_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **extrahieren** -Funktion eine Menge, die aus Tupeln aus den extrahierten Hierarchieelementen besteht zurück. Zu jedem Tupel in der angegebenen Menge werden die Elemente der angegebenen Hierarchien in neue Tupel im Resultset extrahiert. Doppelte Tupel werden von der Funktion immer entfernt.  
  
 Die **extrahieren** Funktion führt die umkehraktion der [Crossjoin](../mdx/crossjoin-mdx.md) Funktion.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage zeigt, wie die **extrahieren** Funktion für eine Menge von Tupeln, die zurückgegeben werden, indem Sie die **NonEmpty** Funktion:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
