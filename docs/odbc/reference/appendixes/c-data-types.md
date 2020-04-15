---
title: C Datentypen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 979bfe85e1e78b55718e1f12fdcfcc7583097bb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292300"
---
# <a name="c-data-types"></a>C-Datentypen
ODBC C-Datentypen geben den Datentyp von C-Puffern an, die zum Speichern von Daten in der Anwendung verwendet werden.  
  
 Alle Treiber müssen alle C-Datentypen unterstützen. Dies ist erforderlich, da alle Treiber alle C-Typen unterstützen müssen, in die die unterstützten SQL-Typen konvertiert werden können, und alle Treiber mindestens einen SQL-Zeichentyp unterstützen. Da der SQL-Zeichentyp in und von allen C-Typen konvertiert werden kann, müssen alle Treiber alle C-Typen unterstützen.  
  
 Der C-Datentyp wird in den Funktionen **SQLBindCol** und **SQLGetData** mit dem *TargetType-Argument* und in der **SQLBindParameter-Funktion** mit dem *Argument ValueType* angegeben. Es kann auch durch Aufrufen von **SQLSetDescField** angegeben werden, um das SQL_DESC_CONCISE_TYPE Feld einer ARD oder APD festzulegen, oder indem **SQLSetDescRec** mit dem *Type-Argument* (und ggf. dem *SubType-Argument)* und dem *DescriptorHandle-Argument* aufgerufen wird, das auf das Handle einer ARD oder APD festgelegt ist.  
  
 In den folgenden Tabellen sind gültige Typbezeichner für die C-Datentypen aufgeführt. In der Tabelle wird auch der ODBC C-Datentyp aufgeführt, der jedem Bezeichner entspricht, sowie die Definition dieses Datentyps.  
  
|C-Typ-Idonid|ODBC C typdef|C-Typ|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR *|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR *|wchar_t *|  
|SQL_C_SSHORT[j]|SQLSMALLINT|short int|  
|SQL_C_USHORT[j]|SQLUSMALLINT|unsigned short int|  
|SQL_C_SLONG[j]|SQLINTEGER|long int|  
|SQL_C_ULONG[j]|SQLUINTEGER|unsigned long int|  
|SQL_C_FLOAT|SQLREAL|float|  
|SQL_C_DOUBLE|SQLDOUBLE, SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|unsigned char|  
|SQL_C_STINYINT[j]|SQLSCHAR|char mit Vorzeichen|  
|SQL_C_UTINYINT[j]|SQLCHAR|unsigned char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64[h]|  
|SQL_C_UBIGINT|SQLUBIGINT|unsigniert _int64[h]|  
|SQL_C_BINARY|SQLCHAR *|unsigned char *|  
|SQL_C_BOOKMARK[i]|Lesezeichen|unsigniert lange int[d]|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|  
|Alle C-Intervalldatentypen|SQL_INTERVAL_STRUCT|Siehe Abschnitt [C-Intervallstruktur](../../../odbc/reference/appendixes/c-interval-structure.md) weiter unten in diesem Anhang.|  
  
 **C-Typ-Idonid** SQL_C_TYPE_DATE[c]  
  
 **ODBC C typdef** SQL_DATE_STRUCT  
  
 **C-Typ**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **C-Typ-Idonid** SQL_C_TYPE_TIME[c]  
  
 **ODBC C typdef** SQL_TIME_STRUCT  
  
 **C-Typ**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **C-Typ-Idonid** SQL_C_TYPE_TIMESTAMP[c]  
  
 **ODBC C typdef** SQL_TIMESTAMP_STRUCT  
  
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
  
 **C-Typ-Idonid** SQL_C_NUMERIC  
  
 **ODBC C typdef** SQL_NUMERIC_STRUCT  
  
 **C-Typ**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **C-Typ-Idonid** SQL_C_GUID  
  
 **ODBC C typdef** Sqlguid  
  
 **C-Typ**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] Die Werte des Jahres,Monats, Tages, der Stunde, der Minute und des zweiten Feldes in den Datentypen datetime C müssen den Einschränkungen des Gregorianischen Kalenders entsprechen. (Siehe [Einschränkungen des Gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) weiter unten in diesem Anhang.)  
  
 [b] Der Wert des Bruchfeldes ist die Anzahl der Millimillistelen einer Sekunde und reicht von 0 bis 999.999.999 (1 weniger als 1 Milliarde). Zum Beispiel beträgt der Wert des Fraktionsfeldes für eine halbe Sekunde 500.000.000, für eine Tausendstelsekunde (eine Millisekunde) 1.000.000, für eine Millionstelsekunde (eine Mikrosekunde) 1.000 und für eine Millimillidstel Sekunde (eine Nanosekunde) 1.  
  
 [c] In ODBC 2. *x*, die Datentypen C-Datum, Uhrzeit und Zeitstempel sind SQL_C_DATE, SQL_C_TIME und SQL_C_TIMESTAMP.  
  
 [d] ODBC 3 *.x-Anwendungen* sollten SQL_C_VARBOOKMARK verwenden, nicht SQL_C_BOOKMARK. Wenn eine ODBC 3 *.x-Anwendung* mit einer ODBC 2 funktioniert. *x-Treiber,* der ODBC 3 *.x* Driver Manager wird SQL_C_VARBOOKMARK SQL_C_BOOKMARK zuordnen.  
  
 [e] Eine Zahl wird im *Valfeld* der SQL_NUMERIC_STRUCT Struktur als skalierte ganze Zahl im kleinen Endian-Modus gespeichert (das linke byte ist das am wenigsten signifikante Byte). Beispielsweise wird die Zahl 10.001 Basis 10 mit einer Skala von 4 auf eine ganze Zahl von 100010 skaliert. Da dies 186AA im hexadezimalen Format ist, wäre der Wert in SQL_NUMERIC_STRUCT "AA 86 01 00 00 ... 00", mit der Anzahl der Bytes, die vom SQL_MAX_NUMERIC_LEN **#define**definiert werden.  
  
 Weitere Informationen **zu SQL_NUMERIC_STRUCT**finden Sie unter [HOWTO: Abrufen numerischer Daten mit SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] Die Präzisions- und Skalierungsfelder des SQL_C_NUMERIC Datentyps werden für die Eingabe aus einer Anwendung und für die Ausgabe vom Treiber an die Anwendung verwendet. Wenn der Treiber einen numerischen Wert in die SQL_NUMERIC_STRUCT schreibt, verwendet er einen eigenen treiberspezifischen Standardwert als Wert für das *Genauigkeitsfeld* und verwendet den Wert im SQL_DESC_SCALE Feld des Anwendungsdeskriptors (der standardmäßig 0) für das *Maßstabsfeld* verwendet. Eine Anwendung kann ihre eigenen Werte für Genauigkeit und Skalierung bereitstellen, indem sie die SQL_DESC_PRECISION- und SQL_DESC_SCALE Felder des Anwendungsdeskriptors festlegt.  
  
 [g] Das Vorzeichenfeld ist 1, wenn positiv, 0, wenn negativ.  
  
 [h] _int64 werden möglicherweise nicht von einigen Compilern bereitgestellt.  
  
 [i] _SQL_C_BOOKMARK wurde in ODBC 3 *.x*veraltet.  
  
 [j] _SQL_C_SHORT, SQL_C_LONG und SQL_C_TINYINT wurden in ODBC durch signierte und nicht signierte Typen ersetzt: SQL_C_SSHORT und SQL_C_USHORT, SQL_C_SLONG und SQL_C_ULONG sowie SQL_C_STINYINT und SQL_C_UTINYINT. Ein ODBC 3 *.x* Treiber, der mit ODBC 2 funktionieren sollte. *x-Anwendungen* sollten SQL_C_SHORT, SQL_C_LONG und SQL_C_TINYINT unterstützen, da sie, wenn sie aufgerufen werden, vom Treiber-Manager an den Treiber weiterleitet.  
  
 [k] SQL_C_GUID kann nur in SQL_CHAR oder SQL_WCHAR konvertiert werden.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [64-Bit-Ganzzahl-Strukturen](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
