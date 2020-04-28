---
title: Set-Operatoren | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6ad0b92a970c3618584365d9ad6e99420daef05d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037014"
---
# <a name="set-operators"></a>Mengenoperatoren


  In MDX (Multidimensional Expressions) führen Mengenoperatoren Operationen für Elemente oder Mengen aus und geben dann eine Menge zurück. Mengenoperatoren werden häufig als Alternative zu mehreren Mengenfunktionen in MDX-Ausdrücken verwendet.  
  
 MDX unterstützt die Mengenoperatoren, die in der folgenden Tabelle aufgelistet sind.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|[- (Except) (- (Außer))](../mdx/except-mdx-operator.md)|Gibt die Differenzmenge zweier Mengen zurück, wobei doppelte Elemente entfernt werden.<br /><br /> Dieser Operator ist funktionell gleichwertig mit der [Ausnahme](../mdx/except-mdx-function.md) Funktion.|  
|[* (Crossjoin)](../mdx/crossjoin-mdx-operator-reference.md)|Gibt das Kreuzprodukt zweier Mengen zurück.<br /><br /> Dieser Operator ist funktionell gleichwertig mit der [Crossjoin](../mdx/crossjoin-mdx.md) -Funktion.|  
|[: (Range) (: (Bereich))](../mdx/range-mdx.md)|Gibt eine natürlich geordnete Menge zurück, wobei die beiden angegebenen Elemente als Endpunkte und alle Elemente zwischen den beiden angegebenen Elementen als Elemente der Menge eingeschlossen werden.|  
|[+ (Union) (+ (Vereinigung))](../mdx/union-mdx-operator-reference.md)|Gibt eine Vereinigungsmenge zweier Mengen zurück, wobei doppelte Elemente ausgeschlossen werden.<br /><br /> Dieser Operator ist funktionell gleichwertig mit der&#41;Funktion der [Union-&#40;MDX](../mdx/union-mdx.md) .|  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatoren &#40;MDX-Syntax&#41;](../mdx/operators-mdx-syntax.md)  
  
  
