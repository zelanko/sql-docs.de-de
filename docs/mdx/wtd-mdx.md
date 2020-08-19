---
description: Wtd (MDX)
title: WTD (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b45e583da6f7fc18712e432a0c504c3bc813141e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421884"
---
# <a name="wtd-mdx"></a>Wtd (MDX)


  Gibt eine Menge von gleichgeordneten Elementen zurück, die derselben Ebene angehören wie ein angegebenes Element. Die Menge beginnt mit dem ersten gleichgeordneten Element und endet mit dem angegebenen Element, entsprechend der Einschränkung durch die Week-Ebene in der Time-Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Wtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn kein Element Ausdruck angegeben ist, wird standardmäßig der aktuelle Member der ersten Hierarchie mit einer Ebene vom Typ "Wochen" in der ersten Dimension des Typs "Time **. CurrentMember**" in der Measure-Gruppe angegeben.  
  
 Die **WTD** -Funktion ist eine Verknüpfungs Funktion für die [PeriodsToDate](../mdx/periodstodate-mdx.md) -Funktion, bei der die Ebene auf *Wochen*festgelegt ist. Somit ist `Wtd(Member_Expression)` äquivalent zu `PeriodsToDate(Week_Level_Expression,Member_Expression)`.  
  
## <a name="see-also"></a>Weitere Informationen  
 [QTD-&#40;MDX-&#41;](../mdx/qtd-mdx.md)   
 [MTD-&#40;MDX-&#41;](../mdx/mtd-mdx.md)   
 [YTD-&#40;MDX-&#41;](../mdx/ytd-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
