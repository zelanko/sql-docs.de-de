---
title: Freeze-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4738dab411fe55808034a6d9d81a16994089ea74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **Freeze** -Anweisung sperrt die Werte von Zellen in einem angegebenen Teilcube, wodurch verhindert wird, dass nachfolgende Anweisungen in einem MDX-Skript ihre Werte in nachfolgenden Berechnungs Durchläufen ändern.  
  
 Im folgenden Beispiel stellen A und B Teilcubes in einem MDX-Berechnungsskript dar:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 An diesem Punkt ist sowohl A als auch B gleich 3.  
  
 Nun fügen Sie die **Freeze** -Funktion ein, um die Zellen in einem Teilcube zu sperren:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A ist jetzt gleich 2, und B ist gleich 3.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Skript Anweisungen &#40;MDX-&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
