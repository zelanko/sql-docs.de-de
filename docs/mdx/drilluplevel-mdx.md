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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **DrillupLevel** -Funktion gibt basierend auf den Membern, die in der angegebenen Menge enthalten sind, eine hierarchisch strukturierte Menge von Membern zurück. Die Reihenfolge der Elemente in der angegebenen Menge wird beibehalten.  
  
 Wenn ein Ebenenausdruck angegeben wird, erstellt die **DrillupLevel** -Funktion die Menge, indem nur die Elemente abgerufen werden, die sich oberhalb der angegebenen Ebene befinden. Wenn ein Mengenausdruck angegeben ist und kein Element der angegebenen Ebene in der angegebenen Menge vorhanden ist, wird die angegebene Menge zurückgegeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
