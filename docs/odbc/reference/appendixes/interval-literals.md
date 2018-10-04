---
title: Intervall-Literale | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc5d09bca83724bb956d39512c51c3dc47db1bad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854008"
---
# <a name="interval-literals"></a>Intervallliterale
ODBC ist erforderlich, dass alle Treiber Konvertierung des Datentyps SQL_CHAR oder SQL_VARCHAR sein alle C-Intervall-Datentypen zu unterstützen. Wenn die Interval-Datentypen nicht von die zugrunde liegenden Datenquelle unterstützt wird, jedoch muss der Treiber das richtige Format für den Wert im Feld SQL_CHAR zu kennen, um diese Konvertierungen zu unterstützen. Entsprechend muss ODBC an, dass alle ODBC C Typ SQL_CHAR oder SQL_VARCHAR, konvertiert werden, damit ein Treiber, in welchem Format ein Intervall, in das Zeichenfeld gespeichert wissen muss haben soll. Dieser Abschnitt beschreibt die Syntax des Intervall-Literale, die der Treiber-Writer, um die Felder SQL_CHAR während der Konvertierung in oder aus C Interval-Datentypen zu überprüfen verwenden muss.  
  
> [!NOTE]  
>  Die vollständige BNF-Syntax für Literale des Intervalls wird im Abschnitt gezeigten [Intervall Literal-Syntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) in Anhang C: SQL-Grammatik.  
  
 Um Intervall-Literale als Teil einer SQL-Anweisung zu übergeben, wird eine Escape-Klausel-Syntax für die Intervall-Literale definiert. Weitere Informationen finden Sie unter [Date, Time und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Ein Intervall literal hat folgendes Format:  
  
```  
INTERVAL[<sign>] 'value' <interval qualifier>  
```  
  
 "INTERVAL" gibt an, dass das Zeichenfolgenliteral ein Intervall. Die Zeichen können es sich entweder plus oder minus; Dabei handelt es sich außerhalb der Interval-Zeichenfolge ist optional.  
  
 Der Qualifizierer Intervall kann entweder ein einzelnes Datetime-Feld oder sein besteht aus zwei Datetime-Felder, in der Form: \< *führende Feld*> TO \< *nachfolgende Feld*>.  
  
-   Wenn das Intervall eines einzelnen Felds besteht, kann das einzelne Feld ein nicht-Sekunden-Feld sein, die eine optionale führende Genauigkeit in Klammern metaelementtyp enthalten kann. Einzelne Datetime-Feld kann auch ein zweites Feld sein, das die optionale führende Genauigkeit, die optionale Sekundenbruchteil-Genauigkeit in Klammern oder beides metaelementtyp enthalten kann. Wenn sowohl führende Genauigkeit und einer Genauigkeit von Bruchteilen von Sekunden für ein Sekundenfeld vorhanden sind, werden sie durch Kommas getrennt. Wenn der Wert im Sekundenfeld eine Genauigkeit von Bruchteilen von Sekunden aufweist, muss es auch eine führende Genauigkeit verfügen.  
  
-   Wenn das Intervall von führenden und nachgestellten Feldern besteht, ist das führende Feld ein nicht-Sekunden-Feld, das von der in Klammern Feld Genauigkeit für anführenden Intervallwert, begleitet werden kann. Das nachfolgende Feld kann sein, ein nicht-Sekunden-Feld oder ein zweites Feld, das eine Genauigkeit in Sekundenbruchteilen Intervall in Klammern metaelementtyp enthalten kann.  
  
 Die Interval-Zeichenfolge in *Wert* in einfache Anführungszeichen eingeschlossen ist. Sie können entweder ein Jahr-Monat-Literal oder ein Day-Time-Literal sein. Das Format der Zeichenfolge in *Wert* richtet sich nach den folgenden Regeln:  
  
-   Die Zeichenfolge enthält einen decimal-Wert für jedes Feld, das durch impliziert ist die \< *Intervall* *Qualifizierer*>.  
  
-   Wenn die Genauigkeit des Intervalls die Felder, Jahr und Monat enthält, werden die Werte dieser Felder durch ein Minuszeichen (-) getrennt.  
  
-   Wenn die Genauigkeit Intervall Tages- und STUNDENFORMAT Felder enthält, werden die Werte dieser Felder durch ein Leerzeichen getrennt.  
  
-   Wenn die Genauigkeit des Intervalls das Feld "Stunde" und den unteren Feldern (MINUTE und Sekunde) enthält, werden die Werte dieser Felder durch einen Doppelpunkt getrennt.  
  
-   Wenn die Genauigkeit Intervall ein zweites Feld enthält, und die Genauigkeit ausdrückliche oder konkludente ungleich NULL ist, ist das Zeichen direkt vor der ersten Ziffer des Bruchteils der zweiten einen Zeitraum an.  
  
-   Kein Feld kann mehr als zwei Ziffern lang sein, mit Ausnahme sein:  
  
    -   Der Wert des Felds führende kann so lange wie die Genauigkeit für anführenden Intervallwert ausdrückliche oder konkludente sein.  
  
    -   Der entsprechende Teil des zweiten Felds kann so lange wie die ausdrückliche oder konkludente Genauigkeit sein.  
  
    -   Die nachfolgende Felder folgen die üblichen Einschränkungen des gregorianischen Kalenders. (Finden Sie unter [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md).)  
  
 Die folgende Tabelle enthält Beispiele für gültige Intervall-Literale, das in der ODBC-Escape-Klausel für Intervalle zu enthalten. Die Syntax der Escape-Klausel lautet wie folgt aus:  
  
> [!NOTE]  
>  *{Intervall anmelden Interval-Zeichenfolge Intervall-Qualifizierer}*  
  
|Literal-Escape-Klausel|Angegebene Intervall|  
|---------------------------|------------------------|  
|{YEAR(4) INTERVALL '326'}|Gibt ein Intervall von 326 Jahren an. Die Genauigkeit für anführenden Intervallwert ist 4.|  
|{MONTH(3) INTERVALL '326'}|Gibt ein Intervall von 326 Monaten an. Die Genauigkeit für anführenden Intervallwert ist 3.|  
|{DAY(4) INTERVALL '3261'}|Gibt ein Intervall von 3261 Tagen an. Die Genauigkeit für anführenden Intervallwert ist 4.|  
|{HOUR(3) INTERVALL '163'}|Gibt ein Intervall von 163 Tagen an. Die Genauigkeit für anführenden Intervallwert ist 3.|  
|{MINUTE(3) INTERVALL '163'}|Gibt ein Intervall von 163 Minuten an. Die Genauigkeit für anführenden Intervallwert ist 3.|  
|{SECOND(3,2) INTERVALL '223.16'}|Gibt ein Intervall von 223.16 Sekunden an. Die Intervall führende Genauigkeit 3 beträgt, und die Genauigkeit ist 2.|  
|{INTERVALL ' 163-11' YEAR(3) MONAT}|Gibt ein Intervall von 163 Jahre und 11 Monate an. Die Genauigkeit für anführenden Intervallwert ist 3.|  
|{INTERVALL 163 ' 12' DAY(3) STUNDE}|Gibt ein Intervall von 163 Tage und 12 Stunden an. Die Genauigkeit für anführenden Intervallwert ist 3.|  
|{INTERVALL ' 163 12:39 "DAY(3) MINUTE}|Gibt ein Intervall von 163 Tage, 12 Stunden und 39 Minuten an. Die Genauigkeit für anführenden Intervallwert ist 3.|  
|{DAY(3) ZU SECOND(3) INTERVALL '163 12:39:59.163'}|Gibt ein Intervall von 163 Tage, 12 Stunden, 39 Minuten, und 59.163 Sekunden an. Die Intervall führende Genauigkeit 3 beträgt, und die Genauigkeit 3.|  
|{INTERVALL '163:39"HOUR(3) MINUTE}|Gibt ein Intervall von 163 Stunden und 39 Minuten an. Die Genauigkeit für anführenden Intervallwert ist 3.|  
|{INTERVALL '163:39:59.163"HOUR(3) ZU SECOND(4)}|Gibt ein Intervall von 163 Stunden, 39 Minuten, und 59.163 Sekunden an. Die Intervall führende Genauigkeit 3 beträgt, und die Genauigkeit ist 4.|  
|{INTERVALL '163:59.163"MINUTE(3) ZU SECOND(5)}|Gibt ein Intervall von 163 Minuten und 59.163 Sekunden an. Die Intervall führende Genauigkeit 3 beträgt, und die Genauigkeit ist 5.|  
|{INTERVAL-"16 23:39:56.23" FÜR TAG BIS SEKUNDE}|Gibt ein Intervall von minus 16 Tage, 23 Stunden, 39 Minuten, und 56.23 Sekunden an. Die implizite führende Genauigkeit ist 2, und die implizite Genauigkeit ist 6.|  
  
 Die folgende Tabelle enthält Beispiele für ungültige Intervall-Literale:  
  
|Literal-Escape-Klausel|Grund Warum ungültig|  
|---------------------------|------------------------|  
|{HOUR(2) INTERVALL '163'}|Die Intervall führende Genauigkeit ist 2, aber der Wert des Felds führende 163.|  
|{SECOND(2,2) INTERVALL '223.16'}<br /><br /> {SECOND(3,1) INTERVALL '223.16'}|Im ersten Beispiel ist die führende Genauigkeit ist zu klein, und im zweiten Beispiel ist die Genauigkeit zu klein.|  
|{INTERVALL "223.16" ZWEITE}<br /><br /> {INTERVALL "223" JAHR}|Da die führende Genauigkeit nicht angegeben wird, wird standardmäßig auf 2, dies ist zu klein für das angegebene Literal.|  
|{INTERVALL "22.1234567" ZWEITE}|Die Genauigkeit ist nicht angegeben, es 6 standardmäßig. Das Literal weist sieben Ziffern nach dem Dezimaltrennzeichen an.|  
|{INTERVALL ' 163-13' YEAR(3) MONAT}<br /><br /> {INTERVALL 163 ' 65' DAY(3) STUNDE}<br /><br /> {INTERVALL "163 62:39" DAY(3) MINUTE}<br /><br /> {DAY(3) ZU SECOND(3) INTERVALL '163 12:125:59.163'}<br /><br /> {INTERVALL '163:144"HOUR(3) MINUTE}<br /><br /> {INTERVALL '163:567:234.163"HOUR(3) ZU SECOND(4)}<br /><br /> {INTERVALL '163:591.163"MINUTE(3) ZU SECOND(5)}|Das nachfolgende Feld befolgt nicht die Regeln des gregorianischen Kalenders.|
