---
title: Member-Funktionen mit | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1c9979b6b9fcb04115695cbe8d9c224e1c6c1f57
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63251596"
---
# <a name="using-member-functions"></a>Verwenden von Elementfunktionen


  Eine Elementfunktion ist eine Multidimensional Expressions (MDX)-Funktion, die ein Element zurückgibt. Elementfunktionen sind genau wie Tupelfunktionen und Mengenfunktionen wesentlich für das Aushandeln mehrdimensionaler Strukturen, die in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zu finden sind.  
  
 Von den zahlreichen Elementfunktionen in MDX, am wichtigsten ist die **CurrentMember** -Funktion, die verwendet wird, um das aktuelle Element in einer Hierarchie zu ermitteln. Die folgende Abfrage veranschaulicht, wie sie zusammen mit den **übergeordneten**, **Vorgänger**, und **Prevmember** Funktionen:  
  
 `WITH`  
  
 `//Returns the name of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[CurrentMemberDemo] AS [Date].[Calendar].CurrentMember.Name`  
  
 `//Returns the name of the parent of the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[ParentDemo] AS [Date].[Calendar].CurrentMember.Parent.Name`  
  
 `//Returns the name of the ancestor of the currentmember on the Calendar hierarchy at the Year level`  
  
 `MEMBER MEASURES.[AncestorDemo] AS ANCESTOR([Date].[Calendar].CurrentMember, [Date].[Calendar].[Calendar Year]).Name`  
  
 `//Returns the name of the member before the currentmember on the Calendar hierarchy`  
  
 `MEMBER MEASURES.[PrevMemberDemo] AS [Date].[Calendar].CurrentMember.Prevmember.Name`  
  
 `SELECT{MEASURES.[CurrentMemberDemo],MEASURES.[ParentDemo],MEASURES.[AncestorDemo],MEASURES.[PrevMemberDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)   
 [Verwenden von Tupelfunktionen](../mdx/using-tuple-functions.md)   
 [Using Set Functions (Verwenden von Mengenfunktionen)](../mdx/using-set-functions.md)  
  
  
