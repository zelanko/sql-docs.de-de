---
title: Erstellen benannter Mengen im Bereich einer Abfrage (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a611d3d20d269bb9c3fa3a1f764181b1660713b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074071"
---
# <a name="creating-query-scoped-named-sets-mdx"></a>Erstellen benannter Mengen im Bereich einer Abfrage (MDX)
  Wenn eine benannte Menge nur für eine einzelne MDX-Abfrage (Multidimensional Expressions) benötigt wird, können Sie die benannte Menge mit dem WITH-Schlüsselwort definieren. Eine benannte Menge, die mit dem WITH-Schlüsselwort erstellt wird, ist nach der Ausführung der Abfrage nicht länger vorhanden.  
  
 Wie in diesem Thema erläutert wird, ist die Syntax des WITH-Schlüsselworts sehr flexibel und ermöglicht sogar die Verwendung von Funktionen, um die benannte Menge zu definieren.  
  
> [!NOTE]  
>  Weitere Informationen zu benannten Mengen finden Sie unter [Erstellen von benannten Mengen in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).  
  
## <a name="with-keyword-syntax"></a>WITH-Schlüsselwort (Syntax)  
 Verwenden Sie die folgende Syntax, um einer SELECT-Anweisung von MDX das WITH-Schlüsselwort hinzuzufügen:  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 In der Syntax des WITH-Schlüsselworts enthält der `Set_Identifier` -Parameter den Alias für die benannte Menge. Der `Set_Expression` -Parameter enthält den Mengenausdruck, auf den der Alias der benannten Menge verweist.  
  
## <a name="with-keyword-example"></a>Beispiel für das WITH-Schlüsselwort  
 Mit der folgenden MDX-Abfrage werden die umgesetzten Stückzahlen (Unit Sales) der verschiedenen Chardonnay- und Chablis-Weine in `FoodMart 2000` (der Beispieldatenbank für Microsoft SQL Server 2000 Analysis Services) untersucht. Diese Abfrage ist zwar relativ einfach bezüglich des Resultsets, für Wartungszwecke ist sie jedoch zu lang und schwer zu handhaben.  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 Sie können die Wartung der obigen MDX-Abfrage vereinfachen, indem Sie mit dem WITH-Schlüsselwort eine benannte Menge für die Abfrage erstellen. Der folgende Code zeigt, wie mit dem WITH-Schlüsselwort eine benannte Menge, `[ChardonnayChablis]`, erstellt wird und wie durch diese Menge die SELECT-Anweisung verkürzt und ihre Wartung vereinfacht wird.  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a>Verwenden von Funktionen zusammen mit dem WITH-Schlüsselwort  
 Sie können zwar jedes Element einer benannten Menge explizit definieren, dies kann jedoch zu einer sehr langen Anweisung führen. Um die Erstellung und Wartung einer benannten Menge zu vereinfachen, können Sie die Elemente mithilfe von MDX-Funktionen definieren.  
  
 Beispielsweise verwendet die folgende MDX-Abfrage die Funktionen [Filter](/sql/mdx/filter-mdx), [CurrentMember](/sql/mdx/current-mdx)und [Name](/sql/mdx/members-string-mdx) sowie die VBA-Funktion InStr, um die benannte Menge `[ChardonnayChablis]` zu erstellen. Diese Version der benannten Menge `[ChardonnayChablis]` ist identisch mit der explizit definierten Version weiter oben in diesem Thema.  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SELECT-Anweisung &#40;MDX-&#41;](/sql/mdx/mdx-data-manipulation-select)   
 [Erstellen benannter Mengen im Bereich einer Sitzung &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  
