---
title: Unterstützte Datentypen (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92993f7b-7243-4aec-906d-0b0379798242
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2502b65b1b13f8ed819c138fdfe429390a905a56
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939758"
---
# <a name="data-types-supported-ssas-tabular"></a>Unterstützte Datentypen (SSAS – tabellarisch)
  In diesem Artikel werden die Datentypen erläutert, die in tabellarischen Modellen verwendet werden können, und die implizite Konvertierung von Datentypen bei der Berechnung oder Verwendung von Daten in einer Data Analysis Expressions (DAX)-Formel beschrieben.  
  
 Dieser Artikel enthält folgende Abschnitte:  
  
-   [In tabellarischen Modellen verwendete Datentypen](#bkmk_data_types)  
  
-   [Implizite und explizite Datentyp Konvertierungen in DAX-Formeln](#bkmk_implicit)  
  
-   [Behandeln von Leerzeichen, leeren Zeichenfolgen und Nullwerten](#bkmk_hand_blanks)  
  
##  <a name="data-types-used-in-tabular-models"></a><a name="bkmk_data_types"></a>In tabellarischen Modellen verwendete Datentypen  
 Die folgenden Datentypen werden unterstützt. Wenn Sie Daten importieren oder einen Wert in einer Formel verwenden, werden die Daten in einen der folgenden Datentypen konvertiert, auch wenn die ursprüngliche Datenquelle einen anderen Datentyp enthält. Werte, die sich aus Formeln ergeben, verwenden ebenfalls diese Datentypen.  
  
 Im Allgemeinen werden diese Datentypen implementiert, um genaue Berechnungen in berechneten Spalten zu ermöglichen. Die gleichen Einschränkungen gelten aus Konsistenzgründen auch für den Rest der Daten in Modellen.  
  
 Formate für Zahlen, Währungen, Datumsangaben und Uhrzeiten sollten dem Format des Gebietsschemas auf dem Client folgen, der für die Arbeit mit den Modelldaten verwendet wird. Sie können die Formatierungsoptionen im Modell verwenden, um die Darstellung des Werts zu bestimmen.  
  
||||  
|-|-|-|  
|Datentyp im Modell|Datentyp in DAX|Beschreibung|  
|Ganze Zahl|Ein ganzzahliger 64-Bit-Wert (acht Byte) <sup>1, 2</sup>|Zahlen ohne Dezimalstellen. Ganze Zahlen können positiv oder negativ sein, aber müssen ganze Zahlen zwischen -9 223 372 036 854 775 808 (-2^63) und 9 223 372 036 854 775 807 (2^63-1) sein.|  
|Decimal Number|Eine reelle 64-Bit-Zahl (acht Byte) <sup>1, 2</sup>|Reelle Zahlen sind Zahlen, die Dezimalstellen aufweisen können. Reelle Zahlen decken viele Werte ab:<br /><br /> Negative Werte von -1,79E +308 bis -2,23E -308<br /><br /> Zero<br /><br /> Positive Werte von 2,23E -308 bis -1,79E +308<br /><br /> Die Anzahl der relevanten Stellen wird jedoch auf siebzehn Dezimalstellen beschränkt.|  
|Boolean|Boolean|Entweder ein True oder ein False-Wert.|  
|Text|String|Eine Unicodezeichen-Datenzeichenfolge. Dies können Zeichenfolgen, Zahlen oder Datumsangaben im Textformat sein.|  
|Date|Datum/Uhrzeit|Datumsangaben und Uhrzeiten in einer akzeptierten Form für die Darstellung von Datum und Uhrzeit.<br /><br /> Gültig sind alle Datumsangaben nach dem 1. März 1900.|  
|Währung|Währung|Der Währungsdatentyp lässt Werte zwischen -922 337 203 685 477,5808 und 922 337 203 685 477,5807 mit vier Dezimalstellen unveränderlicher Genauigkeit zu.|  
|–|Leer|Ein leerer Datentyp in DAX, der SQL-NULLEN darstellt und ersetzt. Sie können mit der BLANK-Funktion ein Leerzeichen erstellen und mit der logischen ISBLANK-Funktion nach Leerzeichen suchen.|  
  
 <sup>1</sup> DAX-Formeln unterstützen keine Datentypen, die kleiner sind als die in der Tabelle aufgeführten.  
  
 <sup>2</sup> Wenn Sie versuchen, Daten mit sehr großen numerischen Werten zu importieren, schlägt der Import möglicherweise mit folgendem Fehler fehl:  
  
 Fehler in der Arbeitsspeicher Datenbank: die \<column name> Spalte "" der \<table name> Tabelle "" enthält den Wert "1.7976931348623157 e + 308", der nicht unterstützt wird. Der Vorgang wurde abgebrochen.  
  
 Dieser Fehler tritt auf, da der Modell-Designer diesen Wert zur Darstellung von Nullen verwendet. Die Werte in der folgenden Liste sind zum vorherigen erwähnten Nullwert synonym:  
  
||  
|-|  
|Value|  
|9223372036854775807|  
|-9223372036854775808|  
|1.7976931348623158e+308|  
|2.2250738585072014e-308|  
  
 Sie sollten den Wert aus den Daten entfernen und erneut importieren.  
  
> [!NOTE]  
>  Sie können keine Elemente aus einer **varchar(max)** -Spalte importieren, die eine Zeichenfolgenlänge von mehr als 131.072 Zeichen enthält.  
  
### <a name="table-data-type"></a>Table-Datentyp  
 Außerdem verwendet DAX einen *table* -Datentyp. Dieser Datentyp wird von DAX in vielen Funktionen verwendet, z. B. in Aggregationen und Zeitintelligenzberechnungen. Einige Funktionen erfordern einen Verweis auf eine Tabelle, während andere Funktionen eine Tabelle zurückgeben, die dann als Eingabe für andere Funktionen verwendet werden kann. In einigen Funktionen, die eine Tabelle als Eingabe erfordern, können Sie einen Ausdruck angeben, der eine Tabelle ergibt. Bei einigen Funktionen ist ein Verweis auf eine Basistabelle erforderlich. Informationen zu den Anforderungen bestimmter Funktionen finden Sie unter [DAX-Funktionsreferenz](/dax/dax-function-reference).  
  
##  <a name="implicit-and-explicit-data-type-conversion-in-dax-formulas"></a><a name="bkmk_implicit"></a>Implizite und explizite Datentyp Konvertierungen in DAX-Formeln  
 Jede DAX-Funktion hat bestimmte Anforderungen im Hinblick auf die Datentypen, die als Eingaben und Ausgaben verwendet werden. Einige Funktionen erfordern z. B. ganze Zahlen für einige Argumente und Daten für andere, während für andere Funktionen Text oder Tabellen erforderlich sind.  
  
 Wenn die Daten in der Spalte, die Sie als Argument angeben, nicht mit dem erforderlichen Datentyp kompatibel sind, gibt DAX in vielen Fällen einen Fehler zurück. Wo immer möglich, versucht DAX jedoch, die Daten implizit in den erforderlichen Datentyp zu konvertieren. Beispiel:  
  
-   Sie können eine Zahl, z. b. "123", als Zeichenfolge eingeben. DAX analysiert die Zeichenfolge und versucht, diese als Zahlendatentyp anzugeben.  
  
-   Sie können TRUE + 1 addieren und erhalten als Ergebnis 2, da TRUE implizit in die Zahl 1 konvertiert wird und die Operation 1+1 ausgeführt wird.  
  
-   Wenn Sie Werte in zwei Spalten addieren und ein Wert als Text ("12") und der andere als Zahl (12) dargestellt wird, konvertiert DAX die Zeichenfolge implizit in eine Zahl und führt dann die Addition für ein numerisches Ergebnis durch. Vom folgenden Ausdruck wird 44 zurückgegeben: = "22" + 22  
  
-   Wenn Sie zwei Zahlen verketten möchten, stellt das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Add-In sie als Zeichenfolgen dar und verkettet sie dann. Vom folgenden Ausdruck wird "1234" zurückgegeben: = 12 & 34  
  
 In der folgenden Tabelle werden die impliziten Datentypkonvertierungen zusammengefasst, die in Formeln ausgeführt werden. Im Allgemeinen verhält sich der Designer für semantische Modelle wie Microsoft Excel und führt implizite Konvertierungen aus, wann immer dies möglich und bei dem betreffenden Vorgang erforderlich ist.  
  
### <a name="table-of-implicit-data-conversions"></a>Tabelle mit impliziten Datenkonvertierungen  
 Der ausgeführte Konvertierungstyp wird durch den Operator bestimmt, der die Werte umwandelt, bevor die entsprechende Operation durchgeführt wird. In diesen Tabellen sind die Operatoren aufgeführt. Außerdem wird die Konvertierung angegeben, die für die einzelnen Datentypen in der Spalte ausgeführt wird, wenn dieser dem Datentyp in der überschneidenden Zeile zugeordnet wird.  
  
> [!NOTE]  
>  Textdatentypen sind in diesen Tabellen nicht enthalten. Wenn eine Zahl wie in einem Textformat dargestellt wird, versucht der Modell-Designer in einigen Fällen, den Zahlentyp zu bestimmen und ihn als Zahl anzugeben.  
  
#### <a name="addition-"></a>Addition (+)  
  
||||||  
|-|-|-|-|-|  
|Operator (+)|INTEGER|WÄHRUNG|REAL|Datum/Uhrzeit|  
|INTEGER|INTEGER|WÄHRUNG|REAL|Datum/Uhrzeit|  
|WÄHRUNG|WÄHRUNG|WÄHRUNG|real|Datum/Uhrzeit|  
|real|real|real|real|Datum/Uhrzeit|  
|Datum/Uhrzeit|Datum/Uhrzeit|Datum/Uhrzeit|Datum/Uhrzeit|Datum/Uhrzeit|  
  
 Wenn beispielsweise eine reelle Zahl bei einer Addition in Verbindung mit Währungsdaten verwendet wird, werden beide Werte in REAL konvertiert, und das Ergebnis wird als REAL zurückgegeben.  
  
#### <a name="subtraction--"></a>Subtraction (-)  
 In der folgenden Tabelle ist die Zeilenüberschrift der Minuend (linke Seite), und die Spaltenüberschrift ist der Subtrahend (rechte Seite).  
  
||||||  
|-|-|-|-|-|  
|Operator (-)|INTEGER|WÄHRUNG|real|Datum/Uhrzeit|  
|INTEGER|INTEGER|WÄHRUNG|real|real|  
|WÄHRUNG|WÄHRUNG|WÄHRUNG|real|real|  
|real|real|real|real|real|  
|Datum/Uhrzeit|Datum/Uhrzeit|Datum/Uhrzeit|Datum/Uhrzeit|Datum/Uhrzeit|  
  
 Wenn beispielsweise ein Datum bei einer Subtraktion mit einem beliebigen anderen Datentyp verwendet wird, werden beide Werte in Datumsangaben konvertiert, und der Rückgabewert ist ebenfalls ein Datum.  
  
> [!NOTE]  
>  Tabellarische Modelle unterstützen auch den unären Operator "-" (negativ). Dieser Operator ändert den Datentyp des Operanden jedoch nicht.  
  
#### <a name="multiplication-"></a>Multiplikation (*)  
  
||||||  
|-|-|-|-|-|  
|Operator (*)|INTEGER|WÄHRUNG|real|Datum/Uhrzeit|  
|INTEGER|INTEGER|WÄHRUNG|real|INTEGER|  
|WÄHRUNG|WÄHRUNG|real|WÄHRUNG|WÄHRUNG|  
|real|real|WÄHRUNG|real|real|  
  
 Wenn beispielsweise eine Ganzzahl bei einer Multiplikation mit einer reellen Zahl kombiniert wird, werden beide Zahlen in reelle Zahlen konvertiert, und der Rückgabewert ist ebenfalls REAL.  
  
#### <a name="division-"></a>Division (/)  
 In der folgenden Tabelle ist die Zeilenüberschrift der Zähler, und die Spaltenüberschrift ist der Nenner.  
  
||||||  
|-|-|-|-|-|  
|Operator (/)<br /><br /> (Zeile/Spalte)|INTEGER|WÄHRUNG|real|Datum/Uhrzeit|  
|INTEGER|REAL|WÄHRUNG|real|real|  
|WÄHRUNG|WÄHRUNG|real|WÄHRUNG|real|  
|real|real|real|real|real|  
|Datum/Uhrzeit|real|real|real|REAL|  
  
 Wenn beispielsweise eine Ganzzahl bei einer Division mit einem Währungswert kombiniert wird, werden beide Werte in reelle Zahlen konvertiert, und das Ergebnis ist ebenfalls eine reelle Zahl.  
  
#### <a name="comparison-operators"></a>Vergleichsoperatoren  
 In Vergleichsausdrücken werden boolesche Werte als größer als Zeichenfolgenwerte betrachtet, und Zeichenfolgenwerte werden als größer als numerische Werte oder Datums-/Uhrzeitwerte betrachtet. Zahlen- und Datums-/Uhrzeitwerte werden als gleichrangig betrachtet. Für boolesche Werte oder Zeichenfolgewerte werden keine impliziten Konvertierungen ausgeführt. BLANK oder ein leerer Wert wird abhängig vom Datentyp des anderen verglichenen Werts in 0/""/false konvertiert.  
  
 Die folgenden DAX-Ausdrücke veranschaulichen dieses Verhalten:  
  
 `=IF(FALSE()>"true","Expression is true", "Expression is false")`, gibt zurück.`"Expression is true"`  
  
 `=IF("12">12,"Expression is true", "Expression is false")`, gibt zurück.`"Expression is true"`  
  
 `=IF("12"=12,"Expression is true", "Expression is false")`, gibt zurück.`"Expression is false"`  
  
 Konvertierungen werden implizit für numerische oder Datum/Uhrzeit-Typen ausgeführt, wie in der folgenden Tabelle beschrieben:  
  
||||||  
|-|-|-|-|-|  
|Vergleichsoperator|INTEGER|WÄHRUNG|real|Datum/Uhrzeit|  
|INTEGER|INTEGER|WÄHRUNG|real|REAL|  
|WÄHRUNG|WÄHRUNG|WÄHRUNG|real|REAL|  
|REAL|REAL|REAL|REAL|REAL|  
|Datum/Uhrzeit|real|REAL|REAL|Datum/Uhrzeit|  
  
##  <a name="handling-of-blanks-empty-strings-and-zero-values"></a><a name="bkmk_hand_blanks"></a>Behandlung von Leerzeichen, leeren Zeichen folgen und NULL-Werten  
 DAX behandelt Nullwerte (0), Null und leere Zeichenfolgen anders als Microsoft Excel und SQL Server. In diesem Abschnitt werden die Unterschiede beschrieben, und es wird erläutert, wie diese Datentypen behandelt werden.  
  
 Dabei ist wichtig zu beachten, dass ein leerer Wert, eine leere Zelle oder ein fehlender Wert alle durch den gleichen neuen Werttyp (BLANK) dargestellt werden. Wie Leerzeichen in Vorgängen gehandhabt werden (z. B. Hinzufügen oder Verketten), hängt von der jeweiligen Funktion ab. Sie können auch Leerzeichen mit der BLANK-Funktion generieren oder mit der ISBLANK-Funktion nach Leerzeichen suchen. Datenbank-NULLEN werden innerhalb eines Semantikmodells nicht unterstützt, und NULLEN werden implizit in Leerzeichen konvertiert, wenn in einer DAX-Formel auf eine Spalte mit einem Nullwert verwiesen wird.  
  
### <a name="defining-blanks-nulls-and-empty-strings"></a>Definieren von Leerzeichen, NULLEN und leeren Zeichenfolgen  
 In der folgenden Tabelle werden die Unterschiede zwischen DAX und Microsoft Excel in Bezug auf die Behandlung von Leerzeichen zusammengefasst.  
  
||||  
|-|-|-|  
|Ausdruck (Expression)|DAX|Excel|  
|BLANK + BLANK|BLANK|0 (Null)|  
|BLANK +5|5|5|  
|BLANK * 5|BLANK|0 (Null)|  
|5/BLANK|Unendlich|Fehler|  
|0/BLANK|NaN|Fehler (Error)|  
|BLANK/BLANK|BLANK|Fehler|  
|FALSE OR BLANK|FALSE|FALSE|  
|FALSE AND BLANK|FALSE|FALSE|  
|TRUE OR BLANK|TRUE|TRUE|  
|TRUE AND BLANK|FALSE|TRUE|  
|BLANK OR BLANK|BLANK|Fehler|  
|BLANK AND BLANK|BLANK|Fehler|  
  
 Informationen zur Behandlung von Leerzeichen durch eine bestimmte Funktion oder einen Operator finden Sie in den einzelnen Themen zu den verschiedenen DAX-Funktionen im Abschnitt [DAX-Funktionsreferenz](/dax/dax-function-reference).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellen &#40;tabellarischen SSAS-&#41;](../data-sources-ssas-tabular.md)   
 [Importieren von Daten &#40;SSAS – tabellarisch&#41;](../import-data-ssas-tabular.md)  
  
  
