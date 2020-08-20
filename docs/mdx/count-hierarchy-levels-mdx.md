---
description: Count (Hierarchieebenen) (MDX)
title: Count (Hierarchieebenen) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a5ebf525df144b0fd1dd81ba5b223045b2ecfd88
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461642"
---
# <a name="count-hierarchy-levels-mdx"></a>Count (Hierarchieebenen) (MDX)


  Gibt die Anzahl der Ebenen in der Hierarchie zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchy_Expression.Levels.Count  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Gibt die Anzahl der Ebenen in einer Hierarchie zurück, ggf. einschließlich der `[All]`-Ebene.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension nur eine einzige sichtbare Hierarchie enthält, kann auf die Hierarchie entweder mit dem Dimensionsnamen oder mit dem Hierarchienamen verwiesen werden, weil der Dimensionsname in seine einzige sichtbare Hierarchie aufgelöst wird. `Measures.Levels.Count` ist z. B. ein gültiger MDX-Ausdruck, weil er in die einzige vorhandene Hierarchie in der Measures-Dimension aufgelöst wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Anzahl der Ebenen in der benutzerdefinierten Product Categories-Hierarchie des Adventure Works-Cubes zurückgegeben.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Product Categories].Levels.Count   
Select Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzahl &#40;Dimensions&#41; &#40;MDX-&#41;](../mdx/count-dimension-mdx.md)   
 [Count &#40;Tupel&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [Anzahl &#40;fest geleg&#41; &#40;MDX-&#41;](../mdx/count-set-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
