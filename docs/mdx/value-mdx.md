---
title: Wert (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6eb91bb43407311a58e495b5f9391186821d3a67
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63251428"
---
# <a name="value-mdx"></a>Value (MDX)


  Gibt den Wert des aktuellen Elements der Measure-Dimension zurück, die sich mit dem aktuellen Element der Attributhierarchien im Kontext der Abfrage überschneidet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression[.Value]   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Wert** Funktion gibt den Wert des angegebenen Elements als Zeichenfolge. Die **Wert** Argument ist optional, da der Wert eines Elements die Standardeigenschaft eines Elements, und ist-Wert, der für ein Element zurückgegeben wird, wenn kein anderer Wert angegeben wird. Weitere Informationen zu Eigenschaften von Elementen, finden Sie unter [integrierte Elementeigenschaften &#40;MDX&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) und [benutzerdefinierte Elementeigenschaften &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Wert eines Elements sowie explizit dessen Name zurückgegeben.  
  
```  
WITH MEMBER [Date].[Calendar].NumericValue as [Date].[Calendar].[July 1, 2001].Value  
MEMBER [Date].[Calendar].MemberName AS [Date].[Calendar].[July 1, 2001].Name  
  
SELECT {[Date].[Calendar].NumericValue, [Date].[Calendar].MemberName} ON 0  
from [Adventure Works]  
```  
  
 Im folgenden Beispiel wird der Wert eines Elements als Standardwert für ein Element auf einer Achse zurückgegeben.  
  
```  
SELECT {[Date].[Calendar].[July 1, 2001]} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MemberValue &#40;MDX&#41;](../mdx/membervalue-mdx.md)   
 [Properties &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [Name &#40;MDX&#41;](../mdx/name-mdx.md)   
 [UniqueName &#40;MDX&#41;](../mdx/uniquename-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
