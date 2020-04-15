---
title: Intervall-Literale | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- interval literals [ODBC]
- interval data type [ODBC], literals
ms.assetid: f9e6c3c7-4f98-483f-89d8-ebc5680f021b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1761ac0acb57b3f375a7d19e9371384c000eca5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304941"
---
# <a name="interval-literals"></a>Intervallliterale
ODBC erfordert, dass alle Treiber die Konvertierung des SQL_CHAR oder SQL_VARCHAR Datentyps in alle C-Intervalldatentypen unterstützen. Wenn die zugrunde liegende Datenquelle jedoch keine Intervalldatentypen unterstützt, muss der Treiber das richtige Format des Wertes im Feld SQL_CHAR kennen, um diese Konvertierungen zu unterstützen. In ähnlicher Weise erfordert ODBC, dass jeder ODBC C-Typ in SQL_CHAR oder SQL_VARCHAR kann, sodass ein Treiber wissen muss, welches Intervall im Zeichenfeld gespeichert sein soll. In diesem Abschnitt wird die Syntax von Intervallliteralen beschrieben, die der Treiberschreiber verwenden muss, um die SQL_CHAR Felder während der Konvertierung in oder von C-Intervalldatentypen zu überprüfen.  
  
> [!NOTE]  
>  Die vollständige BNF-Syntax für Intervallliterale wird im Abschnitt [Intervallliterale Syntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) in Anhang C: SQL Grammar angezeigt.  
  
 Um Intervallliterale als Teil einer SQL-Anweisung zu übergeben, wird eine Escapeklauselsyntax für Intervallliterale definiert. Weitere Informationen finden Sie unter [Datum, Uhrzeit und Zeitstempelliterale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Ein Intervallliteral ist der Folgenden:  
  
```  
INTERVAL[<sign>] 'value' <interval qualifier>  
```  
  
 wobei "INTERVAL" angibt, dass es sich bei dem Zeichenliteral um ein Intervall handelt. Das Zeichen kann entweder plus oder minus sein; Sie befindet sich außerhalb der Intervallzeichenfolge und ist optional.  
  
 Der Intervallqualifizierer kann entweder ein einzelnes Datumszeitfeld sein \<oder aus \<zwei Datumszeitfeldern in der Form bestehen: *führendes Feld*> to *trailing field*>.  
  
-   Wenn das Intervall aus einem einzelnen Feld besteht, kann es sich bei dem einzelnen Feld um ein Feld ohne Sekunde handelt, das von einer optionalen Führungsgenauigkeit in Klammern begleitet werden kann. Das einzelne Datumsuhrfeld kann auch ein zweites Feld sein, das von der optionalen Führungsgenauigkeit, der optionalen Sekundengenauigkeit in Klammern oder beidem begleitet werden kann. Wenn sowohl eine führende Genauigkeit als auch eine Sekundengenauigkeit für ein Sekundenfeld vorhanden sind, werden sie durch Kommas getrennt. Wenn das Sekundenfeld eine Sekundengenauigkeit aufweist, muss es auch eine führende Genauigkeit aufweisen.  
  
-   Wenn das Intervall aus führenden und nachfolgenden Feldern besteht, ist das führende Feld ein Feld, das nicht in sekundender Höhe liegt und von der Intervall-führenden Feldgenauigkeit in Klammern begleitet werden kann. Das nachfolgende Feld kann entweder ein Feld ohne Sekunde oder ein zweites Feld sein, das von einer Intervall-Sekunden-Präzision in Klammern begleitet werden kann.  
  
 Die Intervallzeichenfolge im *Wert* wird in einfache Anführungszeichen eingeschlossen. Es kann entweder ein Jahres-Monats-Literal oder ein Tageszeitliteral sein. Das Format der Zeichenfolge im *Wert* wird durch die folgenden Regeln bestimmt:  
  
-   Die Zeichenfolge enthält einen Dezimalwert für jedes \<Feld, das durch den *Intervallqualifizierer* impliziert wird>. *interval*  
  
-   Wenn die Intervallgenauigkeit die Felder JAHR und MONAT enthält, werden die Werte dieser Felder durch ein Minuszeichen getrennt.  
  
-   Wenn die Intervallgenauigkeit die Felder TAG und STUNDE enthält, werden die Werte dieser Felder durch ein Leerzeichen getrennt.  
  
-   Wenn die Intervallgenauigkeit das Feld HOUR und die Felder niedrigerer Ordnung (MINUTE und SECOND) enthält, werden die Werte dieser Felder durch einen Doppelpunkt getrennt.  
  
-   Wenn die Intervallgenauigkeit ein SECOND-Feld enthält und die Genauigkeit der ausgedrückten oder impliziten Sekunden ungleich Null ist, ist das Zeichen unmittelbar vor der ersten Ziffer des Bruchteils der Sekunde ein Punkt.  
  
-   Kein Feld darf mehr als zwei Ziffern lang sein, außer:  
  
    -   Der Wert des führenden Feldes kann so lang sein wie die implizite oder implizite Intervallführungsgenauigkeit.  
  
    -   Der Bruchteil des SECOND-Feldes kann so lang sein wie die Präzision der ausgedrückten oder impliziten Sekunden.  
  
    -   Die nachfolgenden Felder folgen den üblichen Einschränkungen des Gregorianischen Kalenders. (Siehe [Einschränkungen des Gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md).)  
  
 In der folgenden Tabelle sind Beispiele für gültige Intervallliterale aufgeführt, die in der ODBC-Escapeklausel für Intervalle enthalten sind. Die Syntax der Escape-Klausel lautet wie folgt:  
  
> [!NOTE]  
>  *"INTERVAL-Zeichenintervall-String-Intervall-Qualifizierer"*  
  
|Literale Escape-Klausel|Angegebenes Intervall|  
|---------------------------|------------------------|  
|"INTERVALL '326' JAHR(4)|Gibt ein Intervall von 326 Jahren an. Die Intervallführungsgenauigkeit beträgt 4.|  
|"INTERVALL '326' MONAT(3)|Gibt ein Intervall von 326 Monaten an. Die Intervallführungsgenauigkeit beträgt 3.|  
|"INTERVAL '3261' DAY(4)|Gibt ein Intervall von 3261 Tagen an. Die Intervallführungsgenauigkeit beträgt 4.|  
|INTERVALL '163' STUNDE(3)|Gibt ein Intervall von 163 Tagen an. Die Intervallführungsgenauigkeit beträgt 3.|  
|INTERVALL '163' MINUTE(3)|Gibt ein Intervall von 163 Minuten an. Die Intervallführungsgenauigkeit beträgt 3.|  
|INTERVALL '223.16' SEKUNDE(3,2)"|Gibt ein Intervall von 223,16 Sekunden an. Die Intervall-Führungsgenauigkeit beträgt 3, und die Sekundengenauigkeit ist 2.|  
|"INTERVALL '163-11' JAHR(3) BIS MONAT"|Gibt ein Intervall von 163 Jahren und 11 Monaten an. Die Intervallführungsgenauigkeit beträgt 3.|  
|INTERVAL '163 12' TAG(3) BIS STUNDE'|Gibt ein Intervall von 163 Tagen und 12 Stunden an. Die Intervallführungsgenauigkeit beträgt 3.|  
|INTERVAL '163 12:39' TAG(3) BIS MINUTE'|Gibt ein Intervall von 163 Tagen, 12 Stunden und 39 Minuten an. Die Intervallführungsgenauigkeit beträgt 3.|  
|INTERVAL '163 12:39:59.163' DAY(3) BIS SECOND(3)'|Gibt ein Intervall von 163 Tagen, 12 Stunden, 39 Minuten und 59,163 Sekunden an. Die Intervall-Führungsgenauigkeit beträgt 3, und die Sekundengenauigkeit ist 3.|  
|INTERVAL '163:39' STUNDE(3) BIS MINUTE'|Gibt ein Intervall von 163 Stunden und 39 Minuten an. Die Intervallführungsgenauigkeit beträgt 3.|  
|INTERVALL '163:39:59.163' STUNDE(3) BIS SEKUNDE(4)'|Gibt ein Intervall von 163 Stunden, 39 Minuten und 59,163 Sekunden an. Die Intervall-Führungsgenauigkeit beträgt 3, und die Sekundengenauigkeit beträgt 4.|  
|INTERVALL '163:59.163' MINUTE(3) BIS SECOND(5)'|Gibt ein Intervall von 163 Minuten und 59,163 Sekunden an. Die Intervall-Führungsgenauigkeit beträgt 3, und die Sekundengenauigkeit ist 5.|  
|INTERVALL -'16 23:39:56.23' TAG ZU SEKUNDE|Gibt ein Intervall von minus 16 Tagen, 23 Stunden, 39 Minuten und 56,23 Sekunden an. Die implizite Führungsgenauigkeit beträgt 2, und die implizite Sekundengenauigkeit beträgt 6.|  
  
 In der folgenden Tabelle sind Beispiele für ungültige Intervallliterale aufgeführt:  
  
|Literale Escape-Klausel|Grund, warum ungültig|  
|---------------------------|------------------------|  
|INTERVALL '163' STUNDE(2)|Die Intervallführungsgenauigkeit ist 2, aber der Wert des führenden Feldes ist 163.|  
|INTERVALL '223.16' SEKUNDE(2,2)"<br /><br /> INTERVALL '223.16' SEKUNDE(3,1)"|Im ersten Beispiel ist die Führende Genauigkeit zu klein, und im zweiten Beispiel ist die Sekundengenauigkeit zu klein.|  
|INTERVALL '223.16' SEKUNDE<br /><br /> "INTERVALL''223'-JAHR"|Da die führende Genauigkeit nicht angegeben ist, wird standardmäßig 2 angegeben, was zu klein ist, um das angegebene Literal zu enthalten.|  
|INTERVAL '22.1234567' SEKUNDE'|Die Sekundengenauigkeit ist nicht angegeben, daher ist sie standardmäßig auf 6 festgelegt. Das Literal hat sieben Ziffern hinter dem Dezimaltrennzeichen.|  
|"INTERVALL '163-13' JAHR(3) BIS MONAT"<br /><br /> INTERVAL '163 65' TAG(3) BIS STUNDE'<br /><br /> INTERVAL '163 62:39' TAG(3) BIS MINUTE'<br /><br /> INTERVAL '163 12:125:59.163' DAY(3) BIS SECOND(3)'<br /><br /> INTERVAL '163:144' STUNDE(3) BIS MINUTE'<br /><br /> INTERVALL '163:567:234.163' STUNDE(3) BIS SEKUNDE(4)'<br /><br /> INTERVALL '163:591.163' MINUTE(3) BIS SECOND(5)'|Das nachfolgende Feld folgt nicht den Regeln des Gregorianischen Kalenders.|
