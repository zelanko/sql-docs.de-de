---
title: Cuberaum | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: c3a012b4-9ca0-4fb8-9c26-5ecc0e2e2b2b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 029492a13a3b332ba05ff7f0b84ea06a4d2a0fd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725585"
---
# <a name="cube-space"></a>Cuberaum
  Der Cuberaum ist das Produkt aus den Elementen der Attributhierarchien eines Cubes und den Measures des Cubes. Daher wird der Cuberaum durch das Kombinationsprodukt aller Attributhierarchieelemente im Cube und den Measures des Cubes bestimmt und definiert die maximale Größe des Cubes. Beachten Sie, dass dieser Raum alle potenziellen Kombinationen von Attributhierarchieelementen umfasst, einschließlich Kombinationen, die in der wirklichen Welt unmöglich sind, z. B. Kombinationen aus der Stadt Paris und den Ländern England, Spanien, Japan oder Indien.  
  
## <a name="autoexists-and-cube-space"></a>Autoexists und Cuberaum  
 *Autoexists* schränkt den Cuberaum auf solche Zellen ein, die tatsächlich vorhanden sind. Elemente einer Attributhierarchie in einer Dimension sind möglicherweise nicht gemeinsam mit Elementen einer anderen Attributhierarchie in der gleichen Dimension vorhanden.  
  
 Bei einem Cube z. B., der eine City-Attributhierarchie, eine Country-Attributhierarchie und eine Internet Sales Amount-Measure aufweist, schließt der Cuberaum nur solche Elemente ein, die gemeinsam vorhanden sind. Wenn beispielsweise die City-Attributhierarchie die Städte New York, London, Paris, Tokyo und Melbourne und die Country-Attributhierarchie die Länder United States, United Kingdom, France, Japan, and Australia umfasst, schließt der Cuberaum nicht den Raum (die Zelle) am Schnittpunkt von Paris und United States ein.  
  
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
  
 Die vorherige Abfrage gibt nur Zellen für Elemente der Attributhierarchien in der Abfrage zurück, die gemeinsam vorhanden sind. Die vorherige Abfrage kann auch geschrieben werden mithilfe der neuen *-Variante der der [ \* (Crossjoin) (MDX)](/sql/mdx/crossjoin-mdx) Funktion.  
  
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
  
 Alle drei vorherigen Abfragen veranschaulichen die Auswirkung des „auto-exist“-Verhaltens in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="user-defined-hierarchies-and-cube-space"></a>Benutzerdefinierte Hierarchien und Cuberaum  
 In den vorherigen Beispielen in diesem Thema wurden Positionen im Cuberaum mithilfe von Attributhierarchien definiert. Es ist jedoch auch möglich, Positionen um Cuberaum mithilfe von benutzerdefinierten Hierarchien zu definieren, die basierend auf Attributhierarchien in einer Dimension definiert wurden. Eine benutzerdefinierte Hierarchie ist eine Hierarchie von Attributhierarchien, die es dem Benutzer ermöglicht, Cubedaten zu durchsuchen.  
  
 Beispielsweise ließe sich die `CROSSJOIN`-Abfrage im vorherigen Abschnitt auch wie folgt formulieren:  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[Customer Geography].[State-Province].Members  
   )   
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 In der vorherigen Abfrage wurde die benutzerdefinierte Customer Geography-Hierarchie innerhalb der Customer-Dimension zum Definieren der Position im Cuberaum verwendet, die zuvor über eine Attributhierarchie definiert worden war. Die gleiche Position im Cuberaum kann sowohl mithilfe von Attributhierarchien als auch mithilfe von benutzerdefinierten Hierarchien definiert werden.  
  
##  <a name="AttribRelationships"></a> Attributbeziehungen und Cuberaum  
 Das Definieren von Attributbeziehungen zwischen verknüpften Attributen verbessert die Abfrageleistung (durch vereinfachte Erstellung von entsprechenden Aggregationen) und wirkt sich auf das Element einer verknüpften Attributhierarchie aus, das zusammen mit einem Attributhierarchie-Element auftritt. Wenn Sie beispielsweise ein Tupel definieren, das ein Element der City-Attributhierarchie einschließt, und das Tupel nicht explizit die Country-Attributelemente definiert, wäre zu erwarten, dass das Element der Country-Attributhierarchie das verknüpfte Element der Country-Attributhierarchie darstellt. Dies ist jedoch nicht der Fall, wenn eine Attributbeziehung zwischen der City-Attributhierarchie und der Country-Attributhierarchie definiert ist.  
  
 Im folgenden Beispiel wird das Element einer verknüpften Attributhierarchie zurückgegeben, die nicht explizit in der Abfrage eingeschlossen ist.  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Country.CurrentMember.Name  
SELECT Measures.x ON 0,  
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Beachten Sie, dass die `WITH` -Schlüsselwort wird verwendet, mit der [CurrentMember (MDX)](/sql/mdx/current-mdx) und [Name (MDX)](/sql/mdx/members-string-mdx) Funktionen, um ein berechnetes Element für die Verwendung in der Abfrage zu erstellen. Weitere Informationen finden Sie unter [Die grundlegende MDX-Abfrage&#40;MDX&#41;](mdx-query-the-basic-query.md).  
  
 In der vorherigen Abfrage wurde der Name des Elements der Country-Attributhierarchie zurückgegeben, das mit jedem Element der State-Attributhierarchie verknüpft ist. Das erwartete Country-Element wird angezeigt (weil eine Attributbeziehung zwischen City- und Country-Attributen definiert ist). Ohne Attributbeziehung zwischen Attributhierarchien der gleichen Dimension wäre das (Alle)-Element zurückgegeben worden, wie die folgende Abfrage veranschaulicht.  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Education.Currentmember.Name  
SELECT Measures.x  ON 0,   
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
 In der vorherigen Abfrage wird das (Alle)-Element ("All Customers") zurückgegeben, weil keine Beziehung zwischen Education und City besteht. Daher ist das (Alle)-Element der Education-Attributhierarchie das Standardelement der Education-Attributhierarchie, das in jedem Tupel verwendet wird, in dem die City-Attributhierarchie vorkommt und in dem kein Education-Element explizit bereitgestellt wird.  
  
## <a name="calculation-context"></a>Berechnungskontext  
  
## <a name="see-also"></a>Siehe auch  
 [Schlüsselkonzepte in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)   
 [Tupel](tuples.md)   
 [Autoexists](autoexists.md)   
 [Verwenden von Elementen, Tupeln und Mengen &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Sichtbare Gesamtwerte und nicht sichtbare Gesamtwerte](visual-totals-and-non-visual-totals.md)   
 [MDX-Sprachreferenz &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)   
 [Mehrdimensionale Ausdrücke &#40;MDX&#41; – Referenz](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
