---
title: Blätter (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d29c77250c23900d74d1969a6c37bc719c89cdd7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905735"
---
# <a name="leaves-mdx"></a>Leaves (MDX)


  Gibt eine Menge mit allen Attribute zurück (kann optional auf die Attribute einer bestimmten Dimension beschränkt werden) Für alle Attribute x in der zurückgegebenen Menge gilt: Wenn x das Granularitätsattribut ist oder direkt oder indirekt mit diesem verknüpft ist, wird die Granularität ohne Auswirkung auf den Slice für das Attribut x festgelegt. Die Left **-Funktion ist** für die Verwendung in einer SCOPE-Anweisung oder auf der linken Seite einer Zuweisung konzipiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Dimension_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Dimension zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Blattelemente sind Tupel, die durch der Cross Join der niedrigsten Ebene aller Attributhierarchien gebildet werden. Berechnete Elemente sind ausgeschlossen.  
  
-   Wenn ein Dimensions Name angegeben wird, gibt die **Blätter** -Funktion eine Menge zurück, die die Blatt Elemente des Schlüssel Attributs für die angegebene Dimension enthält.  
  
-   Wenn die Dimension mit mehreren Measuregruppen verknüpft ist, wird die des Measure im aktuellen Geltungsbereich verwendet.  
  
-   Wenn kein Dimensionsname angegeben wird, gibt die Funktion eine Menge mit den Blattelementen des gesamten Cubes zurück.  
  
    > [!NOTE]  
    >  Wenn der Dimensionsname in eine Hierarchie aufgelöst wird und der eindeutige Name der Hierarchie mit dem eindeutigen Dimensionsnamen identisch ist (Cubedimensionseigenschaft HierarchyUniqueNameStyle=ExcludeDimensionName und hierarchy name=dimension name), wird die Dimension verwendet.  
  
    > [!IMPORTANT]  
    >  Wenn nicht alle Attribute die gleiche Granularität für die Measuregruppe im aktuellen Bereich haben, wird ein Fehler erzeugt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
