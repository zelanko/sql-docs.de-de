---
description: Union-MDX-Operator Referenz
title: + Union (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 84e6bc2b6b8460b90013ade5f0981af7f0ed8432
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341189"
---
# <a name="union---mdx-operator-reference"></a>Union-MDX-Operator Referenz


  Führt eine Mengenoperation aus, die die Vereinigungsmenge zweier Mengen zurückgibt. Dabei werden doppelte Elemente entfernt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>Parameter  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Menge, die die Elemente der beiden angegebenen Mengen enthält.  
  
## <a name="remarks"></a>Bemerkungen  
 Der **+ (Union)** -Operator ist funktionell gleichwertig mit der&#41;-Funktion der [Union-&#40;MDX ](../mdx/union-mdx.md) .  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators.  
  
```  
-- This member returns the gross profit margin for each year for North American countries.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members ON 0,  
    {[Sales Territory].[Sales Territory].[Country].[United States]} +  
     {[Sales Territory].[Sales Territory].[Country].[Canada]} ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
