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
manager: craigg
ms.openlocfilehash: 3f948b50fae0995e16024ac41d8dd891630d1dbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62447539"
---
# <a name="c-data-types"></a>C-Datentypen
ODBC C-Datentypen anzugeben, den den Datentyp des C-Puffer zum Speichern von Daten in der Anwendung verwendet wird.  
  
 Alle Treiber müssen alle C-Datentypen unterstützen. Dies ist erforderlich, da alle Treiber alle C-Typen unterstützen müssen, die in denen SQL-Typen, die sie unterstützen konvertiert werden können, und alle Treiber unterstützen mindestens ein Zeichen SQL-Typ. Da der SQL-Zeichentyp in und aus allen C-Datentypen konvertiert werden kann, müssen alle Treiber alle C-Typen unterstützt.  
  
 Die C-Datentyp angegeben ist, der **SQLBindCol** und **SQLGetData** funktioniert mit der die *TargetType* Argument und der **SQLBindParameter**-Funktion mit den *ValueType* Argument. Es kann auch durch den Aufruf angegeben werden **SQLSetDescField** festzulegende Feld SQL_DESC_CONCISE_TYPE eines ARD oder APD, oder durch Aufrufen von **SQLSetDescRec** mit der *Typ* Argument (und die *Untertyp* Argument, falls erforderlich) und die *DescriptorHandle* Argument festgelegt wird, auf das Handle eines ARD oder APD.  
  
 Die folgenden Tabellen Listen gültiger Typenbezeichner für die C-Datentypen. Die Tabelle enthält auch den ODBC-C-Datentyp, der jeden Bezeichner und der Definition dieser Datentyp entspricht.  
  
|C-Typ-ID|ODBC-C-Typdefinition|C-Typ|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR *|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR *|wchar_t *|  
|SQL_C_SSHORT[j]|SQLSMALLINT|short int|  
|SQL_C_USHORT[j]|SQLUSMALLINT|kurze ganze Zahl ohne Vorzeichen|  
|SQL_C_SLONG[j]|SQLINTEGER|Long int|  
|SQL_C_ULONG[j]|SQLUINTEGER|lange ganze Zahl ohne Vorzeichen|  
|SQL_C_FLOAT|SQLREAL|FLOAT|  
|SQL_C_DOUBLE|SQLDOUBLE, SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|ohne Vorzeichen|  
|SQL_C_STINYINT[j]|SQLSCHAR|Char mit Vorzeichen|  
|SQL_C_UTINYINT[j]|SQLCHAR|ohne Vorzeichen|  
|SQL_C_SBIGINT|SQLBIGINT|_int64[h]|  
|SQL_C_UBIGINT|SQLUBIGINT|unsigned __int64 [h]|  
|SQL_C_BINARY|SQLCHAR *|unsigned char *|  
|SQL_C_BOOKMARK[i]|LESEZEICHEN|lange ganze Zahl ohne Vorzeichen [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|  
|Alle Datentypen der C-Intervall|SQL_INTERVAL_STRUCT|Finden Sie unter den [C-Intervall-Struktur](../../../odbc/reference/appendixes/c-interval-structure.md) weiter unten in diesem Anhang.|  
  
 **C-Typ-ID** SQL_C_TYPE_DATE [c]  
  
 **ODBC-C-Typdefinition** SQL_DATE_STRUCT  
  
 **C-Typ**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **C-Typ-ID** SQL_C_TYPE_TIME [c]  
  
 **ODBC-C-Typdefinition** SQL_TIME_STRUCT  
  
 **C-Typ**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **C-Typ-ID** SQL_C_TYPE_TIMESTAMP [c]  
  
 **ODBC-C-Typdefinition** SQL_TIMESTAMP_STRUCT  
  
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
  
 **C-Typ-ID** SQL_C_NUMERIC  
  
 **ODBC-C-Typdefinition** SQL_NUMERIC_STRUCT  
  
 **C-Typ**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **C-Typ-ID** SQL_C_GUID  
  
 **ODBC-C-Typdefinition** SQLGUID  
  
 **C-Typ**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] die Werte der Jahr, Monat, Tag, Stunde, Minute und Sekunde Felder in den Datentypen "DateTime" C müssen den Einschränkungen des gregorianischen Kalenders entsprechen. (Finden Sie unter [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) weiter unten in diesem Anhang.)  
  
 [b] der Wert des Felds Bruchzahl ist die Anzahl der milliardste Teil einer Sekunde und reicht von 0 bis 999.999.999 (1 weniger als 1 Milliarde). Beispielsweise ist der Wert des Felds "Fraction" für eine halbe Sekunde 500,000,000, für die ein Tausendstel einer Sekunde (eine Millisekunde) beträgt 1.000.000 übersteigen, die für ein Millionstel einer Sekunde (einer Mikrosekunde) ist 1000, und eine den milliardsten Teil eine Sekunde (einer Nanosekunde) ist 1.  
  
 [c] in ODBC 2. *x*, die C-Date, Time und Timestamp-Datentypen sind SQL_C_DATE, SQL_C_TIME und SQL_C_TIMESTAMP.  
  
 [d] ODBC 3 *.x* SQL_C_VARBOOKMARK, nicht SQL_C_BOOKMARK sollte von Anwendungen verwendet. Wenn eine ODBC 3 *.x* Anwendung funktioniert mit einer ODBC 2.*x* -Treiber verwenden, die ODBC 3 *.x* -Treiber-Manager SQL_C_BOOKMARK SQL_C_VARBOOKMARK zugeordnet.  
  
 [e] eine Anzahl befindet sich in der *Val* -Feld der Struktur SQL_NUMERIC_STRUCT als skaliert eine ganze Zahl im little-endian-Modus (das am weitesten links stehende Byte das niederwertigste Byte). Beispielsweise wird die Anzahl 10,001 Basis 10, mit einer Skala von 4, in eine ganze Zahl von 100010 skaliert. Da dies 186AA im Hexadezimalformat angegeben ist, wäre der Wert in SQL_NUMERIC_STRUCT "AA 86 01 00 00... 00", mit der Anzahl von Bytes, die durch die SQL_MAX_NUMERIC_LEN definierten **#define**.  
  
 Weitere Informationen zu **SQL_NUMERIC_STRUCT**, finden Sie unter [so wird's gemacht: Abrufen von numerischen Daten mit SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] Felder für Genauigkeit und Dezimalstellenanzahl SQL_C_NUMERIC Daten geben Areused für die Eingabe aus einer Anwendung und für die Ausgabe aus dem Treiber für die Anwendung. Wenn der Treiber einen numerischen Wert in der SQL_NUMERIC_STRUCT schreibt, verwendet einen eigenen Treiber-spezifische standardmäßig als Wert für die *Genauigkeit* Feld, und es wird verwenden Sie den Wert im Feld SQL_DESC_SCALE von der Anwendung Deskriptor ( Standardwert: 0) für die *Skalierung* Feld. Eine Anwendung kann eigene Werte für Genauigkeit und Dezimalstellen angeben, durch die SQL_DESC_PRECISION und SQL_DESC_SCALE Felder den Anwendungsdienst-Deskriptor.  
  
 [g] das Feld "Anmelden" ist 1, wenn positiv, 0, wenn negative.  
  
 [h] __int64 kann nicht durch einige Compiler bereitgestellt werden.  
  
 [i] _SQL_C_BOOKMARK veraltet in ODBC 3 *.x*.  
  
 [j] _SQL_C_SHORT SQL_C_LONG und SQL_C_TINYINT wurden in ODBC von signierten und nicht signierten Typen ersetzt: SQL_C_SSHORT und SQL_C_USHORT, SQL_C_SLONG und SQL_C_ULONG, und SQL_C_STINYINT und SQL_C_UTINYINT. Eine ODBC 3 *.x* Treiber, die mit ODBC 2. funktionieren sollte.*x* Anwendungen sollten SQL_C_SHORT, SQL_C_LONG und SQL_C_TINYINT, unterstützen, da Wenn sie aufgerufen werden, der Treiber-Manager über an den Treiber übergeben.  
  
 [k] SQL_C_GUID kann nur für SQL_CHAR oder SQL_WCHAR konvertiert werden.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [64-Bit-Ganzzahl-Strukturen](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>Siehe auch  
 [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
