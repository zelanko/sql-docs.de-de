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
ms.openlocfilehash: 1898f3e9807d2ea4f80f99e9a7ef27e672d58a18
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017081"
---
# <a name="arithmetic-operators"></a>Arithmetische Operatoren


  Sie können arithmetische Operatoren in MDX (Multidimensional Expressions) für beliebige arithmetische Berechnungen verwenden. Dazu gehören Addition, Subtraktion, Multiplikation und Division.  
  
 MDX unterstützt die arithmetischen Operatoren, die in der folgenden Tabelle aufgelistet sind.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|[+ (Addition)](../mdx/add-mdx.md)|Addition zweier Zahlen.|  
|[/ (Dividieren)](../mdx/divide-mdx-operator-reference.md)|Dividiert eine Zahl durch eine andere Zahl.|  
|[* (Multiplikation)](../mdx/multiply-mdx.md)|Multipliziert zwei Zahlen.|  
|[- (Subtraktion)](../mdx/subtract-mdx.md)|Subtraktion zweier Zahlen.|  
|^ (Potenz) |Potenziert eine Zahl mit einer anderen Zahl.|  
  
> [!NOTE]  
>  MDX enthält keine Funktion, um die Quadratwurzel einer Zahl zu erhalten. Um die Quadratwurzel einer Zahl zu erhalten, potenzieren Sie sie mit 0,5 unter Verwendung des ^-Operators.  
  
## <a name="order-of-precedence"></a>Rangfolge  
 Die folgenden Regeln bestimmen die Rangfolge, die arithmetische Operatoren in einem MDX-Ausdruck haben.  
  
-   Sind in einem Ausdruck mehrere arithmetische Operatoren vorhanden, führt MDX Multiplikationen und Divisionen vor Subtraktionen und Additionen aus.  
  
-   Wenn alle arithmetischen Operatoren in einem Ausdruck die gleiche Rangfolge aufweisen, wird die Reihenfolge der Ausführung von links nach rechts angezeigt.  
  
-   Ausdrücke in Klammern erhalten Vorrang vor allen anderen Operationen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatoren &#40;MDX-Syntax&#41;](../mdx/operators-mdx-syntax.md)  
  
  
