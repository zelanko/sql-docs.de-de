---
title: Autoist vorhanden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 56283497-624c-45b5-8a0d-036b0e331d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd35958a364456c12d58392afe3754f6adcf97b8
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546592"
---
# <a name="autoexists"></a>Autoexists
  Das *Autoexists* -Konzept beschränkt den Cuberaum auf Zellen, die tatsächlich im Cube enthalten sind, anstatt alle Zellen einzubeziehen, die durch die Erstellung aller potenziellen Kombinationen von Attributhierarchieelementen in der gleichen Hierarchie vorhanden sein könnten. Dies liegt daran, dass Elemente einer Attributhierarchie nicht gemeinsam mit Elementen einer anderen Attributhierarchie in der gleichen Dimension vorhanden sein können. Wenn zwei oder mehr Attributhierarchien der gleichen Dimension in einer SELECT-Anweisung verwendet werden, wertet Analysis Services die Ausdrücke der Attribute aus, damit die Elemente dieser Attribute ordnungsgemäß beschränkt werden, so dass sie die Kriterien aller anderen Attribute erfüllen.  
  
 Angenommen, Sie arbeiten mit Attributen der Geography-Dimension. Wenn ein Ausdruck alle Elemente des City-Attributs zurückgibt und ein anderer Ausdruck die Elemente des Country-Attributs auf alle Länder Europas beschränkt, sind als City-Elemente nur Orte in europäischen Ländern möglich. Dies ist auf das Autoexists-Merkmal von Analysis Services zurückzuführen. Autoexists gilt nur für Attribute der gleichen Dimension, denn es versucht zu verhindern, dass die in einem Attributausdruck ausgeschlossenen Dimensionsdatensätze von den anderen Attributausdrücken eingeschlossen werden. Autoexists kann auch als resultierende Schnittmenge der unterschiedlichen Attributausdrücke in den Dimensionszeilen bezeichnet werden.  
  
## <a name="cell-existence"></a>Vorhandensein von Zellen  
 Die folgenden Zellen sind immer vorhanden:  
  
-   Das (All)-Element jeder Hierarchie bei einer Schnittmenge mit Elementen anderer Hierarchien in der gleichen Dimension.  
  
-   Berechnete Elemente bei einer Schnittmenge mit nicht berechneten gleichgeordneten Elementen oder mit den übergeordneten Elementen oder Nachfolgern der nicht berechneten gleichgeordneten Elemente  
  
## <a name="providing-non-existing-cells"></a>Bereitstellen von nicht vorhandenen Zellen  
 Eine nicht vorhandene Zelle ist eine Zelle, die vom System als Antwort auf eine Abfrage oder eine Berechnung bereitgestellt wird, in der eine im Cube nicht vorhandene Zelle angefordert wird. Wenn beispielsweise ein Cube eine City-Attributhierarchie und eine Country-Attributhierarchie, die zur Geography-Dimension gehören, und eine Internet Sales Amount-Measure aufweist, schließt der Cuberaum nur solche Elemente ein, die gemeinsam vorhanden sind. Wenn beispielsweise die City-Attributhierarchie die Städte New York, London, Paris, Tokyo und Melbourne und die Country-Attributhierarchie die Länder United States, United Kingdom, France, Japan, and Australia umfasst, schließt der Cuberaum nicht den Raum (die Zelle) am Schnittpunkt von Paris und United States ein.  
  
 Beim Abfragen von nicht vorhandenen Zellen wird NULL zurückgegeben, d. h., nicht vorhandene Zellen können keine Berechnungen enthalten, und Sie können auch keine Berechnungen definieren, die in sie schreiben. Die folgende Anweisung beinhaltet beispielsweise Zellen, die nicht vorhanden sind:  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  Diese Abfrage verwendet die [Members (Menge) (MDX)](/sql/mdx/members-set-mdx) -Funktion, um eine Menge von Elementen der Gender-Attributhierarchie auf der Spaltenachse zurückzugeben und diese Menge mit der angegebenen Menge von Elementen der Customer-Attributhierarchie auf der Zeilenachse zu kreuzen.  
  
 Beim Ausführen der vorherigen Abfrage zeigt die Zelle am Schnittpunkt zwischen Aaron A. Allen und Female eine Null an. Entsprechend zeigt die Zelle am Schnittpunkt zwischen Abigail Clark und Male ebenfalls eine Null an. Diese Zellen sind nicht vorhanden und können daher keine Werte enthalten, sie können jedoch im Ergebnis einer Abfrage angezeigt werden.  
  
 Wenn Sie die [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) -Funktion verwenden, um das Kreuzprodukt von Attributhierarchie-Elementen und Attributhierarchien in der gleichen Dimension zurückzugeben, beschränkt Auto-exist das zurückgegebene Ergebnis auf die Menge der Tupel, die tatsächlich vorhanden sind, und gibt nicht das vollständige kartesische Produkt zurück. Führen Sie z. B. die folgenden Abfrage aus, und überprüfen Sie die Ergebnisse.  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[State-Province].Members  
  ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  Beachten Sie, dass 0 hier für die Spaltenachse steht (als Kurzform für axis(0)).  
  
 Die vorherige Abfrage gibt nur Zellen für Elemente der Attributhierarchien in der Abfrage zurück, die gemeinsam vorhanden sind. Die vorherige Abfrage kann auch mithilfe der neuen *-Variante der [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) -Funktion geschrieben werden.  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 Die vorherige Abfrage kann auch wie folgt formuliert werden:  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 Die zurückgegebenen Zellenwerte sind identisch, die Metadaten im Resultset sind jedoch verschieden. Beispielsweise wurde in der vorherigen Abfrage die Country-Hierarchie auf die Slicerachse verschoben (in die WHERE-Klausel), sodass sie nicht explizit im Resultset angezeigt wird.  
  
 Jede dieser drei vorherigen Abfragen veranschaulicht die Auswirkung des Auto-es-Verhaltens in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
## <a name="deep-and-shallow-autoexists"></a>Tiefe und flache Autoexists  
 Autoexists können tief oder flach auf Ausdrücke angewendet werden. `Deep Autoexists` bedeutet, dass alle Ausdrücke ausgewertet werden, um nach Anwendung der Slicerausdrücke, untergeordneten SELECT-Ausdrücke usw. einen möglichst tiefen Raum abzudecken. `Shallow Autoexists` bedeutet, dass externe Ausdrücke vor dem aktuellen Ausdruck ausgewertet werden und dass diese Ergebnisse an den aktuellen Ausdruck übergeben werden. Die Standardeinstellung sind tiefe Autoexists.  
  
 Das folgende Szenario und die Beispiele veranschaulichen die verschiedenen Typen von Autoexists. In den folgenden Beispielen werden zwei Gruppen erstellt: eine als berechneteter Ausdruck und die andere als konstanter Ausdruck.  
  
 `//Obtain the Top 10 best reseller selling products by Name`  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 Das Resultset lautet:  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Mountain-200**|**14.356.699,36 €**|**19.012,71 €**|**0,13%**|  
|**Road-250**|**9.377.457,68 €**|**4.032,47 €**|**0,04 %**|  
|**Mountain-100**|**8.568.958,27 €**|**139.393,27 €**|**1,63%**|  
|**Road-650**|**7.442.141,81 €**|**39.698,30 €**|**0,53 %**|  
|**Touring-1000**|**6.723.794,29 €**|**166.144,17 €**|**2,47%**|  
|**Road-550-W**|**3.668.383,88 €**|**1.901,97 €**|**0,05%**|  
|**Road-350-W**|**3.665.932,31 €**|**20.946,50 €**|**0,57%**|  
|**HL Mountain Frame**|**3.365.069,27 €**|**174,11 €**|**0,01%**|  
|**Road-150**|**2.363.805,16 €**|**$0,00**|**0,00%**|  
|**Touring-3000**|**2.046.508,26 €**|**79.582,15 €**|**3,89%**|  
  
 Die erhaltene Produktgruppe ist offenbar die gleiche wie Preferred10Products. Die Gruppe Preferred10Products wird deshalb überprüft:  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 Laut den folgenden Ergebnissen sind beide Gruppen (Top10SellingProducts, Preferred10Products) identisch.  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Mountain-200**|**14.356.699,36 €**|**19.012,71 €**|**0,13%**|  
|**Road-250**|**9.377.457,68 €**|**4.032,47 €**|**0,04 %**|  
|**Mountain-100**|**8.568.958,27 €**|**139.393,27 €**|**1,63%**|  
|**Road-650**|**7.442.141,81 €**|**39.698,30 €**|**0,53 %**|  
|**Touring-1000**|**6.723.794,29 €**|**166.144,17 €**|**2,47%**|  
|**Road-550-W**|**3.668.383,88 €**|**1.901,97 €**|**0,05%**|  
|**Road-350-W**|**3.665.932,31 €**|**20.946,50 €**|**0,57%**|  
|**HL Mountain Frame**|**3.365.069,27 €**|**174,11 €**|**0,01%**|  
|**Road-150**|**2.363.805,16 €**|**$0,00**|**0,00%**|  
|**Touring-3000**|**2.046.508,26 €**|**79.582,15 €**|**3,89%**|  
  
 Im folgenden Beispiel wird der Begriff "tiefes Autoexists" veranschaulicht. Im Beispiel filtern wir Top10SellingProducts mit dem [Product].[Product Line]-Attribut nach den in der [Mountain]-Gruppe enthaltenen Produkten. Beachten Sie, dass beide Attribute (Slicer und Achse) zur gleichen Dimension [Produkt] gehören.  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `// Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 Dadurch ergibt sich folgendes Resultset:  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Mountain-200**|**14.356.699,36 €**|**19.012,71 €**|**0,13%**|  
|**Mountain-100**|**8.568.958,27 €**|**139.393,27 €**|**1,63%**|  
|**HL Mountain Frame**|**3.365.069,27 €**|**174,11 €**|**0,01%**|  
|**Mountain-300**|**1.907.249,38 €**|**876,95 €**|**0,05%**|  
|**Mountain-500**|**1.067.327,31 €**|**17.266,09 €**|**1,62%**|  
|**Mountain-400-W**|**592.450,05 €**|**303,49 €**|**0,05%**|  
|**LL Mountain Frame**|**521.864,42 €**|**252,41 €**|**0,05%**|  
|**ML Mountain Frame-W**|**482.953,16 €**|**$206,95**|**0,04 %**|  
|**ML Mountain Frame**|**343.785,29 €**|**161,82 €**|**0,05%**|  
|**Women's Mountain Shorts**|**260.304,09 €**|**6.675,56 €**|**2,56%**|  
  
 Das obige Resultset enthält sieben Neueinträge für die Liste mit den Top10SellingProducts und Mountain-200, Mountain-100 sowie HL Mountain Frame wurden an den Anfang der Liste verschoben. Im vorherigen Resultset befanden sich diese drei Werte an verschiedenen Stellen.  
  
 Dies wird als tiefes Autoexists bezeichnet, da die Gruppe Top10SellingProducts so ausgewertet wird, dass die Slicingbedingungen der Abfrage erfüllt werden. Tiefes Autoexists bedeutet, dass alle Ausdrücke so ausgewertet werden, dass nach Anwendung der Slicerausdrücke, der untergeordneten SELECT-Ausdrücke in der Achse usw. der tiefstmögliche Bereich erfüllt ist.  
  
 Eventuell soll es jedoch auch möglich sein, die Analyse der Top10SellingProducts als Entsprechung zu Preferred10Products auszuführen wie im folgenden Beispiel:  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 Dadurch ergibt sich folgendes Resultset:  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Mountain-200**|**14.356.699,36 €**|**19.012,71 €**|**0,13%**|  
|**Mountain-100**|**8.568.958,27 €**|**139.393,27 €**|**1,63%**|  
|**HL Mountain Frame**|**3.365.069,27 €**|**174,11 €**|**0,01%**|  
  
 Nach den oben aufgeführten Ergebnissen führt das Slicing zu einem Ergebnis, das nur die Produkte von Preferred10Products enthält, die Teil der Gruppe [Mountain] in [Product].[Product Line] sind. Dies entspricht den Erwartungen, da Preferred10Products ein konstanter Ausdruck ist.  
  
 Dieses Resultset wird auch als "flaches Autoexists" bezeichnet. Das liegt daran, dass der Ausdruck vor der Slicingklausel ausgewertet wird. Im vorherigen Beispiel war der Ausdruck ein konstanter Ausdruck, damit das Konzept anschaulicher eingeführt werden konnte.  
  
 Das Autoexists-Verhalten kann mit der `Autoexists`-Eigenschaft der Verbindungszeichenfolge auf Sitzungsebene geändert werden. Im folgenden Beispiel wird zunächst eine neue Sitzung geöffnet und dann die *Autoexists=3* -Eigenschaft zur Verbindungszeichenfolge hinzugefügt. Sie müssen eine neue Verbindung öffnen, um das Beispiel ausführen zu können. Sobald die Verbindung mit der Autoexist-Einstellung hergestellt ist, bleibt diese Einstellung bis zum Ende der Verbindung wirksam.  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `//Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 Das folgende Resultset zeigt jetzt das flache Verhalten von Autoexists.  
  
|||||  
|-|-|-|-|  
||**Reseller Sales Amount**|**Discount Amount**|**PCT Discount**|  
|**Mountain-200**|**14.356.699,36 €**|**19.012,71 €**|**0,13%**|  
|**Mountain-100**|**8.568.958,27 €**|**139.393,27 €**|**1,63%**|  
|**HL Mountain Frame**|**3.365.069,27 €**|**174,11 €**|**0,01%**|  
  
 Das autoes-Verhalten kann mithilfe des Parameters autoist = [1 | 2 | 3] in der Verbindungs Zeichenfolge geändert werden. Weitere Informationen finden Sie [unter Unterstützte XMLA-Eigenschaften &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) und <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> zur Parameter Verwendung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wichtige Konzepte in MDX-&#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Cube-Bereich](cube-space.md)   
 [Tupel](tuples.md)   
 [Arbeiten mit Membern, Tupeln und Mengen &#40;MDX-&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Visuelle Gesamtsummen und nicht visuelle Gesamtwerte](visual-totals-and-non-visual-totals.md)   
 [MDX-Sprachreferenz &#40;MDX-&#41;](/sql/mdx/mdx-language-reference-mdx)   
 [Multidimensional Expressions &#40;MDX&#41; – Referenz](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
