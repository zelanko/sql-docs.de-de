---
title: NonEmpty (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45daf970f69322cad36bbe5419bf1dc8cc8009b9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088342"
---
# <a name="nonempty-mdx"></a>NonEmpty (MDX)


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
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion gibt die Tupel in der ersten angegebenen Menge zurück, die nach Auswertung über die Tupel in der zweiten Menge nicht leer sind. Die **NonEmpty** -Funktion berücksichtigt Berechnungen und behält doppelte Tupel bei. Wenn keine zweite Menge bereitgestellt ist, wird der Ausdruck im Kontext der aktuellen Koordinaten der Elemente der Attributhierarchien und der Measures im Cube ausgewertet.  
  
> [!NOTE]  
>  Verwenden Sie diese Funktion anstelle der veralteten Funktion [NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md) .  
  
> [!IMPORTANT]  
>  Nicht leer ist eine Eigenschaft der Zellen, auf die die Tupel verweisen, keine Eigenschaft der Tupel selbst.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage zeigt ein einfaches Beispiel für **NonEmpty**, bei dem alle Kunden mit einem Wert ungleich NULL für Internet Sales Amount am 1. Juli 2001 zurückgegeben werden:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `, {([Date].[Calendar].[Date].&[20010701], [Measures].[Internet Sales Amount])}`  
  
 `)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 Im folgenden Beispiel wird der Satz von Tupeln mit Kunden und Kauf Daten mithilfe der **Filter** -Funktion und der **nicht leeren** Funktionen zurückgegeben, um das letzte Datum zu ermitteln, an dem der Kunde einen Kauf getätigt hat:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [DefaultMember &#40;MDX-&#41;](../mdx/defaultmember-mdx.md)   
 [&#40;MDX-&#41;Filtern](../mdx/filter-mdx.md)   
 [IsEmpty &#40;MDX-&#41;](../mdx/isempty-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [NonEmptyCrossjoin-&#40;MDX-&#41;](../mdx/nonemptycrossjoin-mdx.md)  
  
  
