---
title: '- Davon (MDX) | Microsoft-Dokumentation'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cf0121d1be3cd2943a801f3c72ca4952b70ec681
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139079"
---
# <a name="except-mdx-operator"></a>Ausnahme (MDX)-Operator


  Führt eine Mengenoperation aus, die die Differenz zwischen zwei Mengen zurückgibt. Dabei werden doppelte Werte entfernt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression - Set_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Menge mit Elementen, die nicht in beiden angegebenen Parametern vorkommen.  
  
## <a name="remarks"></a>Bemerkungen  
 Der **-(außer)-** Operator ist funktionell gleichwertig mit der-Funktion [mit Ausnahme](../mdx/except-mdx-function.md) von.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators:  
  
```  
// This query shows the quantity of orders for all product categories  
// with the exception of Components.  
SELECT   
   [Measures].[Order Quantity] ON COLUMNS,  
   [Product].[Product Categories].[All].Children   
   - [Product].[Product Categories].[Components] ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
