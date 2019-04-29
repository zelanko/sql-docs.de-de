---
title: + (Union) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: be12a1af53957ab0d8f3347a0464dd987152bca0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63129824"
---
# <a name="union---mdx-operator-reference"></a>Union - MDX-operatorreferenz


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
  
## <a name="remarks"></a>Hinweise  
 Die **+ (Union)** Operator ist funktionell gleichwertig mit der [Union &#40;MDX&#41; ](../mdx/union-mdx.md) Funktion.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
