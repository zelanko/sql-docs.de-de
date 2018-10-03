---
title: 'SQL to C: Day-Time-Intervallen SQL | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5e6629ca60201d701eab3c487e68cb4faad04087
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776358"
---
# <a name="sql-to-c-day-time-intervals"></a>SQL zu C: Tag-Uhrzeit-Intervalle
Der Bezeichner für die Tag-Zeitintervall ODBC-SQL-Datentypen sind:  
  
 SQL_INTERVAL_DAY  
  
 SQL_INTERVAL_DAY_TO_MINUTE  
  
 SQL_INTERVAL_HOUR  
  
 SQL_INTERVAL_DAY_TO_SECOND  
  
 SQL_INTERVAL_MINUTE  
  
 SQL_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_INTERVAL_SECOND  
  
 SQL_INTERVAL_HOUR_TO_SECOND  
  
 SQL_INTERVAL_DAY_TO_HOUR  
  
 SQL_INTERVAL_MINUTE_TO_SECOND  
  
 Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in denen Tag-Zeitintervall SQL-Daten konvertiert werden kann. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-ID|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Alle Day-Time-C-Intervall-Typen|Nachfolgende Felder Teil nicht abgeschnitten<br /><br /> Nachfolgende Felder Teil abgeschnitten<br /><br /> Die führende Genauigkeit des Ziels ist nicht groß genug zum Speichern von Daten aus der Quelle|data<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 01 S 07<br /><br /> 22015|  
|SQL_C_STINYINT [b] SQL_C_UTINYINT [b] SQL_C_USHORT [b] SQL_C_SHORT [b] SQL_C_SLONG [b] SQL_C_ULONG [b] SQL_C_NUMERIC [b] SQL_C_BIGINT [b]|Intervall-Genauigkeit wurde ein einzelnes Feld aus, und die Daten ohne Abschneiden konvertiert wurde<br /><br /> Intervall-Genauigkeit wurde von einem einzelnen Feld und die Sekundenbruchteile abgeschnitten<br /><br /> Intervall-Genauigkeit wurde ein einzelnes Feld und das gesamte abgeschnittene<br /><br /> Intervall-Genauigkeit war kein einzelnes Feld|data<br /><br /> Abgeschnittene Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Länge der Daten<br /><br /> Länge der Daten<br /><br /> Anzahl der C-Datentyp|–<br /><br /> 01 S 07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Die Bytelänge der Daten < = *Pufferlänge*<br /><br /> Die Bytelänge der Daten > *Pufferlänge*|data<br /><br /> Nicht definiert|Länge der Daten<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_CHAR|Zeichen-Byte-Länge < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) > = *Pufferlänge*|data<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Anzahl der C-Datentyp<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
_C_WCHAR|Zeichenlänge < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) < *Pufferlänge*<br /><br /> Anzahl von Ziffern für ganze (im Gegensatz zu Bruch) > = *Pufferlänge*|data<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Anzahl der C-Datentyp<br /><br /> Anzahl der C-Datentyp<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
  
 [a] A Day-Time-Intervall SQL-Typ kann zu einem beliebigen Tag-Zeitintervall C-Typ konvertiert werden.  
  
 [b] Wenn das Intervall ein einzelnes Feld (eine der Tag, Stunde, MINUTE oder Sekunde) übersteigt, kann das Intervall SQL-Typ in genauer numerischer Wert (SQL_C_STINYINT SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) konvertiert werden.  
  
 Die standardkonvertierung eines Intervalls SQL-Typ ist in den Datentyp der entsprechenden C-Intervall. Die Anwendung dann bindet die Spalte oder des Parameters (oder legt das SQL_DESC_DATA_PTR-Feld in den entsprechenden Datensatz der ARD), zeigen Sie auf die initialisierte SQL_INTERVAL_STRUCT-Struktur (oder übergibt einen Zeiger auf die SQL_ INTERVAL_STRUCT-Struktur wie die *TargetValuePtr* Argument in einem Aufruf von **SQLGetData**).  
  
 Im folgende Beispiel wird veranschaulicht, wie Daten aus einer Spalte vom Typ SQL_INTERVAL_DAY_TO_MINUTE in die Struktur SQL_INTERVAL_STRUCT übertragen wird, so, dass es wieder als Intervall DAY_TO_HOUR verfügbar ist.  
  
```  
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
