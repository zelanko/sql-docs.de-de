---
title: MDX-Syntaxelemente (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b530205a5165c9be77710bf86e8600174be890dc
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581022"
---
# <a name="mdx-syntax-elements-mdx"></a>MDX-Syntaxelemente (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  MDX (Multidimensional Expressions) hat mehrere Syntaxelemente, die von den meisten Anweisungen verwendet werden bzw. sich auf die meisten Anweisungen auswirken:  
  
|Begriff|Definition|  
|----------|----------------|  
|[Identifiers (Bezeichner)](../mdx/identifiers-mdx.md)|Ein Bezeichner ist der Name eines Objekts (z. B. eines Cubes, einer Dimension, eines Elements oder eines Measures).|  
|**Datentypen**|Definieren die Typen der Daten, die in Zellen, Elementeigenschaften oder Zelleigenschaften enthalten sind. MDX unterstützt nur den OLE VARIANT-Datentyp. Weitere Informationen zur Koersion, Konvertierung und Bearbeitung des VARIANT-Datentyps finden Sie in der Dokumentation für Platform SDK im Abschnitt über VARIANT und VARIANTARG.|  
|[Ausdrücke &#40;MDX&#41;](../mdx/expressions-mdx.md)|Ausdrücke ist eine Syntaxeinheit, die [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] auflösen kann, um die einzelnen (skalaren) Werten oder Objekten. Ausdrücke enthalten Funktionen, die einen einzelnen Wert, einen Mengenausdruck usw. zurückgeben.|  
|[Operatoren](../mdx/operators-mdx-syntax.md)|Operatoren sind Syntaxelemente, die mit einem oder mehreren einfachen MDX-Ausdrücken verwendet werden, um komplexere MDX-Ausdrücke zu erstellen.|  
|[Funktionen](../mdx/functions-mdx-syntax.md)|Funktionen sind Syntaxelemente, die keinen, einen oder mehrere Eingabewerte annehmen und einen Skalarwert oder ein Objekt zurückgeben. Beispiele hierfür sind die [Summe](../mdx/sum-mdx.md) -Funktion zum Hinzufügen mehrerer Werte, die [Elemente](../mdx/members-set-mdx.md) -Funktion zum Zurückgeben einer Menge von Elementen aus einer Dimension oder Ebene, und so weiter.|  
|[Kommentare](../mdx/comments-mdx-syntax.md)|Kommentare sind Texte, die in MDX-Anweisungen oder Skripts eingefügt werden, um den Zweck der Anweisung zu erklären. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Kommentare wird nicht ausgeführt werden.|  
|[Reservierte Schlüsselwörter](../mdx/reserved-keywords-mdx-syntax.md)|Reservierte Schlüsselwörter sind Wörter, die für die Verwendung durch MDX reserviert sind. Sie dürfen nicht für Objektnamen verwendet werden, die in MDX-Anweisungen verwendet werden.|  
|[Elemente, Tupel und Mengen](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)|Elemente, Tupel und Mengen sind Bestandteile des Kernkonzepts für mehrdimensionale Daten. Sie sollten diese Begriffe verstanden haben, bevor Sie eine MDX-Abfrage erstellen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Mehrdimensionale Ausdrücke &#40;MDX&#41; Verweis](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
