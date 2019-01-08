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
manager: craigg
ms.openlocfilehash: 623ac38791eebc6db84380dfadd499651af938af
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52507505"
---
# <a name="sql-data-types"></a>SQL-Datentypen
Jede DBMS definiert eine eigene SQL-Datentypen. Jede ODBC-Treiber stellt nur die SQL-Datentypen, die das zugeordnete DBMS definiert. Informationen dazu, wie ein Treiber zuordnet DBMS SQL-Typen zu den SQL ODBC-definierten Typ-IDs und wie ein Treiber einen eigenen Treiber-spezifische SQL-Typenbezeichner DBMS-SQL-Typen zugeordnet, wird durch einen Aufruf zurückgegeben **SQLGetTypeInfo**. Ein Treiber gibt auch die SQL-Datentypen zurück, wenn Sie die Datentypen der Spalten und Parametern, die durch Aufrufe von beschreiben **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLProcedureColumns**, und **SQLSpecialColumns**.  
  
> [!NOTE]  
>  Die SQL-Datentypen sind in den Feldern SQL_DESC_ CONCISE_TYPE, SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE Deskriptor Implementierung enthalten. Eigenschaften der SQL-Datentypen sind in den Feldern SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH und SQL_DESC_OCTET_LENGTH Deskriptor Implementierung enthalten. Weitere Informationen finden Sie unter [-datentypbezeichnungen und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) weiter unten in diesem Anhang.  
  
 Eine bestimmte Treiber und die Datenquelle unterstützen unbedingt nicht alle SQL-Datentypen, die in diesem Anhang definiert sind. Treiberunterstützung für SQL-Datentypen hängt von der Ebene der SQL-92, die der Treiber entspricht. Um zu bestimmen, die Ebene der SQL-92-Grammatik, die vom Treiber unterstützt werden, eine Anwendung ruft **SQLGetInfo** mit dem Typ der SQL_SQL_CONFORMANCE-Informationen. Darüber hinaus kann eine bestimmte Treiber und die Datenquelle zusätzliche, treiberspezifischen SQL-Datentypen unterstützen. Um zu bestimmen, welche Datentypen einen Treiber unterstützt, eine Anwendung ruft **SQLGetTypeInfo**. Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation. Informationen zu den Datentypen in einer bestimmten Datenquelle finden Sie in der Dokumentation für diese Datenquelle.  
  
> [!IMPORTANT]  
>  Die Tabellen in diesem Anhang werden nur Richtlinien und Namen anzeigen, die in der Regel verwendet, Bereiche und Einschränkungen von SQL-Datentypen. Unterstützen einer bestimmten Datenquelle möglicherweise nur einige der aufgeführten Datentypen, und die Merkmale der unterstützten Datentypen aus der Liste unterscheiden können.  
  
 Die folgende Tabelle enthält die gültige SQL-Typ-IDs für alle SQL-Datentypen. Die Tabelle enthält auch den Namen und die Beschreibung des entsprechenden Datentyps von SQL-92 (falls vorhanden).  
  
|SQL-Typ-ID [1]|Typische SQL-Daten<br /><br /> Typ [2]|Typische typbeschreibung|  
|------------------------------|------------------------------------|------------------------------|  
|SQL_CHAR|CHAR (*n*)|Zeichenfolge mit fester Zeichenfolgenlänge *n*.|  
|SQL_VARCHAR|VARCHAR (*n*)|Zeichenfolge mit variabler Länge mit einer maximalen Zeichenfolgenlänge *n*.|  
|SQL_LONGVARCHAR|LONG VARCHAR|Zeichendaten variabler Länge. Maximale Länge ist datenquellenabhängig. [9]|  
|SQL_WCHAR|WCHAR (*n*)|Unicode-Zeichenfolge mit fester Zeichenfolgenlänge *n*|  
|SQL_WVARCHAR|VARWCHAR (*n*)|Unicode-Zeichenfolge variabler Länge mit einer maximalen Zeichenfolgenlänge *n*|  
|SQL_WLONGVARCHAR|LONGWVARCHAR|Unicode-Daten variabler Länge. Maximale Länge ist datenquellenabhängig|  
|SQL_DECIMAL|DECIMAL (*p*,*s*)|Signiert, genauen numerischen Wert mit einer Genauigkeit von mindestens *p* und Skalierung *s.* (Die maximale Genauigkeit treiberdefinierten ist). (1 < = *p* < = 15; *s* <= *p*). [ 4]|  
|SQL_NUMERIC|NUMERISCH (*p*,*s*)|Signiert, genauen numerischen Wert mit einer Genauigkeit *p* und Skalierung *s* (1 < = *p* < = 15; *s* <= *p*). [ 4]|  
|SQL_SMALLINT|SMALLINT|Genauer numerischer Wert mit einer Genauigkeit von 5 und Skalierung von 0 (signiert: -32.768 < = *n* < = 32.767, ohne Vorzeichen:  0 < = *n* < = 65.535) [3].|  
|SQL_INTEGER|INTEGER|Genauer numerischer Wert mit einer Genauigkeit von 10 und Skalierung von 0 (signiert: – 2 [31] < = *n* < = 2 [31] – 1, ohne Vorzeichen:  0 < = *n* < = 2 [32] – 1) [3].|  
|SQL_REAL|real|Numerischer Wert mit einer binären Genauigkeit von 24 mit Vorzeichen (0 oder absoluter Wert von 10 [-38] zu 10[38]).|  
|SQL_FLOAT|"Float" (*p*)|Signiert, numerischer Wert mit einer binären Genauigkeit von mindestens *p*. (Die maximale Genauigkeit treiberdefinierten ist). [5]|  
|SQL_DOUBLE|DOUBLE PRECISION|Numerischer Wert mit einer binären Genauigkeit von 53 mit Vorzeichen (0 oder absoluter Wert von 10 [-308] zu 10[308]).|  
|SQL_BIT|BIT|Einzelnes Bit-Binärdaten. [8]|  
|SQL_TINYINT|TINYINT|Genauer numerischer Wert mit einer Genauigkeit von 3 und Skalierung von 0 (signiert:-128 < = *n* < = 127, ohne Vorzeichen:  0 < = *n* < = 255) [3].|  
|SQL_BIGINT|bigint|Genauer numerischer Wert mit einer Genauigkeit von 19 (falls mit Vorzeichen) oder 20, (falls ohne Vorzeichen) und Skalierung von 0 (signiert: – 2 [63] < = *n* < = 2 [63] – 1, ohne Vorzeichen: 0 < = *n* < = 2 [64] – 1) [3], [9].|  
|SQL_BINARY|BINÄRE (*n*)|Binärdaten fester Länge *n*. [ 9]|  
|SQL_VARBINARY|VARBINARY (*n*)|Binärdaten variabler Länge, maximale Länge *n*. Der Höchstwert wird vom Benutzer festgelegt. [9]|  
|SQL_LONGVARBINARY|LANGE VARBINARY|Binärdaten variabler Länge. Maximale Länge ist datenquellenabhängig. [9]|  
|SQL_TYPE_DATE [6]|DATE|Jahr, Monat und Tag-Felder entsprechen den Regeln des gregorianischen Kalenders. (Finden Sie unter [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)weiter unten in diesem Anhang.)|  
|SQL_TYPE_TIME [6]|Zeit (*p*)|Stunde, Minute und Sekunde Feldern, die gültige Werte für Stunden mit gültigen Werten von 00 bis 23, 00 bis 59 Minuten und gültige Werte für Sekunden von 00 bis 61. Genauigkeit *p* die Genauigkeit angibt.|  
|SQL_TYPE_TIMESTAMP [6]|Zeitstempel (*p*)|Jahr, Monat, Tag, Stunde, Minute und Sekunde Felder mit gültigen Werten für die Datentypen für Datum und Uhrzeit definiert.|  
|SQL_TYPE_UTCDATETIME|UTCDATETIME|Jahr, Monat, Tag, Stunde, Minute, Sekunde, Utchour und Utcminute Felder. Die Felder Utchour und Utcminute haben die Genauigkeit von 1/10 in Mikrosekunden.|  
|SQL_TYPE_UTCTIME|UTCTIME|Felder für Stunde, Minute, Sekunde, Utchour und Utcminute. Die Felder Utchour und Utcminute haben die Genauigkeit von 1/10 in Mikrosekunden...|  
|SQL_INTERVAL_MONTH [7]|Intervall Monat (*p*)|Die Anzahl der Monate zwischen zwei Datumsangaben; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_YEAR [7]|INTERVAL YEAR (*p*)|Die Anzahl der Jahre zwischen zwei Datumsangaben; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_YEAR_TO_MONTH [7]|INTERVAL YEAR (*p*) zum Monat|Die Anzahl von Jahren und Monaten zwischen zwei Datumsangaben, *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_DAY [7]|Intervall-Tag (*p*)|Die Anzahl von Tagen zwischen zwei Datumsangaben; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_HOUR [7]|Intervall Stunde (*p*)|Anzahl der Stunden zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_MINUTE [7]|Intervall MINUTE (*p*)|Anzahl der Minuten zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_SECOND [7]|Intervall zweite (*p*,*q*)|Anzahl der Sekunden zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert und *q* ist die Genauigkeit, Intervall Sekunden.|  
|SQL_INTERVAL_DAY_TO_HOUR [7]|Intervall-Tag (*p*) und Stunde|Anzahl der datenbanktage/-Stunden zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_DAY_TO_MINUTE [7]|Intervall-Tag (*p*) auf MINUTE|Anzahl der Tage/Stunden/Minuten zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_DAY_TO_SECOND [7]|Intervall-Tag (*p*) zweiten (*q*)|Anzahl von Tagen Stunden/Minuten/Sekunden zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert und *q* ist die Genauigkeit, Intervall Sekunden.|  
|SQL_INTERVAL_HOUR_TO_MINUTE [7]|Intervall Stunde (*p*) auf MINUTE|Anzahl der Stunden/Minuten zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert.|  
|SQL_INTERVAL_HOUR_TO_SECOND [7]|Intervall Stunde (*p*) zweiten (*q*)|Anzahl der Stunden/Minuten/Sekunden zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert und *q* ist die Genauigkeit, Intervall Sekunden.|  
|SQL_INTERVAL_MINUTE_TO_SECOND [7]|Intervall MINUTE (*p*) zweiten (*q*)|Anzahl von Minuten/Sekunden zwischen zwei Datumsangaben und Uhrzeiten; *p* ist die Genauigkeit für anführenden Intervallwert und *q* ist die Genauigkeit, Intervall Sekunden.|  
|SQL_GUID|GUID|GUID mit fester Länge.|  
  
 [1] Dies ist der Rückgabewert in der DATA_TYPE-Spalte durch einen Aufruf von **SQLGetTypeInfo**.  
  
 [2] Dies ist der Rückgabewert in der Spalte NAME und erstellen Sie Parameter durch einen Aufruf von **SQLGetTypeInfo**. Die Spalte "NAME" gibt die Bezeichnung – z. B. CHAR-während die erstellen-PARAMS-Spalte eine durch Trennzeichen getrennte Liste von Parametern erstellen, z. B. mit einfacher Genauigkeit, Dezimalstellen und Länge zurückgegeben.  
  
 [3] eine Anwendung verwendet **SQLGetTypeInfo** oder **SQLColAttribute** zu bestimmen, ob ein bestimmter Datentyp oder eine bestimmte Spalte in einem Resultset nicht signiert ist.  
  
 [4] Datentypen SQL_DECIMAL und SQL_NUMERIC unterscheiden sich nur hinsichtlich ihrer Genauigkeit. Die Genauigkeit einer Dezimalzahl (*p*,*s*) ist eine Implementierung definierten Anzahl von Dezimalstellen, die nicht kleiner als *p*, während die Genauigkeit einer numerischen (*p* ,*s*) genau gleich *p*.  
  
 [5] abhängig von der Implementierung, kann die Genauigkeit der SQL_FLOAT 24 oder 53 sein: Wenn es sich um 24 ist, der Datentyp SQL_FLOAT entspricht SQL_REAL; Wenn sie auf "53" ist, ist die SQL_FLOAT-Datentyp SQL_DOUBLE identisch.  
  
 [6] in ODBC 3.*.x*, die SQL-Date, Time und Timestamp-Datentypen sind SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP, in ODBC 2. *X*, sind die Datentypen, SQL_DATE, SQL_TIME und SQL_TIMESTAMP.  
  
 [7] Weitere Informationen zu den Intervall SQL-Datentypen finden Sie unter den [Interval-Datentypen](../../../odbc/reference/appendixes/interval-data-types.md) weiter unten in diesem Anhang.  
  
 [8] Datentyp SQL_BIT weist unterschiedliche Eigenschaften als der BIT-Typ in SQL-92.  
  
 [9] dieser Datentyp hat keine entsprechenden Daten in SQL-92.  
  
 Dieser Abschnitt enthält das folgende Beispiel.  
  
-   [Example SQLGetTypeInfo Result Set (Beispielergebnis des SQLGetTypeInfo-Resultsets)](../../../odbc/reference/appendixes/example-sqlgettypeinfo-result-set.md)
