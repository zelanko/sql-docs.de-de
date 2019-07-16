---
title: DrillupLevel (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ef2f94eb843b3ffbfbb67eb6ca01f2114522e024
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049219"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)


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
 Die **DrillupLevel** Funktion gibt eine Menge untergeordneter Elemente hierarchisch organisiert werden basierend auf den Elementen in der angegebenen Menge. Die Reihenfolge der Elemente in der angegebenen Menge wird beibehalten.  
  
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
  
  
