---
title: Mengenoperatoren | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1388c5ef1f263f4ef326485c662a82ee11c569d0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580952"
---
# <a name="set-operators"></a>Mengenoperatoren
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  In MDX (Multidimensional Expressions) führen Mengenoperatoren Operationen für Elemente oder Mengen aus und geben dann eine Menge zurück. Mengenoperatoren werden häufig als Alternative zu mehreren Mengenfunktionen in MDX-Ausdrücken verwendet.  
  
 MDX unterstützt die Mengenoperatoren, die in der folgenden Tabelle aufgelistet sind.  
  
|Operator|Description|  
|--------------|-----------------|  
|[- (Except) (- (Außer))](../mdx/except-mdx-operator.md)|Gibt die Differenzmenge zweier Mengen zurück, wobei doppelte Elemente entfernt werden.<br /><br /> Dieser Operator ist funktionell gleichwertig mit der [außer](../mdx/except-mdx-function.md) Funktion.|  
|[* (Crossjoin)](../mdx/crossjoin-mdx-operator-reference.md)|Gibt das Kreuzprodukt zweier Mengen zurück.<br /><br /> Dieser Operator ist funktionell gleichwertig mit der [Crossjoin](../mdx/crossjoin-mdx.md) Funktion.|  
|[: (Range) (: (Bereich))](../mdx/range-mdx.md)|Gibt eine natürlich geordnete Menge zurück, wobei die beiden angegebenen Elemente als Endpunkte und alle Elemente zwischen den beiden angegebenen Elementen als Elemente der Menge eingeschlossen werden.|  
|[+ (Union) (+ (Vereinigung))](../mdx/union-mdx-operator-reference.md)|Gibt eine Vereinigungsmenge zweier Mengen zurück, wobei doppelte Elemente ausgeschlossen werden.<br /><br /> Dieser Operator ist funktionell gleichwertig mit der [Union &#40;MDX&#41; ](../mdx/union-mdx.md) Funktion.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatoren &#40;MDX-Syntax&#41;](../mdx/operators-mdx-syntax.md)  
  
  
