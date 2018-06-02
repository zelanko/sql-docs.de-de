---
title: DrillupLevel (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19d6443857d53d835db4c395ddd43dc4a305ad8c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579452"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt einen Drillup bei Elementen einer Menge aus, die sich unterhalb einer angegebenen Ebene befinden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **DrillupLevel** Funktion gibt eine Menge von Elementen hierarchisch organisiert basierend auf den Elementen in der angegebenen Menge. Die Reihenfolge der Elemente in der angegebenen Menge wird beibehalten.  
  
 Wenn ein Ebenenausdruck angegeben wird, die **DrillupLevel** Funktion erstellt die Menge, indem nur die Elemente, die über der angegebenen Ebene abgerufen. Wenn ein Mengenausdruck angegeben ist und kein Element der angegebenen Ebene in der angegebenen Menge vorhanden ist, wird die angegebene Menge zurückgegeben.  
  
 Wenn kein Ebenenausdruck angegeben wird, erstellt die Funktion die Menge, indem nur die Elemente eine Ebene über der untersten Ebene der ersten Dimension abgerufen werden, auf die in der angegebenen Menge verwiesen wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Menge der Elemente oberhalb der Subcategory-Ebene aus der ersten Menge zurückgegeben.  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
