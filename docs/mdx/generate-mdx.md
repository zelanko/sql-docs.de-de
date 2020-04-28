---
title: Generate (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c7a6008129d6b0a4c59412428c31f6e5de625f1f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68005906"
---
# <a name="generate-mdx"></a>Generate (MDX)


  Wendet eine Menge auf jedes Element einer anderen Menge an und verknüpft dann die entstehenden Mengen durch den Vereinigungsoperator. Alternativ gibt die Funktion eine verkettete Zeichenfolge zurück, die durch Auswerten eines Zeichenfolgenausdrucks über einer Menge erstellt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set expression syntax  
Generate( Set_Expression1 ,  Set_Expression2 [ , ALL ]  )  
  
String expression syntax  
Generate( Set_Expression1 ,  String_Expression [ ,Delimiter ]  )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *String_Expression*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich in der Regel um den Namen des aktuellen Elements (CurrentMember.Name) jedes Tupels in der angegebenen Menge handelt.  
  
 *Trennzeichen*  
 Ein gültiges Trennzeichen, ausgedrückt als Zeichenfolgenausdruck.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine zweite Menge angegeben wird, gibt die **Generate** -Funktion eine Menge zurück, die durch Anwenden der Tupel in der zweiten Menge auf jedes Tupel in der ersten Menge generiert wird. Anschließend wird die resultierende Menge nach Union zusammengeführt. Wenn **all** angegeben wird, behält die Funktion Duplikate in der resultierenden Menge bei.  
  
 Wenn ein Zeichen folgen Ausdruck angegeben wird, gibt die **Generate** -Funktion eine Zeichenfolge zurück, die durch Auswerten des angegebenen Zeichen folgen Ausdrucks für jedes Tupel in der ersten Menge generiert wird. Anschließend werden die Ergebnisse verkettet. Optional kann die Zeichenfolge begrenzt werden, sodass die einzelnen Ergebnisse in der verketteten Ergebniszeichenfolge voneinander getrennt sind.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="set"></a>Set  
 Im folgenden Beispiel gibt die Abfrage eine Menge zurück, die Measure Internet Sales Amount vier Mal enthält, da in der Menge [Date].[Calendar Year].[Calendar Year].ELEMENTE vier Elemente zu finden sind:  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]}, ALL)  
ON 0  
FROM [Adventure Works]  
```  
  
 Lässt man ALL weg, gibt die Abfrage Internet Sales Amount nur ein Mal zurück:  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]})  
ON 0  
FROM [Adventure Works]  
```  
  
 Die häufigste praktische Verwendung von **Generate** besteht darin, einen komplexen Mengen Ausdruck, z. b. TopCount, über eine Menge von Membern auszuwerten. Die folgende Beispielabfrage zeigt die obersten 10 Produkte für jedes Kalenderjahr in Zeilen an:  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS  
, TOPCOUNT(  
[Date].[Calendar Year].CURRENTMEMBER  
*  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount]))  
ON 1  
FROM [Adventure Works]  
```  
  
 Beachten Sie, dass für jedes Jahr jeweils ein anderer Top 10 angezeigt wird, und dass die Verwendung von **Generate** die einzige Möglichkeit ist, um dieses Ergebnis zu erhalten. Ein einfacher Crossjoin der Kalenderjahre und der Menge der obersten 10 Produkte würde mit jährlicher Wiederholung die 10 obersten Produkte der ewigen Bestenliste anzeigen, wie das folgende Beispiel zeigt:  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS  
*   
TOPCOUNT(  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount])  
ON 1  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 Das folgende Beispiel zeigt die Verwendung von **Generate** zum Zurückgeben einer Zeichenfolge:  
  
```  
WITH   
MEMBER MEASURES.GENERATESTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME)  
MEMBER MEASURES.GENERATEDELIMITEDSTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME, " AND ")  
SELECT   
{MEASURES.GENERATESTRINGDEMO, MEASURES.GENERATEDELIMITEDSTRINGDEMO}  
ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Diese Form der Funktion **generieren** kann beim Debuggen von Berechnungen nützlich sein, da Sie eine Zeichenfolge mit den Namen aller Member in einer Menge zurückgeben können. Dies ist möglicherweise einfacher zu lesen als die strikte MDX-Darstellung einer Menge, die die [Set&#40;MDX-&#41;](../mdx/settostr-mdx.md) Funktion zurückgibt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
