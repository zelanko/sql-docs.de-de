---
title: FREEZE-Anweisung (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b7eb3a3939ce8525dc57d27a24ac005ecb2cf2d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579902"
---
# <a name="mdx-scripting---freeze"></a>MDX-Skripts - fixiert werden soll
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Fixiert die Zellenwerte eines angegebenen Teilcubes auf die aktuellen Werte. Wenn die Zellenwerte fixiert sind, wirken sich Änderungen an anderen Zellen nicht auf die fixierten Zellen aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Argumente  
 *Subcube_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen Teilcube zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **FIXIEREN** -Anweisung fixiert die Werte von Zellen in einem angegebenen Teilcube, sodass nachfolgende Anweisungen in einem MDX Skript ändern ihrer Werte in nachfolgenden Berechnungsdurchläufen übergibt.  
  
 Im folgenden Beispiel stellen A und B Teilcubes in einem MDX-Berechnungsskript dar:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 An diesem Punkt ist sowohl A als auch B gleich 3.  
  
 Wir fügen Sie nun die **fixieren** Funktion, die Zellen im Teilcube A zu sperren:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A ist jetzt gleich 2, und B ist gleich 3.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Skriptanweisungen &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
