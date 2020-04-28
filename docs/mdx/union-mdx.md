---
title: Union (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 170e3764795e1bb6db3fc9589ecf1fe486078633
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097302"
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
 *Festlegen von Ausdruck 1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Festlegen von Ausdruck 2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion gibt die Union von zwei oder mehr angegebenen Mengen zurück. Mit der Standard Syntax und mit der alternativen Syntax 1 werden Duplikate standardmäßig gelöscht. Mit der Standard Syntax speichert das **all** -Flag Duplikate in der verbundenen Menge. Doppelte Werte werden vom Ende her gelöscht. Bei Verwendung der alternativen Syntax 2 werden doppelte Elemente immer beibehalten.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird das Verhalten der **Union** -Funktion unter Verwendung der einzelnen-Syntax veranschaulicht.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [+ &#40;Union&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
