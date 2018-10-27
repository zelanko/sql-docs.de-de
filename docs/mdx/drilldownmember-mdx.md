---
title: DrilldownMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f5ab4ee77bad08ab3883645ad5e2628a265aa4e9
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144895"
---
# <a name="drilldownmember-mdx"></a>DrilldownMember (MDX)


  Führt einen Drilldown für Elemente in einer angegebenen Menge aus, die in einer angegebenen zweiten Menge vorhanden sind.  
  
 Alternativ führt die Funktion einen Drilldown für eine Menge von Tupeln unter Verwendung der ersten Tupelhierarchie oder der optional angegebenen Hierarchie aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DrillDownMember(<Set_Expression1>, <Set_Expression2> [,[<Target_Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Target_Hierarchy*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Rekursive*  
 Ein Schlüsselwort, das einen rekursiven Vergleich von Mengen angibt.  
  
 *Include_Calc_Members*  
 Ein Schlüsselwort, durch das berechnete Elemente in Drilldownergebnisse eingeschlossen werden können.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion gibt untergeordnete Elemente zurück, die nach Hierarchie sortiert werden, und schließt in der ersten Menge angegebene Elemente ein, die auch in der zweiten Menge vorhanden sind. Für übergeordnete Elemente wird kein Drilldown ausgeführt, wenn die erste Menge das übergeordnete Element und ein oder mehrere untergeordnete Elemente enthält. Die erste Menge kann jede beliebige Dimensionalität aufweisen, die zweite muss jedoch eine eindimensionale Menge enthalten. Die Reihenfolge der ursprünglichen Elemente in der ersten Menge wird beibehalten, wobei jedoch alle in das Resultset der Funktion aufgenommenen untergeordneten Elemente direkt unter ihrem übergeordneten Element aufgenommen werden. Die Funktion bildet das Resultset, indem die untergeordneten Elemente für jedes Element in der ersten Menge abgerufen werden, das auch in der zweiten vorhanden ist. Wenn **RECURSIVE** angegeben wird, vergleicht die Funktion weiterhin rekursiv die Elemente des Resultsets mit der zweiten Menge und ruft dabei die untergeordneten Elemente für jedes Element im Resultset ab, das auch in der zweiten Menge vorhanden ist, bis keine weiteren Elemente aus dem Resultset in der zweiten Menge gefunden werden.  
  
 Abfrage der XMLA-Eigenschaft **MdpropMdxDrillFunctions** ermöglicht es Ihnen, überprüfen Sie, ob das Maß an Unterstützung, die der Server die drillingfunktionen bereitgestellt; Siehe [unterstützte XMLA-Eigenschaften &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)Details.  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
> [!IMPORTANT]  
>  In ein Element wird kein Drilldown ausgeführt, wenn unmittelbar auf das Element eines seiner untergeordneten Elemente folgt. Die Reihenfolge der Elemente in der Menge ist wichtig, für die Drilldown * und einen Drillup\* Funktionsreihe.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Drilldown für das Australia-Element der ersten Menge, das auch in der zweiten Menge enthalten ist, ausgeführt.  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   )  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird ein Drilldown für das Australia-Element der ersten Menge, das auch in der zweiten Menge enthalten ist, ausgeführt. Da jedoch das RECURSIVE-Argument angegeben ist, vergleicht die Funktion weiterhin rekursiv die Elemente des Resultsets (Elemente der State-Province-Ebene) mit der zweiten Menge und ruft dabei die untergeordneten Elemente für jedes Element im Resultset (Elemente der City-Ebene) ab, das auch in der zweiten Menge vorhanden ist, bis keine weiteren Elemente aus dem Resultset in der zweiten Menge gefunden werden.  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   ,RECURSIVE)  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
