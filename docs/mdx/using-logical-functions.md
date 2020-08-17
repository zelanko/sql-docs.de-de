---
description: Verwenden von logischen Funktionen
title: Verwenden von logischen Funktionen | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2a13f9fa95878277b164b37bb71e3d9af646d89f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340996"
---
# <a name="using-logical-functions"></a>Verwenden von logischen Funktionen


  Eine logische Funktion führt eine logische Operation oder einen logischen Vergleich für Objekte sowie Ausdrücke aus und gibt einen booleschen Wert zurück. Logische Funktionen sind in MDX (Multidimensional Expressions) unverzichtbar, um die Position eines Elements zu ermitteln.  
  
 Die am häufigsten verwendete logische Funktion ist die **IsEmpty** -Funktion. Weitere Informationen zur Verwendung der **IsEmpty** -Funktion finden Sie unter [Arbeiten mit leeren Werten](../mdx/working-with-empty-values.md).  
  
 Die folgende Abfrage zeigt, wie die Funktionen **IsLeaf** und **isvorgänger** verwendet werden:  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)  
  
  
