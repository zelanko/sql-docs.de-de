---
title: IsAncestor (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 59c997398ce7a3e4477136d1c5ef2ebcd2686e2d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578622"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt zurück, ob ein angegebenes Element ein Vorgänger eines anderen angegebenen Elements ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Argumente  
 *Element_Ausdruck1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Element_Ausdruck2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **IsAncestor** -Funktion gibt **"true"** das erste angegebene Element ein Vorgänger des zweiten Elements angegeben ist. Die Funktion hingegen gibt **"false"**.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt **"true"** Wenn [Date]. [ Fiscal]. CurrentMember ist ein Vorgänger von Januar 2003:  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgänger &#40;MDX&#41;](../mdx/ancestor-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
