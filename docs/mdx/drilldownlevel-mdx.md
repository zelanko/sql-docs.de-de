---
title: DrilldownLevel (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fbab3ea6efe0c1e5b896febeef4d1f38877b8965
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145655"
---
# <a name="drilldownlevel-mdx"></a>DrilldownLevel (MDX)


  Führt einen Drilldown der Elemente einer Menge in eine Ebene unter der untersten Ebene aus, die in der Menge dargestellt ist.  
  
 Angeben der Ebene klicken Sie, einen Drilldown nach unten ist optional, aber wenn Sie die Ebene festlegen, können Sie entweder eine **Ebene Ausdruck** oder **Indexebene**. Diese Argumente schließen sich gegenseitig aus. Wenn berechnete Elemente in der Abfrage vorhanden sind, können Sie ein Argument angeben, um sie in das Rowset einzubeziehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
DrilldownLevel(Set_Expression [,[Level_Expression] ,[Index]] [,INCLUDE_CALC_MEMBERS])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Level_Expression*  
 (Optional). Ein MDX-Ausdruck, der explizit die Ebene für den Drilldown identifiziert. Wenn Sie einen Ebenenausdruck angegeben, überspringen Sie das Indexargument unten.  
  
 *Index*  
 (Optional). Ein gültiger numerischer Ausdruck, der die Nummer der Hierarchie angibt, in die innerhalb der Menge ein Drilldown durchgeführt werden soll. Sie können die Indexebene statt Level_Expression verwenden, um explizit die Ebene festzulegen, auf die ein Drilldown ausgeführt werden soll.  
  
 *Include_Calc_Members*  
 (Optional). Ein Flag, das anzeigt, ob berechnete Elemente eingeschlossen werden sollen, wenn sie vorhanden sind (auf Drilldownebene).  
  
## <a name="remarks"></a>Hinweise  
 Die **DrilldownLevel** Funktion gibt einen Satz untergeordneter Elemente in einer hierarchischen Reihenfolge, basierend auf den Elementen, die in der angegebenen Menge enthalten. Die Reihenfolge der ursprünglichen Elemente in der angegebenen Menge wird beibehalten, wobei jedoch alle in das Resultset der Funktion aufgenommenen untergeordneten Elemente direkt unter ihrem übergeordneten Element aufgenommen werden.  
  
 Wenn eine Datenstruktur mit einer Hierarchie mit mehreren Ebenen vorliegt, können Sie explizit eine Ebene auswählen, auf die der Drilldown erfolgen soll. Es gibt zwei Möglichkeiten, die Ebene festzulegen. Diese schließen sich gegenseitig aus. Der erste Ansatz besteht darin, legen Sie die **Level_expression** Arguments mithilfe eines MDX-Ausdrucks, der die Ebene, ein alternativer Ansatz zurückgibt, ist die Angabe der **Index** Argument, das mithilfe eines numerischen Ausdrucks, Gibt die Ebene nach Zahlen an.  
  
 Wenn ein Ebenenausdruck angegeben wird, erstellt die Funktion eine Menge in einer hierarchischen Reihenfolge, indem die untergeordneten Elemente nur für diejenigen Elemente abgerufen werden, die sich auf der angegebenen Ebene befinden. Wenn ein Ebenenausdruck festgelegt ist und sich auf dieser Ebene kein Element befindet, wird der Ebenenausdruck ignoriert.  
  
 Wenn ein Indexwert angegeben wird, erstellt die Funktion basierend auf einem nullbasierten Index eine Menge in einer hierarchischen Reihenfolge, indem die untergeordneten Elemente nur für die Elemente auf der nächstunteren Ebene der Dimension abgerufen werden, auf die in der Menge verwiesen wird.  
  
 Wenn weder ein Ebenenausdruck noch ein Indexwert angegeben wird, erstellt die Funktion eine Menge in einer hierarchischen Reihenfolge, indem die untergeordneten Elemente nur für die Elemente, die auf der untersten Ebene der ersten Dimension in der angegebenen Menge verwiesen werden abgerufen.  
  
 Abfrage der XMLA-Eigenschaft MdpropMdxDrillFunctions können Sie das Maß an Unterstützung, die der Server die drillingfunktionen bereitgestellt; finden Sie unter [unterstützte XMLA-Eigenschaften &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) Details.  
  
## <a name="examples"></a>Beispiele  
 Sie können die folgenden Beispiele im MDX-Abfragefenster in SSMS ausprobieren. Verwenden Sie dafür den Adventure Works-Cube.  
  
 **Beispiel 1 – zeigt minimale syntax**  
  
 Das erste Beispiel zeigt die minimale Syntax für **DrilldownLevel**. Das einzige erforderliche Argument ist ein Mengenausdruck. Beachten Sie, dass wenn Sie diese Abfrage ausführen, die übergeordnete [All Categories] und die Elemente der nächstniedrigeren Ebene Sie nach unten erhalten: [Accessories], [Bikes] und so weiter. Obwohl in diesem Beispiel einfach ist, wird den grundlegenden Zweck von veranschaulicht die **DrilldownLevel** -Funktion, die auf der darunter liegenden Ebene einen Drilldown ist.  
  
```  
SELECT DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]}}) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 Beispiel 2 – Alternative Syntax mit expliziter Indexebene  
  
 Dieses Beispiel zeigt die alternative Syntax. Hier wird die Indexebene über einen numerischen Ausdruck festgelegt. In diesem Fall ist die Indexebene 0. Für einen nullbasierten Index ist das die unterste Ebene.  
  
```  
SELECT  
DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]},,0) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 Beachten Sie, dass das Resultset mit der vorherigen Abfrage identisch ist. Allgemein gilt, ein Festlegen der Indexebene ist unnötig, es sei denn, der Drilldown soll auf einer bestimmten Ebene beginnen. Führen Sie die vorherige Abfrage erneut aus, und legen Sie einen Indexwert von 1 und dann von 2 fest. Ist der Indexwert auf 1 festgelegt, beginnt der Drilldown auf der zweiten Ebene der Hierarchie. Ist der Indexwert auf 2 festgelegt, beginnt der Drilldown auf der dritten Ebene, der höchsten Ebene in diesem Beispiel. Je höher der numerische Ausdruck, desto höher die Indexebene.  
  
 **Beispiel 3 – zeigt einen Ebenenausdruck**  
  
 Im folgenden Beispiel wird die Verwendung eines Ebenenausdrucks veranschaulicht. Wenn eine Menge vorliegt, die eine hierarchische Struktur darstellt, können Sie mit einem Ebenenausdruck eine Ebene in der Hierarchie auswählen, auf der der Drilldown beginnen soll.  
  
 In diesem Beispiel beginnt die Stufe des Drilldowns auf [City], als das zweite Argument der der **DrilldownLevel** Funktion. Wenn Sie diese Abfrage ausführen, beginnt der Drilldown auf der Ebene [City] für die Staaten Washington und Oregon. Pro dem **DrilldownLevel** -Funktion, auch das Resultset enthält die Elemente auf der nächstniedrigeren Ebene, [Postal Codes].  
  
```  
SELECT [Measures].[Internet Sales Amount] ON COLUMNS,  
   NON EMPTY (  
   DRILLDOWNLEVEL(  
       {[Customer].[Customer Geography].[Country].[United States],  
           DESCENDANTS(  
             { [Customer].[Customer Geography].[State-Province].[Washington],    
               [Customer].[Customer Geography].[State-Province].[Oregon]},   
               [Customer].[Customer Geography].[City]) } ,  
[Customer].[Customer Geography].[City] ) )  ON ROWS  
FROM [Adventure Works]  
```  
  
 **Beispiel 4 – einschließen berechneter Elemente**  
  
 Das letzte Beispiel zeigt ein berechnetes Element, das am Ende das Ergebnis angezeigt wird. Legen Sie beim Hinzufügen der **Include_calculated_members** Flag. Beachten Sie, dass das Flag als vierter Parameter festgelegt ist.  
  
 Dieses Beispiel funktioniert, weil das berechnete Element sich auf derselben Ebene befindet wie die nicht berechneten Elemente. Das berechnete Element [West Coast] ist aus den Elementen aus [United States] und allen Elementen aus einer Ebene unter [United States] zusammengesetzt.  
  
```  
WITH MEMBER   
[Customer].[Customer Geography].[Country].&[United States].[West Coast] AS  
[Customer].[Customer Geography].[State-Province].&[OR]&[US] +  
[Customer].[Customer Geography].[State-Province].&[WA]&[US] +  
[Customer].[Customer Geography].[State-Province].&[CA]&[US]  
SELECT [Measures].[Internet Order Count] ON 0,  
DRILLDOWNLEVEL([Customer].[Customer Geography].[Country].&[United States],,,INCLUDE_CALC_MEMBERS) on 1  
FROM [Adventure Works]  
```  
  
 Wenn Sie nur das Flag entfernen und die Abfrage erneut ausführen, erhalten Sie die gleichen Ergebnisse, nur ohne das berechnete Element [West Coast].  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
