---
title: IIf (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ca6449308f9683bccf55e58d9cec6d5d5a97a59e
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247134"
---
# <a name="iif-mdx"></a>IIf (MDX)


  Wertet verschiedene Verzweigungsausdrücke abhängig davon aus, ob eine boolesche Bedingung "True" oder "False" ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IIf(Logical_Expression, Expression1 [HINT <hints>], Expression2 [HINT <hints>])  
```  
  
## <a name="arguments"></a>Argumente  
 Die IIf-Funktion nimmt drei Argumente an: IIf ( \<condition> , \<then branch> , \<else branch> ).  
  
 *Logical_Expression*  
 Eine Bedingung, die zu **true** (1) oder **false** (0) ausgewertet wird. Es muss sich um einen gültigen logischen Multidimensional Expressions (MDX)-Ausdruck handeln.  
  
 *Expression1-Hinweis [eifrig | Strict | Verzögert]]*  
 Wird verwendet, wenn der logische Ausdruck **true**ergibt. Expression1 muss ein gültiger Multidimensional Expressions (MDX)-Ausdruck sein.  
  
 *Expression2-Hinweis [eifrig | Strict | Verzögert]]*  
 Wird verwendet, wenn der logische Ausdruck als **false**ausgewertet wird. Expression2 muss ein gültiger Multidimensional Expressions (MDX)-Ausdruck sein.  
  
## <a name="remarks"></a>Bemerkungen  
 Die vom logischen Ausdruck angegebene Bedingung wird zu **false** ausgewertet, wenn der Wert dieses Ausdrucks 0 (null) ist. Alle anderen Werte werden als **true**ausgewertet.  
  
 Wenn die Bedingung " **true**" ist, gibt die **IIf** -Funktion den ersten Ausdruck zurück. Andernfalls gibt die Funktion den zweiten Ausdruck zurück.  
  
 Die angegebene Ausdrücke können Werte oder MDX-Objekte zurückgeben. Ferner muss der Typ der angegebenen Ausdrücke nicht übereinstimmen.  
  
 Die **IIf** -Funktion wird nicht zum Erstellen eines Satzes von Membern basierend auf Suchkriterien empfohlen. Verwenden Sie stattdessen die [Filter](../mdx/filter-mdx.md) -Funktion, um jedes Element in einer angegebenen Menge anhand eines logischen Ausdrucks auszuwerten und eine Teilmenge der Member zurückzugeben.  
  
> [!NOTE]  
>  Wenn die Auswertung einer der beiden Ausdrücke NULL ergibt, ist das Resultset NULL, wenn diese Bedingung erfüllt wird.  
  
 Ein Tipp ist ein optionaler Modifizierer, der festlegt, wie und wann der Ausdruck ausgewertet wird. Er ermöglicht es Ihnen, den Standard-Abfrageplan zu überschreiben, indem Sie angeben, wie der Ausdruck ausgewertet wird.  
  
-   EAGER wertet den Ausdruck für den ursprünglichen IIF-Teilbereich aus.  
  
-   STRICT wertet den Ausdruck nur im eingeschränkten Teilbereich aus, der durch den logischen Bedingungsausdruck erstellt wird.  
  
-   LAZY wertet den Ausdruck im zellenweisen Modus aus.  
  
 Während EAGER und STRICT nur für then-else-Verzweigungen von IIF gelten, gilt LAZY für alle MDX-Ausdrücke. Nach jedem MDX-Ausdruck kann HINT LAZY folgen, sodass dieser Ausdruck im zellenweisen Modus ausgewertet wird.  
  
 EAGER und STRICT schließen sich im Tipp gegenseitig aus. Sie können in IIF(,,) für verschiedene Ausdrücke verwendet werden.  
  
 Weitere Informationen finden Sie unter [Abfrage Hinweise der IIf-Funktion in SQL Server Analysis Services 2008](http://www.ssas-info.com/analysis-services-articles/50-mdx/1103-iif-function-query-hints-in-sql-server-analysis-services-2008) und [Ausführungspläne und Plan Hinweise für die MDX IIf-Funktion und Case-Anweisung](https://go.microsoft.com/fwlink/?LinkId=269565).  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage zeigt eine einfache Verwendung von **IIf** in einem berechneten Measure, um einen von zwei unterschiedlichen Zeichen folgen Werten zurückzugeben, wenn das Measure Internet Sales Amount größer oder kleiner als $10000 ist:  
  
 `WITH MEMBER MEASURES.IIFDEMO AS`  
  
 `IIF([Measures].[Internet Sales Amount]>10000`  
  
 `, "Sales Are High", "Sales Are Low")`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.IIFDEMO} ON 0,`  
  
 `[Date].[Date].[Date].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Sehr häufig wird IIF zur Fehlerbehandlung bei „Division durch Null“ innerhalb von berechneten Measures eingesetzt wie im folgenden Beispiel:  
  
 `WITH`  
  
 `//Returns 1.#INF when the previous period contains no value`  
  
 `//but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth With Errors] AS`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `,FORMAT_STRING='PERCENT'`  
  
 `//Traps division by zero and returns null when the previous period contains`  
  
 `//no value but the current period does`  
  
 `MEMBER MEASURES.[Previous Period Growth] AS`  
  
 `IIF(([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)=0,`  
  
 `NULL,`  
  
 `([Measures].[Internet Sales Amount]-([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER))`  
  
 `/`  
  
 `([Measures].[Internet Sales Amount], [Date].[Date].CURRENTMEMBER.PREVMEMBER)`  
  
 `),FORMAT_STRING='PERCENT'`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.[Previous Period Growth With Errors], MEASURES.[Previous Period Growth]} ON 0,`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004],`  
  
 `[Date].[Calendar].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 Im folgenden finden Sie ein Beispiel für **IIf** , das einen von zwei Sätzen innerhalb der Funktion generieren zurückgibt, um einen komplexen Satz von Tupeln für Zeilen zu erstellen:  
  
 `SELECT {[Measures].[Internet Sales Amount]} ON 0,`  
  
 `//If Internet Sales Amount is zero or null`  
  
 `//returns the current year and the All Customers member`  
  
 `//else returns the current year broken down by Country`  
  
 `GENERATE(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `, IIF([Measures].[Internet Sales Amount]=0,`  
  
 `{([Date].[Calendar Year].CURRENTMEMBER, [Customer].[Country].[All Customers])}`  
  
 `, {{[Date].[Calendar Year].CURRENTMEMBER} * [Customer].[Country].[Country].MEMBERS}`  
  
 `))`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Product].[Product Categories].[Subcategory].&[26])`  
  
 Schließlich wird in diesem Beispiel gezeigt, wie PLAN-Tipps verwendet werden:  
  
 `WITH MEMBER MEASURES.X AS`  
  
 `IIF(`  
  
 `[Measures].[Internet Sales Amount]=0`  
  
 `, NULL`  
  
 `, (1/[Measures].[Internet Sales Amount]) HINT EAGER)`  
  
 `SELECT {[Measures].x} ON 0,`  
  
 `[Customer].[Customer Geography].[Country].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
