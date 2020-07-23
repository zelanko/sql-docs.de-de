---
title: Drilldownmembership Top (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5bed7dfcf82b7f768ba1dc1e98128424665af6bd
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970041"
---
# <a name="drilldownmembertop-mdx"></a>DrilldownMemberTop (MDX)


  Führt einen Drilldown bei Elementen in einer angegebenen Menge aus, die in einer angegebenen zweiten Menge vorhanden sind, wobei das Resultset auf eine angegebene Anzahl von Elementen beschränkt wird. Alternativ führt diese Funktion einen Drilldown für eine Menge von Tupeln mithilfe der ersten tupelhierarchie oder der optional angegebenen Hierarchie aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DrillDownMemberTop(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expression>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
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
  
 *include_calc_members*  
 Ein Schlüsselwort, durch das berechnete Elemente in Drilldownergebnisse eingeschlossen werden können.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein numerischer Ausdruck angegeben wird, sortiert die **drilldownmembership Top** -Funktion die untergeordneten Elemente jedes Elements in der ersten Menge in absteigender Reihenfolge nach dem Wert des numerischen Ausdrucks, der über die Menge der untergeordneten Elemente ausgewertet wird. Wenn kein numerischer Wert angegeben wird, sortiert die Funktion die untergeordneten Elemente jedes Elements in der ersten Menge absteigend nach den Werten der durch die Menge der untergeordneten Elemente dargestellten Zellen, bestimmt durch den Abfragekontext. Dieses Verhalten ähnelt dem der TopCount-Funktion und der Head (MDX)-Funktion, die eine Menge untergeordneter Elemente in natürlicher Reihenfolge ohne Sortierung zurückgeben.  
  
 Nach dem Sortieren gibt die **drilldownmembership Top** -Funktion eine Menge zurück, die die übergeordneten Elemente und die in *count* angegebene Anzahl von untergeordneten Elementen mit dem höchsten Wert enthält und in beiden Sätzen enthalten ist.  
  
 Wenn **recursive** angegeben wird, sortiert die Funktion die erste Menge wie oben beschrieben und vergleicht dann rekursiv die Elemente der ersten Menge, wie Sie in einer Hierarchie angeordnet sind, mit der zweiten Menge. Die-Funktion Ruft die höchste Anzahl von untergeordneten Elementen für jedes Element in der ersten Menge ab, das auch in der zweiten Menge vorhanden ist.  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
 Die **drilldownmembership Top** -Funktion ähnelt der [DrilldownMember](../mdx/drilldownmember-mdx.md) -Funktion. statt jedoch alle untergeordneten Elemente für jedes Element in der ersten Menge einzuschließen, das auch in der zweiten Menge vorhanden ist, gibt die **drilldownmembership Top** -Funktion die höchste Anzahl der untergeordneten Elemente für jedes Element zurück.  
  
 Durch Abfragen der XMLA-Eigenschaft "mdpropmdxdrillfunctions" können Sie den Grad der Unterstützung überprüfen, den der Server für die Bohr Funktionen bereitstellt. Weitere Informationen finden Sie [unter Unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](https://docs.microsoft.com/analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Drilldown in die Bekleidungskategorie durchgeführt, damit die drei Unterkategorien von Bekleidung mit den meisten gelieferten Bestellungen zurückgegeben werden.  
  
```  
SELECT DrilldownMemberTop   ({[Product].[Product Categories].[All Products],        
[Product].[Product Categories].[Category].Bikes,        
[Product].[Product Categories].[Category].Clothing},     
{[Product].[Product Categories].[Category].Clothing},     
3,     
[Measures].[Reseller Order Quantity])     
ON 0     
FROM [Adventure Works]     
WHERE [Measures].[Reseller Order Quantity]  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
