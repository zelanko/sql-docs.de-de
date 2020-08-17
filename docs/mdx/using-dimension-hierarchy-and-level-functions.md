---
description: Verwenden von Dimensions-, Hierarchie- und Ebenenfunktionen
title: Verwenden von Dimensions-, Hierarchie-und Level-Funktionen | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: afb7d324a2a4450a4df09ec3493954f0566a2cfc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341106"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Verwenden von Dimensions-, Hierarchie- und Ebenenfunktionen


  Mit Dimensions-, Hierarchie- und Ebenenfunktionen lassen sich die mehrdimensionalen Strukturen traversieren, die in Analysis Services zu finden sind. Üblicherweise verwenden Sie solche Funktionen zusammen mit anderen Funktionen dazu, Informationen zu den Elementen einer Dimension, Hierarchie oder Ebene abzurufen.  
  
 Im folgenden Beispiel wird gezeigt, wie verwendet wird **. Dimension**, **. Hierarchie**und **. Level** -Funktionen:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions &#40;MDX-&#41;](../mdx/dimension-mdx.md)   
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)   
 [Hierarchie &#40;MDX-&#41;](../mdx/hierarchy-mdx.md)   
 [&#41;der Ebene &#40;MDX ](../mdx/level-mdx.md)  
  
  
