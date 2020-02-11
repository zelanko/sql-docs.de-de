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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion ist in erster Linie für die Verwendung der Time-Dimension gedacht, kann jedoch mit jeder beliebigen Dimension verwendet werden.  
  
-   Wenn ein Ebenenausdruck angegeben ist, verwendet die **OpeningPeriod** -Funktion die Hierarchie, die die angegebene Ebene enthält, und gibt das erste gleich geordnete Element unter den nachfolgenden Werten des Standard Elements auf der angegebenen Ebene zurück.  
  
-   Wenn sowohl ein Ebenenausdruck als auch ein Element Ausdruck angegeben werden, gibt die **OpeningPeriod** -Funktion das erste gleich geordnete Element unter den nachfolgenden Werten des angegebenen Elements auf der angegebenen Ebene in der Hierarchie zurück, die die angegebene Ebene enthält.  
  
-   Wenn weder ein Ebenenausdruck noch ein Element Ausdruck angegeben ist, verwendet die **OpeningPeriod** -Funktion die Standard Ebene und den Member der Dimension mit einem Zeittyp.  
  
> [!NOTE]  
>  Die [ClosingPeriod](../mdx/closingperiod-mdx.md) -Funktion ähnelt der **OpeningPeriod** -Funktion, mit der Ausnahme, dass die **ClosingPeriod** -Funktion das letzte gleich geordnete Element anstelle des ersten gleich geordneten Elements zurückgibt.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [TopCount &#40;MDX-&#41;](../mdx/topcount-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Firstsierend &#40;MDX-&#41;](../mdx/firstsibling-mdx.md)  
  
  
