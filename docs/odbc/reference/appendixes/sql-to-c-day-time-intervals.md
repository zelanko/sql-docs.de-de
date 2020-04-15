---
title: 'SQL zu C: Day-Time-Intervalle | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1318da5285ba2384dd23e4c235e698aa72c7658e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296470"
---
# <a name="sql-to-c-day-time-intervals"></a>SQL zu C: Tag-Uhrzeit-Intervalle

Die Bezeichner für das Tagesintervall ODBC SQL-Datentypen lauten wie folgt:

- SQL_INTERVAL_DAY
- SQL_INTERVAL_DAY_TO_MINUTE
- SQL_INTERVAL_HOUR
- SQL_INTERVAL_DAY_TO_SECOND
- SQL_INTERVAL_MINUTE
- SQL_INTERVAL_HOUR_TO_MINUTE
- SQL_INTERVAL_SECOND
- SQL_INTERVAL_HOUR_TO_SECOND
- SQL_INTERVAL_DAY_TO_HOUR
- SQL_INTERVAL_MINUTE_TO_SECOND

Die folgende Tabelle zeigt die ODBC C-Datentypen, in die Tagesintervall-SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).

|C-Typ-Idonid|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Alle Tages-C-Intervalltypen|Trailing-Felder-Teil nicht abgeschnitten<br /><br /> Trailing-Felder-Teil abgeschnitten<br /><br /> Führende Genauigkeit des Ziels ist nicht groß genug, um Daten aus der Quelle zu halten|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b] SQL_C_UTINYINT[b] SQL_C_USHORT[b] SQL_C_SHORT[b] SQL_C_SLONG[b] SQL_C_ULONG[b] SQL_C_NUMERIC[b] SQL_C_BIGINT[b]|Intervallgenauigkeit war ein einzelnes Feld und die Daten wurden ohne Abschneide konvertiert<br /><br /> Intervallgenauigkeit war ein einzelnes Feld und abgeschnittene<br /><br /> Intervallgenauigkeit war ein einzelnes Feld und abgeschnitten<br /><br /> Intervallgenauigkeit war kein einzelnes Feld|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Länge der Daten<br /><br /> Länge der Daten<br /><br /> Größe des Datentyps C|–<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_CHAR|Zeichenbytelänge < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu bruchstückhzu- ) Ziffern < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu fraktionierten) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Größe des Datentyps C<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichenlänge < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu bruchstückhzu- ) Ziffern < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu fraktionierten) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Größe des Datentyps C<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
  
 [a] Ein SQL-Typ für das Tagesintervall kann in einen beliebigen Day-Time-Intervall-C-Typ konvertiert werden.  
  
 [b] Wenn es sich bei der Intervallgenauigkeit um ein einzelnes Feld handelt (eines von DAY, HOUR, MINUTE oder SECOND), kann der INTERVALL-SQL-Typ in eine beliebige numerische (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) konvertiert werden.  
  
Die Standardkonvertierung eines Intervall-SQL-Typs ist der entsprechende C-Intervalldatentyp. Die Anwendung bindet dann die Spalte oder den Parameter (oder legt das SQL_DESC_DATA_PTR Feld im entsprechenden Datensatz der ARD fest), um auf die initialisierte SQL_INTERVAL_STRUCT-Struktur zu verweisen (oder übergibt einen Zeiger an die SQL_ INTERVAL_STRUCT Struktur als *TargetValuePtr-Argument* in einem Aufruf von **SQLGetData**).  
  
Im folgenden Beispiel wird veranschaulicht, wie Daten aus einer Spalte vom Typ SQL_INTERVAL_DAY_TO_MINUTE in die SQL_INTERVAL_STRUCT Struktur übertragen werden, sodass sie als DAY_TO_HOUR Intervall zurückkommt.  

```cpp
SQL_INTERVAL_STRUCT is;  
SQLINTEGER    cbValue;  
SQLUINTEGER   days, hours;  
  
// Execute a select statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &is, sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Fetch  
SQLFetch(hstmt);  
  
// Process data  
days = is.intval.day_second.day;  
hours = is.intval.day_second.hour;  
```
