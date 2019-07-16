---
title: Var (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 96bb307607792a3846ee6566027457a05ce3b905
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037934"
---
# <a name="var-mdx"></a>Var (MDX)


  Gibt die Stichprobenvarianz eines numerischen Ausdrucks, ausgewertet über einer Menge mithilfe der nicht unausgewogenen Auffüllungsformel (geteilt durch *n*).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **Var** Funktion gibt die ausgewogene Varianz eines angegebenen numerischen Ausdrucks, ausgewertet über einer angegebenen Menge zurück.  
  
 Die **Var** -Funktion verwendet die Formel für die ausgewogene Auffüllung, und die [VarP](../mdx/varp-mdx.md) -Funktion verwendet die Formel für die unausgewogene Auffüllung berechnet wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
