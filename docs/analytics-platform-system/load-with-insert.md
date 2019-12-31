---
title: Laden von Daten mit SSIS
description: Verwenden der T-SQL-INSERT-Anweisung zum Laden von Daten in eine verteilte oder replizierte Tabelle mit paralleler Data Warehouse (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: bbcf1a8bd16d7446841bb6d7dd86bd1ad350280d
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401019"
---
# <a name="load-data-with-insert-into-parallel-data-warehouse"></a>Laden von Daten mit INSERT INTO parallel Data Warehouse

Mithilfe der INSERT-Anweisung von "TQL" können Sie Daten in eine verteilte oder replizierte Tabelle mit SQL Server parallel Data Warehouse (PDW) laden. Weitere Informationen zum Einfügen finden Sie unter [Insert](../t-sql/statements/insert-transact-sql.md). Bei replizierten Tabellen und allen nicht Verteilungs Spalten in einer verteilten Tabelle verwendet PDW SQL Server, um die in der-Anweisung angegebenen Datenwerte implizit in den Datentyp der Ziel Spalte zu konvertieren. Weitere Informationen zu SQL Server Daten Konvertierungsregeln finden Sie unter [Datentyp Konvertierung für SQL](../t-sql/data-types/data-type-conversion-database-engine.md). Für Verteilungs Spalten unterstützt PDW jedoch nur eine Teilmenge der impliziten Konvertierungen, die SQL Server unterstützt. Wenn Sie also die INSERT-Anweisung verwenden, um Daten in eine Verteilungs Spalte zu laden, müssen die Quelldaten in einem der Formate angegeben werden, die in den folgenden Tabellen definiert sind.  
  
  
## <a name="InsertingLiteralsBinary"></a>Einfügen von Literalen in binäre Typen  
In der folgenden Tabelle sind die akzeptierten Literaltypen, das Format und die Konvertierungsregeln für das Einfügen eines Literalwerts in eine Verteilungs Spalte vom Typ " **Binary** (*n*)" oder " **varbinary**(*n*)" definiert.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Binäres wahrsten|0x*hexidecimal_string*<br /><br />Beispiel: 0x12ef|Binären literalen muss das Präfix 0x vorangestellt sein.<br /><br />Die Datenquellen Länge darf die für den Datentyp angegebene Anzahl von Bytes nicht überschreiten.<br /><br />Wenn die Datenquellen Länge kleiner als die Größe des **Binary** -Datentyps ist, werden die Daten nach rechts mit Nullen aufgefüllt, um die Größe des Datentyps zu erreichen.|  
  
## <a name="InsertingLiteralsDateTime"></a>Einfügen von Literalen in Datums-und Uhrzeit Typen  
Datums-und Uhrzeit Literale werden mithilfe von Zeichen Werten in bestimmten Formaten dargestellt, die in einfache Anführungszeichen eingeschlossen sind. In den folgenden Tabellen werden die zulässigen Literaltypen, das Format und die Konvertierungsregeln für das Einfügen eines Datums-oder Uhrzeitliterals in eine SQL Server PDW Verteilungs Spalte vom Typ **DateTime**, **smalldatetime**, **Date**, **time**, **DateTimeOffset**oder **datetime2**definiert.  
  
### <a name="datetime-data-type"></a>datetime-Datentyp  
In der folgenden Tabelle werden die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ " **DateTime**" definiert. Jede leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 12:00:00.000 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Zeichenfolgenliterale im **DateTime** -Format|"Yyyy-mm-dd hh: mm: SS [. nnn]"<br /><br />Beispiel: "2007-05-08 12:35:29.123"|Fehlende Bruch Ziffern werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08 12:35" als "2007-05-08 12:35:00.000" eingefügt.|  
|String-Literale im **smalldatetime** -Format|"Yyyy-mm-dd hh: mm"<br /><br />Beispiel: "2007-05-08 12:35"|Sekunden und übrige Bruch Ziffern werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchteile) werden auf 12:00:00.000 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliterale im **datetime2**|"Yyyy-mm-dd hh: mm: SS. nnnnnnn"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567"|Die Quelldaten dürfen nicht mehr als drei Dezimalstellen umfassen. Beispielsweise wird das Literale ' 2007-05-08 12:35:29.123 ' eingefügt, aber der Wert ' 2007-05-08 12:35:29.1234567 ' generiert einen Fehler.|  
  
### <a name="smalldatetime-data-type"></a>smalldatetime-Datentyp  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **smalldatetime**definiert. Eine leere Zeichenfolge ("") wird in den Standardwert "1900-01-01 12:00" konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|String-Literale im **smalldatetime** -Format|"Yyyy-mm-dd hh: mm" oder "yyyy-mm-dd hh: mm: 00"<br /><br />Beispiel: "2007-05-08 12:00" oder "2007-05-08 12:00:00"|Die Quelldaten müssen Werte für das Jahr, den Monat, das Datum, die Stunde und die Minute enthalten. Sekunden sind optional und müssen, falls vorhanden, auf den Wert 00 festgelegt werden. Jeder andere Wert generiert einen Fehler.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchzahlen) werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
  
### <a name="date-data-type"></a>date-Datentyp  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **Date**definiert. Eine leere Zeichenfolge ("") wird in den Standardwert "1900-01-01" konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Dies ist das einzige akzeptierte Format.|  
  
### <a name="time-data-type"></a>time-Datentyp  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **time**definiert. Eine leere Zeichenfolge ("") wird in den Standardwert "00:00:00.0000" konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Zeichen folgen Literale im **Zeit** Format|"hh: mm: SS. nnnnnnn"<br /><br />Beispiel: "12:35:29.1234567"|Wenn die Datenquelle kleiner oder gleich genau (Anzahl der Dezimalstellen) als die Genauigkeit des **time** -Datentyps ist, werden die Daten mit Nullen auf der rechten Seite aufgefüllt. Beispielsweise wird ein Literalwert "12:35:29.123" als "12:35:29.1230000" eingefügt.<br /><br />Ein Wert, der eine höhere Genauigkeit aufweist als der Ziel Datentyp, wird zurückgewiesen.|  
  
### <a name="datetimeoffset-data-type"></a>datetimeoffset-Datentyp  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **DateTimeOffset** (*n*) definiert. Das Standardformat ist ' yyyy-mm-dd hh: mm: SS. nnnnnnn {+ |-} hh: mm '. Eine leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 12:00:00.0000000 + 00:00 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler. Die Anzahl der Dezimalstellen hängt von der Spaltendefinition ab. Beispielsweise weist eine Spalte, die als **DateTimeOffset** (2) definiert ist, zwei Dezimalstellen auf.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Zeichenfolgenliterale im **DateTime** -Format|"Yyyy-mm-dd hh: mm: SS [. nnn]"<br /><br />Beispiel: "2007-05-08 12:35:29.123"|Fehlende Bruch Ziffern und Offset Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08 12:35:29.123" als "2007-05-08 12:35:29.1230000 + 00:00" eingefügt.|  
|String-Literale im **smalldatetime** -Format|"Yyyy-mm-dd hh: mm"<br /><br />Beispiel: "2007-05-08 12:35"|Sekunden, die restlichen Dezimalstellen und Offset Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchzahlen) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08" als "2007-05-08 00:00:00.0000000 + 00:00" eingefügt.|  
|Zeichenfolgenliterale im **datetime2**|"Yyyy-mm-dd hh: mm: SS. nnnnnnn"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567"|Die Quelldaten dürfen die angegebene Anzahl von Sekundenbruchteilen in der DateTimeOffset-Spalte nicht überschreiten. Wenn die Datenquelle kleiner oder gleich der Anzahl der Sekundenbruchteile ist, werden die Daten mit Nullen nach rechts aufgefüllt. Wenn der Datentyp z. b. DateTimeOffset (5) lautet, wird der Literalwert "2007-05-08 12:35:29.123 + 12:15" als "12:35:29.12300 + 12:15" eingefügt.|  
|String-Literale im **DateTimeOffset** -Format|"Yyyy-mm-dd hh: mm: SS. nnnnnnn {+&#124;-} hh: mm"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567 + 12:15"|Die Quelldaten dürfen die angegebene Anzahl von Sekundenbruchteilen in der DateTimeOffset-Spalte nicht überschreiten. Wenn die Datenquelle kleiner oder gleich der Anzahl der Sekundenbruchteile ist, werden die Daten mit Nullen nach rechts aufgefüllt. Wenn der Datentyp z. b. DateTimeOffset (5) lautet, wird der Literalwert "2007-05-08 12:35:29.123 + 12:15" als "12:35:29.12300 + 12:15" eingefügt.|  
  
### <a name="datetime2-data-type"></a>datetime2-Datentyp  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **datetime2** (*n*) definiert. Das Standardformat ist "yyyy-mm-dd hh: mm: SS. nnnnnnn". Eine leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 12:00:00 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler. Die Anzahl der Dezimalstellen hängt von der Spaltendefinition ab. Beispielsweise weist eine Spalte, die als **datetime2** (2) definiert ist, zwei Dezimalstellen auf.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Zeichenfolgenliterale im **DateTime** -Format|"Yyyy-mm-dd hh: mm: SS [. nnn]"<br /><br />Beispiel: "2007-05-08 12:35:29.123"|Sekundenbruchteile sind optional und werden auf 0 festgelegt, wenn der Wert eingefügt wird.<br /><br />Ein Wert, der mehr Bruch Ziffern als der Ziel Datentyp aufweist, wird zurückgewiesen.|  
|String-Literale im **smalldatetime** -Format|"Yyyy-mm-dd hh: mm"<br /><br />Beispiel: "2007-05-08 12"|Optionale Sekunden und übrige Bruch Ziffern werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchzahlen) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08" als "2007-05-08 12:00:00.0000000" eingefügt.|  
|Zeichenfolgenliterale im **datetime2**|"Yyyy-mm-dd hh: mm: SS: nnnnnnn"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567"|Wenn die Datenquelle Daten-und Zeit Komponenten enthält, die kleiner oder gleich dem in **datetime2**(*n*) angegebenen Wert sind, werden die Daten eingefügt. Andernfalls wird ein Fehler generiert.|  
  
## <a name="InsertLiteralsNumeric"></a>Einfügen von Literalen in numerische Typen  
In den folgenden Tabellen werden die zulässigen Formate und Konvertierungsregeln für das Einfügen eines Literalwerts in eine SQL Server PDW Verteilungs Spalte definiert, in der ein numerischer Typ verwendet wird.  
  
### <a name="bit-data-type"></a>bit-Datentyp  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **Bit**definiert. Eine leere Zeichenfolge ("") oder eine Zeichenfolge, die nur Leerzeichen ("") enthält, wird in 0 konvertiert.  
  
|Literaltyp|format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteralformat ****|"nnnnnnnnnn"<br /><br />Beispiel: "1" oder "321"|Ein ganzzahliger Wert, der als Zeichenfolgenliterals formatiert ist, darf keinen Beispielsweise generiert der Wert "-123" einen Fehler.<br /><br />Ein Wert, der größer als 1 ist, wird in 1 konvertiert. Beispielsweise wird der Wert "123" in 1 konvertiert.|  
|String-Literale|' True ' oder ' false '<br /><br />Beispiel: ' true '|Der Wert ' true ' wird in 1 konvertiert. der Wert "false" wird in 0 konvertiert.|  
|Ganzzahliges Format|nnnnnnnn<br /><br />Beispiel: 1 oder 321|Ein Wert, der größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Die Werte 123 und-123 werden z. b. in 1 konvertiert.|  
|Decimal-Literale|nnnnn. nnnn<br /><br />Beispiel: 1234,5678|Ein Wert, der größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Die Werte 123,45 und-123,45 werden z. b. in 1 konvertiert.|  
  
### <a name="decimal-data-type"></a>decimal-Datentyp  
In der folgenden Tabelle werden die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ " **Decimal** (*p, s*)" definiert. Die Daten Konvertierungsregeln sind identisch mit denen für SQL Server. Weitere Informationen finden Sie unter [Datentyp Konvertierung](../t-sql/data-types/data-type-conversion-database-engine.md) auf MSDN.  
  
|Literaltyp|Format|  
|----------------|----------|  
|Zeichenfolgenliteralformat ****|nnnnnnnnnnnn<br /><br />Beispiel: "321312313123"|  
|Zeichenfolgenliteralformat ****|"nnnnnn. nnnnn"<br /><br />Beispiel: "123344,34455"|  
|Ganzzahliges Format|nnnnnnnnnnnn<br /><br />Beispiel: 321312313123|  
|Decimal-Literale|nnnnnn. nnnnn<br /><br />Beispiel: "123344,34455"|  
  
### <a name="float-and-real-data-types"></a>float-und Real-Datentypen  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **float** oder **Real**definiert. Daten Konvertierungsregeln sind identisch mit denen für SQL Server. Weitere Informationen finden Sie unter [Datentyp Konvertierung](../t-sql/data-types/data-type-conversion-database-engine.md) auf MSDN.  
  
|Literaltyp|Format|  
|----------------|----------|  
|Zeichenfolgenliteralformat ****|nnnnnnnnnnnn<br /><br />Beispiel: "321312313123"|  
|Zeichenfolgenliteralformat ****|"nnnnnn. nnnnn"<br /><br />Beispiel: "123344,34455"|  
|Zeichenfolgenliterale im Gleit **Komma** Format|"n. nnnne + NN"<br /><br />Beispiel: "3.12323 e + 14"|  
|Ganzzahliges Format|nnnnnnnnnnnn<br /><br />Beispiel: 321312313123|  
|Decimal-Literale|nnnnnn. nnnnn<br /><br />Beispiel: 123344,34455|  
|Gleit Komma Literale|n. nnnne + NN<br /><br />Beispiel: 3.12323 e + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int, bigint, tinyint, smallint-Datentypen  
In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ " **int**", " **bigint**", " **tinyint**" oder " **smallint**" definiert. Die Datenquelle darf nicht den für den angegebenen Datentyp zulässigen Bereich überschreiten. Beispielsweise liegt der Bereich für **tinyint** zwischen 0 und 255, und der Bereich für **int** ist-2.147.483.648 bis 2.147.483.647.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|------------|------|----------------|
|Zeichenfolgenliteralformat ****|"nnnnnnnnnnnnnnn"<br /><br />Beispiel: "321312313123"| Keine |  
|Ganzzahliges Format|nnnnnnnnnnnnnnn<br /><br />Beispiel: 321312313123| Keine|  
|Decimal-Literale|nnnnnn. nnnnn<br /><br />Beispiel: 123344,34455|Die Werte auf der rechten Seite des Dezimal Trennzeichens werden abgeschnitten.|  
  
### <a name="money-and-smallmoney-data-types"></a>Money-und smallmoney-Datentypen  
Money-Literalwerte werden als Zahlen mit einem optionalen Dezimal-und Währungssymbol als Präfix dargestellt. Die Datenquelle darf nicht den für den angegebenen Datentyp zulässigen Bereich überschreiten. Der Bereich für **smallmoney** beträgt z. b.-214.748,3648 bis 214.748,3647 und der Bereich für **Money** den Wert-922.337.203.685.477,5808 bis 922.337.203.685.477,5807. In der folgenden Tabelle sind die zulässigen Formate und Regeln zum Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **Money** oder **smallmoney**definiert.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|Zeichenfolgenliteralformat ****|nnnnnnnn<br /><br />Beispiel: "123433"|Fehlende Ziffern nach dem Dezimaltrennzeichen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "12345" als 12345,0000 eingefügt.|  
|Zeichenfolgenliteralformat ****|"nnnnnn. nnnnn"<br /><br />Beispiel: "123344,34455"|Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet. Beispielsweise wird der Wert "123344,34455" als 123344,3446 eingefügt.|  
|Zeichenfolgenliteralformat ****|"$nnnnnn. nnnn"<br /><br />Beispiel: "$123456,7890"|Das optionale Währungssymbol wird nicht mit dem Wert eingefügt.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet.|  
|Ganzzahliges Format|nnnnnnnn<br /><br />Beispiel: 123433|Fehlende Ziffern nach dem Dezimaltrennzeichen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale 12345 als 12345,0000 eingefügt.|  
|Decimal-Literale|nnnnnn. nnnnn<br /><br />Beispiel: 123344,34455|Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet. Beispielsweise wird der Wert 123344,34455 als 123344,3446 eingefügt.|  
|Money-Literale|$nnnnnn. nnnn<br /><br />Beispiel: $123456,7890|Das optionale Währungssymbol wird nicht mit dem Wert eingefügt.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet.|  
  
## <a name="InsertLiteralsString"></a>Einfügen von Literalen in Zeichen folgen Typen  
In den folgenden Tabellen werden die zulässigen Formate und Konvertierungsregeln für das Einfügen eines Literalwerts in eine SQL Server PDW Spalte, die einen Zeichen Folgentyp verwendet, definiert.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>Datentypen char, varchar, nchar und nvarchar  
In der folgenden Tabelle sind die zulässigen Formate und Regeln für das Einfügen von Literalwerten in eine Verteilungs Spalte vom Typ **char**, **varchar**, **NCHAR** und **nvarchar**definiert. Die Datenquellen Länge darf die für den Datentyp angegebene Größe nicht überschreiten. Wenn die Datenquellen Länge kleiner als die Größe des Datentyps **char** oder **NCHAR** ist, werden die Daten rechts mit Leerzeichen aufgefüllt, um die Größe des Datentyps zu erreichen.  
  
|Literaltyp|Format|Konvertierungsregeln|  
|----------------|----------|--------------------|  
|String-Literale|Format: ' Zeichenfolge '<br /><br />Beispiel: "ABC"| Keine|  
|Unicode String-Literale|Format: n ' Zeichenfolge '<br /><br />Beispiel: n ' abc '|  Keine |  
|Ganzzahliges Format|Format: nnnnnnnnnnn<br /><br />Beispiel: 321312313123| Keine |  
|Decimal-Literale|Format: nnnnnn. nnnnnnn<br /><br />Beispiel: 12344,34455| Keine |  
|Money-Literale|Format: $nnnnnn. nnnnn<br /><br />Beispiel: $123456,99|Das Währungssymbol wird nicht mit dem Wert eingefügt. Fügen Sie den Wert als Zeichenfolgenliterale ein, um das Währungssymbol einzufügen. Dies entspricht dem Format des **"dwloader** -Tools, das jedes Literale als zeichenfolgenliteralvorgang behandelt.<br /><br />Kommas sind nicht zulässig.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 2 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet. Beispielsweise wird der Wert 123,946789 als 123,95 eingefügt.<br /><br />Nur der Standardstil 0 (keine Kommas und 2 Ziffern nach dem Dezimaltrennzeichen) ist zulässig, wenn die Convert-Funktion verwendet wird, um Geld Literale einzufügen.|  

  
## <a name="see-also"></a>Weitere Informationen  
 
[Verteilte Daten](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-distributed-data/)  
[Setze](../t-sql/statements/insert-transact-sql.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Metadata query examples](metadata-query-examples.md) 
-->
