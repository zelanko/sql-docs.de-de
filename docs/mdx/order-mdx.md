---
description: Order (MDX)
title: Reihenfolge (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4db745ea01a56d68fe259ebb2fffb5aae250abd4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471742"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **Order** -Funktion kann entweder hierarchisch (entsprechend der Angabe mit **ASC** dem ASC **-oder dem** Debug-Flag) oder nicht hierarchisch (wie durch das BASC-oder bdebug-Flag angegeben) oder nicht hierarchisch (wie **durch das** **BASC** -oder **bdebug** -Flag angegeben) sein Wenn **ASC** oder **Debug** angegeben ist, ordnet die **Order** -Funktion die Member zuerst entsprechend ihrer Position in der Hierarchie an und ordnet dann jede Ebene an. Wenn **BASC** oder **bdebug** angegeben ist, ordnet die **Order** -Funktion Elemente im Satz ohne Berücksichtigung der Hierarchie an. Wenn kein Flag angegeben ist, wird **ASC** als Standardwert angegeben.  
  
 Wenn die **Order** -Funktion mit einer Menge verwendet wird, in der zwei oder mehr Hierarchien quer verknüpft sind, und **das Flag zum** Aufheben der Verwendung verwendet wird, werden nur die Elemente der letzten Hierarchie in der Gruppe sortiert. Dies ist eine Änderung im Vergleich zu Analysis Services 2000, wo alle Hierarchien im Satz befohlen wurden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Anzahl der Bestellungen des Wiederverkäufers für alle Kalender Quartale der Kalender Hierarchie in der Date-Dimension aus dem **Adventure Works** -Cube zurückgegeben. Die **Order** -Funktion ordnet den Satz für die ROWS-Achse neu an. Die **Order** -Funktion ordnet den Satz `[Reseller Order Count]` in absteigender hierarchischer Reihenfolge an, wie von der `[Calendar]` Hierarchie bestimmt.  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,DESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Beachten Sie, dass in diesem Beispiel die Hierarchie Unterbrechung und die Liste der Kalender Quartale ohne Berücksichtigung der Hierarchie zurückgegeben wird, wenn das Flag " **Entsc** " in " **BDE SC**" geändert wird:  
  
 `SELECT`  
  
 `Measures.[Reseller Order Count] ON COLUMNS,`  
  
 `Order(`  
  
 `[Date].[Calendar].[Calendar Quarter].MEMBERS`  
  
 `,Measures.[Reseller Order Count]`  
  
 `,BDESC`  
  
 `) ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Im folgenden Beispiel wird das Reseller Sales-Measure für die fünf bestverkauften Produktunterkategorien unabhängig von der Hierarchie basierend auf Reseller Gross Profit zurückgegeben. Die **Subset** -Funktion wird verwendet, um nur die ersten 5 Tupel in der Menge zurückzugeben, nachdem das Ergebnis mithilfe der **Order** -Funktion sortiert wurde.  
  
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
  
 Im folgenden Beispiel wird die **Rang** Funktion verwendet, um die Elemente der City-Hierarchie basierend auf dem Reseller Sales Amount-Measure zu ordnen und Sie dann in der Reihenfolge der Rangfolge anzeigt. Wenn Sie die **Order** -Funktion verwenden, um die Menge der Elemente der City-Hierarchie zuerst zu sortieren, erfolgt die Sortierung nur ein Mal und anschließend eine lineare Überprüfung, bevor Sie in sortierter Reihenfolge dargestellt werden.  
  
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
  
 Im folgenden Beispiel wird die Anzahl der Produkte in der Menge zurückgegeben, die eindeutig sind. dabei wird die **Order** -Funktion verwendet, um die nicht leeren Tupel vor der Verwendung der **Filter** Funktion zu sortieren. Die **CurrentOrdinal** -Funktion wird zum Vergleichen und Entfernen von Beziehungen verwendet.  
  
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
  
 Um zu verstehen, wie das Flag " **Entsc** " mit Sätzen von Tupeln funktioniert, sollten Sie zunächst die Ergebnisse der folgenden Abfrage beachten:  
  
```  
  
SELECT  
{[Measures].[Tax Amount]} ON 0,  
ORDER(  
[Sales Territory].[Sales Territory].[Group].MEMBERS  
,[Measures].[Tax Amount], DESC)  
ON 1  
FROM [Adventure Works]  
  
```  
  
 Auf der Zeilenachse sehen Sie, dass die Vertriebsgebietsgruppen in absteigender Reihenfolge des Steuerbetrags wie folgt sortiert wurden: Nordamerika, Europa, Pazifik, NA. Sehen Sie sich nun an, was geschieht, wenn wir den Satz von Sales Territory-Gruppen mit dem Satz von Produkt Unterkategorien verbinden und die **Order** -Funktion wie folgt auf die gleiche Weise anwenden:  
  
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
  
 Während der Satz von Produktunterkategorien in absteigender, hierarchischer Reihenfolge angeordnet wurde, werden die Vertriebsgebietsgruppen jetzt nicht sortiert und werden in der Reihenfolge angezeigt, in der sie auf der Hierarchie angezeigt werden: Europa, NA, Nordamerika und Pazifik. Das liegt daran, dass nur die letzte Hierarchie im Satz von Tupeln, Produktunterkategorien, sortiert ist. Um das Verhalten von Analysis Services 2000 zu reproduzieren, verwenden Sie eine Reihe von Funktionen zum **generieren** von Funktionen, um die einzelnen Sätze zu sortieren, bevor Sie quer verknüpft werden, z. b.:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
