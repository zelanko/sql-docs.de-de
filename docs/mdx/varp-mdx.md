---
title: VarP (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bb28851863864520a67cacbb2cb9a2a84d9fd6a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135056"
---
# <a name="varp-mdx"></a>VarP (MDX)


  Gibt die auffüllungs Varianz eines numerischen Ausdrucks zurück, der für eine Menge mithilfe der Formel für die unausgewogene Auffüllung (geteilt durch *n*-1) ausgewertet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **VarP** -Funktion gibt die unausgewogene Varianz eines angegebenen numerischen Ausdrucks zurück, der über einer angegebenen Menge ausgewertet wird.  
  
 Die **VarP** -Funktion verwendet die Formel für die unausgewogene Auffüllung, während die [var](../mdx/var-mdx.md) -Funktion die Formel für die ausgewogene Auffüllung verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
