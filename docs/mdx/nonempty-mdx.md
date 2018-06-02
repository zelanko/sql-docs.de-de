---
title: NonEmpty (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a718a7e75a9b31b7d35cdc33883c97739aee68c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580282"
---
# <a name="nonempty-mdx"></a>NonEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Menge der nicht leeren Tupel einer angegebenen Menge zurück, basierend auf dem Kreuzprodukt der angegebenen Menge mit einer zweiten Menge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NONEMPTY(set_expression1 [,set_expression2])  
```  
  
## <a name="arguments"></a>Argumente  
 *set_expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *set_expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt die Tupel in der ersten angegebenen Menge zurück, die nach Auswertung über die Tupel in der zweiten Menge nicht leer sind. Die **NonEmpty** -Funktion berücksichtigt Berechnungen und behält doppelt vorhandene Tupel. Wenn keine zweite Menge bereitgestellt ist, wird der Ausdruck im Kontext der aktuellen Koordinaten der Elemente der Attributhierarchien und der Measures im Cube ausgewertet.  
  
> [!NOTE]  
>  Verwenden Sie diese Funktion anstelle der veralteten [NonEmptyCrossjoin &#40;MDX&#41; ](../mdx/nonemptycrossjoin-mdx.md) Funktion.  
  
> [!IMPORTANT]  
>  Nicht leer ist eine Eigenschaft der Zellen, auf die die Tupel verweisen, keine Eigenschaft der Tupel selbst.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage zeigt ein einfaches Beispiel **NonEmpty**, alle Kunden, die einen Wert ungleich Null für Internet Sales Amount auf den 1. Juli 2001 hatte zurückgeben:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 Im folgende Beispiel gibt die Menge von Tupeln, die mit Kunden- und Kaufdaten, mit der **Filter** Funktion und die **NonEmpty** Funktionen, um das letzte Datum gefunden werden, dass jeder Kunde einen Kauf vorgenommen:  
  
 `WITH SET MYROWS AS FILTER`  
  
 `(NONEMPTY`  
  
 `([Customer].[Customer Geography].[Customer].MEMBERS`  
  
 `* [Date].[Date].[Date].MEMBERS`  
  
 `, [Measures].[Internet Sales Amount]`  
  
 `) AS MYSET`  
  
 `, NOT(MYSET.CURRENT.ITEM(0)`  
  
 `IS MYSET.ITEM(RANK(MYSET.CURRENT, MYSET)).ITEM(0))`  
  
 `)`  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `MYROWS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [DefaultMember &#40;MDX&#41;](../mdx/defaultmember-mdx.md)   
 [Filter &#40;MDX&#41;](../mdx/filter-mdx.md)   
 [IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)  
  
  
