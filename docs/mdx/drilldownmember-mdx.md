---
description: DrilldownMember (MDX)
title: DrilldownMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 284456995d163c04bc315424ea04b76f17dc228e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421924"
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
  
 *include_calc_members*  
 Ein Schlüsselwort, durch das berechnete Elemente in Drilldownergebnisse eingeschlossen werden können.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion gibt untergeordnete Elemente zurück, die nach Hierarchie sortiert werden, und schließt in der ersten Menge angegebene Elemente ein, die auch in der zweiten Menge vorhanden sind. Für übergeordnete Elemente wird kein Drilldown ausgeführt, wenn die erste Menge das übergeordnete Element und ein oder mehrere untergeordnete Elemente enthält. Die erste Menge kann jede beliebige Dimensionalität aufweisen, die zweite muss jedoch eine eindimensionale Menge enthalten. Die Reihenfolge der ursprünglichen Elemente in der ersten Menge wird beibehalten, wobei jedoch alle in das Resultset der Funktion aufgenommenen untergeordneten Elemente direkt unter ihrem übergeordneten Element aufgenommen werden. Die Funktion bildet das Resultset, indem die untergeordneten Elemente für jedes Element in der ersten Menge abgerufen werden, das auch in der zweiten vorhanden ist. Wenn **RECURSIVE** angegeben wird, vergleicht die Funktion weiterhin rekursiv die Elemente des Resultsets mit der zweiten Menge und ruft dabei die untergeordneten Elemente für jedes Element im Resultset ab, das auch in der zweiten Menge vorhanden ist, bis keine weiteren Elemente aus dem Resultset in der zweiten Menge gefunden werden.  
  
 Durch Abfragen der XMLA-Eigenschaft " **mdpropmdxdrillfunctions** " können Sie den Grad der Unterstützung überprüfen, den der Server für die Bohr Funktionen bereitstellt. Weitere Informationen finden Sie [unter Unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](https://docs.microsoft.com/analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
 Die erste Menge kann auch Tupel anstelle von Elementen enthalten. Der Drilldown für Tupel ist eine Erweiterung von OLE DB und gibt eine Menge von Tupeln anstelle von Elementen zurück.  
  
> [!IMPORTANT]  
>  In ein Element wird kein Drilldown ausgeführt, wenn unmittelbar auf das Element eines seiner untergeordneten Elemente folgt. Die Reihenfolge der Elemente in der Gruppe ist für die Drilldown-und Drillup- \* Funktions Familien von Bedeutung.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
