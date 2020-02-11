---
title: Drilldownmembership Bottom (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 79bea49705c4f2fb66b8c9866be335433cbb783f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68049261"
---
# <a name="drilldownmemberbottom-mdx"></a>DrilldownMemberBottom (MDX)


  Führt einen Drilldown bei Elementen in einer angegebenen Menge aus, die in einer angegebenen zweiten Menge vorhanden sind, wobei das Resultset auf eine angegebene Anzahl von Elementen beschränkt wird. Alternativ führt diese Funktion auch einen Drilldown für einen Satz von Tupeln mithilfe der ersten tupelhierarchie oder der optional angegebenen Hierarchie aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DrillDownMemberBottom(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expresion>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Countdown*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *Hierarchy*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Rekursive*  
 Ein Schlüsselwort, das einen rekursiven Vergleich von Mengen angibt.  
  
 *include_calc_members*  
 Ein Schlüsselwort, durch das berechnete Elemente in Drilldownergebnisse eingeschlossen werden können.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein numerischer Ausdruck angegeben wird, sortiert die **drilldownmembership Bottom** -Funktion die untergeordneten Elemente jedes Elements in der ersten Menge in aufsteigender Reihenfolge nach dem Wert des numerischen Ausdrucks, der über die Menge der untergeordneten Elemente ausgewertet wird. Wenn kein numerischer Wert angegeben wird, sortiert die Funktion die untergeordneten Elemente jedes Elements in der ersten Menge aufsteigend nach den Werten der durch die Menge der untergeordneten Elemente dargestellten Zellen, wie durch den Abfragekontext bestimmt. Dieses Verhalten ähnelt dem der BottomCount-Funktion und der Tail (MDX)-Funktion, die eine MEnge untergeordneter Elemente in natürlicher Reihenfolge ohne Sortierung zurückgeben.  
  
 Nach dem Sortieren gibt die **drilldownmembership Bottom** -Funktion eine Menge zurück, die die übergeordneten Elemente und die in *count* angegebene Anzahl von untergeordneten Elementen mit dem niedrigsten Wert enthält und in beiden Sätzen enthalten ist.  
  
 Wenn **recursive** angegeben wird, sortiert die Funktion die erste Menge wie oben beschrieben und vergleicht dann rekursiv die Elemente der ersten Menge, wie Sie in einer Hierarchie angeordnet sind, mit der zweiten Menge. Die Funktion ruft die Anzahl der untersten untergeordneten Elemente für jedes Element in der ersten Menge ab, das auch in der zweiten vorhanden ist.  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
 Die **drilldownmembership Bottom** -Funktion ähnelt der [DrilldownMember](../mdx/drilldownmember-mdx.md) -Funktion. statt jedoch alle untergeordneten Elemente für jedes Element in der ersten Menge einzuschließen, das auch in der zweiten Menge vorhanden ist, gibt die **drilldownmembership Bottom** -Funktion die untersten Anzahl der untergeordneten Elemente für jedes Element zurück.  
  
 Durch Abfragen der XMLA-Eigenschaft "mdpropmdxdrillfunctions" können Sie den Grad der Unterstützung überprüfen, den der Server für die Bohr Funktionen bereitstellt. Weitere Informationen finden Sie [unter Unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
