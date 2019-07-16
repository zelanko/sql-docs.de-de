---
title: Vorgänger (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8551e6fdac54b3eb4c20f13f6722936df1c92feb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017102"
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)


  Eine Funktion, die die Menge aller Vorgänger eines angegebenen Elements in einer angegebenen Ebene oder in einem angegebenen Abstand vom Element zurückgibt. Mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], die zurückgegebene Menge stets ein einzelnes Element – besteht aus [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt nicht mehrere übergeordnete Elemente für ein einzelnes Element.  
  
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
  
## <a name="remarks"></a>Hinweise  
 Mit der **Vorgänger** -Funktion, Sie stellen die Funktion einen MDX-Elementausdruck bereit und anschließend entweder einen MDX-Ausdruck einer Ebene, die sich um einen Vorgänger dieses Members oder ein numerischer Ausdruck, der die Anzahl der Ebenen darstellt oberhalb dieses Elements. Mit diesen Informationen die **Vorgänger** Funktion gibt die Menge der Elemente (die einen Satz von einem Element sein wird) auf dieser Ebene zurück.  
  
> [!NOTE]  
>  Zur Rückgabe eines Vorgängerelements eine vorgängermenge, anstatt einen Satz Vorgänger der [Vorgänger](../mdx/ancestor-mdx.md) Funktion.  
  
 Wenn ein Ebenenausdruck angegeben wird, die **Vorgänger** -Funktion die Menge aller Vorgänger des angegebenen Elements auf der angegebenen Ebene zurück. Wenn das angegebene Element nicht innerhalb der gleichen Hierarchie wie die angegebene Ebene ist, gibt die Funktion einen Fehler auf.  
  
 Wenn ein Abstand angegeben wird, die **Vorgänger** Funktion gibt die Menge aller Elemente, die die Anzahl der Schritte, die sich in der Hierarchie, die anhand der im Elementausdruck angegeben sind. Ein Element kann als ein Element einer Attributhierarchie, einer benutzerdefinierten Hierarchie oder in einigen Fällen eine über-/ unterordnungshierarchie angegeben werden. 1 gibt die Menge der Elemente auf der übergeordneten Ebene und 2 die Menge der Elemente auf der dieser Ebene übergeordneten Ebene (sofern vorhanden) zurück. 0 gibt die Menge zurück, die nur das Element selbst enthält.  
  
> [!NOTE]  
>  Verwenden Sie dieses Formular aus, der die **Vorgänger** -Funktion in Fällen, in dem die Ebene des übergeordneten Elements ist unbekannt oder nicht benannt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **Vorgänger** Funktion, um das Internet Sales Amount-Measure für ein Element, das übergeordnete Element und das diesem übergeordnete Element zurückzugeben. In diesem Beispiel werden Ebenenausdrücke zum Angeben der zurückzugebenden Ebene verwendet. Die Ebenen befinden sich in der gleichen Hierarchie wie das im Elementausdruck angegebene Element.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die **Vorgänger** Funktion, um das Internet Sales Amount-Measure für ein Element, das übergeordnete Element und das diesem übergeordnete Element zurückzugeben. In diesem Beispiel werden numerische Ausdrücke zum Angeben der zurückzugebenden Ebene verwendet. Die Ebenen befinden sich in der gleichen Hierarchie wie das im Elementausdruck angegebene Element.  
  
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
  
 Im folgenden Beispiel wird die **Vorgänger** Funktion, um das Internet Sales Amount-Measure für das übergeordnete Element eines Elements der Attributhierarchie zurückzugeben. In diesem Beispiel wird ein numerischer Ausdruck zum Angeben der zurückzugebenden Ebene verwendet. Da das Element im Elementausdruck ein Element einer Attributhierarchie darstellt, ist das ihm übergeordnete Element die [All]-Ebene.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
