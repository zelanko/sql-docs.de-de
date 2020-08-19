---
description: Var (MDX)
title: Var (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 46aad9a9b7c328d23680df3c74bcf09a465b868d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483713"
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
