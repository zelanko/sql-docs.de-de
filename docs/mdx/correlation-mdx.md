---
description: Correlation (MDX)
title: Korrelation (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ae050b681830b81ffa63ae82c714d69d54b03c91
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387646"
---
# <a name="correlation-mdx"></a>Correlation (MDX)


  Gibt den Korrelationskoeffizienten von X-Y-Wertepaaren zurück, die über einer Menge ausgewertet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Correlation( Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression_y*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die Y-Achse dar.  
  
 *Numeric_Expression_x*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt. Die vom Ausdruck zurückgegebene Zahl stellt den Wert für die X-Achse dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Korrelations** Funktion berechnet den Korrelationskoeffizient zweier Wertepaare, indem zuerst die angegebene Menge anhand des ersten numerischen Ausdrucks ausgewertet wird, um die Werte für die y-Achse zu erhalten. Anschließend wertet die Funktion die angegebene Menge für den zweiten numerischen Ausdruck aus, sofern vorhanden, um den Satz von Werten für die x-Achse zu erhalten. Wenn kein zweiter numerischer Ausdruck angegeben wird, verwendet die Funktion den aktuellen Kontext der Zellen in der angegebenen Menge als Werte für die X-Achse.  
  
> [!NOTE]  
>  Die **Korrelations** Funktion ignoriert leere Zellen oder Zellen, die Text oder logische Werte enthalten. Zellen mit dem Wert Null (0) werden jedoch von der Funktion berücksichtigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
