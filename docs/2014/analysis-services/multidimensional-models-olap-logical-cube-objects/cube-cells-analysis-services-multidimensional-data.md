---
title: Cubezellen (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d9ca444c4e889c68f90abf4cf76c07d1c2d574a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887913"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a>Cubezellen (Analysis Services – Mehrdimensionale Daten)
  Ein Cube besteht aus Zellen, die nach Measuregruppen und nach Dimensionen organisiert werden. Eine Zelle stellt den eindeutigen logischen Schnittpunkt in einem Cube eines Elements aus jeder Dimension des Cubes dar. Der im folgenden Diagramm beschriebene Cube enthält beispielsweise eine Measuregruppe mit zwei Measures, die nach den drei Dimensionen Source, Route und Time organisiert sind.  
  
 ![Cubediagramm mit identifizierter einzelner Zelle](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-cubeintro5.gif "Cubediagramm mit identifizierter einzelner Zelle")  
  
 Die schattierte Zelle in diesem Diagramm ist der Schnittpunkt der folgenden Elemente:  
  
-   Das air-Element der Route-Dimension.  
  
-   Das Africa-Element der Source-Dimension.  
  
-   Das 4th quarter-Element der Time-Dimension.  
  
-   Das Packages-Measure.  
  
## <a name="leaf-and-nonleaf-cells"></a>Blatt- und Nichtblattzellen  
 Der Wert für eine Zelle in einem Cube kann auf eine der folgenden Arten abgerufen werden. Im vorherigen Beispiel kann der Wert in der Zelle direkt aus der Fakten Tabelle des Cubes abgerufen werden, da alle Elemente, die zum Identifizieren dieser Zelle verwendet werden, *Blatt*Elemente sind. Ein Blattelement weist in der Hierarchie keine untergeordneten Elemente auf und verweist normalerweise auf einen einzelnen Datensatz in einer Dimensionstabelle. Diese Art von Zelle wird als *Blatt Zelle*bezeichnet.  
  
 Eine Zelle kann jedoch auch mit *nicht Blatt*Elementen identifiziert werden. Ein Nichtblattelement ist ein Element, das mindestens ein untergeordnetes Element aufweist. In diesem Fall wird der Wert der Zelle normalerweise aus der Aggregation der mit dem Nichtblattelement verknüpften untergeordneten Elemente abgeleitet. Der Schnittpunkt der folgenden Elemente und Dimensionen bezieht sich z. B. auf eine Zelle, deren Wert durch Aggregation angegeben wird:  
  
-   Das air-Element der Route-Dimension.  
  
-   Das Africa-Element der Source-Dimension.  
  
-   Das 2nd half-Element der Time-Dimension.  
  
-   Das Packages-Element.  
  
 Das 2nd half-Element der Time-Dimension ist ein Nichtblattelement. Daher müssen alle mit ihm verbundenen Elemente aggregierte Werte sein, wie im folgenden Diagramm dargestellt.  
  
 ![Zellen '3rd quarter' und '4th quarter' für '2nd half'-Element](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-cubeintro6.gif "Zellen '3rd quarter' und '4th quarter' für '2nd half'-Element")  
  
 Wenn es sich beispielsweise bei den Aggregationen für das 3rd quarter- und 4th quarter-Element um Summen handelt, dann ist der Wert der angegebenen Zelle 400, die Summe aller Blattzellen, die im vorherigen Diagramm schattiert sind. Da der Wert der Zelle von der Aggregation anderer Zellen abgeleitet ist, wird die angegebene Zelle als eine *nicht Blatt Zelle*betrachtet.  
  
 Die Zellenwerte, die für Elemente, die benutzerdefinierte Rollups und Elementgruppen verwenden, sowie für benutzerdefinierte Elemente abgeleitet werden, werden ähnlich behandelt. Zellwerte, die für berechnete Elemente abgeleitet werden, basieren jedoch vollständig auf dem MDX-Ausdruck (Multidimensional Expressions), der zum Definieren des berechneten Elements verwendet wird. Möglicherweise sind in einigen Fällen keine tatsächlichen Zellendaten betroffen. Weitere Informationen finden Sie unter [benutzerdefinierte Rollup-Operatoren in über-und untergeordneten Dimensionen](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [Definieren von benutzerdefinierten Element Formeln](../multidimensional-models/attribute-properties-define-custom-member-formulas.md)und [Berechnungen](../multidimensional-models-olap-logical-cube-objects/calculations.md).  
  
## <a name="empty-cells"></a>Leere Zellen  
 Nicht jede Zelle in einem Cube muss einen Wert enthalten. Es können Schnittpunkte in einem Cube enthalten sein, die keine Daten enthalten. Diese Schnittpunkte, die als leere Zellen bezeichnet werden, treten in Cubes häufig auf, da nicht jeder Schnittpunkt eines Dimensionsattributs mit einem Measure innerhalb eines Cubes einen entsprechenden Datensatz in einer Faktentabelle enthält. Das Verhältnis leerer Zellen in einem Cube zur Gesamtanzahl der Zellen in einem Cube wird häufig als die *sparacity* eines Cubes bezeichnet.  
  
 Die in dem folgenden Diagramm abgebildete Cubestruktur ähnelt z. B. anderen Beispielen in diesem Thema. In diesem Beispiel sind jedoch keine Luftfrachtlieferungen nach Afrika im dritten Quartal oder nach Australien im vierten Quartal vorhanden. In der Faktentabelle sind keine Daten enthalten, die die Schnittpunkte dieser Dimensionen und Measures unterstützen können, sodass die Zellen an diesen Schnittpunkten leer sind.  
  
 ![Cubediagramm mit identifizierten leeren Zellen](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-cubeintro7.gif "Cubediagramm mit identifizierten leeren Zellen")  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]handelt es sich bei einer leeren Zelle um eine Zelle, die über besondere Qualitäten verfügt. Da leere Zellen die Ergebnisse von Crossjoins, Zählungen usw. verfälschen können, ermöglichen viele MDX-Funktionen das Ignorieren dieser leeren Zellen bei der Berechnung. Weitere Informationen finden Sie unter mehr [dimensionale Ausdrücke &#40;MDX-&#41; Referenz](/sql/mdx/multidimensional-expressions-mdx-reference)und [wichtige Konzepte in MDX &#40;Analysis Services&#41;](../multidimensional-models/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="security"></a>Sicherheit  
 Der Zugriff auf Zellendaten wird in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf Rollenebene verwaltet und kann mithilfe von MDX-Ausdrücken genau gesteuert werden. Weitere Informationen finden Sie unter [Erteilen eines benutzerdefinierten Zugriffs auf Dimensions Daten &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)und [Erteilen von benutzerdefiniertem Zugriff auf Zellen Daten &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cube-Speicher &#40;Analysis Services Mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)   
 [Aggregations and Aggregation Designs](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
