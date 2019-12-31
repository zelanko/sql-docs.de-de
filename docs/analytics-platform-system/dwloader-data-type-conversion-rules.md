---
title: Regeln für die Datentyp Konvertierung von dwloader
description: In diesem Thema werden die Eingabedaten Formate und die impliziten Datentyp Konvertierungen beschrieben, die vom Befehlszeilen Lade Tool von "dwloader unterstützt werden, wenn Daten in parallele Data Warehouse (PDW) geladen werden.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: fe5d8790b5adb8477c994d265f458cdb1ceda61a
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401181"
---
# <a name="data-type-conversion-rules-for-dwloader---parallel-data-warehouse"></a>Datentyp-Konvertierungsregeln für "dwloader-parallel Data Warehouse
In diesem Thema werden die Eingabedaten Formate und die impliziten Datentyp Konvertierungen beschrieben, die vom [Befehlszeilen Lader von "dwloader](dwloader.md) unterstützt werden, wenn Daten in PDW geladen werden. Die impliziten Datenkonvertierungen treten auf, wenn die Eingabedaten nicht dem Datentyp in der SQL Server PDW Ziel Tabelle entsprechen. Verwenden Sie diese Informationen beim Entwerfen des Ladevorgangs, um sicherzustellen, dass Ihre Daten erfolgreich in SQL Server PDW geladen werden.  
   
  
## <a name="InsertBinaryTypes"></a>Einfügen von Literalen in binäre Typen  
In der folgenden Tabelle werden die zulässigen Literaltypen, das Format und die Konvertierungsregeln für das Laden eines Literalwerts in eine SQL Server PDW Spalte vom Typ " **Binary** (*n*)" oder " **varbinary**(*n*)" definiert.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in einen binary-oder varbinary-Datentyp|  
|-------------------|-----------------------|-----------------------------------------------|  
|Binäres wahrsten|0x *hexidecimal_string*<br /><br />Beispiel: 12ef oder 0x12ef|Das 0x-Präfix ist optional.<br /><br />Die Datenquellen Länge darf die für den Datentyp angegebene Anzahl von Bytes nicht überschreiten.<br /><br />Wenn die Datenquellen Länge kleiner als die Größe des **Binary** -Datentyps ist, werden die Daten nach rechts mit Nullen aufgefüllt, um die Größe des Datentyps zu erreichen.|  
  
## <a name="InsertDateTimeTypes"></a>Einfügen von Literalen in Datums-und Uhrzeit Typen  
Datums-und Uhrzeit Literale werden mithilfe von Zeichenfolgenliteralen in bestimmten Formaten dargestellt, die in einfache Anführungszeichen eingeschlossen sind. In den folgenden Tabellen werden die zulässigen Literaltypen, das Format und die Konvertierungsregeln für das Laden eines Datums-oder Uhrzeitliterals in eine Spalte vom Typ **DateTime**, **smalldatetime**, **Date**, **time**, **DateTimeOffset**oder **datetime2**definiert. Die Tabellen definieren das Standardformat für den angegebenen Datentyp. Andere Formate, die angegeben werden können, werden im Abschnitt [DateTime-Formate](#DateFormats)definiert. Datums-und Uhrzeit Literale dürfen keine führenden oder nachfolgenden Leerzeichen enthalten. die Werte **Date**, **smalldatetime**und NULL können nicht im Modus für die fest Breite geladen werden.  
  
### <a name="datetime-data-type"></a>datetime-Datentyp  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **DateTime**definiert. Eine leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 12:00:00.000 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in DateTime-Datentyp|  
|-------------------|-----------------------|------------------------------------|  
|Zeichenfolgenliterale im **DateTime** -Format|"yyyy-mm-dd hh: mm: SS [. fff]"<br /><br />Beispiel: "2007-05-08 12:35:29.123"|Fehlende Bruch Ziffern werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08 12:35" als "2007-05-08 12:35:00.000" eingefügt.|  
|String-Literale im **smalldatetime** -Format|"yyyy-mm-dd hh: mm"<br /><br />Beispiel: "2007-05-08 12:35"|Sekunden und übrige Bruch Ziffern werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchteile) werden auf 12:00:00.000 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliterale im **datetime2**|"yyyy-mm-dd hh: mm: SS. fffffff"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567"|Die Quelldaten dürfen nicht mehr als drei Dezimalstellen umfassen. Beispielsweise wird das Literale ' 2007-05-08 12:35:29.123 ' eingefügt, aber der Wert ' 2007-05-8 12:35:29.1234567 ' generiert einen Fehler.|  
  
### <a name="smalldatetime-data-type"></a>smalldatetime-Datentyp  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **smalldatetime**definiert. Eine leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 12:00 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in smalldatetime-Datentyp|  
|-------------------|-----------------------|-----------------------------------------|  
|String-Literale im **smalldatetime** -Format|"yyyy-mm-dd hh: mm" oder "yyyy-mm-dd hh: mm: SS"<br /><br />Beispiel: "2007-05-08 12:00" oder "2007-05-08 12:00:15"|Die Quelldaten müssen Werte für das Jahr, den Monat, das Datum, die Stunde und die Minute enthalten. Sekunden sind optional und müssen, falls vorhanden, auf den Wert 00 festgelegt werden. Jeder andere Wert generiert einen Fehler.<br /><br />Sekunden sind optional. Beim Laden in eine smalldatetime-Spalte wird "dwloader in Sekunden und Sekundenbruchteilen aufgerundet. Beispiel: 1999-01-05 20:10:35.123 wird als 01-05 20:11 geladen.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchzahlen) werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
  
### <a name="date-data-type"></a>date-Datumstyp  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **Date**definiert. Eine leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in Date-Datentyp|  
|-------------------|-----------------------|--------------------------------|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"||  
  
### <a name="time-data-type"></a>Time-Datentyp  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **time**definiert. Eine leere Zeichenfolge ("") wird in den Standardwert "00:00:00.0000" konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in Time-Datentyp|  
|-------------------|-----------------------|--------------------------------|  
|Zeichen folgen Literale im **Zeit** Format|"hh: mm: SS. fffffff"<br /><br />Beispiel: "12:35:29.1234567"|Wenn die Datenquelle kleiner oder gleich genau (Anzahl der Dezimalstellen) als die Genauigkeit des **time** -Datentyps ist, werden die Daten mit Nullen auf der rechten Seite aufgefüllt. Beispielsweise wird ein Literalwert "12:35:29.123" als "12:35:29.1230000" eingefügt.|  
  
### <a name="datetimeoffset-data-type"></a>DateTimeOffset-Datentyp  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **DateTimeOffset** (*n*) definiert. Das Standardformat ist ' yyyy-mm-dd hh: mm: SS. fffffff {+ |-} hh: mm '. Eine leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 12:00:00.0000000 + 00:00 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler. Die Anzahl der Dezimalstellen hängt von der Spaltendefinition ab. Beispielsweise weist eine Spalte, die als **DateTimeOffset** (2) definiert ist, zwei Dezimalstellen auf.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertieren in DateTimeOffset-Datentyp|  
|-------------------|-----------------------|------------------------------------------|  
|Zeichenfolgenliterale im **DateTime** -Format|"yyyy-mm-dd hh: mm: SS [. fff]"<br /><br />Beispiel: "2007-05-08 12:35:29.123"|Fehlende Bruch Ziffern und Offset Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08 12:35:29.123" als "2007-05-08 12:35:29.1230000 + 00:00" eingefügt.|  
|String-Literale im **smalldatetime** -Format|"yyyy-mm-dd hh: mm"<br /><br />Beispiel: "2007-05-08 12:35"|Sekunden, die restlichen Dezimalstellen und Offset Werte werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchzahlen) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08" als "2007-05-08 00:00:00.0000000 + 00:00" eingefügt.|  
|Zeichenfolgenliterale im **datetime2**|"yyyy-mm-dd hh: mm: SS. fffffff"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567"|Die Quelldaten dürfen die angegebene Anzahl von Sekundenbruchteilen in der DateTimeOffset-Spalte nicht überschreiten. Wenn die Datenquelle kleiner oder gleich der Anzahl der Sekundenbruchteile ist, werden die Daten mit Nullen nach rechts aufgefüllt. Wenn der Datentyp z. b. DateTimeOffset (5) lautet, wird der Literalwert "2007-05-08 12:35:29.123 + 12:15" als "12:35:29.12300 + 12:15" eingefügt.|  
|String-Literale im **DateTimeOffset** -Format|"yyyy-mm-dd hh: mm: SS. fffffff {+&#124;-} hh: mm"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567 + 12:15"|Die Quelldaten dürfen die angegebene Anzahl von Sekundenbruchteilen in der DateTimeOffset-Spalte nicht überschreiten. Wenn die Datenquelle kleiner oder gleich der Anzahl der Sekundenbruchteile ist, werden die Daten mit Nullen nach rechts aufgefüllt. Wenn der Datentyp z. b. DateTimeOffset (5) lautet, wird der Literalwert "2007-05-08 12:35:29.123 + 12:15" als "12:35:29.12300 + 12:15" eingefügt.|  
  
### <a name="datetime2-data-type"></a>datetime2-Datentyp  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **datetime2** (*n*) definiert. Das Standardformat ist "yyyy-mm-dd hh: mm: SS. fffffff". Eine leere Zeichenfolge (' ') wird in den Standardwert ' 1900-01-01 12:00:00 ' konvertiert. Zeichen folgen, die nur Leerzeichen (' ') enthalten, generieren einen Fehler. Die Anzahl der Dezimalstellen hängt von der Spaltendefinition ab. Beispielsweise weist eine Spalte, die als **datetime2** (2) definiert ist, zwei Dezimalstellen auf.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in den datetime2-Datentyp|  
|-------------------|-----------------------|-------------------------------------|  
|Zeichenfolgenliterale im **DateTime** -Format|"yyyy-mm-dd hh: mm: SS [. fff]"<br /><br />Beispiel: "2007-05-08 12:35:29.123"|Sekundenbruchteile sind optional und werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|String-Literale im **smalldatetime** -Format|"yyyy-mm-dd hh: mm"<br /><br />Beispiel: "2007-05-08 12"|Optionale Sekunden und übrige Bruch Ziffern werden auf 0 festgelegt, wenn der Wert eingefügt wird.|  
|Zeichenfolgenliteralformat ****|"yyyy-mm-dd"<br /><br />Beispiel: "2007-05-08"|Uhrzeitwerte (Stunden, Minuten, Sekunden und Bruchzahlen) werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale "2007-05-08" als "2007-05-08 12:00:00.0000000" eingefügt.|  
|Zeichenfolgenliterale im **datetime2**|"yyyy-mm-dd hh: mm: SS: fffffff"<br /><br />Beispiel: "2007-05-08 12:35:29.1234567"|Wenn die Datenquelle Daten-und Zeit Komponenten enthält, die kleiner oder gleich dem in **datetime2**(*n*) angegebenen Wert sind, werden die Daten eingefügt. Andernfalls wird ein Fehler generiert.|  
  
### <a name="DateFormats"></a>DateTime-Formate  
Dwloader unterstützt die folgenden Datenformate für die Eingabedaten, die in SQL Server PDW geladen werden. Weitere Details werden nach der Tabelle aufgelistet.  
  
|datetime|smalldatetime|date|datetime2|datetimeoffset|  
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
  
-   Zum Trennen der Werte für Monat, Tag und Jahr können Sie "-", "/" oder "" verwenden. '. Der Einfachheit halber wird in die Tabelle nur das Trennzeichen „-“ verwendet.  
  
-   Wenn Sie den Monat als Text angeben möchten, verwenden Sie drei oder mehr Zeichen. Monate mit einem oder zwei Zeichen werden als Zahl interpretiert.  
  
-   Verwenden Sie zum Trennen von Zeitwerten das Symbol ":".  
  
-   Buchstaben in eckigen Klammern sind optional.  
  
-   Die Buchstaben „tt“ kennzeichnen [AM|PM|am|pm]. AM ist die Standardeinstellung. Wenn „tt“ angegeben ist, muss der Wert für die Stunde (hh) in einem Bereich von 0 bis 12 liegen.  
  
-   Die Buchstaben „zzz“ kennzeichnen den Offsetwert für die Zeitzone für die aktuelle Zeitzone des Systems im Format {+|-}HH:ss].  
  
## <a name="InsertNumerictypes"></a>Einfügen von Literalen in numerische Typen  
Die folgenden Tabellen definieren das Standardformat und die Konvertierungsregeln für das Laden eines Literalwerts in eine SQL Server PDW Spalte, die einen numerischen Typ verwendet.  
  
### <a name="bit-data-type"></a>Bit-Datentyp  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **Bit**definiert. Eine leere Zeichenfolge ("") oder eine Zeichenfolge, die nur Leerzeichen ("") enthält, wird in 0 konvertiert.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in den Bit-Datentyp|  
|-------------------|-----------------------|-------------------------------|  
|Zeichenfolgenliteralformat ****|"ffffffffff"<br /><br />Beispiel: "1" oder "321"|Ein ganzzahliger Wert, der als Zeichenfolgenliterals formatiert ist, darf keinen Beispielsweise generiert der Wert "-123" einen Fehler.<br /><br />Ein Wert, der größer als 1 ist, wird in 1 konvertiert. Beispielsweise wird der Wert "123" in 1 konvertiert.|  
|String-Literale|' True ' oder ' false '<br /><br />Beispiel: ' true '|Der Wert ' true ' wird in 1 konvertiert. der Wert "false" wird in 0 konvertiert.|  
|Ganzzahliges Format|fffffffn<br /><br />Beispiel: 1 oder 321|Ein Wert, der größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Die Werte 123 und-123 werden z. b. in 1 konvertiert.|  
|Decimal-Literale|fffnn. fffn<br /><br />Beispiel: 1234,5678|Ein Wert, der größer als 1 oder kleiner als 0 ist, wird in 1 konvertiert. Die Werte 123,45 und-123,45 werden z. b. in 1 konvertiert.|  
  
### <a name="decimal-data-type"></a>Decimal-Datentyp  
In der folgenden Tabelle sind die Regeln zum Laden von Literalwerten in eine Spalte vom Typ " **Decimal** (*p, s*)" definiert. Daten Konvertierungsregeln sind identisch mit denen für SQL Server. Weitere Informationen finden Sie unter [Datentyp Konvertierung (Datenbank-Engine)](https://go.microsoft.com/fwlink/?LinkId=202128) auf MSDN.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|  
|-------------------|-----------------------|  
|Ganzzahliges Format|321312313123|  
|Decimal-Literale|123344,34455|  
  
### <a name="float-and-real-data-types"></a>float-und Real-Datentypen  
In der folgenden Tabelle werden Regeln zum Laden von Literalwerten in eine Spalte vom Typ **float** oder **Real**definiert. Daten Konvertierungsregeln sind identisch mit denen für SQL Server. Weitere Informationen finden Sie unter [Datentyp Konvertierung (Datenbank-Engine)](../t-sql/data-types/data-type-conversion-database-engine.md) auf MSDN.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|  
|-------------------|-----------------------|  
|Ganzzahliges Format|321312313123|  
|Decimal-Literale|123344,34455|  
|Gleit Komma Literale|3.12323 e + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int, bigint, tinyint, smallint-Datentypen  
In der folgenden Tabelle sind die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **int**, **bigint**, **tinyint**oder **smallint**definiert. Die Datenquelle darf nicht den für den angegebenen Datentyp zulässigen Bereich überschreiten. Beispielsweise liegt der Bereich für **tinyint** zwischen 0 und 255, und der Bereich für **int** ist-2.147.483.648 bis 2.147.483.647.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertieren in ganzzahlige Datentypen|  
|-------------------|-----------------------|------------------------------------|  
|Ganzzahliges Format|321312313123||  
|Decimal-Literale|123344,34455|Die Werte auf der rechten Seite des Dezimal Trennzeichens werden abgeschnitten.|  
  
### <a name="money-and-smallmoney-data-types"></a>Money-und smallmoney-Datentypen  
Money-Literalwerte werden als Zeichenfolge von Zahlen mit einem optionalen Dezimaltrennzeichen und einem optionalen Währungssymbol als Präfix dargestellt. Die Datenquelle darf nicht den für den angegebenen Datentyp zulässigen Bereich überschreiten. Der Bereich für **smallmoney** beträgt z. b.-214.748,3648 bis 214.748,3647 und der Bereich für **Money** den Wert-922.337.203.685.477,5808 bis 922.337.203.685.477,5807. In der folgenden Tabelle sind die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **Money** oder **smallmoney**definiert.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertierung in Money-oder smallmoney-Datentyp|  
|-------------------|-----------------------|-----------------------------------------------|  
|Ganzzahliges Format|321312|Fehlende Ziffern nach dem Dezimaltrennzeichen werden auf 0 festgelegt, wenn der Wert eingefügt wird. Beispielsweise wird das Literale 12345 als 12345,0000 eingefügt.|  
|Decimal-Literale|123344,34455|Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet. Beispielsweise wird der Wert 123344,34455 als 123344,3446 eingefügt.|  
|Money-Literale|$123456,7890|Das Währungssymbol wird nicht mit dem Wert eingefügt.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 4 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet.|  
  
## <a name="InsertStringTypes"></a>Einfügen von Literalen in Zeichen folgen Typen  
Die folgenden Tabellen definieren das Standardformat und die Konvertierungsregeln für das Laden eines Literalwerts in eine SQL Server PDW Spalte, die einen Zeichen Folgentyp verwendet.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>Datentypen char, varchar, nchar und nvarchar  
In der folgenden Tabelle werden das Standardformat und die Regeln zum Laden von Literalwerten in eine Spalte vom Typ **char**, **varchar**, **NCHAR** und **nvarchar**definiert. Die Datenquellen Länge darf die für den Datentyp angegebene Größe nicht überschreiten. Wenn die Datenquellen Länge kleiner als die Größe des Datentyps **char** oder **NCHAR** ist, werden die Daten rechts mit Leerzeichen aufgefüllt, um die Größe des Datentyps zu erreichen.  
  
|Eingabe Datentyp|Beispiele für Eingabedaten|Konvertieren in Zeichen Datentypen|  
|---------------|-------------------|----------------------------------|  
|String-Literale|Format: ' Zeichenfolge '<br /><br />Beispiel: "ABC"| Nicht verfügbar |  
|Unicode String-Literale|Format: n ' Zeichenfolge '<br /><br />Beispiel: n ' abc '| Nicht verfügbar |  
|Ganzzahliges Format|Format: ffffffffffn<br /><br />Beispiel: 321312313123| Nicht verfügbar |  
|Decimal-Literale|Format: FFFFFF. fffffff<br /><br />Beispiel: 12344,34455| Nicht verfügbar |  
|Money-Literale|Format: $FFFFFF. fffnn<br /><br />Beispiel: $123456,99|Das optionale Währungssymbol wird nicht mit dem Wert eingefügt. Fügen Sie den Wert als Zeichenfolgenliterale ein, um das Währungssymbol einzufügen. Dies entspricht dem Format des Lade Moduls, das jedes Literale als zeichenfolgenliteralvorgang behandelt.<br /><br />Kommas sind nicht zulässig.<br /><br />Wenn die Anzahl der Ziffern nach dem Dezimaltrennzeichen 2 überschreitet, wird der Wert auf den nächstgelegenen Wert aufgerundet. Beispielsweise wird der Wert 123,946789 als 123,95 eingefügt.<br /><br />Nur der Standardstil 0 (keine Kommas und 2 Ziffern nach dem Dezimaltrennzeichen) ist zulässig, wenn die Convert-Funktion verwendet wird, um Geld Literale einzufügen.|  
  
### <a name="general-remarks"></a>Allgemeine Hinweise  
**"dwloader** führt dieselben impliziten Konvertierungen aus, die von SMP SQL Server durchführt, unterstützt jedoch nicht alle impliziten Konvertierungen, die von SMP SQL Server unterstützt werden.  
 
<!-- MISSING LINKS 
## See Also  
[Grant Permissions to Load Data &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-load-data-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  

-->
  
