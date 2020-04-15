---
title: SQL-Datentypen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3cc91213533aa39f30be1bc838cc014c20e70884
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305004"
---
# <a name="sql-data-types"></a>SQL-Datentypen
Jedes DBMS definiert seine eigenen SQL-Typen. Jeder ODBC-Treiber macht nur die SQL-Datentypen verfügbar, die vom zugeordneten DBMS definiert werden. Informationen darüber, wie ein Treiber DBMS SQL-Typen den ODBC-definierten SQL-Typbezeichnern zuordnet und wie ein Treiber DBMS SQL-Typen seinen eigenen treiberspezifischen SQL-Typbezeichnern zuordnet, wird durch einen Aufruf von **SQLGetTypeInfo**zurückgegeben. Ein Treiber gibt auch die SQL-Datentypen zurück, wenn die Datentypen von Spalten und Parametern durch Aufrufe von **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLProcedureColumns**und **SQLSpecialColumns**beschrieben werden.  
  
> [!NOTE]  
>  Die SQL-Datentypen sind in den Feldern SQL_DESC_ CONCISE_TYPE, SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE der Implementierungsdeskriptoren enthalten. Merkmale der SQL-Datentypen sind in den Feldern SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH und SQL_DESC_OCTET_LENGTH der Implementierungsdeskriptoren enthalten. Weitere Informationen finden Sie weiter unten in diesem Anhang unter [Datentypbezeichner und Deskriptoren.](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
 Ein gegebener Treiber und eine datenquelle unterstützen nicht unbedingt alle SQL-Datentypen, die in diesem Anhang definiert sind. Die Unterstützung eines Treibers für SQL-Datentypen hängt von der Sql-92-Ebene ab, die der Treiber erfüllt. Um die vom Treiber unterstützte Sql-92-Grammatikebene zu bestimmen, ruft eine Anwendung **SQLGetInfo** mit dem SQL_SQL_CONFORMANCE-Informationstyp auf. Darüber hinaus können ein bestimmter Treiber und eine Datenquelle zusätzliche, treiberspezifische SQL-Datentypen unterstützen. Um zu bestimmen, welche Datentypen ein Treiber unterstützt, ruft eine Anwendung **SQLGetTypeInfo**auf. Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers. Informationen zu den Datentypen in einer bestimmten Datenquelle finden Sie in der Dokumentation zu dieser Datenquelle.  
  
> [!IMPORTANT]  
>  Die Tabellen in diesem Anhang sind nur Richtlinien und zeigen in der Regel verwendete Namen, Bereiche und Grenzwerte von SQL-Datentypen an. Eine bestimmte Datenquelle unterstützt möglicherweise nur einige der aufgeführten Datentypen, und die Merkmale der unterstützten Datentypen können von den aufgeführten abweichen.  
  
 In der folgenden Tabelle sind gültige SQL-Typbezeichner für alle SQL-Datentypen aufgeführt. In der Tabelle sind auch der Name und die Beschreibung des entsprechenden Datentyps aus SQL-92 aufgeführt (falls vorhanden).  
  
|SQL-Typbezeichner[1]|Typische SQL-Daten<br /><br /> Typ[2]|Typische Typbeschreibung|  
|------------------------------|------------------------------------|------------------------------|  
|SQL_CHAR|CHAR(*n*)|Zeichenkette der festen Zeichenfolgenlänge *n*.|  
|SQL_VARCHAR|VARCHAR(*n*)|Zeichenkette variabler Länge mit einer maximalen Zeichenfolgenlänge *n*.|  
|SQL_LONGVARCHAR|LONG VARCHAR|Zeichendaten mit variabler Länge. Die maximale Länge ist datenquellenabhängig. [9]|  
|SQL_WCHAR|WCHAR(*n*)|Unicode-Zeichenzeichenfolge der festen Zeichenfolgenlänge *n*|  
|SQL_WVARCHAR|VARWCHAR(*n*)|Unicode-Zeichenfolge mit variabler Länge mit einer maximalen Zeichenfolgenlänge *n*|  
|SQL_WLONGVARCHAR|LONGWVARCHAR|Daten mit Unicode-Zeichen von variabler Länge. Maximale Länge ist datenquellenabhängig|  
|SQL_DECIMAL|DECIMAL(*p*,*s*)|Signierter, exakter, numerischer Wert mit einer Genauigkeit von mindestens *p* und Scale *s.* (Die maximale Genauigkeit ist treiberdefiniert.) (1 <= *p* <= 15; *s* <= *p*). [4]|  
|SQL_NUMERIC|NUMERIC(*p*,*s*)|Signierter, exakter, numerischer Wert mit einer Genauigkeit *p* und Maßstab *s* (1 <= *p* <= 15; *s* <= *p*). [4]|  
|SQL_SMALLINT|SMALLINT|Exakter numerischer Wert mit Genauigkeit 5 und Skala 0 (signiert: -32.768 <= *n* <= 32.767, unsigniert: 0 <= *n* <= 65.535)[3].|  
|SQL_INTEGER|INTEGER|Exakter numerischer Wert mit Genauigkeit 10 und Skala 0 (signiert: -2[31] <= *n* <= 2[31] - 1, unsigniert: 0 <= *n* <= 2[32] - 1)[3].|  
|SQL_REAL|real|Signierter, ungefährer, numerischer Wert mit einer binären Genauigkeit 24 (Null- oder Absolutwert 10[-38] bis 10[38]).|  
|SQL_FLOAT|FLOAT(*p*)|Signierter, ungefährer, numerischer Wert mit einer binären Genauigkeit von mindestens *p*. (Die maximale Genauigkeit ist treiberdefiniert.) [5]|  
|SQL_DOUBLE|DOUBLE PRECISION|Signierter, ungefährer, numerischer Wert mit einer binären Genauigkeit 53 (Null- oder Absolutwert 10[-308] bis 10[308]).|  
|SQL_BIT|BIT|Einzelne Bit-Binärdaten. [8]|  
|SQL_TINYINT|TINYINT|Exakter numerischer Wert mit Genauigkeit 3 und Skala 0 (signiert: -128 <= *n* <= 127, unsigniert: 0 <= *n* <= 255)[3].|  
|SQL_BIGINT|bigint|Exakter numerischer Wert mit Genauigkeit 19 (falls signiert) oder 20 (falls nicht signiert) und Skala 0 (signiert: -2[63] <= *n* <= 2[63] - 1, nicht signiert: 0 <= *n* <= 2[64] - 1)[3],[9].|  
|SQL_BINARY|BINARY(*n*)|Binäre Daten mit fester Länge *n*. [9]|  
|SQL_VARBINARY|VARBINARY(*n*)|Binärdaten mit variabler Länge von maximaler Länge *n*. Das Maximum wird vom Benutzer festgelegt. [9]|  
|SQL_LONGVARBINARY|LONG VARBINARY|Binäre Daten mit variabler Länge. Die maximale Länge ist datenquellenabhängig. [9]|  
|SQL_TYPE_DATE[6]|DATE|Jahres-, Monats- und Tagesfelder, die den Regeln des Gregorianischen Kalenders entsprechen. (Siehe [Einschränkungen des Gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md), weiter unten in diesem Anhang.)|  
|SQL_TYPE_TIME[6]|ZEIT(*p*)|Stunden-, Minuten- und Sekundenfelder mit gültigen Werten für Stunden von 00 bis 23, gültigen Werten für Minuten von 00 bis 59 und gültigen Werten für Sekunden von 00 bis 61. Präzision *p* gibt die Sekundengenauigkeit an.|  
|SQL_TYPE_TIMESTAMP[6]|TIMESTAMP(*p*)|Jahr, Monat, Tag, Stunde, Minute und zweites Feld mit gültigen Werten, wie für die Datentypen DATE und TIME definiert.|  
|SQL_TYPE_UTCDATETIME|Utcdatetime|Die Felder Jahr, Monat, Tag, Stunde, Minute, Sekunde, utchour und utcminute. Die Felder utchour und utcminute haben eine Genauigkeit von 1/10 Mikrosekunden.|  
|SQL_TYPE_UTCTIME|UTCTIME|Stunden-, Minuten-, Sekunden-, utchour- und utcminute-Felder. Die Felder utchour und utcminute haben eine Genauigkeit von 1/10 Mikrosekunden.|  
|SQL_INTERVAL_MONTH[7]|INTERVAL MONAT(*p*)|Anzahl der Monate zwischen zwei Datumsangaben; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_YEAR[7]|INTERVAL JAHR(*p*)|Anzahl der Jahre zwischen zwei Daten; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_YEAR_TO_MONTH[7]|INTERVAL JAHR(*p*) ZU MONAT|Anzahl der Jahre und Monate zwischen zwei Daten; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_DAY[7]|INTERVAL DAY(*p*)|Anzahl der Tage zwischen zwei Datumsangaben; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_HOUR[7]|INTERVAL HOUR(*p*)|Anzahl der Stunden zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_MINUTE[7]|INTERVAL MINUTE(*p*)|Anzahl der Minuten zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_SECOND[7]|INTERVAL SECOND(*p*,*q*)|Anzahl der Sekunden zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervall-Führende-Präzision und *q* ist die Intervallsekunden-Präzision.|  
|SQL_INTERVAL_DAY_TO_HOUR[7]|INTERVAL DAY(*p*) TO HOUR|Anzahl der Tage/Stunden zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_DAY_TO_MINUTE[7]|INTERVAL DAY(*p*) TO MINUTE|Anzahl der Tage/Stunden/Minuten zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_DAY_TO_SECOND[7]|INTERVAL DAY(*p*) ZU SECOND(*q*)|Anzahl der Tage/Stunden/Minuten/Sekunden zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervall-Führende-Präzision und *q* ist die Intervallsekunden-Präzision.|  
|SQL_INTERVAL_HOUR_TO_MINUTE[7]|INTERVAL HOUR(*p*) TO MINUTE|Anzahl der Stunden/Minuten zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervallführungsgenauigkeit.|  
|SQL_INTERVAL_HOUR_TO_SECOND[7]|INTERVAL HOUR(*p*) ZU SECOND(*q*)|Anzahl der Stunden/Minuten/Sekunden zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervall-Führende-Präzision und *q* ist die Intervallsekunden-Präzision.|  
|SQL_INTERVAL_MINUTE_TO_SECOND[7]|INTERVAL MINUTE(*p*) ZU SECOND(*q*)|Anzahl der Minuten/Sekunden zwischen zwei Datums-/Uhrzeiten; *p* ist die Intervall-Führende-Präzision und *q* ist die Intervallsekunden-Präzision.|  
|SQL_GUID|GUID|GUID der festen Länge.|  
  
 [1] Dies ist der Wert, der in der Spalte DATA_TYPE durch einen Aufruf von **SQLGetTypeInfo**zurückgegeben wird.  
  
 [2] Dies ist der Wert, der in der Spalte NAME und CREATE PARAMS durch einen Aufruf von **SQLGetTypeInfo**zurückgegeben wird. Die Spalte NAME gibt die Bezeichnung zurück, z. B. CHAR- während die Spalte CREATE PARAMS eine durch Kommas getrennte Liste von Erstellungsparametern wie Genauigkeit, Maßstab und Länge zurückgibt.  
  
 [3] Eine Anwendung verwendet **SQLGetTypeInfo** oder **SQLColAttribute,** um zu bestimmen, ob ein bestimmter Datentyp oder eine bestimmte Spalte in einem Resultset nicht signiert ist.  
  
 [4] SQL_DECIMAL und SQL_NUMERIC Datentypen unterscheiden sich nur in ihrer Genauigkeit. Die Genauigkeit eines DECIMAL(*p*,*s*) ist eine implementierungsdefinierte Dezimalgenauigkeit, die nicht weniger als *p*ist, während die Genauigkeit eines NUMERIC(*p*,*s*) genau gleich *p*ist.  
  
 [5] Je nach Implementierung kann die Genauigkeit von SQL_FLOAT entweder 24 oder 53 betragen: Wenn er 24 jahre alt ist, entspricht der SQL_FLOAT Datentyp dem SQL_REAL; Wenn er 53 Jahre alt ist, entspricht der SQL_FLOAT Datentyp dem SQL_DOUBLE.  
  
 [6] In ODBC *3.x*sind die SQL-Datentypen Datum, Uhrzeit und Zeitstempel SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP. in ODBC *2.x*sind die Datentypen SQL_DATE, SQL_TIME und SQL_TIMESTAMP.  
  
 [7] Weitere Informationen zu den INTERVALL-SQL-Datentypen finden Sie im Abschnitt [Intervalldatentypen](../../../odbc/reference/appendixes/interval-data-types.md) weiter unten in diesem Anhang.  
  
 [8] Der SQL_BIT Datentyp hat andere Merkmale als der BIT-Typ in SQL-92.  
  
 [9] Dieser Datentyp hat keinen entsprechenden Datentyp in SQL-92.  
  
 Dieser Abschnitt enthält das folgende Beispiel.  
  
-   [Example SQLGetTypeInfo Result Set (Beispielergebnis des SQLGetTypeInfo-Resultsets)](../../../odbc/reference/appendixes/example-sqlgettypeinfo-result-set.md)
