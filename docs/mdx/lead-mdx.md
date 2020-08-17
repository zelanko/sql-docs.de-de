---
description: Lead (MDX)
title: Lead (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ca78bdeca6103758d5d102ed8b85eb00b3138e18
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387326"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die Elementpositionen auf einer Ebene werden über die natürliche Reihenfolge der Attributhierarchie bestimmt. Die Nummerierung der Positionen basiert auf Null.  
  
 Wenn der angegebene Lead NULL (0) ist, gibt die **Lead** -Funktion den angegebenen Member zurück.  
  
 Wenn der angegebene Lead negativ ist, gibt die **Lead** -Funktion einen früheren Member zurück.  
  
 `Lead(1)` entspricht der [NextMember](../mdx/nextmember-mdx.md) -Funktion. `Lead(-1)` entspricht der [PrevMember](../mdx/prevmember-mdx.md) -Funktion.  
  
 Die **Lead** -Funktion ähnelt der [lag](../mdx/lag-mdx.md) -Funktion, mit der Ausnahme, dass die **lag** -Funktion in umgekehrter Richtung zur **Lead** -Funktion sucht. Somit ist `Lead(n)` äquivalent zu `Lag(-n)`.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
