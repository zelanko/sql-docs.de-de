---
title: Count (Dimension) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b84c5a1902e80f8abe3828f4be1b5d570ec026ce
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68104810"
---
# <a name="count-dimension-mdx"></a>Count (Dimension) (MDX)


  Gibt die Anzahl der Hierarchien in einem Cube zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Dimensions.Count   
```  
  
## <a name="remarks"></a>Bemerkungen  
 Gibt die Anzahl der Hierarchien in einem Cube zurück, einschließlich der `[Measures].[Measures]`-Hierarchie.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Anzahl der Hierarchien im Adventure Works-Cube zurückgegeben.  
  
```  
WITH MEMBER measures.X AS  
  dimensions.count   
SELECT Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Count &#40;Tupel&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [&#40;Hierarchieebenen&#41; &#40;MDX-&#41;zählen](../mdx/count-hierarchy-levels-mdx.md)   
 [Anzahl &#40;fest geleg&#41; &#40;MDX-&#41;](../mdx/count-set-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
