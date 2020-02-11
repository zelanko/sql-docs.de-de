---
title: SQL-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC]
- SQL data types [ODBC], about SQL data types
- data types [ODBC], SQL data types
ms.assetid: 1b22f985-f5e4-4779-87eb-e43329a442b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4be0e017988670d740067011f775f8477037aa18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057032"
---
# <a name="sql-data-types"></a>SQL-Datentypen
Jedes DBMS definiert seine eigenen SQL-Typen. Jeder ODBC-Treiber macht nur die SQL-Datentypen verfügbar, die das zugehörige DBMS definiert. Informationen dazu, wie ein Treiber DBMS-SQL-Typen den ODBC-definierten SQL-typbezeichgern zuordnet und wie ein Treiber DBMS-SQL-Typen eigenen treiberspezifischen SQL-typbezeichatoren zuordnet, wird durch einen **SQLGetTypeInfo-Befehl**zurückgegeben. Ein Treiber gibt auch die SQL-Datentypen zurück, wenn die Datentypen von Spalten und Parametern durch Aufrufe von **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLDescribeParam**, **sqlprocedurecolrens**und **SQLSpecialColumns**beschrieben werden.  
  
> [!NOTE]  
>  Die SQL-Datentypen sind in den SQL_DESC_ Felder CONCISE_TYPE, SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE der Implementierungs Deskriptoren enthalten. Die Eigenschaften der SQL-Datentypen sind in den Feldern SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH und SQL_DESC_OCTET_LENGTH der Implementierungs Deskriptoren enthalten. Weitere Informationen finden Sie unter [Datentyp Bezeichner und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) weiter unten in diesem Anhang.  
  
 Ein bestimmter Treiber und eine Datenquelle unterstützen nicht notwendigerweise alle SQL-Datentypen, die in diesem Anhang definiert sind. Die Unterstützung eines Treibers für SQL-Datentypen hängt von der Ebene von SQL-92 ab, der der Treiber entspricht. Um die vom Treiber unterstützte Ebene der SQL-92-Grammatik zu ermitteln, ruft eine Anwendung **SQLGetInfo** mit dem SQL_SQL_CONFORMANCE Informationstyp auf. Darüber hinaus können ein bestimmter Treiber und eine Datenquelle zusätzliche, Treiber spezifische SQL-Datentypen unterstützen. Um zu ermitteln, welche Datentypen ein Treiber unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers. Informationen zu den Datentypen in einer bestimmten Datenquelle finden Sie in der Dokumentation für diese Datenquelle.  
  
> [!IMPORTANT]  
>  Die Tabellen in diesem Anhang sind nur Richtlinien und zeigen in der Regel verwendete Namen, Bereiche und Grenzwerte für SQL-Datentypen an. Eine bestimmte Datenquelle unterstützt möglicherweise nur einige der aufgelisteten Datentypen, und die Merkmale der unterstützten Datentypen können sich von den aufgelisteten Datentypen unterscheiden.  
  
 In der folgenden Tabelle sind gültige SQL-Typbezeichner für alle SQL-Datentypen aufgeführt. In der Tabelle sind außerdem der Name und die Beschreibung des entsprechenden Datentyps von SQL-92 (sofern vorhanden) aufgeführt.  
  
|SQL-Typbezeichner [1]|Typische SQL-Daten<br /><br /> Typ [2]|Typische Typbeschreibung|  
|------------------------------|------------------------------------|------------------------------|  
|SQL_CHAR|CHAR (*n*)|Zeichenfolge mit fester Zeichen folgen Länge *n*.|  
|SQL_VARCHAR|Varchar (*n*)|Zeichenfolge variabler Länge mit einer maximalen Zeichen folgen Länge *n*.|  
|SQL_LONGVARCHAR|LONG VARCHAR|Zeichendaten mit variabler Länge. Die maximale Länge ist Datenquellen abhängig. 21.00|  
|SQL_WCHAR|WCHAR (*n*)|Unicode-Zeichenfolge mit fester Zeichen folgen Länge *n*|  
|SQL_WVARCHAR|VarWChar (*n*)|Unicode-Zeichenfolge variabler Länge mit einer maximalen Zeichen folgen Länge *n*|  
|SQL_WLONGVARCHAR|Longwvarchar|Unicode-Zeichendaten variabler Länge. Die maximale Länge ist Datenquellen abhängig.|  
|SQL_DECIMAL|Dezimalzahl (*p*,*s*)|Signierter, genauer numerischer Wert mit einer Genauigkeit von mindestens *p* und Skalierung *s.* (Die maximale Genauigkeit ist Treiber definiert.) (1 <= *p* <= 15; *s* <= *p*). 0:|  
|SQL_NUMERIC|Numerisch (*p*,*s*)|Signierter, genauer numerischer Wert mit einer Genauigkeit von *p* und Skalierung *s* (1 <= *p* <= 15; *s* <= *p*). 0:|  
|SQL_SMALLINT|SMALLINT|Genauer numerischer Wert mit einer Genauigkeit von 5 und Dezimalstelle 0 (signiert:-32.768 <= *n* <= 32.767, unsigned: 0 <= *n* <= 65535) [3].|  
|SQL_INTEGER|INTEGER|Genauer numerischer Wert mit einer Genauigkeit von 10 und Dezimalstelle 0 (signiert:-2 [31] <= *n* <= 2 [31]-1, ohne Vorzeichen: 0 <= *n* <= 2 [32]-1) [3].|  
|SQL_REAL|real|Ein numerischer Wert mit Vorzeichen und einer binären Genauigkeit von 24 (0 oder absoluter Wert 10 [-38] bis 10 [38]).|  
|SQL_FLOAT|FLOAT (*p*)|Ein numerischer Wert mit Vorzeichen und einer binären Genauigkeit von mindestens *p*. (Die maximale Genauigkeit ist Treiber definiert.) 5|  
|SQL_DOUBLE|DOUBLE PRECISION|Signierter, näherer numerischer Wert mit der binären Genauigkeit 53 (0 oder absoluter Wert 10 [-308] bis 10 [308]).|  
|SQL_BIT|BIT|Einzelbit-Binärdaten. 88|  
|SQL_TINYINT|TINYINT|Genauer numerischer Wert mit einer Genauigkeit von 3 und Dezimalstelle 0 (signiert:-128 <= *n* <= 127, unsigned: 0 <= *n* <= 255) [3].|  
|SQL_BIGINT|BIGINT|Genauer numerischer Wert mit einer Genauigkeit von 19 (bei Vorzeichen) oder 20 (wenn nicht signiert) und Skala 0 (signiert:-2 [63] <= *n* <= 2 [63]-1, unsigniert: 0 <= *n* <= 2 [64]-1) [3], [9].|  
|SQL_BINARY|Binary (*n*)|Binärdaten mit fester Länge *n*. 21.00|  
|SQL_VARBINARY|Varbinary (*n*)|Binäre Daten variabler Länge mit einer maximalen Länge von *n*. Das Maximum wird vom Benutzer festgelegt. 21.00|  
|SQL_LONGVARBINARY|Long varbinary|Binäre Daten mit variabler Länge. Die maximale Länge ist Datenquellen abhängig. 21.00|  
|SQL_TYPE_DATE [6]|DATE|Felder "Jahr", "Monat" und "Tag", die den Regeln des gregorianischen Kalenders entsprechen. (Weitere Informationen finden Sie unter [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)weiter unten in diesem Anhang.)|  
|SQL_TYPE_TIME [6]|Zeit (*p*)|Die Felder "Hour", "Minute" und "Second" mit gültigen Werten für Stunden von 00 bis 23, gültige Werte für Minuten von 00 bis 59 und gültige Werte für Sekunden von 00 bis 61. Genauigkeit *p* gibt die Genauigkeit der Sekunden an.|  
|SQL_TYPE_TIMESTAMP [6]|Zeitstempel (*p*)|Felder für Jahr, Monat, Tag, Stunde, Minute und Sekunde mit gültigen Werten, die für die Datums-und Uhrzeit Datentypen definiert sind.|  
|SQL_TYPE_UTCDATETIME|UTCDATETIME|Felder für Jahr, Monat, Tag, Stunde, Minute, Sekunde, utchour und utcminute. Die Felder "utchour" und "utcminute" haben eine Genauigkeit von 1/10 Mikrosekunden.|  
|SQL_TYPE_UTCTIME|UtcTime|Die Felder Hour, Minute, Second, utchour und utcminute. Die Felder "utchour" und "utcminute" haben eine Genauigkeit von 1/10 Mikrosekunden.|  
|SQL_INTERVAL_MONTH [7]|Intervall Monat (*p*)|Anzahl von Monaten zwischen zwei Datumsangaben, *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_YEAR [7]|Intervall Jahr (*p*)|Anzahl von Jahren zwischen zwei Datumsangaben, *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_YEAR_TO_MONTH [7]|Intervall Jahr (*p*) bis Monat|Anzahl von Jahren und Monaten zwischen zwei Datumsangaben *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_DAY [7]|Intervalltag (*p*)|Anzahl von Tagen zwischen zwei Datumsangaben, *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_HOUR [7]|Intervall Stunde (*p*)|Anzahl von Stunden zwischen zwei Datums-/Uhrzeitangaben; *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_MINUTE [7]|Intervall Minute (*p*)|Anzahl von Minuten zwischen zwei Datums-/Uhrzeitangaben; *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_SECOND [7]|Intervall Sekunde (*p*,*q*)|Anzahl von Sekunden zwischen zwei Datums-/Uhrzeitangaben; *p* ist die Genauigkeit der Intervall Spitze, und *q* ist die Genauigkeit in Sekundenbruchteilen.|  
|SQL_INTERVAL_DAY_TO_HOUR [7]|Intervalltag (*p*) bis Stunde|Anzahl der Tage/Stunden zwischen zwei Datums-/Uhrzeitangaben; *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_DAY_TO_MINUTE [7]|Intervalltag (*p*) bis Minute|Anzahl der Tage/Stunden/Minuten zwischen zwei Datums-/Uhrzeitangaben; *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_DAY_TO_SECOND [7]|Intervalltag (*p*) bis Sekunde (*q*)|Anzahl der Tage/Stunden/Minuten/Sekunden zwischen zwei Datums-/Uhrzeitangaben; *p* ist die Genauigkeit der Intervall Spitze, und *q* ist die Genauigkeit in Sekundenbruchteilen.|  
|SQL_INTERVAL_HOUR_TO_MINUTE [7]|Intervall Stunde (*p*) bis Minute|Anzahl von Stunden/Minuten zwischen zwei Datums-/Uhrzeitangaben; *p* ist die für das Intervall führende Genauigkeit.|  
|SQL_INTERVAL_HOUR_TO_SECOND [7]|Intervall Stunde (*p*) bis Sekunde (*q*)|Anzahl von Stunden/Minuten/Sekunden zwischen zwei Datums-/Uhrzeitangaben; *p* ist die Genauigkeit der Intervall Spitze, und *q* ist die Genauigkeit in Sekundenbruchteilen.|  
|SQL_INTERVAL_MINUTE_TO_SECOND [7]|Intervall Minute (*p*) bis Sekunde (*q*)|Anzahl der Minuten/Sekunden zwischen zwei Datums-/Uhrzeitangaben; *p* ist die Genauigkeit der Intervall Spitze, und *q* ist die Genauigkeit in Sekundenbruchteilen.|  
|SQL_GUID|GUID|GUID mit fester Länge.|  
  
 [1] Dies ist der Wert, der in der DATA_TYPE-Spalte durch einen **SQLGetTypeInfo-Befehl**zurückgegeben wird.  
  
 [2] Dies ist der Wert, der in der Spalte "Name" und "Create parameams" durch einen **SQLGetTypeInfo-Befehl**zurückgegeben wird. In der Spalte Name wird die Bezeichnung (z. b. Char) zurückgegeben, während die Spalte Create parameams eine durch Trennzeichen getrennte Liste von Erstellungs Parametern (z. b. Genauigkeit, Skala und Länge) zurückgibt.  
  
 [3] eine Anwendung verwendet **SQLGetTypeInfo** oder **SQLColAttribute** , um zu bestimmen, ob ein bestimmter Datentyp oder eine bestimmte Spalte in einem Resultset nicht signiert ist.  
  
 [4] SQL_DECIMAL-und SQL_NUMERIC-Datentypen unterscheiden sich nur hinsichtlich ihrer Genauigkeit. Die Genauigkeit einer Dezimalzahl (*p*,*s*) ist eine Implementierungs definierte Dezimal Genauigkeit, die nicht kleiner als *p*ist, wohingegen die Genauigkeit eines numerischen Werts (*p*,*s*) exakt gleich *p*ist.  
  
 [5] abhängig von der Implementierung kann die Genauigkeit von SQL_FLOAT entweder 24 oder 53 sein: Wenn es 24 ist, ist der SQL_FLOAT Datentyp identisch mit SQL_REAL. Wenn der Wert 53 ist, ist der SQL_FLOAT-Datentyp mit SQL_DOUBLE identisch.  
  
 [6] in ODBC *3. x*sind die SQL Date-, Time-und Zeitstempel-Datentypen SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP. in ODBC *2. x*sind die Datentypen SQL_DATE, SQL_TIME und SQL_TIMESTAMP.  
  
 [7] Weitere Informationen zu den Intervall-SQL-Datentypen finden Sie im Abschnitt [interval-Datentypen](../../../odbc/reference/appendixes/interval-data-types.md) weiter unten in diesem Anhang.  
  
 [8] der SQL_BIT Datentyp hat unterschiedliche Merkmale als der Bit-Typ in SQL-92.  
  
 [9] dieser Datentyp verfügt über keinen entsprechenden Datentyp in SQL-92.  
  
 Dieser Abschnitt enthält das folgende Beispiel.  
  
-   [SQLGetTypeInfo-Resultset – Beispiel](../../../odbc/reference/appendixes/example-sqlgettypeinfo-result-set.md)
