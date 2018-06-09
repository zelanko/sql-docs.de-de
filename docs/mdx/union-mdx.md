---
title: Union (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e51749416c0668ccc4760132bb860121ebae6e3d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743489"
---
# <a name="union--mdx"></a>Union (MDX)


  Gibt die Vereinigungsmenge zweier Mengen zurück, wobei optional doppelte Elemente beibehalten werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Standard syntax  
Union(Set_Expression1, Set_Expression2 [,...n][, ALL])  
  
Alternate syntax 1  
Set_Expression1 + Set_Expression2 [+...n]  
  
Alternate syntax 2  
{Set_Expression1 , Set_Expression2 [,...n]}  
```  
  
## <a name="arguments"></a>Argumente  
 *Der Mengenausdruck 1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Der Mengenausdruck 2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt die Vereinigung von zwei oder mehr angegebenen Mengen *.* Bei Verwendung der Standardsyntax und mit der alternativen Syntax 1 werden standardmäßig Duplikate entfernt. Bei Verwendung der Standardsyntax mithilfe der **alle** Flags bleiben bei der Duplikate in der Vereinigten Menge. Doppelte Werte werden vom Ende her gelöscht. Bei Verwendung der alternativen Syntax 2 werden doppelte Elemente immer beibehalten.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele veranschaulichen das Verhalten der **Union** Syntaxvarianten-Funktion.  
  
### <a name="standard-syntax-duplicates-eliminated"></a>Standardsyntax – Löschen der doppelten Werte  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="standard-syntax-duplicates-retained"></a>Standardsyntax – Beibehalten der doppelten Werte  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   , ALL  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-1-duplicates-eliminated"></a>Alternative Syntax 1 – Löschen der doppelten Werte  
  
```  
SELECT   
   [Date].[Calendar Year].children   
   + {[Date].[Calendar Year].[CY 2002]}   
   + {[Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-2-duplicates-retained"></a>Alternative Syntax 2 – Beibehalten der doppelten Werte  
  
```  
SELECT   
   {[Date].[Calendar Year].children  
   , [Date].[Calendar Year].[CY 2002]  
   , [Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [+ &#40;Union&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
