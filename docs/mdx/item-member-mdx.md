---
title: Item (Element) (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7cb7c3825f2a319282788c222a7ebb46cec2b532
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578832"
---
# <a name="item-member-mdx"></a>Item (Element) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
  
