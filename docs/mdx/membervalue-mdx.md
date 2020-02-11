---
title: Mitgliedwert (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4db81766060f8f1afde2241d0c89407ad3cbb864
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001406"
---
# <a name="membervalue-mdx"></a>MemberValue (MDX)


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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
