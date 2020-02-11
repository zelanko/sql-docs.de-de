---
title: "\"Tggledrillstate\" (MDX) | Microsoft-Dokumentation"
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8d027a76a82de3fd82b6c0c81c54ace08167039b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036613"
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (MDX)


  Schaltet den Drillstatus von Elementen zwischen den Modi für Drilldown und Drillup um.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ToggleDrillState(Set_Expression1,Set_Expression2 [, [RECURSIVE] [,INCLUDE_CALC_MEMBERS] ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Rekursive*  
 (Optional). Ein Schlüsselwort, das einen rekursiven Vergleich von Mengen angibt. Die Funktion " **deggledrillstate** " ist eine Kombination der **DrillupMember** -Funktion und der **DrilldownMember** -Funktion. Die Rekursion wird nur angewendet, wenn sich der Member im **DrilldownMember** -Zustand befindet.  
  
 *Include_calc_members*  
 (Optional). Ein Flag, das anzeigt, ob berechnete Elemente eingeschlossen werden sollen, wenn sie vorhanden sind (auf Drilldownebene).  
  
## <a name="remarks"></a>Bemerkungen  
 Die Funktion " **teggledrillstate** " schaltet den Drill Status der einzelnen Elemente der zweiten Menge ein, die in der ersten Menge vorhanden ist. Die erste Menge kann Tupel beliebiger Dimensionalität aufweisen, die zweite Menge muss jedoch ausschließlich Elemente einer einzigen Dimension enthalten. Die Funktion " **deggledrillstate** " ist eine Kombination der **DrillupMember** -Funktion und der **DrilldownMember** -Funktion. Wenn der Member, *m*, der zweiten Menge in der ersten Menge vorhanden ist und dieser Member Drilldown ausgeführt wird (d. h. einen Nachfolger direkt darauf folgt), `DrillupMember(Set_Expression1, {m})` wird auf das Element oder Tupel in der ersten Menge angewendet. Wenn für dieses *m* -Element ein Drilldown ausgeführt wird (d. h. es gibt keinen Nachfolger von *m* , der unmittelbar auf *m*folgt), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` wird auf die erste Menge angewendet.  
  
 Wenn das optionale **rekursive** Flag verwendet wird, werden Drillup und Drilldown rekursiv angewendet. Weitere Informationen zum rekursiven Flag finden Sie unter den [DrillupMember](../mdx/drillupmember-mdx.md) -und [DrilldownMember](../mdx/drilldownmember-mdx.md) -Funktionen.  
  
 Durch Abfragen der XMLA-Eigenschaft "mdpropmdxdrillfunctions" können Sie den Grad der Unterstützung überprüfen, den der Server für die Bohr Funktionen bereitstellt. Weitere Informationen finden Sie [unter Unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
 Weitere Informationen finden Sie [unter Daten Bank Journal: MDX-Set-Funktionen: die Funktion "deggledrillstate ()](https://go.microsoft.com/fwlink/?LinkId=517759) " für Szenarien und Beispiele für diese Funktion.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Drilldown für das Australia-Element der ersten Menge und ein Drillup für das United States-Element der ersten Menge ausgeführt.  
  
```  
SELECT ToggleDrillState  
   ({[Geography].[Geography].[Country].Members, [Geography].[Geography].[Country].&[United States].Children},  
      {[Geography].[Geography].[Country].[Australia]  
      , [Geography].[Geography].[Country].&[United States]}  
      --, recursive  
      --, include_calc_members  
   ) ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
