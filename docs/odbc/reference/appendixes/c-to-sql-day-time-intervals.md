---
title: 'C to SQL: Day-Time-Intervallen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb41d658637258c6d60b5adb4e0d7abb9ae81d91
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757658"
---
# <a name="c-to-sql-day-time-intervals"></a>C zu SQL: Tag-Uhrzeit-Intervalle
Der Bezeichner für die Tag-Zeitintervall ODBC C-Datentypen sind:  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen in denen Intervall C-Daten konvertiert werden kann. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR [a]<br /><br /> SQL_LONGVARCHAR [a]|Spalte-Byte-Länge > = Zeichen-Byte-Länge<br /><br /> Byte-Länge der Spalte < Zeichen Länge in Byte [a]<br /><br /> Datenwert ist es sich nicht um ein gültiges Intervall-Literale|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Spalte Zeichenlänge > = Zeichenlänge der Daten<br /><br /> Spaltenlänge für die Zeichen < Zeichen Länge der Daten [a]<br /><br /> Datenwert ist es sich nicht um ein gültiges Intervall-Literale|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b] SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b] SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Konvertierung von einem Intervall von einem einzigen Feld führten nicht Abschneiden von ganzen Zahlen<br /><br /> Konvertierung führte Abschneiden von ganzen Zahlen|–<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|Der Datenwert wurde ohne Abschneiden von Feldern konvertiert.<br /><br /> Ein oder mehrere Felder der Datenwert wurde während der Konvertierung abgeschnitten.|–<br /><br /> 22015|  
  
 [a] alle C-Interval-Datentypen können in einen Zeichendatentyp konvertiert werden.  
  
 [b] ist das Typfeld in die Intervall-Struktur, für die das Intervall ein einzelnes Feld (SQL_DAY SQL_HOUR, SQL_MINUTE oder SQL_SECOND) entspricht, kann das Intervall C-Typ in jedem genauer numerischer Wert (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT konvertiert werden SQL_DECIMAL oder SQL_NUMERIC).  
  
 Die standardkonvertierung von C Intervalltyp werden das entsprechende Tag-Zeitintervall SQL-Typ ab.  
  
 Der Treiber ignoriert den Längenindikator /-Wert, bei der Konvertierung von Daten aus dem Intervall C-Datentyp, und es wird davon ausgegangen, dass die Größe des Datenpuffers die Größe des Datentyps Interval C. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.  
  
 Im folgenden Beispiel wird veranschaulicht, wie zum Senden von C Intervalldaten, die in der SQL_INTERVAL_STRUCT-Struktur in eine Datenbankspalte gespeichert wird. Die Intervall-Struktur, ein Intervall DAY_TO_SECOND enthält; Es wird in einer Datenbankspalte vom Typ SQL_INTERVAL_DAY_TO_MINUTE gespeichert werden.  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
