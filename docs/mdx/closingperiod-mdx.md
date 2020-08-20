---
description: ClosingPeriod (MDX)
title: ClosingPeriod (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f457a941c8967ce6f3c6700760ff95d5c2999d0f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487633"
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion ist hauptsächlich zur Verwendung mit einer Dimension des Typ Time vorgesehen, kann jedoch auch mit beliebigen anderen Dimensionen verwendet werden.  
  
-   Wenn ein Ebenenausdruck angegeben wird, verwendet die **ClosingPeriod** -Funktion die Dimension, die die angegebene Ebene enthält, und gibt das letzte gleich geordnete Element unter den nachfolgenden Werten des Standard Elements auf der angegebenen Ebene zurück.  
  
-   Wenn sowohl ein Ebenenausdruck als auch ein Element Ausdruck angegeben werden, gibt die **ClosingPeriod** -Funktion das letzte gleich geordnete Element unter den nachfolgenden Werten des angegebenen Elements auf der angegebenen Ebene zurück.  
  
-   Wenn weder ein Ebenenausdruck noch ein Element Ausdruck angegeben ist, verwendet die **ClosingPeriod** -Funktion die Standard Ebene und den Member der Dimension (sofern vorhanden) im Cube mit einem Zeittyp.  
  
 Die **ClosingPeriod** -Funktion entspricht der folgenden MDX-Anweisung:  
  
 `Tail(Descendants(Member_Expression, Level_Expression), 1)`.  
  
> [!NOTE]  
>  Die [OpeningPeriod](../mdx/openingperiod-mdx.md) -Funktion ähnelt der **ClosingPeriod** -Funktion, mit der Ausnahme, dass die **OpeningPeriod** -Funktion das erste gleich geordnete Element anstelle des letzten gleich geordneten Elements zurückgibt.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [OpeningPeriod &#40;MDX-&#41;](../mdx/openingperiod-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Lastsierend &#40;MDX-&#41;](../mdx/lastsibling-mdx.md)  
  
  
