---
title: Order (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43a75f4a42193c231c1acc710512b05537675991
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63277844"
---
# <a name="order-mdx"></a>Order (MDX)


  Ordnet die Elemente einer angegebenen Menge an, wobei die Hierarchie optional beibehalten wird oder nicht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric expression syntax  
Order(Set_Expression, Numeric_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
String expression syntax  
Order(Set_Expression, String_Expression   
[ , { ASC | DESC | BASC | BDESC } ] )  
  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *String_Expression*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich in der Regel um einen gültigen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, der eine als Zeichenfolge ausgedrückte Zahl zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Reihenfolge** Funktion kann entweder hierarchisch sein (angegeben mit der **ASC** oder **DESC** Flag) oder hierarchisch (angegeben mit der **BASC**  oder **BDESC** kennzeichnen; die **B** steht für "Break Hierarchy"). Wenn **ASC** oder **DESC** angegeben wird, die **Reihenfolge** -Funktion zuerst ordnet die Elemente entsprechend ihrer Position in der Hierarchie und sortiert dann jede Ebene. Wenn **BASC** oder **BDESC** angegeben wird, die **Reihenfolge** Funktion ordnet die Elemente in der Menge ungeachtet der Hierarchie. Kein Flag angegeben ist, **ASC** ist die Standardeinstellung.  
  
 Wenn die **Reihenfolge** Funktion mit einem Satz verwendet wird, in denen zwei oder mehr Hierarchien kreuzverknüpft sind, sind und die **DESC** Flag verwendet wird, werden nur die Elemente der letzten Hierarchie im Satz sortiert. Dies ist eine Änderung im Vergleich zu Analysis Services 2000, wo alle Hierarchien im Satz befohlen wurden.  
  
## <a name="examples"></a>Beispiele  
 Im folgende Beispiel wird von der **Adventure Works** cube die Anzahl der Bestellungen des Wiederverkäufers für alle Kalenderquartale der Kalenderhierarchie auf der Date-Dimension. Die **Reihenfolge** Funktion ordnet den Satz für die ROWS-Achse. Die **Reihenfolge** -Funktion sortiert die Menge von `[Reseller Order Count]` hierarchische absteigend, laut der `[Calendar]` Hierarchie.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Beachten Sie, dass wie in diesem Beispiel ist bei der **DESC** Flag geändert wird, um **BDESC**, die Hierarchie unterbrochen wird, und die Liste der Kalenderquartale wird ohne Beachtung der Hierarchie zurückgegeben:  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Im folgenden Beispiel wird das Reseller Sales-Measure für die fünf bestverkauften Produktunterkategorien unabhängig von der Hierarchie basierend auf Reseller Gross Profit zurückgegeben. Die **Teilmenge** Funktion verwendet, um nur die ersten 5 Tupeln in der Gruppe zurückzugeben, nach dem Sortieren des Ergebnisses mithilfe der **Reihenfolge** Funktion.  
  
 `SELECT Subset`  
  
 `(Order`  
  
 `([Product].[Product Categories].[SubCategory].members`  
  
 `,[Measures].[Reseller Gross Profit]`  
  
 `,BDESC`  
  
 `)`  
  
 `,0`  
  
 `,5`  
  
 `) ON 0`  
  
 `FROM [Adventure Works]`  
  
 Im folgenden Beispiel wird die **Rang** Funktion, um die Elemente der City-Hierarchie Rangfolge basierend auf dem Reseller Sales Amount-Measure, und Sie anschließend in der Rangreihenfolge. Mithilfe der **Reihenfolge** -Funktion zum vorsortieren der Menge der Elemente der City-Hierarchie, die Sortierung nur einmal durchgeführt und anschließend ein linearer Scan vor der Anzeige der Sortierreihenfolge.  
  
```  
WITH   
SET OrderedCities AS Order  
   ([Geography].[City].[City].members  
   , [Measures].[Reseller Sales Amount], BDESC  
   )  
MEMBER [Measures].[City Rank] AS Rank  
   ([Geography].[City].CurrentMember, OrderedCities)  
SELECT {[Measures].[City Rank],[Measures].[Reseller Sales Amount]}  ON 0   
,Order  
   ([Geography].[City].[City].MEMBERS  
   ,[City Rank], ASC)  
    ON 1  
FROM [Adventure Works]  
```  
  
 Das folgende Beispiel gibt die Anzahl der Produkte in der Gruppe, die eindeutig ist, mit der **Reihenfolge** Funktion, um die Reihenfolge der nicht leeren Tupel vor Verwendung der **Filter** Funktion. Die **CurrentOrdinal** Funktion zum Vergleichen und Ausschließen von Gleichrangigkeit verwendet wird.  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , (OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          )  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
 Um zu verstehen wie das **DESC** flag mit Sätzen von Tupeln funktioniert, betrachten Sie zuerst die Ergebnisse der folgenden Abfrage:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Auf der Zeilenachse sehen Sie sich, dass die Vertriebsgebietsgruppen in absteigender Reihenfolge nach Steuerbetrag wie folgt angeordnet wurden: Nordamerika, Europa, Pazifik, Na Jetzt finden Sie unter Was geschieht, wenn wir Crossjoin aus dem Satz der Vertriebsgebietsgruppen mit den Produktunterkategorien Kreuzverknüpfen und Anwenden der **Reihenfolge** -Funktion auf die gleiche Weise wie folgt:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Während der Satz von Produktunterkategorien in absteigender, hierarchischen Reihenfolge angeordnet wurde die Vertriebsgebietsgruppen jetzt nicht sortiert sind, und werden in der Reihenfolge, die sie in der Hierarchie angezeigt werden: Europa, NA, Nordamerika und Pazifik. Das liegt daran, dass nur die letzte Hierarchie im Satz von Tupeln, Produktunterkategorien, sortiert ist. Um das Verhalten von Analysis Services 2000 zu reproduzieren, verwenden Sie eine Reihe von geschachtelten **generieren** Funktionen, um jeden Satz zu sortieren, bevor er kreuzverknüpft wird, z. B. ist:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
GENERATE(  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
,  
ORDER(  
[Sales Territory].[Sales Territory].CURRENTMEMBER  
*  
{[Product].[Product Categories].[subCategory].Members}  
,[Measures].[Tax Amount], DESC))  
ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
