---
title: Führen Sie (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d72af1bf0b671eeb2bd4b84c194f129ed1ce6bfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63205434"
---
# <a name="lead-mdx"></a>Lead (MDX)


  Gibt das Element zurück, das eine angegebene Anzahl von Positionen auf ein angegebenes Element entlang der Ebene des Elements folgt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Index*  
 Ein gültiger numerischer Ausdruck, der eine Anzahl der Elementpositionen angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die Elementpositionen auf einer Ebene werden über die natürliche Reihenfolge der Attributhierarchie bestimmt. Die Nummerierung der Positionen basiert auf Null.  
  
 Wenn der angegebene Abstand null (0), ist die **führen** Funktion gibt das angegebene Element zurück.  
  
 Wenn der angegebene Abstand negativ ist, ist die **führen** -Funktion ein vorausgehendes Element zurück.  
  
 `Lead(1)` entspricht der [NextMember](../mdx/nextmember-mdx.md) Funktion. `Lead(-1)` entspricht der [PrevMember](../mdx/prevmember-mdx.md) Funktion.  
  
 Die **führen** Funktion ist vergleichbar mit der [Lag](../mdx/lag-mdx.md) ordnungsgemäß verwendet werden, außer dass die **Lag** -Funktion sucht, in die entgegengesetzte Richtung auf die **führen** -Funktion. Somit ist `Lead(n)` äquivalent zu `Lag(-n)`.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Wert December 2001 zurückgegeben:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(-2) ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird der Wert March 2002 zurückgegeben:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
