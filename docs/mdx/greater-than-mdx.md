---
title: '&gt;(Größer als) (MDX) | Microsoft-Dokumentation'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bb4f04e623096857cce9dd27f0cddc77f6a59798
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67906030"
---
# <a name="gt-greater-than-mdx"></a>&gt;(Größer als) MDX


  Führt eine Vergleichsoperation aus, die bestimmt, ob der Wert eines MDX-Ausdrucks (Multidimensional Expressions) größer als der Wert eines anderen MDX-Ausdrucks ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MDX_Expression > MDX_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der auf den folgenden Bedingungen basiert:  
  
-   **true** , wenn beide Parameter ungleich NULL sind und der erste Parameter einen Wert hat, der größer ist als der Wert des zweiten Parameters.  
  
-   **false** , wenn beide Parameter ungleich NULL sind und der erste Parameter einen Wert hat, der entweder gleich oder kleiner als der Wert des zweiten Parameters ist.  
  
-   NULL, wenn mindestens einer der Parameter zu einem NULL-Wert ausgewertet wird.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Beispielabfrage zeigt die Verwendung dieses Operators.  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is more than 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] > .5,  
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
  
  
