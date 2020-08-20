---
description: Ancestors (MDX)
title: Vorgänger (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d92f15f20c872fbe63db09a55356b5d1e35ff0d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461682"
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)


  Eine Funktion, die die Menge aller Vorgänger eines angegebenen Elements in einer angegebenen Ebene oder in einem angegebenen Abstand vom Element zurückgibt. Bei [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] besteht der zurückgegebene Satz immer aus einem einzelnen Member [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . unterstützt nicht mehrere übergeordnete Elemente für einen einzelnen Member.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Entfernung*  
 Ein gültiger numerischer Ausdruck, der den Abstand vom angegebenen Element angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der Vorgänger Funktion stellen Sie **der Funktion einen** MDX-Element Ausdruck bereit und stellen dann entweder einen MDX-Ausdruck einer Ebene bereit, die ein Vorgänger dieses Members ist, oder einen numerischen Ausdruck, der die Anzahl der Ebenen oberhalb dieses Elements darstellt. Mit diesen Informationen gibt die **Vorgänger Funktion die** Menge der Elemente (die eine Menge aus einem Element) auf dieser Ebene zurück.  
  
> [!NOTE]  
>  Verwenden Sie die [Vorgänger](../mdx/ancestor-mdx.md) Funktion, um einen Vorgänger Member anstelle eines Vorgänger Satzes zurückzugeben.  
  
 Wenn ein Ebenenausdruck angegeben wird, gibt die **Vorgänger Funktion die** Menge aller Vorgänger des angegebenen Elements auf der angegebenen Ebene zurück. Wenn sich der angegebene Member nicht in derselben Hierarchie wie die angegebene Ebene befindet, gibt die Funktion einen Fehler zurück.  
  
 Wenn ein Abstand angegeben wird, gibt die **Vorgänger Funktion die** Menge aller Elemente zurück, die die in der durch den Element Ausdruck angegebene Hierarchie angegebene Anzahl von Schritten bilden. Ein Member kann als Element einer Attribut Hierarchie, einer benutzerdefinierten Hierarchie oder in einigen Fällen eine über-/unterordnungshierarchie angegeben werden. 1 gibt die Menge der Elemente auf der übergeordneten Ebene und 2 die Menge der Elemente auf der dieser Ebene übergeordneten Ebene (sofern vorhanden) zurück. 0 gibt die Menge zurück, die nur das Element selbst enthält.  
  
> [!NOTE]  
>  Verwenden Sie diese **Form der Vorgänger Funktion in** Fällen, in denen die Ebene des übergeordneten Elements unbekannt ist oder nicht benannt werden kann.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel **wird die-Vorgänger Funktion verwendet** , um das Internet Sales Amount-Measure für ein Element, das übergeordnete Element und dessen übergeordnetes Element zurückzugeben. In diesem Beispiel werden Ebenenausdrücke zum Angeben der zurückzugebenden Ebene verwendet. Die Ebenen befinden sich in der gleichen Hierarchie wie das im Elementausdruck angegebene Element.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel **wird die-Vorgänger Funktion verwendet** , um das Internet Sales Amount-Measure für ein Element, das übergeordnete Element und dessen übergeordnetes Element zurückzugeben. In diesem Beispiel werden numerische Ausdrücke zum Angeben der zurückzugebenden Ebene verwendet. Die Ebenen befinden sich in der gleichen Hierarchie wie das im Elementausdruck angegebene Element.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],2  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],1  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],0  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM  [Adventure Works]  
```  
  
 Im folgenden Beispiel **wird die-Vorgänger Funktion verwendet** , um das Internet Sales Amount-Measure für das übergeordnete Element einer Attribut Hierarchie zurückzugeben. In diesem Beispiel wird ein numerischer Ausdruck zum Angeben der zurückzugebenden Ebene verwendet. Da das Element im Elementausdruck ein Element einer Attributhierarchie darstellt, ist das ihm übergeordnete Element die [All]-Ebene.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
