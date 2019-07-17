---
title: OpeningPeriod (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 07f94c3ed850af10120b1de7d95941bc5c90e826
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088223"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)


  Gibt das erste gleichgeordnete Element unter den nachfolgenden Werten einer angegebenen Ebene optional bei einem angegebenen Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ist, werden hauptsächlich verwendet, die Time-Dimension, jedoch mit einer beliebigen Dimension verwendet werden kann.  
  
-   Wenn ein Ebenenausdruck angegeben wird, die **OpeningPeriod** -Funktion verwendet die Hierarchie, die die angegebene Ebene enthält, und gibt Sie das erste gleichgeordnete Element unter den nachfolgenden Werten des Standardelements auf der angegebenen Ebene zurück.  
  
-   Wenn sowohl ein Ebenenausdruck als auch ein Elementausdruck angegeben sind, die **OpeningPeriod** Funktion gibt das erste gleichgeordnete Element unter den nachfolgenden Werten des angegebenen Elements auf der angegebenen Ebene innerhalb der mit dem angegebenen Hierarchie zurück. Ebene.  
  
-   Wenn weder ein Ebenenausdruck noch ein Elementausdruck angegeben sind, die **OpeningPeriod** Funktion verwendet die Standardebene und-Element der Dimension vom Typ Time.  
  
> [!NOTE]  
>  Die [ClosingPeriod](../mdx/closingperiod-mdx.md) Funktion ist vergleichbar mit der **OpeningPeriod** ordnungsgemäß verwendet werden, außer dass die **ClosingPeriod** Funktion gibt das letzte gleichgeordnete Element statt dem ersten zurück. gleichgeordnetes Element.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das FY2002-Element der Date-Dimension (die den Typ Time aufweist) zurückgegeben. Dieses Element wird zurückgegeben, weil die Fiscal Year-Ebene der erste nachfolgende Wert der [All]-Ebene ist. Die Fiscal-Hierarchie ist die Standardhierarchie, weil sie die erste benutzerdefinierte Hierarchie in der Hierarchie-Auflistung darstellt, und das FY2002-Element ist das erste gleichgeordnete Element in dieser Hierarchie auf dieser Ebene.  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das July 1, 2001-Element auf der Date.Date.Date-Ebene für die Date.Date-Attributhierarchie zurückgegeben. Dieses Element ist das erste gleichgeordnete Element des nachfolgenden Wertes der [All]-Ebene in der Date.Date-Attributhierarchie.  
  
```  
SELECT OpeningPeriod([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das January, 2003-Element zurückgegeben. Dieses Element ist das erste gleichgeordnete Element des nachfolgenden Wertes des 2003-Elements auf der Year-Ebene in der benutzerdefinierten Calendar-Hierarchie.  
  
```  
SELECT OpeningPeriod([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
 Im folgenden Beispiel wird der Wert des Standardmeasures für das July, 2002-Element zurückgegeben. Dieses Element ist das erste gleichgeordnete Element des nachfolgenden Wertes des 2003-Elements auf der Year-Ebene in der benutzerdefinierten Fiscal-Hierarchie.  
  
```  
SELECT OpeningPeriod([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;MDX&#41;](../mdx/firstsibling-mdx.md)  
  
  
