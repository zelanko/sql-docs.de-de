---
title: 'Dwloader Datentyp Konvertierungsregeln: Parallel Data Warehouse | Microsoft-Dokumentation'
description: Dieses Thema beschreibt die Eingabedaten-Formate und die implizite datentypkonvertierungen, Dwloader, die Command-Line-Ladeprogramm unterstützt, wenn Daten in Parallel Data Warehouse (PDW) geladen."
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: a15e129ad1cbf52a3daab5459e9ca7d06d195b9d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961039"
---
# <a name="data-type-conversion-rules-for-dwloader---parallel-data-warehouse"></a>Konvertierungsregeln für Dwloader – Parallel Data Warehouse-Datentyp
In diesem Thema wird beschrieben, die Eingabedaten-Formate und die implizite datentypkonvertierungen, [Dwloader Command-Line-Ladeprogramm](dwloader.md) unterstützt Sie beim Laden von Daten in PDW. Die implizite datenkonvertierungen auftreten, wenn die Eingabedaten nicht den Datentyp in der SQL Server-PDW-Zieltabelle übereinstimmt. Verwenden Sie diese Informationen beim Entwerfen Ihres Ladeprozesses, um sicherzustellen, dass Ihre Daten erfolgreich in SQL Server PDW geladen wird.  
   
  
## <a name="InsertBinaryTypes"></a>Einfügen von Literalen in binäre Typen  
In der folgende Tabelle definiert, der akzeptierten Literaltypen, Format und Konvertierungsregeln für einen literalen Wert in eine SQL Server-PDW-Spalte vom Typ laden **binäre** (*n*) oder **Varbinary** (*n*).  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in den Binary oder Varbinary-Datentyp|  
|-------------------|-----------------------|-----------------------------------------------|  
|Binäres literal|[0 X] *Hexidecimal_string*<br /><br />Beispiel: 12Ef oder 0x12Ef|Das Präfix 0 X ist optional.<br /><br />Die Länge der Daten-Quelle kann nicht die angegebene Anzahl von Bytes für den Datentyp nicht überschreiten.<br /><br />Kleiner als ist die Datenlänge für die Quelle der **binäre** -Datentyp, die Daten werden aufgefüllt, auf der rechten Seite mit Nullen aufgefüllt, um die Datengröße für den Typ zu erreichen.|  
  
## <a name="InsertDateTimeTypes"></a>Einfügen von Literalen in Datums- und Uhrzeittypen  
Datum und Uhrzeit – Literale werden von mithilfe von Zeichenfolgenliteralen in bestimmten Formaten, eingeschlossen in einfache Anführungszeichen dargestellt. In den folgenden Tabellen definieren, die zulässige Literaltypen, Format und Konvertierungsregeln für ein Datum oder Uhrzeit-literal in einer Spalte vom Typ laden **"DateTime"** , **Smalldatetime**, **Datum**, **Zeit**, **Datetimeoffset**, oder **datetime2**. Die Tabellen definieren, das Standardformat für den angegebenen Datentyp. Andere Formate, die angegeben werden können, werden im Abschnitt definiert [Datetime-Formate](#DateFormats). Datum und Uhrzeit – Literale darf keine führende oder nachgestellte Leerzeichen enthalten. **Datum**, **Smalldatetime**, null-Werte können nicht geladen werden, im Modus mit fester Breite.  
  
### <a name="datetime-data-type"></a>datetime-Datentyp  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **"DateTime"** . Eine leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 12:00:00.000 von 1900-01-01 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in Datetime-Datentyp|  
|-------------------|-----------------------|------------------------------------|  
|Zeichenfolgenliteral in **"DateTime"** Format|"Yyyy-MM-Dd hh: mm: [: ss. fff]"<br /><br />Beispiel: '2007-05-08 12:35:29.123'|Fehlende Dezimalstellen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. das Literal "2007-05-08 12:35 ' wird als eingefügt" 2007-05-08-12:35:00.000 ".|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"Yyyy-MM-Dd hh: mm"<br /><br />Beispiel: "2007-05-08 12:35"|Sekunden und die restlichen Dezimalstellen werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **Datum** Format|'yyyy-MM-dd'<br /><br />Beispiel: "2007-05-08"|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 12:00:00.000 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **datetime2** Format|"JJJJ-MM-TT ss.fffffff"<br /><br />Beispiel: '2007-05-08 12:35:29.1234567'|Die Quelldaten können drei Dezimalstellen nicht überschreiten. Z. B. das Literal "2007-05-08-12:35:29.123' eingefügt werden soll, aber der Wert ' 2007-05-8-12:35:29.1234567" wird ein Fehler generiert.|  
  
### <a name="smalldatetime-data-type"></a>smalldatetime-Datentyp  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **Smalldatetime**. Eine leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 12:00 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in den Smalldatetime-Datentyp|  
|-------------------|-----------------------|-----------------------------------------|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"Yyyy-MM-Dd hh: mm" oder "Yyyy-MM-Dd hh: mm:"<br /><br />Beispiel: "2007-05-08 12:00 ' oder ' 2007-05-08 12:00:15"|Die Quelldaten müssen Werte für Jahr, Monat, Datum, Stunde und Minute. Sekunden sind optional und, falls vorhanden, müssen auf den Wert 00 festgelegt werden. Ein anderer Wert erzeugt einen Fehler.<br /><br />Sekunden sind optional. Beim Laden in einen Smalldatetime-Spalte rundet Dwloader Sekunden und Bruchteilen von Sekunden. Zum Beispiel lädt die 1999-01-05-20:10:35.123 als 01-05-20:11.|  
|Zeichenfolgenliteral in **Datum** Format|'yyyy-MM-dd'<br /><br />Beispiel: "2007-05-08"|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
  
### <a name="date-data-type"></a>date-Datumstyp  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **Datum**. Eine leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Konvertierung in Date-Datentyp|  
|-------------------|-----------------------|--------------------------------|  
|Zeichenfolgenliteral in **Datum** Format|'yyyy-MM-dd'<br /><br />Beispiel: "2007-05-08"||  
  
### <a name="time-data-type"></a>Time-Datentyp  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **Zeit**. Eine leere Zeichenfolge (") wird auf den Standardwert"00:00:00.0000"konvertiert. Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in Time-Datentyp|  
|-------------------|-----------------------|--------------------------------|  
|Zeichenfolgenliteral in **Zeit** Format|'hh:mm:ss.fffffff'<br /><br />Beispiel: '12:35:29.1234567'|Wenn die Datenquelle mit einer Genauigkeit kleiner oder gleich (Anzahl der Dezimalstellen) als die Genauigkeit des verfügt über die **Zeit** -Datentyp, werden die Daten auf der rechten Seite mit Nullen aufgefüllt. Beispielsweise wird ein Literalwert "12:35:29.123" als "12:35:29.1230000" eingefügt.|  
  
### <a name="datetimeoffset-data-type"></a>DateTimeOffset-Datentyp  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **Datetimeoffset** (*n*). Das Standardformat ist ' Yyyy-MM-TT ss.FFFFFFF {+ |-} hh: mm ". Eine leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 12:00:00.0000000 + 00:00 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert. Die Anzahl der Dezimalstellen, hängt von der Definition der Spalte ab. Z. B. eine Spalte, die als definiert **Datetimeoffset** (2) hat zwei Dezimalstellen.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in Datetimeoffset-Datentyp|  
|-------------------|-----------------------|------------------------------------------|  
|Zeichenfolgenliteral in **"DateTime"** Format|"Yyyy-MM-Dd hh: mm: [: ss. fff]"<br /><br />Beispiel: '2007-05-08 12:35:29.123'|Fehlende Dezimalstellen und Offset-Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. das Literal "2007-05-08-12:35:29.123" eingefügt wird, als "2007-05-08-12:35:29.1230000 + 00:00".|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"Yyyy-MM-Dd hh: mm"<br /><br />Beispiel: "2007-05-08 12:35"|Sekunden, die restlichen Dezimalstellen und die Offset-Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **Datum** Format|'yyyy-MM-dd'<br /><br />Beispiel: "2007-05-08"|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. literal ' 2007-05-08' wird als eingefügt "2007-05-08-00:00:00.0000000 + 00:00".|  
|Zeichenfolgenliteral in **datetime2** Format|"JJJJ-MM-TT ss.fffffff"<br /><br />Beispiel: '2007-05-08 12:35:29.1234567'|Die Quelldaten darf die angegebene Anzahl von Sekundenbruchteilen in der Spalte "DateTimeOffset" nicht überschreiten. Wenn die Datenquelle eine Zahl kleinere oder gleich der Bruchteile von Sekunden aufweist, werden die Daten auf der rechten Seite mit Nullen aufgefüllt. Wenn der Datentyp "DateTimeOffset" (5), der literale Wert ist z. B. ' 2007-05-08-12:35:29.123 + 12:15 ' wird als eingefügt "12:35:29.12300 + 12:15 '.|  
|Zeichenfolgenliteral in **Datetimeoffset** Format|'yyyy-MM-dd hh:mm:ss.fffffff {+&#124;-} hh:mm'<br /><br />Beispiel: '2007-05-08 12:35:29.1234567 +12:15'|Die Quelldaten darf die angegebene Anzahl von Sekundenbruchteilen in der Spalte "DateTimeOffset" nicht überschreiten. Wenn die Datenquelle eine Zahl kleinere oder gleich der Bruchteile von Sekunden aufweist, werden die Daten auf der rechten Seite mit Nullen aufgefüllt. Wenn der Datentyp "DateTimeOffset" (5), der literale Wert ist z. B. ' 2007-05-08-12:35:29.123 + 12:15 ' wird als eingefügt "12:35:29.12300 + 12:15 '.|  
  
### <a name="datetime2-data-type"></a>datetime2-Datentyp  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **datetime2** (*n*). Das Standardformat ist "Yyyy-MM-TT ss.fffffff". Eine leere Zeichenfolge (") konvertiert wird, auf den Standardwert" 1900-01-01 12:00:00 ". Zeichenfolgen, die nur Leerzeichen enthalten ("") ein Fehler generiert. Die Anzahl der Dezimalstellen, hängt von der Definition der Spalte ab. Z. B. eine Spalte, die als definiert **datetime2** (2) hat zwei Dezimalstellen.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Konvertierung in datetime2-Datentyp|  
|-------------------|-----------------------|-------------------------------------|  
|Zeichenfolgenliteral in **"DateTime"** Format|"Yyyy-MM-Dd hh: mm: [: ss. fff]"<br /><br />Beispiel: '2007-05-08 12:35:29.123'|Bruchteile von Sekunden sind optional und werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **Smalldatetime** Format|"Yyyy-MM-Dd hh: mm"<br /><br />Beispiel: "2007-05-08-12"|Sekunden (optional) und die restlichen Dezimalstellen werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteral in **Datum** Format|'yyyy-MM-dd'<br /><br />Beispiel: "2007-05-08"|Time-Werten (Stunden, Minuten, Sekunden und Sekundenbruchteile) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Z. B. literal ' 2007-05-08' wird als eingefügt "2007-05-08-12:00:00.0000000".|  
|Zeichenfolgenliteral in **datetime2** Format|"JJJJ-MM-tt Hh:mm:ss:fffffff"<br /><br />Beispiel: '2007-05-08 12:35:29.1234567'|Wenn die Datenquelle und der Zeitpunkt der Komponenten enthält, die kleiner oder gleich dem im angegebenen Wert sind **datetime2**(*n*), die Daten eingefügt; andernfalls wird ein Fehler generiert.|  
  
### <a name="DateFormats"></a>DateTime-Formate  
Dwloader unterstützt die folgenden Formate für die Eingabedaten, die beim Laden in SQL Server PDW. Weitere Details werden nach der Tabelle aufgeführt.  
  
|DATETIME|smalldatetime|date|datetime2|datetimeoffset|  
|------------|-----------------|--------|-------------|------------------|  
|[M[M]]M-[T]T-[JJ]JJ HH:mm:ss[.fff]|[M[M]]M-[T]T-[JJ]JJ HH:mm[:00]|[M[M]]M-[T]T-[JJ]JJ|[M[M]]M-[T]T-[JJ]JJ HH:mm:ss[.fffffff]|[M[M]]M-[T]T-[JJ]JJ HH:mm:ss[.fffffff] zzz|  
|[M[M]]M-[T]T-[JJ]JJ hh:mm:ss[.fff][tt]|[M[M]]M-[T]T-[JJ]JJ hh:mm[:00][tt]||[M[M]]M-[T]T-[JJ]JJ hh:mm:ss[.fffffff][tt]|[M[M]]M-[T]T-[JJ]JJ hh:mm:ss[.fffffff][tt] zzz|  
|[M[M]]M-[JJ]JJ-[T]T HH:mm:ss[.fff]|[M[M]]M-[JJ]JJ-[T]T HH:mm[:00]|[M[M]]M-[JJ]JJ-[T]T|[M[M]]M-[JJ]JJ-[T]T HH:mm:ss[.fffffff]|[M[M]]M-[JJ]JJ-[T]T HH:mm:ss[.fffffff] zzz|  
|[M[M]]M-[JJ]JJ-[T]T hh:mm:ss[.fff][tt]|[M[M]]M-[JJ]JJ-[T]T hh:mm[:00][tt]||[M[M]]M-[JJ]JJ-[T]T hh:mm:ss[.fffffff][tt]|[M[M]]M-[JJ]JJ-[T]T hh:mm:ss[.fffffff][tt] zzz|  
|[JJ]JJ-[M[M]]M-[T]T HH:mm:ss[.fff]|[JJ]JJ-[M[M]]M-[T]T HH:mm[:00]|[JJ]JJ-[M[M]]M-[T]T|[JJ]JJ-[M[M]]M-[T]T HH:mm:ss[.fffffff]|[JJ]JJ-[M[M]]M-[T]T HH:mm:ss[.fffffff] zzz|  
|[JJ]JJ-[M[M]]M-[T]T hh:mm:ss[.fff][tt]|[JJ]JJ-[M[M]]M-[T]T hh:mm[:00][tt]||[JJ]JJ-[M[M]]M-[T]T hh:mm:ss[.fffffff][tt]|[JJ]JJ-[M[M]]M-[T]T hh:mm:ss[.fffffff][tt] zzz|  
|[JJ]JJ-[T]T-[M[M]]M HH:mm:ss[.fff]|[JJ]JJ-[T]T-[M[M]]M HH:mm[:00]|[JJ]JJ-[T]T-[M[M]]M|[JJ]JJ-[T]T-[M[M]]M HH:mm:ss[.fffffff]|[JJ]JJ-[T]T-[M[M]]M HH:mm:ss[.fffffff] zzz|  
|[JJ]JJ-[T]T-[M[M]]M hh:mm:ss[.fff][tt]|[JJ]JJ-[T]T-[M[M]]M hh:mm[:00][tt]||[JJ]JJ-[T]T-[M[M]]M hh:mm:ss[.fffffff][tt]|[JJ]JJ-[T]T-[M[M]]M hh:mm:ss[.fffffff][tt] zzz|  
|[T]T-[M[M]]M-[JJ]JJ HH:mm:ss[.fff]|[T]T-[M[M]]M-[JJ]JJ HH:mm[:00]|[T]T-[M[M]]M-[JJ]JJ|[T]T-[M[M]]M-[JJ]JJ :mm:ss[.fffffff]|[T]T-[M[M]]M-[JJ]JJ HH:mm:ss[.fffffff] zzz|  
|[T]T-[M[M]]M-[JJ]JJ hh:mm:ss[.fff][tt]|[T]T-[M[M]]M-[JJ]JJ hh:mm[:00][tt]||[T]T-[M[M]]M-[JJ]JJ hh:mm:ss[.fffffff][tt]|[T]T-[M[M]]M-[JJ]JJ hh:mm:ss[.fffffff][tt] zzz|  
|[T]T-[JJ]JJ-[M[M]]M HH:mm:ss[.fff]|[T]T-[JJ]JJ-[M[M]]M HH:mm[:00]|[T]T-[JJ]JJ-[M[M]]M|[T]T-[JJ]JJ-[M[M]]M HH:mm:ss[.fffffff]|[T]T-[JJ]JJ-[M[M]]M HH:mm:ss[.fffffff] zzz|  
|[T]T-[JJ]JJ-[M[M]]M hh:mm:ss[.fff][tt]|[T]T-[JJ]JJ-[M[M]]M hh:mm[:00][tt]||[T]T-[JJ]JJ-[M[M]]M hh:mm:ss[.fffffff][tt]|[T]T-[JJ]JJ-[M[M]]M hh:mm:ss[.fffffff][tt] zzz|  
  
Details:  
  
-   Um die Werte für Monat, Tag und Jahr zu trennen, können Sie '-', '/' oder '. '. Der Einfachheit halber wird in die Tabelle nur das Trennzeichen „-“ verwendet.  
  
-   Klicken Sie zum Angeben des Monats als Text drei oder mehr Zeichen verwenden. Monate mit 1 oder 2-Zeichen werden als Zahl interpretiert werden.  
  
-   Um die Time-Werte zu trennen, verwenden Sie die ': ' Symbol.  
  
-   Buchstaben in eckigen Klammern sind optional.  
  
-   Die Buchstaben „tt“ kennzeichnen [AM|PM|am|pm]. AM ist die Standardeinstellung. Wenn „tt“ angegeben ist, muss der Wert für die Stunde (hh) in einem Bereich von 0 bis 12 liegen.  
  
-   Die Buchstaben „zzz“ kennzeichnen den Offsetwert für die Zeitzone für die aktuelle Zeitzone des Systems im Format {+|-}HH:ss].  
  
## <a name="InsertNumerictypes"></a>Einfügen von Literalen in numerische Typen  
In den folgenden Tabellen definieren, die Standardregeln Format und die Konvertierung zum Laden von einen literalen Wert in eine SQL Server-PDW-Spalte, die einen numerischen Typ verwendet.  
  
### <a name="bit-data-type"></a>Bit-Datentyp  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **Bit**. Eine leere Zeichenfolge (") oder eine Zeichenfolge, die nur Leerzeichen enthalten (" ") wird in 0 konvertiert.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in die vom Datentyp bit|  
|-------------------|-----------------------|-------------------------------|  
|Zeichenfolgenliteral in **Ganzzahl** Format|"Ffffffffff"<br /><br />Beispiel: '1' oder "321"|Ein ganzzahliger Wert formatiert als Zeichenfolgenliteral kann nicht auf einen negativen Wert enthalten. Der Wert "-123" generiert z. B. einen Fehler.<br /><br />Ein Wert größer als 1 wird in 1 konvertiert. Beispielsweise wird der Wert "123" in 1 konvertiert.|  
|Zeichenfolgenliteral|'TRUE' oder 'FALSE'<br /><br />Beispiel: 'true'|Der Wert 'TRUE' wird in 1 konvertiert. der Wert 'FALSE' wird in 0 konvertiert.|  
|Integer-literal|fffffffn<br /><br />Beispiel: 1 oder 321|Ein Wert größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Beispielsweise werden die Werte, 123 "und"-123 in 1 konvertiert.|  
|Dezimales literal|fffnn.fffn<br /><br />Beispiel: 1234.5678|Ein Wert größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Beispielsweise werden die Werte 123,45 und-123.45 in 1 konvertiert.|  
  
### <a name="decimal-data-type"></a>Decimal-Datentyp  
In der folgende Tabelle werden die Regeln zum Laden von literalen Werten in einer Spalte vom Typ definiert **decimal** (*p, s*). Regeln für die Konvertierung von Daten sind identisch mit dem SQL Server. Weitere Informationen finden Sie unter [Datentypkonvertierung (Datenbank-Engine)](https://go.microsoft.com/fwlink/?LinkId=202128) auf MSDN.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|  
|-------------------|-----------------------|  
|Integer-literal|321312313123|  
|Dezimales literal|123344.34455|  
  
### <a name="float-and-real-data-types"></a>float- und Real-Datentypen  
Der folgenden Tabelle werden die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **"float"** oder **echte**. Regeln für die Konvertierung von Daten sind identisch mit dem SQL Server. Weitere Informationen finden Sie unter [Datentypkonvertierung (Datenbank-Engine)](../t-sql/data-types/data-type-conversion-database-engine.md) auf MSDN.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|  
|-------------------|-----------------------|  
|Integer-literal|321312313123|  
|Dezimales literal|123344.34455|  
|Floating-Point-literal|3.12323E+14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>Int, Bigint, Tinyint, Smallint-Datentypen  
In der folgende Tabelle werden die Regeln zum Laden von literalen Werten in einer Spalte vom Typ definiert **Int**, **Bigint**, **Tinyint**, oder **Smallint**. Die Datenquelle kann die für den angegebenen Datentyp zulässigen Bereichs nicht überschreiten. Beispielsweise der Bereich für **Tinyint** ist 0 bis 255 und der Bereich für **Int** wird von – 2.147.483.648 bis 2.147.483.647.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in den Integer-Datentypen|  
|-------------------|-----------------------|------------------------------------|  
|Integer-literal|321312313123||  
|Dezimales literal|123344.34455|Die Werte, die rechts neben dem Dezimaltrennzeichen werden abgeschnitten.|  
  
### <a name="money-and-smallmoney-data-types"></a>Money und Smallmoney-Datentypen  
Money-Literalwerte werden als eine Zeichenfolge von Zahlen mit einem optionalen Dezimaltrennzeichen und einem optionalen Währungssymbol als Präfix dargestellt. Die Datenquelle kann die für den angegebenen Datentyp zulässigen Bereichs nicht überschreiten. Beispielsweise der Bereich für **Smallmoney** ist-214,748.3648 214.748,3647 und der Bereich für **Geld** 922.337.203.685.477,5808 bis 922.337.203.685.477,5807 ist. In der folgende Tabelle werden die Regeln zum Laden von literalen Werten in einer Spalte vom Typ definiert **Geld** oder **Smallmoney**.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Konvertierung zu Geld "oder" Smallmoney-Datentyp|  
|-------------------|-----------------------|-----------------------------------------------|  
|Integer-literal|321312|Fehlende Ziffern nach dem Dezimaltrennzeichen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Das literal 12345 wird beispielsweise als 12345.0000 eingefügt.|  
|Dezimales literal|123344.34455|Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreiten, wird der Wert auf den nächsten Wert aufgerundet. Beispielsweise wird der Wert 123344.34455 als 123344.3446 eingefügt.|  
|Money-literal|$123456.7890|Das Währungssymbol wird nicht mit dem Wert eingefügt.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreiten, wird der Wert auf den nächsten Wert aufgerundet.|  
  
## <a name="InsertStringTypes"></a>Einfügen von Literalen in Zeichenfolgentypen  
In den folgenden Tabellen definieren, die Standardregeln Format und die Konvertierung zum Laden von einen literalen Wert in eine SQL Server-PDW-Spalte, die einen String-Datentyp verwendet.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>Char, Varchar, Nchar und Nvarchar-Datentypen  
In der folgende Tabelle definiert, das Standardformat und die Regeln zum Laden von literalen Werten in einer Spalte vom Typ **Char**, **Varchar**, **Nchar** und **Nvarchar** . Die Länge der Daten-Quelle kann nicht für den Datentyp angegebene Größe überschreiten. Kleiner als ist die Datenlänge für die Quelle der **Char** oder **Nchar** -Datentyp, die Daten werden aufgefüllt, auf der rechten Seite mit Leerzeichen, um die Datengröße für den Typ zu erreichen.  
  
|Eingabe-Datentyp|Beispiele für die Eingabedaten|Die Konvertierung in char-Datentypen|  
|---------------|-------------------|----------------------------------|  
|Zeichenfolgenliteral|Format: "Zeichenfolge"<br /><br />Beispiel: 'Abc'| NA |  
|Unicode-Zeichenfolgenliteral|Format: N'character-Zeichenfolge '<br /><br />Beispiel: N'abc'| NA |  
|Integer-literal|Format: Ffffffffffn<br /><br />Beispiel: 321312313123| NA |  
|Dezimales literal|Format: ffffff.fffffff<br /><br />Beispiel: 12344.34455| NA |  
|Money-literal|Format: $ffffff.fffnn<br /><br />Beispiel: $123456.99|Die optionalen Währungssymbol ist nicht mit dem Wert eingefügt. Um das Währungssymbol einzufügen, fügen Sie den Wert als Zeichenfolgenliteral. Dies entspricht das Format des Ladeprogramms, der jedem Literal als Zeichenfolgenliteral behandelt.<br /><br />Trennzeichen sind nicht zulässig.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 2 überschreitet, wird der Wert auf den nächsten Wert aufgerundet. Beispielsweise wird der Wert 123.946789 als 123.95 eingefügt.<br /><br />Nur das Standardformat 0 (keine Kommas und 2 Ziffern nach dem Dezimaltrennzeichen) ist zulässig, wenn die CONVERT-Funktion verwenden, zum Einfügen von Money-Literale.|  
  
### <a name="general-remarks"></a>Allgemeine Hinweise  
**Dwloader** führt die gleiche implizite Konvertierungen aus, dass SMP-SQL Server ausführt, sondern nicht alle von der impliziten Konvertierungen, SMP-SQLServer unterstützt unterstützt.  
 
<!-- MISSING LINKS 
## See Also  
[Grant Permissions to Load Data &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-load-data-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  

-->
  
