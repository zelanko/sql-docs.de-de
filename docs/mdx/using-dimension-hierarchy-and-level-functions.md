---
title: Mithilfe von Dimensions-, Hierarchie- und Ebenenfunktionen | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fb6460ed28c856ef6b5ceea8bf89c7bf33f54f2e
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743389"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Verwenden von Dimensions-, Hierarchie- und Ebenenfunktionen


  Mit Dimensions-, Hierarchie- und Ebenenfunktionen lassen sich die mehrdimensionalen Strukturen traversieren, die in Analysis Services zu finden sind. Üblicherweise verwenden Sie solche Funktionen zusammen mit anderen Funktionen dazu, Informationen zu den Elementen einer Dimension, Hierarchie oder Ebene abzurufen.  
  
 Das folgende Beispiel zeigt, wie Sie die **. Dimension**, **. Hierarchie**, und **. Ebene** Funktionen:  
  
 `WITH`  
  
 `MEMBER MEASURES.DIMENSIONNAME AS [Date].[Calendar].CURRENTMEMBER.DIMENSION.NAME`  
  
 `MEMBER MEASURES.HIERARCHYNAME AS [Date].[Calendar].CURRENTMEMBER.HIERARCHY.NAME`  
  
 `MEMBER MEASURES.LEVELNAME AS [Date].[Calendar].LEVEL.NAME`  
  
 `SELECT`  
  
 `{MEASURES.DIMENSIONNAME, MEASURES.HIERARCHYNAME, MEASURES.LEVELNAME}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Dimension &#40;MDX&#41;](../mdx/dimension-mdx.md)   
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)   
 [Hierarchie &#40;MDX&#41;](../mdx/hierarchy-mdx.md)   
 [Ebene &#40;MDX&#41;](../mdx/level-mdx.md)  
  
  
