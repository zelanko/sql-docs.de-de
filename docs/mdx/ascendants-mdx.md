---
title: Vorgänger (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ef9cccb488cebb08c1b9721c40cb8037ea8687a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739619"
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)


  Gibt die Menge der vorausgehenden Elemente zu einem angegebenen Element zurück, einschließlich des Elements selbst.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Vorgänger** Funktion gibt alle Vorgänger eines Elements aus der Member selbst bis zum Anfang des Mitglieds der Hierarchie zurück; genauer gesagt, es führt einen Postorder-Durchlauf der Hierarchie für das angegebene Element und dann gibt alle Vorgänger der Elemente im Zusammenhang mit den Member auf, einschließlich selbst in einem Satz. Dies ist im Gegensatz zu den [Vorgänger](../mdx/ancestor-mdx.md) -Funktion, die ein bestimmtes vorausgehendes Element oder Vorgänger, auf einer bestimmten Ebene zurückgibt.  
  
## <a name="examples"></a>Beispiele  
 Im folgende Beispiel gibt die Anzahl der Bestellungen des Wiederverkäufers für die `[Sales Territory].[Northwest]` Element und alle vorausgehenden Elemente des Elements aus der **Adventure Works** Cube. Die **Vorgänger** Funktion bildet die Menge der `[Sales Territory].[Northwest]` Element und seinen vorausgehenden Elementen für die ROWS-Achse.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
