---
title: FREEZE-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4738dab411fe55808034a6d9d81a16994089ea74
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138291"
---
# <a name="mdx-scripting---freeze"></a>MDX-Skripts – FREEZE


  Fixiert die Zellenwerte eines angegebenen Teilcubes auf die aktuellen Werte. Wenn die Zellenwerte fixiert sind, wirken sich Änderungen an anderen Zellen nicht auf die fixierten Zellen aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Argumente  
 *Subcube_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen Teilcube zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **FIXIEREN** -Anweisung sperrt die Werte der Zellen in einem angegebenen Teilcube, sodass nachfolgende Anweisungen in einem MDX-Skript aus, ändern die Werte in den nachfolgenden Berechnungsdurchläufen übergibt.  
  
 Im folgenden Beispiel stellen A und B Teilcubes in einem MDX-Berechnungsskript dar:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 An diesem Punkt ist sowohl A als auch B gleich 3.  
  
 Wir fügen Sie nun die **fixieren** Funktion, die die Zellen im Teilcube A zu sperren:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A ist jetzt gleich 2, und B ist gleich 3.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Skriptanweisungen &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
