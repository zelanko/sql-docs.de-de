---
title: Count (Dimension) (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd8d61e7907a8fb05a016dabdcb65201bffdbbdc
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577642"
---
# <a name="count-dimension-mdx"></a>Count (Dimension) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Anzahl der Hierarchien in einem Cube zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Hinweise  
 Gibt die Anzahl der Hierarchien in einem Cube zurück, einschließlich der `[Measures].[Measures]`-Hierarchie.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Anzahl der Hierarchien im Adventure Works-Cube zurückgegeben.  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anzahl &#40;Tupel&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [Anzahl &#40;Hierarchieebenen&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Anzahl &#40;festgelegt&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
