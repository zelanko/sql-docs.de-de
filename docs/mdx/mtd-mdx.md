---
title: MTD (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e604f66e48c8c8bb93ff5fd4abb174449f0fcdd9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088443"
---
# <a name="mtd-mdx"></a>Mtd (MDX)


  Gibt eine Menge von gleichgeordneten Elementen zurück, die derselben Ebene angehören wie ein angegebenes Element. Die Menge beginnt mit dem ersten gleichgeordneten Element und endet mit dem angegebenen Element, entsprechend der Einschränkung durch die Year-Ebene in der Time-Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn kein Element Ausdruck angegeben ist, wird standardmäßig der aktuelle Member der ersten Hierarchie mit einer Ebene des Typs *Monate* in der ersten Dimension des Typs *time* in der Measure-Gruppe angegeben.  
  
 Die **MTD** -Funktion ist eine Verknüpfungs Funktion für die [PeriodsToDate](../mdx/periodstodate-mdx.md) -Funktion, wenn die Type-Eigenschaft der Attribut Hierarchie, auf der eine Ebene basiert, auf *Monate*festgelegt ist. Somit ist `Mtd(Member_Expression)` äquivalent zu `PeriodsToDate(Month_Level_Expression,Member_Expression)`.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Summe der Monat bis Datum Frachtkosten für Internetverkäufe für den Monat Juli 2002 bis einschließlich 20. Juli zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Summe &#40;MDX-&#41;](../mdx/sum-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
