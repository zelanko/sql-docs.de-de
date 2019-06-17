---
title: Verwenden von Dimensions-, Hierarchie- und Ebenenfunktionen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62982190"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Verwenden von Dimensions-, Hierarchie- und Ebenenfunktionen


  Mit Dimensions-, Hierarchie- und Ebenenfunktionen lassen sich die mehrdimensionalen Strukturen traversieren, die in Analysis Services zu finden sind. Üblicherweise verwenden Sie solche Funktionen zusammen mit anderen Funktionen dazu, Informationen zu den Elementen einer Dimension, Hierarchie oder Ebene abzurufen.  
  
 Das folgende Beispiel zeigt, wie Sie mit der **. Dimension**, **. Hierarchie**, und **. Ebene** Funktionen:  
  
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
 [Hierarchy &#40;MDX&#41;](../mdx/hierarchy-mdx.md)   
 [Level &#40;MDX&#41;](../mdx/level-mdx.md)  
  
  
