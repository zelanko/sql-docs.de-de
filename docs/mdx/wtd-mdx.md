---
title: WTD (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eee40829c72394bf95a1bc06540a434a1c74e166
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125814"
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
  
  
