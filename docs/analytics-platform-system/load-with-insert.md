---
title: Laden von Daten mit INSERT - Parallel Data Warehouse | Microsoft-Dokumentation
description: Verwenden die T-SQL INSERT-Anweisung zum Laden von Daten in Parallel Data Warehouse (PDW) verteilte oder replizierte Tabelle.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b13daf2d32cc41d63deea6c612dde247d541e4d5
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392316"
---
# <a name="load-data-with-insert-into-parallel-data-warehouse"></a>Laden von Daten mit INSERT in Parallel Data Warehouse

Sie können die Tsql-INSERT-Anweisung verwenden, zum Laden von Daten in eine SQLServer Parallel Datawarehouse (PDW) verteilte oder replizierte Tabelle. Weitere Informationen zum Einfügen, finden Sie unter [einfügen](../t-sql/statements/insert-transact-sql.md). Für replizierte Tabellen sowie alle nichtverteilungsspalte-Spalten in einer verteilten Tabelle verwendet PDW SQL Server, um die Datenwerte in der Anweisung in den Datentyp der Zielspalte angegebenen implizit zu konvertieren. Weitere Informationen zu Konvertierungsregeln für SQL Server-Daten, finden Sie unter [datentypkonvertierung für SQL](../t-sql/data-types/data-type-conversion-database-engine.md). Für verteilungsspalten unterstützt PDW jedoch nur eine Teilmenge von impliziten Konvertierungen, die SQL Server unterstützt. Wenn Sie die INSERT-Anweisung, zum Laden von Daten in eine verteilungsspalte verwenden, müssen daher die Quelldaten in eines der Formate, die definiert, die in den folgenden Tabellen angegeben werden.  
  
  
## <a name="InsertingLiteralsBinary"></a>Fügen Sie Literale in binäre Typen  
In der folgende Tabelle definiert, der akzeptierten Literaltypen, Format und Konvertierungsregeln für das Einfügen von eines literalen Werts in eine verteilungsspalte des Typs **binäre** (*n*) oder **Varbinary** (*n*).  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Binäres literal|0 X*Hexidecimal_string*<br /><br />Beispiel: 0x12Ef|Binäre Literale müssen mit ' 0 X vorangestellt werden.<br /><br />Die Länge der Daten-Quelle kann nicht die angegebene Anzahl von Bytes für den Datentyp nicht überschreiten.<br /><br />Kleiner als ist die Datenlänge für die Quelle der **binäre** -Datentyp, die Daten werden aufgefüllt, auf der rechten Seite mit Nullen aufgefüllt, um die Datengröße für den Typ zu erreichen.|  
  
## <a name="InsertingLiteralsDateTime"></a>Fügen Sie Literale in Datums- und Uhrzeittypen  
Datum und Uhrzeit – Literale werden mit Zeichenwerten enthalten, die in bestimmten Formaten, eingeschlossen in einfache Anführungszeichen dargestellt. In den folgenden Tabellen definieren, die zulässige Literaltypen, Format und Konvertierungsregeln für ein Datum oder Uhrzeit-literal in einer SQL Server-PDW-Distribution-Spalte vom Typ eingefügt **"DateTime"**, **Smalldatetime**, **Datum**, **Zeit**, **Datetimeoffset**, oder **datetime2**.  
  
### <a name="datetime-data-type"></a>DateTime-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **"DateTime"**. Leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 12:00:00.000 von 1900-01-01 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **"DateTime"** Format|"YYYY-MM-DD HH: mm: [.nnn]"<br /><br />Beispiel: ' 2007-05-08-12:35:29.123 "|Fehlende Dezimalstellen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. das Literal "2007-05-08 12:35 ' wird als eingefügt" 2007-05-08-12:35:00.000 ".|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"YYYY-MM-DD HH: mm"<br /><br />Beispiel: ' 2007-05-08 12:35 "|Sekunden und die restlichen Dezimalstellen werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **Datum** Format|"YYYY-MM-DD"<br /><br />Beispiel: ' 2007-05-08 "|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 12:00:00.000 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **datetime2** Format|"JJJJ-MM-TT ss.nnnnnnn"<br /><br />Beispiel: ' 2007-05-08-12:35:29.1234567 "|Die Quelldaten können drei Dezimalstellen nicht überschreiten. Z. B. das Literal "2007-05-08-12:35:29.123' eingefügt werden soll, aber der Wert ' 2007-05-08-12:35:29.1234567" wird ein Fehler generiert.|  
  
### <a name="smalldatetime-data-type"></a>Smalldatetime-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Smalldatetime**. Leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 12:00 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"YYYY-MM-DD HH: mm" oder "YYYY-MM-tt Hh:mm:00"<br /><br />Beispiel: ' 2007-05-08 12:00 ' oder ' 2007-05-08 12:00:00 "|Die Quelldaten müssen Werte für Jahr, Monat, Datum, Stunde und Minute. Sekunden sind optional und, falls vorhanden, müssen auf den Wert 00 festgelegt werden. Ein anderer Wert erzeugt einen Fehler.|  
|Zeichenfolgenliteral in **Datum** Format|"YYYY-MM-DD"<br /><br />Beispiel: ' 2007-05-08 "|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
  
### <a name="date-data-type"></a>Date-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Datum**. Leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **Datum** Format|"YYYY-MM-DD"<br /><br />Beispiel: ' 2007-05-08 "|Dies ist das einzige akzeptierte Format.|  
  
### <a name="time-data-type"></a>Time-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Zeit**. Leere Zeichenfolge (") wird auf den Standardwert"00:00:00.0000"konvertiert. Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **Zeit** Format|"ss.nnnnnnn"<br /><br />Beispiel: "12:35:29.1234567"|Wenn die Datenquelle mit einer Genauigkeit kleiner oder gleich (Anzahl der Dezimalstellen) als die Genauigkeit des verfügt über die **Zeit** -Datentyp, werden die Daten auf der rechten Seite mit Nullen aufgefüllt. Beispielsweise wird ein Literalwert "12:35:29.123" als "12:35:29.1230000" eingefügt.<br /><br />Ein Wert, der eine größere Genauigkeit als den Ziel-Datentyp aufweist, wird abgelehnt.|  
  
### <a name="datetimeoffset-data-type"></a>DateTimeOffset-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Datetimeoffset** (*n*). Das Standardformat ist ' YYYY-MM-TT ss.nnnnnnn {+ |-} hh: mm ". Eine leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 12:00:00.0000000 + 00:00 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert. Die Anzahl der Dezimalstellen, hängt von der Definition der Spalte ab. Z. B. eine Spalte, die als definiert **Datetimeoffset** (2) hat zwei Dezimalstellen.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **"DateTime"** Format|"YYYY-MM-DD HH: mm: [.nnn]"<br /><br />Beispiel: ' 2007-05-08-12:35:29.123 "|Fehlende Dezimalstellen und Offset-Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. das Literal "2007-05-08-12:35:29.123" eingefügt wird, als "2007-05-08-12:35:29.1230000 + 00:00".|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"YYYY-MM-DD HH: mm"<br /><br />Beispiel: ' 2007-05-08 12:35 "|Sekunden, die restlichen Dezimalstellen und die Offset-Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **Datum** Format|"YYYY-MM-DD"<br /><br />Beispiel: ' 2007-05-08 "|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. literal ' 2007-05-08' wird als eingefügt "2007-05-08-00:00:00.0000000 + 00:00".|  
|Zeichenfolgenliteral in **datetime2** Format|"JJJJ-MM-TT ss.nnnnnnn"<br /><br />Beispiel: ' 2007-05-08-12:35:29.1234567 "|Die Quelldaten darf die angegebene Anzahl von Sekundenbruchteilen in der Spalte "DateTimeOffset" nicht überschreiten. Wenn die Datenquelle eine Zahl kleinere oder gleich der Bruchteile von Sekunden aufweist, werden die Daten auf der rechten Seite mit Nullen aufgefüllt. Wenn der Datentyp "DateTimeOffset" (5), der literale Wert ist z. B. ' 2007-05-08-12:35:29.123 + 12:15 ' wird als eingefügt "12:35:29.12300 + 12:15 '.|  
|Zeichenfolgenliteral in **Datetimeoffset** Format|"JJJJ-MM-TT ss.nnnnnnn {+&#124;-} hh: mm"<br /><br />Beispiel: ' 2007-05-08-12:35:29.1234567 + 12:15 '|Die Quelldaten darf die angegebene Anzahl von Sekundenbruchteilen in der Spalte "DateTimeOffset" nicht überschreiten. Wenn die Datenquelle eine Zahl kleinere oder gleich der Bruchteile von Sekunden aufweist, werden die Daten auf der rechten Seite mit Nullen aufgefüllt. Wenn der Datentyp "DateTimeOffset" (5), der literale Wert ist z. B. ' 2007-05-08-12:35:29.123 + 12:15 ' wird als eingefügt "12:35:29.12300 + 12:15 '.|  
  
### <a name="datetime2-data-type"></a>datetime2-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **datetime2** (*n*). Das Standardformat ist "YYYY-MM-TT ss.nnnnnnn". Eine leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 12:00:00 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert. Die Anzahl der Dezimalstellen, hängt von der Definition der Spalte ab. Z. B. eine Spalte, die als definiert **datetime2** (2) hat zwei Dezimalstellen.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **"DateTime"** Format|"YYYY-MM-DD HH: mm: [.nnn]"<br /><br />Beispiel: ' 2007-05-08-12:35:29.123 "|Bruchteile von Sekunden sind optional und werden auf 0 festgelegt, wenn der Wert eingefügt wird.<br /><br />Ein Wert, der mehr Dezimalstellen als der Zieltyp für die Daten hat, wird abgelehnt.|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"YYYY-MM-DD HH: mm"<br /><br />Beispiel: ' 2007-05-08-12 "|Sekunden (optional) und die restlichen Dezimalstellen werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **Datum** Format|"YYYY-MM-DD"<br /><br />Beispiel: ' 2007-05-08 "|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. literal ' 2007-05-08' wird als eingefügt "2007-05-08-12:00:00.0000000".|  
|Zeichenfolgenliteral in **datetime2** Format|"JJJJ-MM-tt Hh:mm:ss:nnnnnnn"<br /><br />Beispiel: ' 2007-05-08-12:35:29.1234567 "|Wenn die Datenquelle und der Zeitpunkt der Komponenten enthält, die kleiner oder gleich dem im angegebenen Wert sind **datetime2**(*n*), die Daten eingefügt; andernfalls wird ein Fehler generiert.|  
  
## <a name="InsertLiteralsNumeric"></a>Einfügen von Literalen in numerische Typen  
In den folgenden Tabellen definieren, die zulässigen Formate und die Konvertierungsregeln für das Einfügen von eines literalen Werts in einer SQL Server-PDW-verteilungsspalte, die einen numerischen Typ verwendet.  
  
### <a name="bit-data-type"></a>bit-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Bit**. Eine leere Zeichenfolge (") oder eine Zeichenfolge, die nur Leerzeichen enthalten (" ") wird in 0 konvertiert.  
  
|Literaltyp|format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **Ganzzahl** Format|"Nnnnnnnnnn"<br /><br />Beispiel: '1' oder "321"|Ein ganzzahliger Wert formatiert als Zeichenfolgenliteral kann nicht auf einen negativen Wert enthalten. Der Wert "-123" generiert z. B. einen Fehler.<br /><br />Ein Wert größer als 1 wird in 1 konvertiert. Beispielsweise wird der Wert "123" in 1 konvertiert.|  
|Zeichenfolgenliteral|'TRUE' oder 'FALSE'<br /><br />Beispiel: 'true'|Der Wert 'TRUE' wird in 1 konvertiert. der Wert 'FALSE' wird in 0 konvertiert.|  
|Integer-literal|nnnnnnnn<br /><br />Beispiel: 1 oder 321|Ein Wert größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Beispielsweise werden die Werte, 123 "und"-123 in 1 konvertiert.|  
|Dezimales literal|nnnnn.nnnn<br /><br />Beispiel: 1234.5678|Ein Wert größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Beispielsweise werden die Werte 123,45 und-123.45 in 1 konvertiert.|  
  
### <a name="decimal-data-type"></a>decimal-Datentyp  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **decimal** (*p, s*). Die Konvertierungsregeln für die Daten sind identisch mit dem SQL Server. Weitere Informationen finden Sie unter [datentypkonvertierung](../t-sql/data-types/data-type-conversion-database-engine.md) auf MSDN.  
  
|Literaltyp|Format|  
|----------------|----------|  
|Zeichenfolgenliteral in **Ganzzahl** Format|"Nnnnnnnnnnnn"<br /><br />Beispiel: "321312313123"|  
|Zeichenfolgenliteral in **decimal** Format|"nnnnnn.nnnnn"<br /><br />Beispiel: "123344.34455"|  
|Integer-literal|nnnnnnnnnnnn<br /><br />Beispiel: 321312313123|  
|Dezimales literal|nnnnnn.nnnnn<br /><br />Beispiel: "123344.34455"|  
  
### <a name="float-and-real-data-types"></a>float- und Real-Datentypen  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **"float"** oder **echte**. Regeln für die Konvertierung von Daten sind identisch mit dem SQL Server. Weitere Informationen finden Sie unter [datentypkonvertierung](../t-sql/data-types/data-type-conversion-database-engine.md) auf MSDN.  
  
|Literaltyp|Format|  
|----------------|----------|  
|Zeichenfolgenliteral in **Ganzzahl** Format|"Nnnnnnnnnnnn"<br /><br />Beispiel: "321312313123"|  
|Zeichenfolgenliteral in **decimal** Format|"nnnnnn.nnnnn"<br /><br />Beispiel: "123344.34455"|  
|Zeichenfolgenliteral in **Gleitkomma** Format|"n.nnnnnE+nn"<br /><br />Beispiel: "3.12323E + 14"|  
|Integer-literal|nnnnnnnnnnnn<br /><br />Beispiel: 321312313123|  
|Dezimales literal|nnnnnn.nnnnn<br /><br />Beispiel: 123344.34455|  
|Floating-Point-literal|n.nnnnnE+nn<br /><br />Beispiel: 3.12323E + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>Int, Bigint, Tinyint, Smallint-Datentypen  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Int**, **Bigint**, **Tinyint**, oder **Smallint**. Die Datenquelle kann die für den angegebenen Datentyp zulässigen Bereichs nicht überschreiten. Beispielsweise der Bereich für **Tinyint** ist 0 bis 255 und der Bereich für **Int** wird von – 2.147.483.648 bis 2.147.483.647.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|------------|------|----------------|
|Zeichenfolgenliteral in **Ganzzahl** Format|"Nnnnnnnnnnnnnn"<br /><br />Beispiel: "321312313123"| None |  
|Integer-literal|nnnnnnnnnnnnnn<br /><br />Beispiel: 321312313123| None|  
|Dezimales literal|nnnnnn.nnnnn<br /><br />Beispiel: 123344.34455|Die Werte, die rechts neben dem Dezimaltrennzeichen werden abgeschnitten.|  
  
### <a name="money-and-smallmoney-data-types"></a>Money und Smallmoney-Datentypen  
Money-literal-Werte werden als Zahlen mit einem optionalen Dezimaltrennzeichen und das Währungssymbol als Präfix dargestellt. Die Datenquelle kann die für den angegebenen Datentyp zulässigen Bereichs nicht überschreiten. Beispielsweise der Bereich für **Smallmoney** ist-214,748.3648 214.748,3647 und der Bereich für **Geld** 922.337.203.685.477,5808 bis 922.337.203.685.477,5807 ist. Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Geld** oder **Smallmoney**.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral in **Ganzzahl** Format|"Nnnnnnnn"<br /><br />Beispiel: "123433"|Fehlende Ziffern nach dem Dezimaltrennzeichen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das literal "12345" als 12345.0000 eingefügt.|  
|Zeichenfolgenliteral in **decimal** Format|"nnnnnn.nnnnn"<br /><br />Beispiel: "123344.34455"|Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreiten, wird der Wert auf den nächsten Wert aufgerundet. Beispielsweise wird der Wert "123344.34455" als 123344.3446 eingefügt.|  
|Zeichenfolgenliteral in **Geld** Format|'$nnnnnn.nnnn'<br /><br />Beispiel: "$123456.7890"|Die optionalen Währungssymbol ist nicht mit dem Wert eingefügt.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreiten, wird der Wert auf den nächsten Wert aufgerundet.|  
|Integer-literal|nnnnnnnn<br /><br />Beispiel: 123433|Fehlende Ziffern nach dem Dezimaltrennzeichen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das literal 12345 als 12345.0000 eingefügt.|  
|Dezimales literal|nnnnnn.nnnnn<br /><br />Beispiel: 123344.34455|Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreiten, wird der Wert auf den nächsten Wert aufgerundet. Beispielsweise wird der Wert 123344.34455 als 123344.3446 eingefügt.|  
|Money-literal|$nnnnnn.nnnn<br /><br />Beispiel: $123456.7890|Die optionalen Währungssymbol ist nicht mit dem Wert eingefügt.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreiten, wird der Wert auf den nächsten Wert aufgerundet.|  
  
## <a name="InsertLiteralsString"></a>Einfügen von Literalen in Zeichenfolgentypen  
In den folgenden Tabellen definieren, die zulässigen Formate und die Konvertierungsregeln für das Einfügen von einen literalen Wert in eine SQL Server-PDW-Spalte, die einen String-Datentyp verwendet.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>Char, Varchar, Nchar und Nvarchar-Datentypen  
Der folgenden Tabelle werden die zulässigen Formate und die Regeln für das Einfügen von literalen Werten in einer verteilungsspalte des Typs **Char**, **Varchar**, **Nchar** und **Nvarchar**. Die Länge der Daten-Quelle kann nicht für den Datentyp angegebene Größe überschreiten. Kleiner als ist die Datenlänge für die Quelle der **Char** oder **Nchar** -Datentyp, die Daten werden aufgefüllt, auf der rechten Seite mit Leerzeichen, um die Datengröße für den Typ zu erreichen.  
  
|Literaltyp|Format|Konvertierungsregeln für|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteral|Format: "Zeichenfolge"<br /><br />Beispiel: 'Abc'| None|  
|Unicode-Zeichenfolgenliteral|: Formatzeichenfolge N'character "<br /><br />Beispiel: N "|  None |  
|Integer-literal|Format: Nnnnnnnnnnn<br /><br />Beispiel: 321312313123| None |  
|Dezimales literal|Format: nnnnnn.nnnnnnn<br /><br />Beispiel: 12344.34455| None |  
|Money-literal|Format: $nnnnnn.nnnnn<br /><br />Beispiel: $123456.99|Das Währungssymbol wird nicht mit dem Wert eingefügt. Um das Währungssymbol einzufügen, fügen Sie den Wert als Zeichenfolgenliteral. Dies entspricht das Format der **Dwloader** -Tool, das jedem Literal als Zeichenfolgenliteral behandelt.<br /><br />Trennzeichen sind nicht zulässig.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 2 überschreitet, wird der Wert auf den nächsten Wert aufgerundet. Beispielsweise wird der Wert 123.946789 als 123.95 eingefügt.<br /><br />Nur das Standardformat 0 (keine Kommas und 2 Ziffern nach dem Dezimaltrennzeichen) ist zulässig, wenn die CONVERT-Funktion verwenden, zum Einfügen von Money-Literale.|  

  
## <a name="see-also"></a>Siehe auch  
 
[Verteilte Daten](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-distributed-data/)  
[INSERT](../t-sql/statements/insert-transact-sql.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Metadata query examples](metadata-query-examples.md) 
-->
