---
title: DrilldownLevelBottom (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14b0b2dfd3e4578558e49cc305c37821e208c65d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62516029"
---
# <a name="drilldownlevelbottom-mdx"></a>DrilldownLevelBottom (MDX)


  Führt einen Drilldown der untersten Elemente einer Menge auf einer angegebenen Ebene in eine darunter liegende Ebene aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
DrilldownLevelBottom(Set_Expression, Count [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Numeric_Expression*  
 Optional. Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *Include_Calc_Members*  
 Optional. Ein Schlüsselwort, das Drilldownergebnissen berechnete Elemente hinzufügt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Wert angegeben wird, sortiert die **DrilldownLevelBottom** -Funktion die untergeordneten Elemente jedes Elements in der angegebenen Menge aufsteigend nach dem angegebenen Wert, ausgewertet über der Menge der untergeordneten Elemente. Wenn kein numerischer Ausdruck angegeben wird, sortiert die Funktion die untergeordneten Elemente jedes Elements in der angegebenen Menge in aufsteigender Reihenfolge nach den durch die Menge der untergeordneten Elemente dargestellten Zellenwerten, wie durch den Abfragekontext bestimmt. Dieses Verhalten ähnelt dem der BottomCount-Funktion und Tail (MDX)-Funktion, die eine Menge von Elementen in natürlicher Reihenfolge ohne Sortierung zurückgeben.  
  
 Nach dem Sortieren gibt die **DrilldownLevelBottom** -Funktion eine Menge zurück, die die übergeordneten Elemente und die in *Count*angegebene Anzahl der untergeordneten Elemente mit dem niedrigsten Wert enthält.  
  
 Die **DrilldownLevelBottom** -Funktion gleicht der [DrilldownLevel](../mdx/drilldownlevel-mdx.md) -Funktion, statt jedoch alle untergeordneten Elemente für jedes Element auf der angegebenen Ebene einzuschließen, gibt die **DrilldownLevelBottom** -Funktion die angegebene Anzahl der untersten untergeordneten Elemente zurück.  
  
 Abfrage der XMLA-Eigenschaft MdpropMdxDrillFunctions können Sie das Maß an Unterstützung, die der Server die drillingfunktionen bereitgestellt; finden Sie unter [unterstützte XMLA-Eigenschaften &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) Details.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die untersten drei untergeordneten Elemente der Product Category-Ebene basierend auf dem Standardmeasure zurückgegeben. Im Adventure Works-Beispielcube sind die untersten drei untergeordneten Elemente für Accessories Tires and Tubes, Pumps und Panniers. In Management Studio können Sie im MDX-Abfragefenster zu Products | Product Categories | Members | All Products | Accessories navigieren, um die vollständige Liste anzuzeigen. Sie können das Count-Argument erhöhen, damit mehr Elemente zurückgegeben werden.  
  
```  
SELECT DrilldownLevelBottom   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Im nächsten Beispiel wird die Verwendung des **include_calc_members** -Flags gezeigt. Dieses wird genutzt, um berechnete Elemente auf Drilldown-Ebene einzuschließen. Das Measure [Reseller Order Count] wird der **DrilldownLevelBottom** -Anweisung hinzugefügt, um sicherzustellen, dass die Ergebnisse nach diesem Measure sortiert werden. Sie müssen Count auf mindestens 9 erhöhen, um diese berechneten Elemente anzuzeigen.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELBOTTOM(  
  [Product].[Product Categories].children ,  
  9,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
