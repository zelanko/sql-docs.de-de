---
title: IsAncestor (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8aacd6825a81ff172d8fdf79373f5b251d6e18b9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62653470"
---
# <a name="isancestor-mdx"></a>IsAncestor (MDX)


  Gibt zurück, ob ein angegebenes Element ein Vorgänger eines anderen angegebenen Elements ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Member_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **IsAncestor** -Funktion zurückgegeben **"true"** das erste angegebene Element ein Vorgänger des zweiten Elements angegeben ist. Die Funktion hingegen gibt **"false"** .  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel zurückgegeben **"true"** Wenn [Date]. [ Fiscal]. CurrentMember ist ein Vorgänger von Januar 2003:  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Ancestor &#40;MDX&#41;](../mdx/ancestor-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
