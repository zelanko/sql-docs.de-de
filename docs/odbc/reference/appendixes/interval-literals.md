---
title: Intervall Literale | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304941"
---
# <a name="interval-literals"></a>Intervallliterale
Für ODBC müssen alle Treiber die Konvertierung der SQL_CHAR oder SQL_VARCHAR Datentyps in alle C-Intervall Datentypen unterstützen. Wenn die zugrunde liegende Datenquelle jedoch keine Intervall Datentypen unterstützt, muss der Treiber das richtige Format des Werts im Feld SQL_CHAR kennen, um diese Konvertierungen zu unterstützen. Ebenso erfordert ODBC, dass alle ODBC C-Typen in SQL_CHAR oder SQL_VARCHAR konvertiert werden können. Daher muss ein Treiber wissen, welches Format ein im Zeichenfeld gespeicherter Zeitraum aufweisen sollte. In diesem Abschnitt wird die Syntax von Intervall literalen beschrieben, die der treiberwriter zum Validieren der SQL_CHAR Felder während der Konvertierung in oder aus C-Intervall Datentypen verwenden muss.  
  
> [!NOTE]  
>  Die gesamte BNF-Syntax für intervallliterale wird im Abschnitt [Interval-Literalsyntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) in Anhang C: SQL-Grammatik gezeigt.  
  
 Um Intervall Literale als Teil einer SQL-Anweisung zu übergeben, wird eine Escape-KlauselSyntax für intervallliterale definiert. Weitere Informationen finden Sie unter [Date-, Time-und Timestamp-Literale](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Ein intervallliteral hat folgendes Format:  
  
```  
INTERVAL[<sign>] 'value' <interval qualifier>  
```  
  
 Where "Interval" gibt an, dass das Zeichen Literale ein Intervall ist. Das Vorzeichen kann entweder Plus oder minus sein. Sie liegt außerhalb der Intervall Zeichenfolge und ist optional.  
  
 Der Intervall Qualifizierer kann entweder ein einzelnes DateTime-Feld sein oder aus zwei DateTime-Feldern bestehen, in \<folgendem Format: *führendes Feld*> an \< *nachfolgende Feld*>.  
  
-   Wenn das Intervall aus einem einzelnen Feld besteht, kann das einzelne Feld ein nicht zweites Feld sein, das möglicherweise von einer optionalen vorangehende Genauigkeit in Klammern begleitet wird. Das einzelne DateTime-Feld kann auch ein zweites Feld sein, das möglicherweise von der optionalen vorangebenden Genauigkeit, der optionalen Genauigkeit in Sekundenbruchteilen in Klammern oder beides begleitet wird. Wenn sowohl eine führende Genauigkeit als auch eine Genauigkeit von Sekundenbruchteilen für ein Sekunden Feld vorhanden sind, werden diese durch Kommas getrennt. Wenn das Sekunden Feld eine Genauigkeit von Sekundenbruchteilen aufweist, muss es auch eine führende Genauigkeit aufweisen.  
  
-   Wenn das Intervall aus führenden und nachfolgenden Feldern besteht, ist das führende Feld ein nicht zweites Feld, das möglicherweise von der in Klammern führenden Feld Genauigkeit begleitet wird. Das nachfolgende Feld kann entweder ein nicht zweites Feld oder ein zweites Feld sein, das von einer Genauigkeit in Sekundenbruchteilen in Klammern eingeschlossen werden kann.  
  
 Die Intervall Zeichenfolge in *value* wird in einfache Anführungszeichen eingeschlossen. Dabei kann es sich entweder um ein Jahr oder einen tagesliteral handeln. Das Format der Zeichenfolge in *value* wird durch die folgenden Regeln bestimmt:  
  
-   Die Zeichenfolge enthält einen Dezimalwert für jedes Feld, das vom \< *Intervall* *Qualifizierer*> impliziert wird.  
  
-   Wenn die Intervall Genauigkeit die Felder Jahr und Monat umfasst, werden die Werte dieser Felder durch ein Minuszeichen voneinander getrennt.  
  
-   Wenn die Intervall Genauigkeit die Felder Day und Hour umfasst, werden die Werte dieser Felder durch ein Leerzeichen voneinander getrennt.  
  
-   Wenn die Genauigkeit des Intervalls die Feld Stunde und die unteren Reihen folgen Felder (Minute und Sekunde) umfasst, werden die Werte dieser Felder durch einen Doppelpunkt getrennt.  
  
-   Wenn die Genauigkeit des Intervalls ein zweites Feld enthält und die angegebene oder implizite Sekunden Genauigkeit nicht NULL ist, ist das Zeichen unmittelbar vor der ersten Ziffer des Bruchteils der zweiten ein Punkt.  
  
-   Ein Feld kann nicht mehr als zwei Ziffern lang sein, außer:  
  
    -   Der Wert des führenden Felds kann so lang sein, wie das angegebene oder implizite Intervall mit der Spitzen Genauigkeit.  
  
    -   Der Bruchteil des zweiten Felds kann so lang sein, dass es die Genauigkeit der Ausdrücken oder implizierten Sekunden aufweist.  
  
    -   Die nachfolgenden Felder folgen den üblichen Einschränkungen des gregorianischen Kalenders. (Siehe [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md).)  
  
 In der folgenden Tabelle sind Beispiele für gültige Intervall Literale aufgeführt, die in der ODBC-Escapesequenz für Intervalle enthalten sind. Die Syntax der Escape-Klausel lautet wie folgt:  
  
> [!NOTE]  
>  *{Intervall Zeichen Intervall-Zeichen folgen Intervall-Qualifizierer}*  
  
|Literale Escape-Klausel|Festgelegtes Intervall|  
|---------------------------|------------------------|  
|{Interval ' 326 ' Jahr (4)}|Gibt ein Intervall von 326 Jahren an. Die angegebene Intervall Genauigkeit beträgt 4.|  
|{Interval ' 326 ' Monat (3)}|Gibt ein Intervall von 326 Monaten an. Die angegebene Intervall Genauigkeit beträgt 3.|  
|{Interval ' 3261 ' Tag (4)}|Gibt ein Intervall von 3261 Tagen an. Die angegebene Intervall Genauigkeit beträgt 4.|  
|{INTERVAL "163" Stunde (3)}|Gibt ein Intervall von 163 Tagen an. Die angegebene Intervall Genauigkeit beträgt 3.|  
|{Interval ' 163 ' Minute (3)}|Gibt ein Intervall von 163 Minuten an. Die angegebene Intervall Genauigkeit beträgt 3.|  
|{Interval ' 223,16 ' Second (3, 2)}|Gibt ein Intervall von 223,16 Sekunden an. Die angegebene Intervall Genauigkeit beträgt 3 und die Sekunden Genauigkeit 2.|  
|{Interval ' 163-11 ' Jahr (3) bis Monat}|Gibt ein Intervall von 163 Jahren und 11 Monaten an. Die angegebene Intervall Genauigkeit beträgt 3.|  
|{Interval ' 163 12 ' Tag (3) bis Stunde}|Gibt ein Intervall von 163 Tagen und 12 Stunden an. Die angegebene Intervall Genauigkeit beträgt 3.|  
|{Interval ' 163 12:39 ' Tag (3) bis Minute}|Gibt ein Intervall von 163 Tagen, 12 Stunden und 39 Minuten an. Die angegebene Intervall Genauigkeit beträgt 3.|  
|{Interval ' 163 12:39:59.163 ' Tag (3) bis Sekunde (3)}|Gibt ein Intervall von 163 Tagen, 12 Stunden, 39 Minuten und 59,163 Sekunden an. Die angegebene Intervall Genauigkeit beträgt 3 und die Sekunden Genauigkeit 3.|  
|{INTERVAL "163:39" Stunde (3) bis Minute}|Gibt ein Intervall von 163 Stunden und 39 Minuten an. Die angegebene Intervall Genauigkeit beträgt 3.|  
|{Interval ' 163:39:59.163 ' Stunde (3) bis Sekunde (4)}|Gibt ein Intervall von 163 Stunden, 39 Minuten und 59,163 Sekunden an. Die angegebene Intervall Genauigkeit beträgt 3 und die Sekunden Genauigkeit 4.|  
|{Interval ' 163:59.163 ' Minute (3) bis Sekunde (5)}|Gibt ein Intervall von 163 Minuten und 59,163 Sekunden an. Die angegebene Intervall Genauigkeit beträgt 3 und die Sekunden Genauigkeit 5.|  
|{INTERVAL-"16 23:39:56.23" Day to Second}|Gibt ein Intervall von minus 16 Tagen, 23 Stunden, 39 Minuten und 56,23 Sekunden an. Die implizite führende Genauigkeit ist 2, und die implizite Sekunden Genauigkeit ist 6.|  
  
 In der folgenden Tabelle sind Beispiele für ungültige Intervall Literale aufgeführt:  
  
|Literale Escape-Klausel|Grund für ungültiges|  
|---------------------------|------------------------|  
|{INTERVAL "163" Stunde (2)}|Die angegebene Intervall Genauigkeit ist 2, aber der Wert des führenden Felds ist 163.|  
|{Interval ' 223,16 ' Second (2, 2)}<br /><br /> {Interval ' 223,16 ' Second (3, 1)}|Im ersten Beispiel ist die führende Genauigkeit zu klein, und im zweiten Beispiel ist die Genauigkeit der Sekunden zu klein.|  
|{Interval ' 223,16 ' Second}<br /><br /> {Interval ' 223 ' Jahr}|Da die führende Genauigkeit nicht angegeben ist, wird standardmäßig 2 verwendet. Dies ist zu klein, um das angegebene Literalzeichen zu speichern.|  
|{Interval ' 22,1234567 ' Second}|Die Sekunden Genauigkeit ist nicht angegeben, d. h., der Standardwert ist 6. Das Literale weist sieben Ziffern nach dem Dezimaltrennzeichen auf.|  
|{Interval ' 163-13 ' Jahr (3) bis Monat}<br /><br /> {Interval ' 163 65 ' Tag (3) bis Stunde}<br /><br /> {Interval ' 163 62:39 ' Tag (3) bis Minute}<br /><br /> {Interval ' 163 12:125:59.163 ' Tag (3) bis Sekunde (3)}<br /><br /> {INTERVAL "163:144" Stunde (3) bis Minute}<br /><br /> {INTERVAL "163:567:234.163" Stunde (3) bis Sekunde (4)}<br /><br /> {Interval ' 163:591.163 ' Minute (3) bis Sekunde (5)}|Das nachfolgende Feld folgt nicht den Regeln des gregorianischen Kalenders.|
