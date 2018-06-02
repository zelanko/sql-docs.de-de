---
title: '* (Crossjoin) (MDX) | Microsoft Docs'
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 03a229dd7ab766a858967eb8c4891edadaaa6b92
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577632"
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin - MDX-Operatorreferenz
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Hinweise  
 Die  **\* (Crossjoin)** Operator ist funktionell gleichwertig mit der [Crossjoin](../mdx/crossjoin-mdx.md) Funktion.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
