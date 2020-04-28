---
title: AVG (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aa8817e35a589def4631bd455637d05fc62d3a0f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017010"
---
# <a name="avg-mdx"></a>Avg (MDX)


  Wertet eine Menge aus und gibt den Durchschnitt der nicht leeren Werte der Zellen in der Menge zurück, gemittelt über die Measures in der Menge oder über ein angegebenes Measure.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Avg( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Satz leerer Tupel oder eine leere Menge angegeben wird, gibt die **AVG** -Funktion einen leeren Wert zurück.  
  
 Die **AVG** -Funktion berechnet den Durchschnitt der nicht leeren Werte der Zellen in der angegebenen Menge, indem zuerst die Summe der Werte in den Zellen in der angegebenen Menge berechnet und dann die berechnete Summe durch die Anzahl der nicht leeren Zellen in der angegebenen Menge dividiert wird.  
  
> [!NOTE]  
>  In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden Nullen ignoriert, wenn der Durchschnittswert in einer Menge von Zahlen berechnet wird.  
  
 Wenn ein bestimmter numerischer Ausdruck (in der Regel ein Measure) nicht angegeben wird, durchläuft die **AVG** -Funktion jedes Measure im aktuellen Abfrage Kontext. Wenn ein bestimmtes Measure bereitgestellt wird, wertet die **AVG** -Funktion zuerst das Measure über den Satz aus, und anschließend berechnet die Funktion den Mittelwert basierend auf dem angegebenen Measure.  
  
> [!NOTE]  
>  Wenn Sie die **CurrentMember** -Funktion in einer berechneten Member-Anweisung verwenden, müssen Sie einen numerischen Ausdruck angeben, da kein Standardmeasure für die aktuelle Koordinate in einem solchen Abfrage Kontext vorhanden ist.  
  
 Um das einschließen leerer Zellen zu erzwingen, muss die Anwendung die [CoalesceEmpty](../mdx/coalesceempty-mdx.md) -Funktion verwenden, oder es muss eine gültige *numeric_expression* angegeben werden, die den Wert 0 (null) für leere Werte bereitstellt. Weitere Informationen zu leeren Zellen finden Sie in der OLE DB-Dokumentation.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Durchschnittswert für ein Measure über eine bestimmte Menge zurückgegeben. Beachten Sie, dass das angegebene Measure dem Standardmeasure für die Elemente der angegebenen Menge oder eines bestimmten Measures entsprechen kann.  
  
 `WITH SET [NW Region] AS`  
  
 `{[Geography].[State-Province].[Washington]`  
  
 `, [Geography].[State-Province].[Oregon]`  
  
 `, [Geography].[State-Province].[Idaho]}`  
  
 `MEMBER [Geography].[Geography].[NW Region Avg] AS`  
  
 `AVG ([NW Region]`  
  
 `--Uncomment the line below to get an average by Reseller Gross Profit Margin`  
  
 `--otherwise the average will be by whatever the default measure is in the cube,`  
  
 `--or whatever measure is specified in the query`  
  
 `--, [Measures].[Reseller Gross Profit Margin]`  
  
 `)`  
  
 `SELECT [Date].[Calendar Year].[Calendar Year].Members ON 0`  
  
 `FROM [Adventure Works]`  
  
 `WHERE ([Geography].[Geography].[NW Region Avg])`  
  
 Im folgenden Beispiel wird der tägliche Durchschnitt des `Measures.[Gross Profit Margin]` Measures zurückgegeben, der über die Tage jedes Monats im 2003-Geschäftsjahr aus dem **Adventure Works** -Cube berechnet wird. Die **AVG** -Funktion berechnet den Durchschnitt aus der Anzahl von Tagen, die in den einzelnen Monaten `[Ship Date].[Fiscal Time]` der Hierarchie enthalten sind. Die erste Berechnungsversion zeigt das Standardverhalten für den Durchschnitt durch Ausschließen von Tagen, an denen keine Verkäufe vom Durchschnitt erfasst wurden. Die zweite Version zeigt, wie Tage ohne Verkäufe in den Durchschnitt eingeschlossen werden.  
  
 `WITH MEMBER Measures.[Avg Gross Profit Margin] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `Measures.[Gross Profit Margin]`  
  
 `), format_String='percent'`  
  
 `MEMBER Measures.[Avg Gross Profit Margin Including Empty Days] AS`  
  
 `Avg(`  
  
 `Descendants(`  
  
 `[Ship Date].[Fiscal].CurrentMember,`  
  
 `[Ship Date].[Fiscal].[Date]`  
  
 `),`  
  
 `CoalesceEmpty(Measures.[Gross Profit Margin],0)`  
  
 `), Format_String='percent'`  
  
 `SELECT`  
  
 `{Measures.[Avg Gross Profit Margin],Measures.[Avg Gross Profit Margin Including Empty Days]} ON COLUMNS,`  
  
 `[Ship Date].[Fiscal].[Fiscal Year].Members ON ROWS`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Product].&[344])`  
  
 Im folgenden Beispiel wird der tägliche Durchschnitt des `Measures.[Gross Profit Margin]` Measures, berechnet über die Tage jedes Semesters im Geschäftsjahr 2003, aus dem **Adventure Works** -Cube zurückgegeben.  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS  
   Avg(  
      Descendants(  
         [Ship Date].[Fiscal].CurrentMember,   
            [Ship Date].[Fiscal].[Date]  
      ),   
      Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
      [Ship Date].[Fiscal].[Fiscal Year].[FY 2003].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
