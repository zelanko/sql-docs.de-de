---
title: Item (Element) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92745085a408503a2b435eb160daf431c7fdaa32
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740339"
---
# <a name="item-member-mdx"></a>Item (Element) (MDX)


  Gibt ein Element aus einem angegebenen Tupel zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Tuple_Expression.Item( Index )  
```  
  
## <a name="arguments"></a>Argumente  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
 *Index*  
 Ein gültiger numerischer Ausdruck, der ein bestimmtes Element über die Position im zurückzugebenden Tupel angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Element** Funktion gibt ein Element aus dem angegebenen Tupel zurück. Die Funktion gibt das Element finden Sie unter der vom angegebenen nullbasierten Position *Index*.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Element `[2003]` auf Spalten zurückgegeben - das erste Element im Tupel `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).`:  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
