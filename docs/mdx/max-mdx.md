---
title: Max (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ad4bc2bf41caacbafb5bf36b5e95263ab2f85d22
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098528"
---
# <a name="max-mdx"></a>Max (MDX)


  Gibt den Maximalwert eines numerischen Ausdrucks zurück, der über einer Menge ausgewertet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Max( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Ausdruck angegeben ist, wird der angegebene numerische Ausdruck über die Menge ausgewertet und anschließend der größte Wert der Auswertung zurückgegeben. Wenn kein numerischer Ausdruck angegeben ist, wird die angegebene Menge im aktuellen Kontext der Elemente der Menge ausgewertet und anschließend der größte Wert der Auswertung zurückgegeben.  
  
> [!NOTE]  
>  In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden Nullen ignoriert, wenn der größte Wert in einer Menge von Zahlen berechnet wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Maximalwert der monatlichen Quartalsumsätze für jede Unterkategorie und jedes Land/jede Region im Adventure Works-Cube zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS Max   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
