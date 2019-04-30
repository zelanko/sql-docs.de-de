---
title: Arithmetische Operatoren | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c422df08152eaf9266a6ca3408bfce12e023c2a3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63284521"
---
# <a name="arithmetic-operators"></a>Arithmetische Operatoren


  Sie können arithmetische Operatoren in MDX (Multidimensional Expressions) für beliebige arithmetische Berechnungen verwenden. Dazu gehören Addition, Subtraktion, Multiplikation und Division.  
  
 MDX unterstützt die arithmetischen Operatoren, die in der folgenden Tabelle aufgelistet sind.  
  
|Operator|Description|  
|--------------|-----------------|  
|[+ (Add) (+ (Addieren))](../mdx/add-mdx.md)|Addition zweier Zahlen.|  
|[/ (Dividieren)](../mdx/divide-mdx-operator-reference.md)|Dividiert eine Zahl durch eine andere Zahl.|  
|[* (Multiply) (* (Multiplizieren))](../mdx/multiply-mdx.md)|Multipliziert zwei Zahlen.|  
|[- (Subtract) (- (Subtrahieren))](../mdx/subtract-mdx.md)|Subtraktion zweier Zahlen.|  
|^ (Potenz) |Potenziert eine Zahl mit einer anderen Zahl.|  
  
> [!NOTE]  
>  MDX enthält keine Funktion, um die Quadratwurzel einer Zahl zu erhalten. Um die Quadratwurzel einer Zahl zu erhalten, potenzieren Sie sie mit 0,5 unter Verwendung des ^-Operators.  
  
## <a name="order-of-precedence"></a>Rangfolge  
 Die folgenden Regeln bestimmen die Rangfolge, die arithmetische Operatoren in einem MDX-Ausdruck haben.  
  
-   Sind in einem Ausdruck mehrere arithmetische Operatoren vorhanden, führt MDX Multiplikationen und Divisionen vor Subtraktionen und Additionen aus.  
  
-   Wenn alle arithmetische Operatoren in einem Ausdruck dieselbe Ebene der Vorrang haben, bleibt die Reihenfolge der Ausführung nach rechts.  
  
-   Ausdrücke in Klammern erhalten Vorrang vor allen anderen Operationen.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatoren &#40;MDX-Syntax&#41;](../mdx/operators-mdx-syntax.md)  
  
  
