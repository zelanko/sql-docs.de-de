---
title: '&gt;= (Größer als oder gleich) (MDX) | Microsoft-Dokumentation'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0e8599378367dd47bd5858c09327795a25852105
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005842"
---
# <a name="gt-greater-than-or-equal-to-mdx"></a>&gt;= (Größer als oder gleich) (MDX)


  Führt eine Vergleichsoperation aus, die bestimmt, ob der Wert eines MDX-Ausdrucks (Multidimensional Expressions) größer oder gleich dem Wert eines anderen MDX-Ausdrucks ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MDX_Expression >= MDX_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der auf den folgenden Bedingungen basiert:  
  
-   **true** , wenn der erste Parameter über einen Wert verfügt, der entweder größer oder gleich dem Wert des zweiten Parameters ist.  
  
-   **false** , wenn der erste Parameter einen Wert hat, der kleiner ist als der Wert des zweiten Parameters.  
  
-   **true** , wenn beide Parameter NULL sind oder wenn ein Parameter NULL ist und der andere Parameter den Wert 0 hat.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators.  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is greater than or equal to 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] >= .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
    NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[HighGPM])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
