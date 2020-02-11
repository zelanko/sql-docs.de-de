---
title: C-Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9fe4383e397c0fd06197be2ff25e6dbb876f6c0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037772"
---
# <a name="c-data-types"></a>C-Datentypen
ODBC C-Datentypen geben den Datentyp von c-Puffern an, die zum Speichern von Daten in der Anwendung verwendet werden.  
  
 Alle Treiber müssen alle C-Datentypen unterstützen. Dies ist erforderlich, da alle Treiber alle C-Typen unterstützen müssen, für die SQL-Typen, die Sie unterstützen, konvertiert werden können, und alle Treiber unterstützen mindestens einen SQL-Datentyp. Da der SQL-Typ der Zeichenfolge in und aus allen c-Typen konvertiert werden kann, müssen alle-Treiber alle c-Typen unterstützen.  
  
 Der C-Datentyp wird in den Funktionen **SQLBindCol** und **SQLGetData** mit dem *TargetType* -Argument und in der **SQLBindParameter** -Funktion mit dem *ValueType* -Argument angegeben. Sie kann auch durch Aufrufen von **SQLSetDescField** angegeben werden, um das SQL_DESC_CONCISE_TYPE-Feld einer ARD oder APD festzulegen, oder durch Aufrufen von **SQLSetDescRec** mit dem *Typargument* (und ggf. mit dem *subtypargument* ) und dem *Deskriptorhandle* -Argument, das auf das Handle einer ARD oder APD festgelegt ist.  
  
 In den folgenden Tabellen sind gültige Typbezeichner für die C-Datentypen aufgeführt. In der Tabelle wird auch der ODBC-C-Datentyp aufgelistet, der den einzelnen Bezeichnern und der Definition dieses Datentyps entspricht.  
  
|C-Typbezeichner|ODBC C-Typedef|C-Typ|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR|wchar_t *|  
|SQL_C_SSHORT [j]|SQLSMALLINT|short int|  
|SQL_C_USHORT [j]|Sqlusmallint|Ganzzahl ohne Vorzeichen short int|  
|SQL_C_SLONG [j]|SQLINTEGER|long int|  
|SQL_C_ULONG [j]|SQLUINTEGER|Ganzzahl ohne Vorzeichen long int|  
|SQL_C_FLOAT|Sqlreal|float|  
|SQL_C_DOUBLE|SqlDouble, sqlfloat|double|  
|SQL_C_BIT|SQLCHAR|Ganzzahl ohne Vorzeichen Char|  
|SQL_C_STINYINT [j]|Sqlschar|char mit Vorzeichen|  
|SQL_C_UTINYINT [j]|SQLCHAR|Ganzzahl ohne Vorzeichen Char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64 [h]|  
|SQL_C_UBIGINT|Sqlubigint|Ganzzahl ohne Vorzeichen _int64 [h]|  
|SQL_C_BINARY|SQLCHAR|unsigned char *|  
|SQL_C_BOOKMARK [i]|Lesezeichen|Ganzzahl ohne Vorzeichen long int [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|  
|Alle C-Intervall Datentypen|SQL_INTERVAL_STRUCT|Weitere Informationen finden Sie weiter unten in diesem Anhang im Abschnitt [C Interval Structure](../../../odbc/reference/appendixes/c-interval-structure.md) .|  
  
 **C-Typbezeichner** SQL_C_TYPE_DATE [C]  
  
 **ODBC C-Typedef** SQL_DATE_STRUCT  
  
 **C-Typ**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **C-Typbezeichner** SQL_C_TYPE_TIME [C]  
  
 **ODBC C-Typedef** SQL_TIME_STRUCT  
  
 **C-Typ**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **C-Typbezeichner** SQL_C_TYPE_TIMESTAMP [C]  
  
 **ODBC C-Typedef** SQL_TIMESTAMP_STRUCT  
  
 **C-Typ**  
  
```  
struct tagTIMESTAMP_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;[b]   
} TIMESTAMP_STRUCT;[a]  
```  
  
 **C-Typbezeichner** SQL_C_NUMERIC  
  
 **ODBC C-Typedef** SQL_NUMERIC_STRUCT  
  
 **C-Typ**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **C-Typbezeichner** SQL_C_GUID  
  
 **ODBC C-Typedef** SqlGuid  
  
 **C-Typ**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] die Werte der Felder Jahr, Monat, Tag, Stunde, Minute und Sekunde in den DateTime-C-Datentypen müssen den Einschränkungen des gregorianischen Kalenders entsprechen. (Weitere Informationen finden Sie unter [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) weiter unten in diesem Anhang.)  
  
 [b] der Wert des bruchfelds ist die Anzahl von Milliardstel einer Sekunde und liegt zwischen 0 und 999.999.999 (1 kleiner als 1 Milliarde). Beispielsweise ist der Wert des bruchfelds für eine Halbsekunde 500 Millionen, für einen Tausendstel einer Sekunde (eine Millisekunde) 1 Million, für eine Millionstel Sekunde (eine Mikrosekunde) 1.000 und für einen Milliardstel einer Sekunde (eine Nanosekunde) 1.  
  
 [c] in ODBC 2. *x*, die Datums-, Uhrzeit-und Zeitstempel Datentypen von C sind SQL_C_DATE, SQL_C_TIME und SQL_C_TIMESTAMP.  
  
 [d] ODBC 3 *. x* -Anwendungen sollten SQL_C_VARBOOKMARK verwenden, nicht SQL_C_BOOKMARK. Wenn eine ODBC 3 *. x* -Anwendung mit einem ODBC 2 funktioniert. *x* -Treiber, der ODBC 3 *. x* -Treiber-Manager wird SQL_C_VARBOOKMARK SQL_C_BOOKMARK zugeordnet.  
  
 [e] eine Zahl wird im *Val* -Feld der SQL_NUMERIC_STRUCT Struktur als eine skalierte Ganzzahl im Little-Endian-Modus gespeichert (das äußteste Byte ist das am wenigsten signifikante Byte). Beispielsweise wird die Zahl 10,001 Basis 10 mit einer Skala von 4 auf eine ganze Zahl von 100010 skaliert. Da dies 186AA im Hexadezimal Format ist, lautet der Wert in SQL_NUMERIC_STRUCT "AA 86 01 00 00... 00 ", mit der Anzahl der Bytes, die vom SQL_MAX_NUMERIC_LEN **#define**definiert werden.  
  
 Weitere Informationen zu **SQL_NUMERIC_STRUCT**finden Sie unter " [HOWTO: Abrufen numerischer Daten mit SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] die Genauigkeits-und Skalierungs Felder des SQL_C_NUMERIC Datentyps, der für die Eingabe aus einer Anwendung und für die Ausgabe des Treibers an die Anwendung analysiert wird. Wenn der Treiber einen numerischen Wert in den SQL_NUMERIC_STRUCT schreibt, verwendet er seinen eigenen treiberspezifischen Standardwert als Wert für das *Genauigkeits* Feld und verwendet den Wert im Feld SQL_DESC_SCALE des Anwendungs Deskriptors (standardmäßig 0) für das Feld *skalieren* . Eine Anwendung kann Ihre eigenen Werte für Genauigkeit und Skalierung bereitstellen, indem Sie die Felder SQL_DESC_PRECISION und SQL_DESC_SCALE des Anwendungs Deskriptors festlegt.  
  
 [g] das Vorzeichen Feld ist 1, wenn es positiv ist, 0, wenn es negativ ist.  
  
 [h] _int64 von einigen Compilern möglicherweise nicht bereitgestellt.  
  
 [i] _SQL_C_BOOKMARK in ODBC 3 *. x*als veraltet markiert.  
  
 [j] _SQL_C_SHORT, SQL_C_LONG und SQL_C_TINYINT wurden in ODBC durch signierte und nicht signierte Typen ersetzt: SQL_C_SSHORT und SQL_C_USHORT, SQL_C_SLONG und SQL_C_ULONG sowie SQL_C_STINYINT und SQL_C_UTINYINT. Ein ODBC 3 *. x* -Treiber, der mit ODBC 2 funktionieren sollte. *x* -Anwendungen sollten SQL_C_SHORT, SQL_C_LONG und SQL_C_TINYINT unterstützen, denn wenn Sie aufgerufen werden, übergibt der Treiber-Manager Sie an den Treiber.  
  
 [k] SQL_C_GUID kann nur in SQL_CHAR oder SQL_WCHAR konvertiert werden.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [64-Bit-Integerstrukturen](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
