---
title: Verwenden von logischen Funktionen | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6bd427ebfca1fbf2f546603853b2352d6dcf4c90
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582462"
---
# <a name="using-logical-functions"></a>Verwenden von logischen Funktionen
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Eine logische Funktion führt eine logische Operation oder einen logischen Vergleich für Objekte sowie Ausdrücke aus und gibt einen booleschen Wert zurück. Logische Funktionen sind in MDX (Multidimensional Expressions) unverzichtbar, um die Position eines Elements zu ermitteln.  
  
 Die am häufigsten verwendete logische Funktion ist die **IsEmpty** Funktion. Weitere Informationen zum Verwenden der **IsEmpty** funktionieren, finden Sie unter [arbeiten mit leeren Werten](../mdx/working-with-empty-values.md).  
  
 Die folgende Abfrage zeigt, wie die **IsLeaf** und **IsAncestor** Funktionen:  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)  
  
  
