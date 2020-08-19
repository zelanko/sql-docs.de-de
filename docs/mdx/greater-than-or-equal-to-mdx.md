---
description: '&gt;= (Größer als oder gleich) (MDX)'
title: '&gt;= (Größer als oder gleich) (MDX) | Microsoft-Dokumentation'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1e9ce7d9f7e372ac9193751c258af63ba6f300fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429932"
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
  
  
