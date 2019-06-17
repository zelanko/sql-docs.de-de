---
title: DrilldownMemberBottom (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 854f880cf9cb4f06ee4fc44fd18cec5f0ab99ca8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62691069"
---
# <a name="drilldownmemberbottom-mdx"></a>DrilldownMemberBottom (MDX)


  Führt einen Drilldown bei Elementen in einer angegebenen Menge aus, die in einer angegebenen zweiten Menge vorhanden sind, wobei das Resultset auf eine angegebene Anzahl von Elementen beschränkt wird. Sie können auch einen Drilldown diese Funktion auch für eine Menge von Tupeln mit der ersten tupelhierarchie oder der optional angegebenen Hierarchie.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DrillDownMemberBottom(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expresion>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *Hierarchy*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Rekursive*  
 Ein Schlüsselwort, das einen rekursiven Vergleich von Mengen angibt.  
  
 *Include_Calc_Members*  
 Ein Schlüsselwort, durch das berechnete Elemente in Drilldownergebnisse eingeschlossen werden können.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Ausdruck angegeben wird, die **DrilldownMemberBottom** sortiert in aufsteigender Reihenfolge der untergeordneten Elemente jedes Elements in der ersten Menge entsprechend dem Wert des numerischen Ausdrucks, ausgewertet über der Menge der untergeordneten Funktion Elemente. Wenn kein numerischer Wert angegeben wird, sortiert die Funktion die untergeordneten Elemente jedes Elements in der ersten Menge aufsteigend nach den Werten der durch die Menge der untergeordneten Elemente dargestellten Zellen, wie durch den Abfragekontext bestimmt. Dieses Verhalten ähnelt dem der BottomCount-Funktion und der Tail (MDX)-Funktion, die eine MEnge untergeordneter Elemente in natürlicher Reihenfolge ohne Sortierung zurückgeben.  
  
 Nach dem Sortieren gibt die **DrilldownMemberBottom** Funktionsergebnis ist eine Gruppe, die die übergeordneten Elemente und die Anzahl der untergeordneten Elemente im angegebenen enthält *Count* mit dem niedrigsten Wert enthalten, sowohl legt diese fest.  
  
 Wenn **REKURSIVE** angegeben wird, sortiert die Funktion die erste Menge wie oben beschrieben, und vergleicht dann rekursiv die Elemente der ersten Menge, mit der zweiten Menge hierarchisch organisiert. Die Funktion ruft die Anzahl der untersten untergeordneten Elemente für jedes Element in der ersten Menge ab, das auch in der zweiten vorhanden ist.  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
 Die **DrilldownMemberBottom** Funktion ist vergleichbar mit der [DrilldownMember](../mdx/drilldownmember-mdx.md) Funktion, statt jedoch alle untergeordneten Elemente für jedes Element in der ersten Menge, der auch einschließlich vorhanden in der zweiten Menge und die  **DrilldownMemberBottom** Funktion gibt die Anzahl der unterste untergeordneten Elemente für jedes Element zurück.  
  
 Abfrage der XMLA-Eigenschaft MdpropMdxDrillFunctions können Sie das Maß an Unterstützung, die der Server die drillingfunktionen bereitgestellt; finden Sie unter [unterstützte XMLA-Eigenschaften &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) Details.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
