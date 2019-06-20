---
title: Generieren von (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 222479dd03263f61a603e30202f2abf54307b0bc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63224883"
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
  
 *Delimiter*  
 Ein gültiges Trennzeichen, ausgedrückt als Zeichenfolgenausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie ein zweiter Satz angegeben wird, die **generieren** Funktionsergebnis ist eine Gruppe, die durch Anwenden der Tupel in der zweiten Menge auf jedes Tupel in der ersten Menge generiert *,* und dann wird die resultierende verknüpft Mengen durch vereinigungsmengenbildung. Wenn **alle** angegeben ist, wird die Funktion behält Duplikate in der sich ergebenden Menge.  
  
 Wenn ein Zeichenfolgenausdruck angegeben wird, die **generieren** Funktion gibt eine Zeichenfolge, die durch die Auswertung der im angegebenen Zeichenfolgenausdruck für jedes Tupel in der ersten Menge generiert *,* und verkettet Sie dann die Ergebnisse. Optional kann die Zeichenfolge begrenzt werden, sodass die einzelnen Ergebnisse in der verketteten Ergebniszeichenfolge voneinander getrennt sind.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="set"></a>Legen Sie  
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
  
 Die am häufigsten verwendeten praktische Verwendung von **generieren** ist um einen komplexen Mengenausdruck wie TopCount auf eine Menge von Elementen. Die folgende Beispielabfrage zeigt die obersten 10 Produkte für jedes Kalenderjahr in Zeilen an:  
  
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
  
 Beachten Sie, dass eine andere Top 10 für jedes Jahr, und dass angezeigt wird die Verwendung von **generieren** ist die einzige Möglichkeit, dieses Ergebnis zu erhalten. Ein einfacher Crossjoin der Kalenderjahre und der Menge der obersten 10 Produkte würde mit jährlicher Wiederholung die 10 obersten Produkte der ewigen Bestenliste anzeigen, wie das folgende Beispiel zeigt:  
  
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
  
### <a name="string"></a>Zeichenfolge  
 Das folgende Beispiel zeigt die Verwendung von **generieren** gibt eine Zeichenfolge zurück:  
  
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
>  Diese Form der **generieren** Funktion ist nützlich, beim Debuggen von Berechnungen, wie Sie zum Zurückgeben einer Zeichenfolge, die die Namen aller Elemente in einer Gruppe anzeigen können. Dies ist möglicherweise einfacher zu lesen als die strikte MDX-Darstellung eines Satzes, der die [SetToStr &#40;MDX&#41; ](../mdx/settostr-mdx.md) -Funktion zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
