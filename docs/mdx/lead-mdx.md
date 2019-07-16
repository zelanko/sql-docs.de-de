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
ms.openlocfilehash: cc4d362fbc7656e9427548a352b32d5d8297071e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905741"
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
  
  
