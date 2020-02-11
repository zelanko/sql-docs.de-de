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
ms.openlocfilehash: f373f626d778c4d77ec5843dca5bb11da728451d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887447"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **value** -Funktion gibt den Wert des angegebenen Elements als Zeichenfolge zurück. Das **value** -Argument ist optional, weil der Wert eines Members die Standard Eigenschaft eines Members ist, und ist ein Wert, der für ein Element zurückgegeben wird, wenn kein anderer Wert angegeben wird. Weitere Informationen zu Eigenschaften von Membern finden Sie unter systeminterne Element [Eigenschaften &#40;MDX-&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties) und [benutzerdefinierte Element Eigenschaften &#40;MDX-&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties).  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Mitgliedwert &#40;MDX-&#41;](../mdx/membervalue-mdx.md)   
 [Eigenschaften &#40;MDX-&#41;](../mdx/properties-mdx.md)   
 [Name &#40;MDX-&#41;](../mdx/name-mdx.md)   
 [UniqueName &#40;MDX-&#41;](../mdx/uniquename-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
