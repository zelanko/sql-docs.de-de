---
description: Item (Element) (MDX)
title: Item (Member) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a374d1fcc7f972828832c2f82375acf640d45fb2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483963"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **Item** -Funktion gibt ein Element aus dem angegebenen Tupel zurück. Die-Funktion gibt das Element zurück, das an der durch *Index*angegebenen Null basierten Position gefunden wurde.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Element `[2003]` auf Spalten zurückgegeben - das erste Element im Tupel `[Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).`:  
  
 `SELECT`  
  
 `{( [Date].[Calendar Year].&[2003], [Measures].[Internet Sales Amount] ).Item(0)} ON 0`  
  
 `,{[Measures].[Reseller Sales Amount]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
