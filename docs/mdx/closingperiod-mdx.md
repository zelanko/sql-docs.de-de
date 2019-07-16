---
title: ClosingPeriod (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 102485ede0e52389d43bdb64742a2564aaa71419
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016792"
---
# <a name="closingperiod-mdx"></a>ClosingPeriod (MDX)


  Gibt das letzte gleichgeordnete Element unter den nachfolgenden Werten eines angegebenen Elements auf einer angegebenen Ebene zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ClosingPeriod( [ Level_Expression [ ,Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ist hauptsächlich zur Verwendung mit einer Dimension des Typ Time vorgesehen, kann jedoch auch mit beliebigen anderen Dimensionen verwendet werden.  
  
-   Wenn ein Ebenenausdruck angegeben wird, die **ClosingPeriod** -Funktion verwendet die Dimension, die die angegebene Ebene enthält, und gibt Sie das letzte gleichgeordnete Element unter den nachfolgenden Werten des Standardelements auf der angegebenen Ebene zurück.  
  
-   Wenn sowohl ein Ebenenausdruck als auch ein Elementausdruck angegeben sind, die **ClosingPeriod** Funktion gibt das letzte gleichgeordnete Element unter den nachfolgenden Werten des angegebenen Elements auf der angegebenen Ebene zurück.  
  
-   Wenn weder ein Ebenenausdruck noch ein Elementausdruck angegeben ist, die **ClosingPeriod** Funktion verwendet die Standardebene und-Element der Dimension (sofern vorhanden) in den Cube mit den Typ Time.  
  
 Die **ClosingPeriod** -Funktion ist gleichbedeutend mit der folgenden MDX-Anweisung:  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`. installiert haben.  
  
> [!NOTE]  
>  Die [OpeningPeriod](../mdx/openingperiod-mdx.md) Funktion ist vergleichbar mit der **ClosingPeriod** ordnungsgemäß verwendet werden, außer dass die **OpeningPeriod** Funktion gibt das erste gleichgeordnete Element statt der letzten zurück. gleichgeordnetes Element.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das FY2007-Element der Date-Dimension (die den semantischen Typ Time aufweist) zurückgegeben. Dieses Element wird zurückgegeben, weil die Fiscal Year-Ebene der erste nachfolgende Wert der [All]-Ebene ist. Die Fiscal-Hierarchie ist die Standardhierarchie, weil sie die erste benutzerdefinierte Hierarchie in der Hierarchie-Auflistung darstellt, und das FY 2007-Element ist das letzte gleichgeordnete Element in dieser Hierarchie auf dieser Ebene.  
  
```  
SELECT ClosingPeriod() ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das Element "30. November 2006" auf der Date.Date.Date-Ebene für die Date.Date-Attributhierarchie zurückgegeben. Dieses Element ist das letzte gleichgeordnete Element des nachfolgenden Wertes der [All]-Ebene in der Date.Date-Attributhierarchie.  
  
```  
SELECT ClosingPeriod ([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das December, 2003-Element zurückgegeben. Dieses Element ist das letzte gleichgeordnete Element des nachfolgenden Wertes des 2003-Elements auf der Year-Ebene in der benutzerdefinierten Calendar-Hierarchie.  
  
```  
SELECT ClosingPeriod ([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das June, 2003-Element zurückgegeben. Dieses Element ist das letzte gleichgeordnete Element des nachfolgenden Wertes des 2003-Elements auf der Year-Ebene in der benutzerdefinierten Fiscal-Hierarchie.  
  
```  
SELECT ClosingPeriod ([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [OpeningPeriod &#40;MDX&#41;](../mdx/openingperiod-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [LastSibling &#40;MDX&#41;](../mdx/lastsibling-mdx.md)  
  
  
