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
ms.openlocfilehash: b9c623a1e99053e796609dc82f27519f27c07a9d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68049289"
---
# <a name="drilldownlevel-mdx"></a>DrilldownLevel (MDX)


  Führt einen Drilldown der Elemente einer Menge in eine Ebene unter der untersten Ebene aus, die in der Menge dargestellt ist.  
  
 Das Angeben der Ebene, bei der der Drilldown durchführen soll, ist optional. Wenn Sie jedoch die Ebene festlegen, können Sie entweder einen **Ebenenausdruck** oder die **Index Ebene**verwenden. Diese Argumente schließen sich gegenseitig aus. Wenn berechnete Elemente in der Abfrage vorhanden sind, können Sie ein Argument angeben, um sie in das Rowset einzubeziehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
DrilldownLevel(Set_Expression [,[Level_Expression] ,[Index]] [,INCLUDE_CALC_MEMBERS])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Level_Expression*  
 (Optional). Ein MDX-Ausdruck, der explizit die Ebene für den Drilldown identifiziert. Wenn Sie einen Ebenenausdruck angegeben, überspringen Sie das Indexargument unten.  
  
 *Sin*  
 (Optional). Ein gültiger numerischer Ausdruck, der die Nummer der Hierarchie angibt, in die innerhalb der Menge ein Drilldown durchgeführt werden soll. Sie können die Indexebene statt Level_Expression verwenden, um explizit die Ebene festzulegen, auf die ein Drilldown ausgeführt werden soll.  
  
 *include_calc_members*  
 (Optional). Ein Flag, das anzeigt, ob berechnete Elemente eingeschlossen werden sollen, wenn sie vorhanden sind (auf Drilldownebene).  
  
## <a name="remarks"></a>Bemerkungen  
 Die **DrilldownLevel** -Funktion gibt eine Menge untergeordneter Elemente in einer hierarchischen Reihenfolge zurück, basierend auf den Membern, die in der angegebenen Menge enthalten sind. Die Reihenfolge der ursprünglichen Elemente in der angegebenen Menge wird beibehalten, wobei jedoch alle in das Resultset der Funktion aufgenommenen untergeordneten Elemente direkt unter ihrem übergeordneten Element aufgenommen werden.  
  
 Wenn eine Datenstruktur mit einer Hierarchie mit mehreren Ebenen vorliegt, können Sie explizit eine Ebene auswählen, auf die der Drilldown erfolgen soll. Es gibt zwei Möglichkeiten, die Ebene festzulegen. Diese schließen sich gegenseitig aus. Der erste Ansatz besteht darin, das **Level_Expression** -Argument mithilfe eines MDX-Ausdrucks festzulegen, der die Ebene zurückgibt. ein alternativer Ansatz besteht darin, das **Index** Argument mithilfe eines numerischen Ausdrucks anzugeben, der die Ebene nach Zahl angibt.  
  
 Wenn ein Ebenenausdruck angegeben wird, erstellt die Funktion eine Menge in einer hierarchischen Reihenfolge, indem die untergeordneten Elemente nur für diejenigen Elemente abgerufen werden, die sich auf der angegebenen Ebene befinden. Wenn ein Ebenenausdruck festgelegt ist und sich auf dieser Ebene kein Element befindet, wird der Ebenenausdruck ignoriert.  
  
 Wenn ein Indexwert angegeben wird, erstellt die Funktion basierend auf einem nullbasierten Index eine Menge in einer hierarchischen Reihenfolge, indem die untergeordneten Elemente nur für die Elemente auf der nächstunteren Ebene der Dimension abgerufen werden, auf die in der Menge verwiesen wird.  
  
 Wenn weder ein Ebenenausdruck noch ein Indexwert angegeben wird, erstellt die Funktion eine Menge in einer hierarchischen Reihenfolge, indem die untergeordneten Elemente von nur den Elementen abgerufen werden, die sich auf der untersten Ebene der ersten Dimension befinden, auf die in der angegebenen Menge verwiesen wird.  
  
 Durch Abfragen der XMLA-Eigenschaft "mdpropmdxdrillfunctions" können Sie den Grad der Unterstützung überprüfen, den der Server für die Bohr Funktionen bereitstellt. Weitere Informationen finden Sie [unter Unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
## <a name="examples"></a>Beispiele  
 Sie können die folgenden Beispiele im MDX-Abfragefenster in SSMS ausprobieren. Verwenden Sie dafür den Adventure Works-Cube.  
  
 **Beispiel 1: veranschaulicht minimale Syntax**  
  
 Im ersten Beispiel wird die minimale Syntax für **DrilldownLevel**veranschaulicht. Das einzige erforderliche Argument ist ein Mengenausdruck. Beachten Sie Folgendes: Wenn Sie diese Abfrage ausführen, erhalten Sie die übergeordnete [alle Kategorien] und Mitglieder der nächsten Ebene nach unten: [Zubehör], [Bikes] usw. Obwohl dieses Beispiel einfach ist, wird der grundlegende Zweck der **DrilldownLevel** -Funktion veranschaulicht, die einen Drilldown zur nächsten Ebene unten durchführt.  
  
```  
SELECT DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]}}) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 Beispiel 2: alternative Syntax mithilfe einer expliziten Index Ebene  
  
 Dieses Beispiel zeigt die alternative Syntax. Hier wird die Indexebene über einen numerischen Ausdruck festgelegt. In diesem Fall ist die Indexebene 0. Für einen nullbasierten Index ist das die unterste Ebene.  
  
```  
SELECT  
DRILLDOWNLEVEL({[Product].[Product Categories]} * {[Sales Territory].[Sales Territory]},,0) ON COLUMNS  
FROM [Adventure Works]  
```  
  
 Beachten Sie, dass das Resultset mit der vorherigen Abfrage identisch ist. Allgemein gilt, ein Festlegen der Indexebene ist unnötig, es sei denn, der Drilldown soll auf einer bestimmten Ebene beginnen. Führen Sie die vorherige Abfrage erneut aus, und legen Sie einen Indexwert von 1 und dann von 2 fest. Ist der Indexwert auf 1 festgelegt, beginnt der Drilldown auf der zweiten Ebene der Hierarchie. Ist der Indexwert auf 2 festgelegt, beginnt der Drilldown auf der dritten Ebene, der höchsten Ebene in diesem Beispiel. Je höher der numerische Ausdruck, desto höher die Indexebene.  
  
 **Beispiel 3: veranschaulicht einen Ebenenausdruck**  
  
 Im folgenden Beispiel wird die Verwendung eines Ebenenausdrucks veranschaulicht. Wenn eine Menge vorliegt, die eine hierarchische Struktur darstellt, können Sie mit einem Ebenenausdruck eine Ebene in der Hierarchie auswählen, auf der der Drilldown beginnen soll.  
  
 In diesem Beispiel beginnt die Drilldown-Ebene bei [City], als zweites Argument der **DrilldownLevel** -Funktion. Wenn Sie diese Abfrage ausführen, beginnt der Drilldown auf der Ebene [City] für die Staaten Washington und Oregon. Gemäß der **DrilldownLevel** -Funktion enthält das Resultset auch Elemente auf der nächsten Ebene ([Postal Codes]).  
  
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
  
 **Beispiel 4: einschließen berechneter Elemente**  
  
 Das letzte Beispiel zeigt ein berechnetes Element, das am Ende des Resultsets angezeigt wird, wenn Sie das **include_calculated_members** -Flag hinzufügen. Beachten Sie, dass das Flag als vierter Parameter festgelegt ist.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
