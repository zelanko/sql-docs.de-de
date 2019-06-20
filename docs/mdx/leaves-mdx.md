---
title: / / Blätter (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b18f283dce1ed5d0d3099dbdc26e27e8aff39ffc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270452"
---
# <a name="leaves-mdx"></a>Leaves (MDX)


  Gibt eine Menge mit allen Attribute zurück (kann optional auf die Attribute einer bestimmten Dimension beschränkt werden) Für alle Attribute x in der zurückgegebenen Menge gilt: Wenn x das Granularitätsattribut ist oder direkt oder indirekt mit diesem verknüpft ist, wird die Granularität ohne Auswirkung auf den Slice für das Attribut x festgelegt. Die **verlässt** Funktion für die Verwendung innerhalb einer SCOPE-Anweisung oder auf der linken Seite einer Zuweisung vorgesehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Dimension_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Dimension zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Blattelemente sind Tupel, die durch der Cross Join der niedrigsten Ebene aller Attributhierarchien gebildet werden. Berechnete Elemente sind ausgeschlossen.  
  
-   Wenn ein Dimensionsname angegeben wird, die **verlässt** Funktionsergebnis ist eine Gruppe, die den Blattelementen des Schlüsselattributs für die angegebene Dimension zurück.  
  
-   Wenn die Dimension mit mehreren Measuregruppen verknüpft ist, wird die des Measure im aktuellen Geltungsbereich verwendet.  
  
-   Wenn kein Dimensionsname angegeben wird, gibt die Funktion eine Menge mit den Blattelementen des gesamten Cubes zurück.  
  
    > [!NOTE]  
    >  Wenn der Dimensionsname in eine Hierarchie aufgelöst wird und der eindeutige Name der Hierarchie mit dem eindeutigen Dimensionsnamen identisch ist (Cubedimensionseigenschaft HierarchyUniqueNameStyle=ExcludeDimensionName und hierarchy name=dimension name), wird die Dimension verwendet.  
  
    > [!IMPORTANT]  
    >  Wenn nicht alle Attribute die gleiche Granularität für die Measuregruppe im aktuellen Bereich haben, wird ein Fehler erzeugt.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
