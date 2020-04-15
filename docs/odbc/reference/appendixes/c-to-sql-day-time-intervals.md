---
title: 'C zu SQL: Day-Time-Intervalle | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c3f7efb443b442d44a94cfd43629cdaedd6195b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291920"
---
# <a name="c-to-sql-day-time-intervals"></a>C zu SQL: Tag-Uhrzeit-Intervalle
Die Bezeichner für das Tagesintervall ODBC C-Datentypen sind:  
  
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
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die Intervall C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|Spaltenbytelänge >= Zeichenbytelänge<br /><br /> Spaltenbytelänge < Zeichenbytelänge[a]<br /><br /> Der Datenwert ist kein gültiges Intervallliteral|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|Spaltenzeichenlänge >= Zeichenlänge der Daten<br /><br /> Spaltenzeichenlänge < Zeichenlänge der Daten[a]<br /><br /> Der Datenwert ist kein gültiges Intervallliteral|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b] SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b] SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|Die Konvertierung eines Einfeldintervalls hat nicht dazu geführt, dass ganze Ziffern abgeschnitten wurden.<br /><br /> Konvertierung führte zum Abschneiden ganzer Ziffern|–<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|Der Datenwert wurde ohne Abschneiden von Feldern konvertiert.<br /><br /> Mindestens ein Datenwertfeld wurde während der Konvertierung abgeschnitten|–<br /><br /> 22015|  
  
 [a] Alle C-Intervalldatentypen können in einen Zeichendatentyp konvertiert werden.  
  
 [b] Wenn das Typfeld in der Intervallstruktur so ist, dass das Intervall ein einzelnes Feld ist (SQL_DAY, SQL_HOUR, SQL_MINUTE oder SQL_SECOND), kann der Intervall-C-Typ in eine beliebige exakte Numerische (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL oder SQL_NUMERIC) konvertiert werden.  
  
 Die Standardkonvertierung eines Intervall-C-Typs ist der entsprechende Sql-Typ für das Tagesintervall SQL.  
  
 Der Treiber ignoriert den Längen-/Indikatorwert beim Konvertieren von Daten aus dem Intervall-C-Datentyp und geht davon aus, dass die Größe des Datenpuffers die Größe des Intervall-C-Datentyps ist. Der Längen-/Indikatorwert wird im *Argument StrLen_or_Ind* in **SQLPutData** und im Puffer übergeben, der mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben ist. Der Datenpuffer wird mit dem *DataPtr-Argument* in **SQLPutData** und dem *ParameterValuePtr-Argument* in **SQLBindParameter**angegeben.  
  
 Im folgenden Beispiel wird veranschaulicht, wie Intervall-C-Daten, die in der SQL_INTERVAL_STRUCT-Struktur gespeichert sind, in eine Datenbankspalte gesendet werden. Die Intervallstruktur enthält ein DAY_TO_SECOND Intervall. Sie wird in einer Datenbankspalte vom Typ SQL_INTERVAL_DAY_TO_MINUTE gespeichert.  
  
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
