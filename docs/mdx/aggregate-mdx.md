---
description: Aggregate (MDX)
title: Aggregat (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d1e3f00ffbf662422f162d493a585d3972518431
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461693"
---
# <a name="aggregate-mdx"></a>Aggregate (MDX)


  Gibt eine Zahl zurück, die durch Aggregieren über die vom Mengenausdruck zurückgegebenen Zellen berechnet wird. Wenn kein numerischer Ausdruck angegeben wird, aggregiert die Funktion jedes Measure im aktuellen Abfragekontext mit dem für jedes Measure definierten Standardaggregationsoperator. Wenn ein numerischer Ausdruck angegeben wird, wertet die Funktion zuerst den numerischen Ausdruck für jede Zelle in der angegebenen Menge aus und summiert dann die Werte.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Aggregate(Set_Expression [ ,Numeric_Expression ])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Menge von leeren Tupeln oder eine leere Menge angegeben wird, gibt die Funktion einen leeren Wert zurück.  
  
 In der folgenden Tabelle wird beschrieben, wie sich die **Aggregat** Funktion mit unterschiedlichen Aggregations Funktionen verhält.  
  
|Aggregations Operator|Ergebnis|  
|--------------------------|------------|  
|SUM|Gibt die Summe der Werte über die Menge zurück.|  
|Anzahl|Gibt die Anzahl der Werte über die Menge zurück.|  
|Max|Gibt den Maximalwert über die Menge zurück.|  
|Min|Gibt den Minimalwert über die Menge zurück.|  
|Semiadditive Aggregationsfunktionen|Gibt die Berechnung von semiadditivem Verhalten über die Menge nach dem Projizieren der Form auf die Zeitachse zurück.|  
|Distinct Count|Aggregiert über die zum Teilcube beitragenden Faktendaten, wenn die Slicerachse eine Menge enthält.<br /><br /> Gibt ein Distinct Count Measure für jedes Element der Menge zurück. Das Ergebnis hängt von der Sicherheit der aggregieren Zellen und nicht von der Sicherheit der Zellen, die für die Berechnung erforderlich sind, ab. Die Zellensicherheit für die Menge generiert einen Fehler. Die Zellensicherheit unterhalb der Granularität der angegebenen Menge wird ignoriert. Berechnungen auf der Menge generieren einen Fehler. Berechnungen unterhalb der Granularität der Menge werden ignoriert. Ein Distinct Count über eine Menge, die ein Element und mindestens ein untergeordnetes Element enthält, gibt den Distinct Count über zum untergeordneten Element beitragende Fakten zurück.|  
|Nicht aggregierbare Attribute|Gibt die Summe der Werte zurück.|  
|Gemischte Aggregationsfunktionen|Nicht unterstützt, lösen einen Fehler aus.|  
|Unäre Operatoren|Nicht berücksichtigt. Die Werte werden durch Summieren aggregiert.|  
|Berechnete Measures|Festgelegte Lösungsreihenfolge, um sicherzustellen, dass das berechnete Measure gilt.|  
|Berechnete Elemente|Die üblichen Regeln gelten, d. h., die letzte Lösungsreihenfolge hat Vorrang.|  
|Zuweisungen|Zuweisungen werden entsprechend der Aggregationsfunktion des Measures aggregieren. Ist die Aggregationsfunktion des Measures Distinct Count, werden die Zuweisungen summiert.|  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Summe des-Elements `Measures.[Order Quantity]` , aggregiert über die ersten acht Monate des Kalender Jahrs 2003, das in der `Date` Dimension enthalten ist, aus dem **Adventure Works** -Cube zurückgegeben.  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Im folgenden Beispiel wird über die ersten zwei Monate des zweiten Semesters des Kalenderjahres 2003 aggregiert.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Im folgenden Beispiel wird die Anzahl der Wiederverkäufer, deren Umsätze im vergangenen Zeitraum zurückgegangen sind, basierend auf vom Benutzer ausgewählten State-Province-Elementwerten zurückgegeben, die mit der Aggregate-Funktion ausgewertet wurden. Die **Hierarchize** -Funktion und die **DrilldownLevel** -Funktion werden verwendet, um Werte für abnehmende Umsätze für Produktkategorien in der Product-Dimension zurückzugeben.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [PeriodsToDate-&#40;MDX-&#41;](../mdx/periodstodate-mdx.md)   
 [Untergeordnete &#40;MDX-&#41;](../mdx/children-mdx.md)   
 [Hierarchize &#40;MDX-&#41;](../mdx/hierarchize-mdx.md)   
 [Anzahl &#40;fest geleg&#41; &#40;MDX-&#41;](../mdx/count-set-mdx.md)   
 [&#40;MDX-&#41;Filtern ](../mdx/filter-mdx.md)   
 [AddCalculatedMembers &#40;MDX-&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [DrilldownLevel-&#40;MDX-&#41;](../mdx/drilldownlevel-mdx.md)   
 [Eigenschaften &#40;MDX-&#41;](../mdx/properties-mdx.md)   
 [PrevMember &#40;MDX-&#41;](../mdx/prevmember-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
