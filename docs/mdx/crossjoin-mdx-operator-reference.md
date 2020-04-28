---
title: '* Crossjoin (MDX) | Microsoft-Dokumentation'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2f8377acec8f213c423de5d19d8859c8b3d93a06
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68047139"
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin-MDX-Operator Referenz


  Führt eine Mengenoperation aus, die das Kreuzprodukt zweier Mengen zurückgibt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>Parameter  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Menge, die das Kreuzprodukt der beiden angegebenen Parameter enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Der ** \* (Crossjoin)** -Operator ist funktionell gleichwertig mit der [Crossjoin](../mdx/crossjoin-mdx.md) -Funktion.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators.  
  
```  
-- This query returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
