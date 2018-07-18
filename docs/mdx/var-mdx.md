---
title: Var (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14caf6e96b41fdf2e7f8b4d20f16852e890bd166
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743919"
---
# <a name="var-mdx"></a>Var (MDX)


  Gibt die Stichprobenvarianz eines numerischen Ausdrucks, ausgewertet über einer Menge mithilfe der unausgewogenen Auffüllungsformel (geteilt durch *n*).  
  
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
  
 Die **Var** Funktion verwendet die Formel für die ausgewogene Auffüllung, und die [VarP](../mdx/varp-mdx.md) Funktion der Formel für die unausgewogene Auffüllung verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
