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
manager: kfile
ms.openlocfilehash: 7d6b2e91504c2c9ba796d2c0a55ba19fb3f6493e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181694"
---
# <a name="avg-mdx"></a>Avg (MDX)


  Wertet eine Menge aus und gibt den Durchschnitt der nicht leeren Werte der Zellen in der Menge zurück, gemittelt über die Measures in der Menge oder über ein angegebenes Measure.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Avg( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger Multidimensional Expressions (MDX)-Ausdruck, der eine Menge zurückgibt  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie ein Satz von leeren Tupeln oder eine leere Menge angegeben wird, die **Avg** Funktion einen leeren Wert zurück.  
  
 Die **Avg** Funktion berechnet den Durchschnitt der nicht leeren Werte der Zellen in der angegebenen Menge, indem Sie zuerst die Summe der Werte in Zellen in der angegebenen Menge berechnet und durch Teilen der Summe durch die Anzahl der nicht leeren Zellen in Der angegebene Satz.  
  
> [!NOTE]  
>  In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] werden Nullen ignoriert, wenn der Durchschnittswert in einer Menge von Zahlen berechnet wird.  
  
 Wenn kein bestimmter numerischer Ausdruck (im Allgemeinen ein Measure) nicht angegeben wird, die **Avg** Funktion MITTELWERT jedes Measures im aktuellen Abfragekontext. Wenn ein bestimmtes Measure bereitgestellt wird, die **Avg** -Funktion wertet zuerst das Measure über die Menge, und klicken Sie dann die Funktion berechnet den Durchschnitt basierend auf das angegebene Measure.  
  
> [!NOTE]  
>  Bei Verwendung der **CurrentMember** Funktion in einer Anweisung eines berechneten Elements, müssen Sie einen numerischen Ausdruck angeben, da ist Sie für die aktuelle Koordinate in solch einem Abfragekontext kein Standardmeasure vorhanden.  
  
 Um die Einbeziehung leerer Zellen zu erzwingen, muss die Anwendung mithilfe der [CoalesceEmpty](../mdx/coalesceempty-mdx.md) Funktion, oder geben Sie einen gültigen *Numeric_Expression* , der den Wert 0 (null) für leere Werte bereitstellt. Weitere Informationen zu leeren Zellen finden Sie in der OLE DB-Dokumentation.  
  
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
  
 Das folgende Beispiel gibt den täglichen Durchschnitt von den `Measures.[Gross Profit Margin]` Measures, berechnet über die Tage jedes Monats im Geschäftsjahr 2003, aus der **Adventure Works** Cube. Die **Avg** Funktion berechnet den Mittelwert aus der Menge der Tage, die in jedem Monat des befinden die `[Ship Date].[Fiscal Time]` Hierarchie. Die erste Berechnungsversion zeigt das Standardverhalten für den Durchschnitt durch Ausschließen von Tagen, an denen keine Verkäufe vom Durchschnitt erfasst wurden. Die zweite Version zeigt, wie Tage ohne Verkäufe in den Durchschnitt eingeschlossen werden.  
  
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
  
 Das folgende Beispiel gibt den täglichen Durchschnitt von den `Measures.[Gross Profit Margin]` Measures, berechnet über die Tage jedes Semesters im Geschäftsjahr 2003, aus der **Adventure Works** Cube.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
