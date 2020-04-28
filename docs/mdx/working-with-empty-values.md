---
title: Arbeiten mit leeren Werten | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ae8d6262f6502add09376b76a767a3076c830cb8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125846"
---
# <a name="working-with-empty-values"></a>Arbeiten mit leeren Werten


  Ein leerer Wert kennzeichnet, dass ein bestimmtes Element, ein bestimmtes Tupel oder eine bestimmte Zelle leer ist. Ein leerer Zellenwert kennzeichnet entweder, dass die Daten für die angegebene Zelle in der zugrunde liegenden Faktentabelle nicht gefunden wurden, oder, dass das Tupel für die angegebene Zelle einer Kombination aus Elementen entspricht, die für den Cube nicht anwendbar ist.  
  
> [!NOTE]  
>  Ein leerer Wert ist zwar nicht mit dem Wert 0 identisch, wird aber meistens wie der Wert 0 behandelt.  
  
 Die folgende Abfrage veranschaulicht das Verhalten von leeren Werten und von 0-Werten:  
  
```  
WITH  
//A calculated Product Category that always returns 0  
MEMBER [Product].[Category].[All Products].ReturnZero AS 0  
//Will return true for any null value  
MEMBER MEASURES.ISEMPTYDemo AS ISEMPTY([Measures].[Internet Tax Amount])  
//Will true for any null or zero value  
//To be clear: the expression 0=null always returns true in MDX  
MEMBER MEASURES.IsZero AS [Measures].[Internet Tax Amount]=0  
SELECT  
{[Measures].[Internet Tax Amount],MEASURES.ISEMPTYDemo,MEASURES.IsZero}  
ON COLUMNS,  
[Product].[Category].[Category].ALLMEMBERS  
ON ROWS  
FROM [Adventure Works]  
WHERE([Date].[Calendar].[Calendar Year].&[2001])  
```  
  
 Die folgenden Informationen gelten für leere Werte:  
  
-   Die [IsEmpty](../mdx/isempty-mdx.md) -Funktion gibt nur dann **true** zurück, wenn die Zelle, die durch das in der-Funktion angegebene Tupel identifiziert wird, leer ist. Andernfalls gibt die Funktion **false**zurück.  
  
    > [!NOTE]  
    >  Die **IsEmpty** -Funktion kann nicht bestimmen, ob ein Element Ausdruck einen NULL-Wert zurückgibt. Verwenden Sie den [is](../mdx/is-mdx.md)-Operator, um zu bestimmen, ob ein NULL-Element von einem Ausdruck zurückgegeben wird.  
  
-   Ist der leere Zellwert ein Operand für einen der numerischen Operatoren (+, -, *, /), wird der leere Zellwert als 0 behandelt, wenn der andere Operand ein nicht leerer Wert ist. Sind beide Operanden leer, gibt der numerische Operator den leeren Zellwert zurück.  
  
-   Ist der leere Zellwert ein Operand für den Operator für Zeichenfolgenverkettungen (+), wird der leere Zellwert als leere Zeichenfolge behandelt, wenn der andere Operand ein nicht leerer Wert ist. Sind beide Operanden leer, gibt der Operator für Zeichenfolgenverkettungen den leeren Zellwert zurück.  
  
-   Wenn der leere Zellwert ein Operand für einen der Vergleichsoperatoren (=. <>, >=, \<=, >, <), wird der leere Zellwert als 0 (null) oder eine leere Zeichenfolge behandelt, je nachdem, ob der Datentyp des anderen Operanden numerisch bzw. Zeichenfolge ist. Sind beide Operanden leer, werden beide als 0 behandelt.  
  
-   Beim Sortieren numerischer Werte nimmt der leere Zellwert dieselbe Stelle ein wie die Zahl Null. Bei der Sortierung zwischen dem leeren Zellwert und null wird der leere Zellwert vor null eingeordnet.  
  
-   Beim Sortieren von Zeichenfolgenwerten nimmt der leere Zellwert dieselbe Stelle ein wie die leere Zeichenfolge. Bei der Sortierung zwischen dem leeren Zellwert und der leeren Zeichenfolge wird der leere Zellwert vor der leeren Zeichenfolge eingeordnet.  
  
## <a name="dealing-with-empty-values-in-mdx-statements-and-cubes"></a>Umgehen mit leeren Werten in MDX-Anweisungen und Cubes  
 In MDX-Anweisungen (Multidimensional Expressions) können Sie nach leeren Werten suchen und dann bestimmte Berechnungen für Zellen ausführen, die gültige (also nicht leere) Daten enthalten. Das Entfernen von leeren Werten aus Berechnungen kann wichtig sein, da bestimmte Berechnungen (z. B. eine Durchschnittsberechnung) verfälscht werden können, wenn leere Zellwerte eingeschlossen werden.  
  
 Leere Werte, die in den Daten der zugrundeliegenden Faktentabelle gespeichert sind, werden bei der Verarbeitung des Cube standardmäßig in 0 konvertiert. Sie können die Option **NULL-Verarbeitung** für ein Measure verwenden, um zu steuern, ob NULL-Fakten in 0 konvertiert werden, in einen leeren Wert konvertiert werden oder sogar während der Verarbeitung einen Fehler auslöst. Wenn Sie nicht möchten, dass die Abfrageergebnisse leere Zellenwerte enthalten, erstellen Sie Abfragen, berechnete Elemente oder MDX-Skriptanweisungen, die leere Werte entweder ausschließen oder durch einen anderen Wert ersetzen.  
  
 Um leere Zeilen oder Spalten aus einer Abfrage zu entfernen, können Sie vor der Achsmengendefinition die NON EMPTY-Anweisung verwenden. Die folgende Beispielabfrage gibt nur die Produktkategorie „Bikes“ zurück, da dies die einzige Kategorie ist, die im Kalenderjahr 2001 verkauft wurde.  
  
 `SELECT`  
  
 `{[Measures].[Internet Tax Amount]}`  
  
 `ON COLUMNS,`  
  
 `//Comment out the following line to display all the empty rows for other Categories`  
  
 `NON EMPTY`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Date].[Calendar].[Calendar Year].&[2001])`  
  
 Um leere Tupel aus einer Menge zu entfernen, können Sie grundsätzlich die NonEmpty-Funktion verwenden. Die folgende Abfrage zeigt zwei berechnete Measures. Eines zählt die Produktkategorien, während das andere die Anzahl der Produktkategorien anzeigt, die Werte für Measure [Internet Tax Amount] und das Kalenderjahr 2001 enthalten:  
  
 `WITH`  
  
 `MEMBER MEASURES.CategoryCount AS`  
  
 `COUNT([Product].[Category].[Category].MEMBERS)`  
  
 `MEMBER MEASURES.NonEmptyCategoryCountFor2001 AS`  
  
 `COUNT(`  
  
 `NONEMPTY(`  
  
 `[Product].[Category].[Category].MEMBERS`  
  
 `,([Date].[Calendar].[Calendar Year].&[2001], [Measures].[Internet Tax Amount])`  
  
 `))`  
  
 `SELECT`  
  
 `{MEASURES.CategoryCount,MEASURES.NonEmptyCategoryCountFor2001 }`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 Weitere Informationen finden Sie unter [nicht leere &#40;MDX-&#41;](../mdx/nonempty-mdx.md).  
  
## <a name="empty-values-and-comparison-operators"></a>Leere Werte und Vergleichsoperatoren  
 Sind leere Werte in den Daten vorhanden, ist es möglich, dass logische Operatoren und Vergleichsoperatoren nicht nur TRUE oder FALSE zurückgeben, sondern ein drittes Ergebnis: EMPTY. Diese Notwendigkeit einer dreiwertigen Logik ist die Ursache für zahlreiche Anwendungsfehler. In den folgenden Tabellen wird dargestellt, welche Auswirkungen die Einführung von Vergleichen zwischen leeren Werten haben kann.  
  
 Die folgende Tabelle zeigt die Ergebnisse des Anwendens eines AND-Operators auf zwei boolesche Operanden.  
  
|AND|TRUE|EMPTY|FALSE|  
|---------|----------|-----------|-----------|  
|**TRUE**|TRUE|FALSE|FALSE|  
|**Leer**|FALSE|EMPTY|FALSE|  
|**FALSE**|FALSE|FALSE|FALSE|  
  
 Diese Tabelle zeigt die Ergebnisse der Anwendung eines OR-Operators auf zwei boolesche Operanden.  
  
|oder|TRUE|FALSE|  
|--------|----------|-----------|  
|**TRUE**|TRUE|TRUE|  
|**Leer**|TRUE|TRUE|  
|**FALSE**|TRUE|FALSE|  
  
 Diese Tabelle zeigt, wie der Not-Operator das Ergebnis eines booleschen Operators negiert oder umgekehrt.  
  
|Boolescher Ausdruck, auf den der NOT-Operator angewendet wird|Auswertungsergebnis|  
|-------------------------------------------------------------|------------------|  
|TRUE|FALSE|  
|EMPTY|EMPTY|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Ausdrücke &#40;MDX-&#41;](../mdx/expressions-mdx.md)  
  
  
