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
ms.openlocfilehash: 16c6f812d1d7cae5a81a8e64fb425f4d33f4cb5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017060"
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
 Die **Vorgänger** Funktion gibt alle Vorgänger eines Elements aus das Element selbst bis zum Anfang des Elements Hierarchie zurück; genauer gesagt wird einen Durchlauf der Hierarchie für das angegebene Element aus, und klicken Sie dann Gibt zurück, der alle vorausgehenden Elemente des Elements, einschließlich selbst, in einer Gruppe verknüpft. Dies ist im Gegensatz zu den [Vorgänger](../mdx/ancestor-mdx.md) -Funktion, die ein bestimmtes vorausgehendes Element oder Vorgänger, auf einer bestimmten Ebene zurückgibt.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt die Anzahl der Bestellungen des Wiederverkäufers für das `[Sales Territory].[Northwest]` Element und alle vorausgehenden Elemente des Elements aus der **Adventure Works** Cube. Die **Vorgänger** Funktion erstellt die Menge der `[Sales Territory].[Northwest]` Element und seinen vorausgehenden Elementen für die ROWS-Achse.  
  
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
  
  
