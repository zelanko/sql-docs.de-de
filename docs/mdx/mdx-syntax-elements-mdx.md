---
title: MDX-Syntax Elemente (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 263238a0d8430928fad99042dfa0ffd06921a33b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68893324"
---
# <a name="mdx-syntax-elements-mdx"></a>MDX-Syntaxelemente (MDX)


  MDX (Multidimensional Expressions) hat mehrere Syntaxelemente, die von den meisten Anweisungen verwendet werden bzw. sich auf die meisten Anweisungen auswirken:  
  
|Begriff|Definition|  
|----------|----------------|  
|[Bezeichner](../mdx/identifiers-mdx.md)|Ein Bezeichner ist der Name eines Objekts (z. B. eines Cubes, einer Dimension, eines Elements oder eines Measures).|  
|**Datentypen**|Definieren die Typen der Daten, die in Zellen, Elementeigenschaften oder Zelleigenschaften enthalten sind. MDX unterstützt nur den OLE VARIANT-Datentyp. Weitere Informationen zur Koersion, Konvertierung und Bearbeitung des VARIANT-Datentyps finden Sie in der Dokumentation für Platform SDK im Abschnitt über VARIANT und VARIANTARG.|  
|[Ausdrücke &#40;MDX-&#41;](../mdx/expressions-mdx.md)|Ausdrücke sind Syntax Einheiten, die Analysis Services in einzelne (skalare) Werte oder Objekte auflösen können. Ausdrücke enthalten Funktionen, die einen einzelnen Wert, einen Mengenausdruck usw. zurückgeben.|  
|[Operatoren](../mdx/operators-mdx-syntax.md)|Operatoren sind Syntaxelemente, die mit einem oder mehreren einfachen MDX-Ausdrücken verwendet werden, um komplexere MDX-Ausdrücke zu erstellen.|  
|[Funktionen](../mdx/functions-mdx-syntax.md)|Funktionen sind Syntaxelemente, die keinen, einen oder mehrere Eingabewerte annehmen und einen Skalarwert oder ein Objekt zurückgeben. Beispiele hierfür sind die [Sum](../mdx/sum-mdx.md) -Funktion zum Hinzufügen von mehreren Werten, die [Members](../mdx/members-set-mdx.md) -Funktion zum Zurückgeben einer Menge von Elementen aus einer Dimension oder Ebene usw.|  
|[Iny](../mdx/comments-mdx-syntax.md)|Kommentare sind Texte, die in MDX-Anweisungen oder Skripts eingefügt werden, um den Zweck der Anweisung zu erklären. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]führt keine Kommentare aus.|  
|[Reservierte Schlüsselwörter](../mdx/reserved-keywords-mdx-syntax.md)|Reservierte Schlüsselwörter sind Wörter, die für die Verwendung durch MDX reserviert sind. Sie dürfen nicht für Objektnamen verwendet werden, die in MDX-Anweisungen verwendet werden.|  
|[Elemente, Tupel und Mengen](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx)|Elemente, Tupel und Mengen sind Bestandteile des Kernkonzepts für mehrdimensionale Daten. Sie sollten diese Begriffe verstanden haben, bevor Sie eine MDX-Abfrage erstellen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mehrdimensionale Ausdrücke &#40;MDX-&#41; Referenz](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
