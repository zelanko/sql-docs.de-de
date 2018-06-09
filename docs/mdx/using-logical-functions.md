---
title: Verwenden von logischen Funktionen | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a63d8cb22a8533cf352acb690f87916e2e9d568d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743519"
---
# <a name="using-logical-functions"></a>Verwenden von logischen Funktionen


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
  
  
