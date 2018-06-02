---
title: MemberValue (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 33e91cadc6a63f6b55403aed552c6a15c8afc03d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580112"
---
# <a name="membervalue-mdx"></a>MemberValue (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt den Wert eines Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.MemberValue  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der zu einem Element ausgewertet wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Der zurückgegebene Elementwert enthält die folgenden Informationen, die in der Reihenfolge aufgelistet werden, in der diese im Rückgabewert angezeigt werden:  
  
-   Die Wertbindung, sofern diese definiert wurde.  
  
-   Der Schlüssel mit dem ursprünglichen Datentyp, wenn keine Namensbindung vorhanden ist bzw. der Schlüssel und die Beschriftung an dieselbe Spalte gebunden sind.  
  
-   Die Beschriftung des Elements.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Wertbindung, der Elementschlüssel sowie die Beschriftung für das erste Datum in der Date-Dimension im Adventure Works-Cube zurückgegeben.  
  
```  
WITH MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn}  ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
