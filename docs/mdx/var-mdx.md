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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037934"
---
# <a name="var-mdx"></a>Var (MDX)


  Gibt die Stichproben Varianz eines numerischen Ausdrucks zurück, der für eine Menge mithilfe der Formel für die unausgewogene Auffüllung (dividiert durch *n*) ausgewertet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **var** -Funktion gibt die unausgewogene Varianz eines angegebenen numerischen Ausdrucks zurück, der für eine angegebene Menge ausgewertet wurde.  
  
 Die **var** -Funktion verwendet die Formel für die unausgewogene Auffüllung. die [VarP](../mdx/varp-mdx.md) -Funktion verwendet die Formel für die unausgewogene Auffüllung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
